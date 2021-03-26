---
title: Оценка локальных переменных | Документация Майкрософт
description: Узнайте, как Visual Studio обращается к расположению в памяти, которое содержит локальное значение, которое зависит от текущего состояния программы.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], evaluating locals
- expression evaluation, evaluating locals
ms.assetid: 7d1ed528-4e7a-4d8f-87b4-162440644a75
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 26543152293cd93bc5565995f2e6c451417aca37
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105096997"
---
# <a name="evaluate-locals"></a>Оценка локальных переменных
> [!IMPORTANT]
> В Visual Studio 2015 такой способ реализации оценивающих выражений является устаревшим. Дополнительные сведения о реализации вычислителей выражений CLR см. в разделе средства [оценки выражений CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) и [Пример управляемого средства оценки выражений](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

[GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) вызывается для получения значения локального, а также имени и типа локального компьютера. Так как значение локального объекта зависит от текущего состояния программы, значение локального объекта должно быть получено из памяти. Объект [идебугбиндер](../../extensibility/debugger/reference/idebugbinder.md) используется для привязки объекта [идебугфиелд](../../extensibility/debugger/reference/idebugfield.md) , представляющего локальный объект, с соответствующим местом в памяти, содержащим значение. Это расположение в памяти представлено объектом [идебугобжект](../../extensibility/debugger/reference/idebugobject.md) .

Эта функция извлечения значения локальной функции инкапсулирована в вспомогательную функцию, которая выполняет следующие задачи:

1. Привязывает `IDebugField` объект к памяти для получения `IDebugObject` объекта.

2. Возвращает значение из памяти. Это значение представлено в виде последовательности байтов.

3. Форматирует значение на основе типа локального объекта.

4. Возвращает универсальный объект, содержащий значение локального объекта. В C# это — `object` , а в C++ — `VARIANT` .

## <a name="managed-code"></a>Управляемый код
 Это реализация функции, которая получает значение локального объекта в управляемом коде.

```csharp
namespace EEMC
{
    internal class Field
    {
        internal static object GetValue(
            IDebugBinder binder,
            IDebugField field,
            Type t,
            uint size)
        {
            if (t == null || size == 0)  return null;

            IDebugObject debugObject = null;
            binder.Bind(null, field, out debugObject);

            byte[] buffer = new byte[size];
            for (int i = 0; i < size; i++)  buffer[i] = 0;

            debugObject.GetValue(buffer, size);

            if (t == typeof(sbyte)) return (sbyte) buffer[0];
            if (t == typeof(short)) return BitConverter.ToInt16(buffer, 0);
            if (t == typeof(int))   return BitConverter.ToInt32(buffer, 0);
            if (t == typeof(long))  return BitConverter.ToInt64(buffer, 0);
            if (t == typeof(byte))  return buffer[0];
            if (t == typeof(char))  return BitConverter.ToChar(buffer, 0);
            if (t == typeof(uint))  return BitConverter.ToUInt32(buffer, 0);
            if (t == typeof(ulong)) return BitConverter.ToUInt64(buffer, 0);
            if (t == typeof(float)) return BitConverter.ToSingle(buffer, 0);
            if (t == typeof(double))  return BitConverter.ToDouble(buffer, 0);
            if (t == typeof(bool))  return BitConverter.ToBoolean(buffer, 0);
            if (t == typeof(string))  return BitConverter.ToString(buffer, 0);
            return null;
        }
    }
}
```

## <a name="unmanaged-code"></a>Неуправляемый код
 Это реализация функции, которая получает значение локального объекта в неуправляемом коде. `FieldGetType` отображается в окне [получение локальных значений](../../extensibility/debugger/getting-local-values.md).

```cpp
HRESULT FieldGetPrimitiveValue(
    in  IDebugBinder* pbinder,
    in  IDebugField*  pfield,
    out VARIANT*      pvarValue
    )
{
    if (pvarValue == NULL)
        return E_INVALIDARG;
    else
        *pvarValue = 0;

    if (pfield == NULL)
        return E_INVALIDARG;

    if (pbinder == NULL)
        return E_INVALIDARG;

    HRESULT hr;
    UINT          valueSize = 0;
    BYTE*         pvalueBits = NULL;
    IDebugObject* pobject    = NULL;

    //get the value as bits
    hr = pbinder->Bind( NULL, pfield, &pobject );
    if (FAILED(hr))
        return hr;

    hr = pobject->GetSize( &valueSize );
    if (FAILED(hr))
    {
        pobject->Release();
        return hr;
    }

    pvalueBits = reinterpret_cast<BYTE *>(malloc(valueSize * sizeof(BYTE)));
    if (!pvalueBits)
    {
        pobject->Release();
        return E_OUTOFMEMORY;
    }

    hr = pobject->GetValue( pvalueBits, valueSize );
    pobject->Release();
    if (FAILED(hr))
    {
        free(pvalueBits);
        return hr;
    }

    //get the type
    VARIANT     valueType;

    hr = FieldGetType( pfield, &valueType );
    if (FAILED(hr))
    {
        free(pvalueBits);
        return hr;
    }

    //copy a primitive value
    switch (valueType.vt)
    {
    case VT_BSTR:
        {
            pvarValue->vt = VT_BSTR;
            if (valueSize == 0)
                pvarValue->bstrVal = SysAllocString( OLE("") );
            else
                pvarValue->bstrVal =
                    SysAllocStringByteLen( reinterpret_cast<char*>(pvalueBits),
                                           valueSize );
        }

    case VT_BOOL:
    case VT_I1:
    case VT_I2:
    case VT_I4:
    case VT_I8:
    case VT_UI1:
    case VT_UI2:
    case VT_UI4:
    case VT_UI8:
    case VT_R4:
    case VT_R8:
        pvarValue->vt = valueType.vt;

        if (valueSize > 8)
            valueSize = 8;
        memcpy( &(pvarValue->iVal), pvalueBits, valueSize );
        break;

    case VT_VOID:
    case VT_EMPTY:
        pvarValue->vt = valueType.vt;
        break;

    default:
        //not a primitive type
        VariantClear(&valueType);
        free(pvalueBits);
        return E_FAIL;
    }

    free(pvalueBits);
    VariantClear(&valueType);
    return S_OK;
}
```

## <a name="see-also"></a>См. также
- [Пример реализации локальных переменных](../../extensibility/debugger/sample-implementation-of-locals.md)
- [Получить локальные значения](../../extensibility/debugger/getting-local-values.md)
- [Контекст оценки](../../extensibility/debugger/evaluation-context.md)
