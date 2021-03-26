---
title: Перечисление локальных переменных | Документация Майкрософт
description: 'Сведения о том, как Visual Studio использует IDebugProperty2:: Енумчилдрен для заполнения окна локальных переменных.'
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], enumerating locals
- expression evaluation, enumerating locals
ms.assetid: 254a88e7-d3a7-447a-bd0c-8985e73d85cf
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 0acacea8ec19319b7c07ff9d9a549410c57862e0
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105097049"
---
# <a name="enumerate-locals"></a>Перечислить локальные переменные
> [!IMPORTANT]
> В Visual Studio 2015 такой способ реализации оценивающих выражений является устаревшим. Дополнительные сведения о реализации вычислителей выражений CLR см. в разделе средства [оценки выражений CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) и [Пример управляемого средства оценки выражений](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

Когда Visual Studio будет готова заполнить окно **локальных переменных** , оно вызывает [Енумчилдрен](../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) для объекта [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) , возвращаемого из [жетмесодпроперти](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md) (см. [реализацию жетмесодпроперти](../../extensibility/debugger/implementing-getmethodproperty.md)). `IDebugProperty2::EnumChildren` Возвращает объект [IEnumDebugPropertyInfo2](../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md) .

Реализация `IDebugProperty2::EnumChildren` выполняет следующие задачи:

1. Гарантирует, что это представляет собой метод.

2. Использует `guidFilter` аргумент для определения метода, вызываемого для объекта [идебугмесодфиелд](../../extensibility/debugger/reference/idebugmethodfield.md) . Если `guidFilter` равно:

    1. `guidFilterLocals`, вызовите [енумлокалс](../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md) , чтобы получить объект [иенумдебугфиелдс](../../extensibility/debugger/reference/ienumdebugfields.md) .

    2. `guidFilterArgs`, вызовите [енумаргументс](../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md) , чтобы получить `IEnumDebugFields` объект.

    3. `guidFilterLocalsPlusArgs`, синтезирование перечисления, объединяющего результаты из `IDebugMethodField::EnumLocals` и `IDebugMethodField::EnumArguments` . Этот синтез представлен классом `CEnumMethodField` .

3. Создает экземпляр класса (вызываемого `CEnumPropertyInfo` в этом примере), который реализует `IEnumDebugPropertyInfo2` интерфейс и содержит `IEnumDebugFields` объект.

4. Возвращает `IEnumDebugProperty2Info2` интерфейс из `CEnumPropertyInfo` объекта.

## <a name="managed-code"></a>Управляемый код
В этом примере показана реализация `IDebugProperty2::EnumChildren` в управляемом коде.

```csharp
namespace EEMC
{
    public class CFieldProperty : IDebugProperty2
    {
        public HRESULT EnumChildren (
                uint                    dwFields,
                uint                    radix,
            ref Guid                    guidFilter,
                ulong                   attribFilter,
                string                  nameFilter,
                uint                    timeout,
            out IEnumDebugPropertyInfo2 properties)
        {
            properties = null;
            IEnumDebugFields fields = null;

            // If this field is a method...
            if (0 != ((uint) fieldKind & (uint) FIELD_KIND.FIELD_TYPE_METHOD))
            {
                IDebugMethodField methodField = (IDebugMethodField) field;

                // Enumerate parameters.
                if (guidFilter == FilterGuids.guidFilterArgs)
                {
                    methodField.EnumParameters(out fields);
                }
                // Enumerate local variables.
                else if (guidFilter == FilterGuids.guidFilterLocals)
                {
                    methodField.EnumLocals(address, out fields);
                }
                // Enumerate all local variables, including invisible compiler temps.
                else if (guidFilter == FilterGuids.guidFilterAllLocals)
                {
                    methodField.EnumAllLocals(address, out fields);
                }
                // Enumerate "this", if any, and all parameters and local variables.
                else if (guidFilter == FilterGuids.guidFilterLocalsPlusArgs)
                {
                    IDebugClassField fieldThis  = null;
                    IEnumDebugFields parameters = null;
                    IEnumDebugFields locals     = null;

                    methodField.GetThis(out fieldThis);
                    methodField.EnumParameters(out parameters);
                    methodField.EnumLocals(address, out locals);

                    CEnumMethodField enumMethodField =
                        new CEnumMethodField(fieldThis, parameters, locals);
                    fields = (IEnumDebugFields) enumMethodField;
                }
                // Enumerate only "this".
                else if (guidFilter == FilterGuids.guidFilterThis)
                {
                    IDebugClassField fieldThis = null;
                    methodField.GetThis(out fieldThis);

                    CEnumMethodField enumMethodField =
                        new CEnumMethodField(fieldThis, null, null);
                    fields = (IEnumDebugFields) enumMethodField;
                }
                else throw new COMException();// E_FAIL
            }
            // Wrap a property enumerator around the field enumerator.
            CEnumPropertyInfo propertiesInfo =
                new CEnumPropertyInfo(provider, address, binder, radix, fields,
                (DEBUGPROP_INFO_FLAGS) dwFields);

            properties = (IEnumDebugPropertyInfo2) propertiesInfo;
            return COM.S_OK;
        }
    }
}
```

## <a name="unmanaged-code"></a>Неуправляемый код
 В этом примере показана реализация `IDebugProperty2::EnumChildren` в неуправляемом коде.

```cpp
STDMETHODIMP CFieldProperty::EnumChildren(
        in DEBUGPROP_INFO_FLAGS        infoFlags,
        in DWORD                       radix,
        in REFGUID                     guidFilter,
        in DBG_ATTRIB_FLAGS            attribFilter,
        in LPCOLESTR                   pszNameFilter,
        in DWORD                       timeout,
        out IEnumDebugPropertyInfo2 ** ppchildren )
{
    if (ppchildren == NULL)
        return E_INVALIDARG;
    else
        *ppchildren = 0;

    //get enumeration
    HRESULT hr;
    IEnumDebugFields*     pfields    = NULL;

    if (m_fieldKind & FIELD_TYPE_METHOD)
    {
        //-----------------------------------------------------
        // A Method

        IDebugMethodField*  pmethod    = NULL;

        //enumerate the requested properties
        hr = m_field->QueryInterface( IID_IDebugMethodField,
            reinterpret_cast<void**>(&pmethod) );
        if (FAILED(hr))
            return hr;

        if (guidFilter == guidFilterArgs)
        {
            hr = pmethod->EnumParameters( &pfields );
        }
        else if (guidFilter == guidFilterLocals)
        {
            hr = pmethod->EnumLocals( m_address, &pfields );
        }
        else if (guidFilter == guidFilterAllLocals)
        {
            hr = pmethod->EnumAllLocals( m_address, &pfields );
        }
        else if (guidFilter == guidFilterLocalsPlusArgs)
        {
            //we create a special enumerator for this
            IDebugClassField* pfieldThis  = NULL;
            IEnumDebugFields* pparameters = NULL;
            IEnumDebugFields* plocals     = NULL;

            pmethod->GetThis( &pfieldThis );
            pmethod->EnumParameters( &pparameters );
            pmethod->EnumLocals( m_address, &plocals );

            CEnumMethodField* penumMethodField =
                new CEnumMethodField( pfieldThis, pparameters, plocals );
            if (pfieldThis != NULL)
                pfieldThis->Release();
            if (pparameters != NULL)
                pparameters->Release();
            if (plocals != NULL)
                plocals->Release();
            if (!penumMethodField)
            {
                hr = E_OUTOFMEMORY;
            }
            else
            {
                hr = penumMethodField->QueryInterface( IID_IEnumDebugFields,
                        reinterpret_cast<void**>(&pfields) );
                penumMethodField->Release();
            }
        }
        else if (guidFilter == guidFilterThis )
        {
            IDebugClassField* pfieldThis = NULL;

            hr = pmethod->GetThis( &pfieldThis );
            if (SUCCEEDED(hr))
            {
                CEnumMethodField* penumMethodField =
                    new CEnumMethodField( pfieldThis, NULL, NULL );
                pfieldThis->Release();
                if (!penumMethodField)
                {
                    hr = E_OUTOFMEMORY;
                }
                else
                {
                    hr = penumMethodField->QueryInterface( IID_IEnumDebugFields,
                        reinterpret_cast<void**>(&pfields) );
                    penumMethodField->Release();
                }
            }
        }
        else
        {
            hr = E_FAIL;
        }

        pmethod->Release();
        if (hr != S_OK)
            return hr;
    }

    //create a property info enumeration around the field enumerator
    CEnumPropertyInfo* pproperties =
        new CEnumPropertyInfo( m_provider, m_address, m_binder,
                               radix, pfields, infoFlags );
    if (pfields != NULL)
        pfields->Release();
    if (pproperties == NULL)
        return E_OUTOFMEMORY;

    hr = pproperties->QueryInterface( IID_IEnumDebugPropertyInfo2,
        reinterpret_cast<void**>(ppchildren) );
    pproperties->Release();

    return hr;
}
```

## <a name="see-also"></a>См. также
- [Пример реализации локальных переменных](../../extensibility/debugger/sample-implementation-of-locals.md)
- [Реализация Жетмесодпроперти](../../extensibility/debugger/implementing-getmethodproperty.md)
- [Контекст оценки](../../extensibility/debugger/evaluation-context.md)
