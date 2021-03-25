---
title: Получение локальных свойств | Документация Майкрософт
description: Узнайте, как Visual Studio использует Енумчилдрен для получения локальных свойств с помощью этих примеров для управляемого и неуправляемого кода.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- expression evaluation, getting local properties
- debugging [Debugging SDK], local properties
- expression evaluation, local properties
ms.assetid: 6c3a79e8-1ba1-4863-97c3-0216c3d9f092
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 1be593d14736a6526cc951bbc01460ce7bdb83f4
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105054807"
---
# <a name="get-local-properties"></a>Получить локальные свойства
> [!IMPORTANT]
> В Visual Studio 2015 такой способ реализации оценивающих выражений является устаревшим. Дополнительные сведения о реализации вычислителей выражений CLR см. в разделе средства [оценки выражений CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) и [Пример управляемого средства оценки выражений](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

Visual Studio вызывает [енумчилдрен](../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) для получения объекта [IEnumDebugPropertyInfo2](../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md) , предоставляющего доступ ко всем локальным переменным, отображаемым в окне **локальные** . Затем Visual Studio вызывает [Next](../../extensibility/debugger/reference/ienumdebugpropertyinfo2-next.md) для получения сведений, отображаемых для каждого локального элемента. В этом примере класс `CEnumPropertyInfo` реализует `IEnumDebugPropertyInfo2` интерфейс.

Эта реализация `IEnumDebugPropertyInfo2::Next` выполняет следующие задачи:

1. Очищает массив, в котором хранятся данные.

2. Вызывает [Next](../../extensibility/debugger/reference/ienumdebugfields-next.md) для каждого локального, сохраняя возвращаемый [DEBUG_PROPERTY_INFO](../../extensibility/debugger/reference/debug-property-info.md) в возвращаемом массиве. Объект [иенумдебугфиелдс](../../extensibility/debugger/reference/ienumdebugfields.md) был передан при `CEnumPropertyInfo` создании экземпляра этого класса.

## <a name="managed-code"></a>Управляемый код
В этом примере показана реализация `IEnumDebugPropertyInfo2::EnumChildren` для локальных переменных метода в управляемом коде.

```csharp
namespace EEMC
{
    public class CEnumMethodField : IEnumDebugFields
    {
        public HRESULT Next(
                uint                  count,
                DEBUG_PROPERTY_INFO[] properties,
            out uint                  fetched)
        {
            if (count > properties.Length)
                throw new COMException();

            // Zero out the array.
            for (int i= 0; i < count; i++)
            {
                properties[i].bstrFullName = "";
                properties[i].bstrName = "";
                properties[i].bstrType = "";
                properties[i].bstrValue = "";
                properties[i].dwAttrib = 0;
                properties[i].dwFields = 0;
                properties[i].pProperty = null;
            }
            fetched = 0;

            // COM interop.
            HRESULT hr;
            uint innerFetched;
            IDebugField[] field = new IDebugField[1];

            while (fetched < count)
            {
                field[0] = null;
                innerFetched = 0;

                // Get next field.
                if (fetched < fieldCount)
                    hr = fields.Next(1, field, ref innerFetched);
                // No more fields.
                else return COM.S_FALSE;

                if (hr != COM.S_OK || innerFetched != 1 || field[0] == null)
                    throw new COMException("CEnumPropertyInfo.Next");

                // Get property from field.
                CFieldProperty fieldProperty =
                        new CFieldProperty(provider, address, binder, field[0]);

                DEBUG_PROPERTY_INFO[] property =
                        new DEBUG_PROPERTY_INFO[1];
                fieldProperty.GetPropertyInfo((uint) infoFlags, radix, 0, null, 0, property);
                properties[fetched++] = property[0];
            }
            return COM.S_OK;
        }
    }
}
```

## <a name="unmanaged-code"></a>Неуправляемый код
 В этом примере показана реализация `IEnumDebugPropertyInfo2::EnumChildren` для локальных переменных метода в неуправляемом коде.

```cpp
STDMETHODIMP CEnumPropertyInfo::Next(
    in  ULONG                count,
    out DEBUG_PROPERTY_INFO* pelements,
    out ULONG*               pfetched )
{
    if (pfetched)
        *pfetched = 0;
    if (!pelements)
        return E_INVALIDARG;
    else
        memset( pelements, 0, count * sizeof(DEBUG_PROPERTY_INFO));

    HRESULT hr  = S_OK;
    ULONG   idx = 0;
    while (idx < count)
    {
        ULONG        fetchedFields;
        IDebugField* pfield;

        //get the next field
        hr = m_fields->Next( 1, &pfield, &fetchedFields );
        if (FAILED(hr))
            return hr;
        if (fetchedFields != 1)
            return E_FAIL;
        idx++;

        //create a CFieldProperty to retrieve the DEBUG_PROPERTY_INFO
        CFieldProperty* pproperty =
            new CFieldProperty( m_provider, m_address, m_binder, pfield );
        pfield->Release();
        if (!pproperty)
            return E_OUTOFMEMORY;

        hr = pproperty->Init();
        if (FAILED(hr))
        {
            pproperty->Release();
            return hr;
        }

        hr = pproperty->GetPropertyInfo( m_infoFlags,
                                         m_radix,
                                         0,
                                         NULL,
                                         0,
                                         pelements + idx - 1);
        pproperty->Release();
        if (FAILED(hr))
            return hr;
    }

    if (pfetched)
        *pfetched = idx;
    return hr;
}
```

## <a name="see-also"></a>См. также
- [Пример реализации локальных переменных](../../extensibility/debugger/sample-implementation-of-locals.md)
- [Перечисление локальных переменных](../../extensibility/debugger/enumerating-locals.md)
