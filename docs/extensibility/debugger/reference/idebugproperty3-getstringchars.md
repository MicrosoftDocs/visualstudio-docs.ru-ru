---
description: Извлекает строку, связанную с этим свойством, и сохраняет ее в предоставляемом пользователем буфере.
title: 'IDebugProperty3:: Жетстрингчарс | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty3::GetStringChars
helpviewer_keywords:
- IDebugProperty3::GetStringChars
ms.assetid: 832c37f3-85cb-4227-8ab2-f27a80eafe90
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d3b220fa02809015d1fa699c5e9eb5edac8cf2f3
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102166688"
---
# <a name="idebugproperty3getstringchars"></a>IDebugProperty3::GetStringChars
Извлекает строку, связанную с этим свойством, и сохраняет ее в предоставляемом пользователем буфере.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetStringChars(
    ULONG  buflen,
    WCHAR* rgString,
    ULONG* pceltFetched
);
```

```csharp
int GetStringChars(
    uint       buflen,
    out string rgString,
    out uint   pceltFetched
);
```

## <a name="parameters"></a>Параметры
`buflen`\
окне Максимальное число символов, которое может храниться в пользовательском буфере.

`rgString`\
заполняет Возвращает строку.

 [Только C++] `rgString` — это указатель на буфер, который получает символы Юникода строки. Размер этого буфера должен быть `buflen` не менее символов (не в байтах).

`pceltFetched`\
заполняет , Где возвращается количество символов, хранимых в буфере. (Может находиться `NULL` в C++.)

## <a name="return-value"></a>Возвращаемое значение
В случае успеха возвращает `S_OK` ; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Комментарии
В C++ необходимо соблюдать осторожность, чтобы убедиться в том, что буфер имеет длину не менее `buflen` Юникода символов. Обратите внимание, что символ Юникода имеет длину 2 байта.

> [!NOTE]
> В C++ возвращаемая строка не содержит завершающего нуль-символа. Если задано `pceltFetched` значение, будет указываться число символов в строке.

## <a name="example"></a>Пример

```cpp
CStringW RetrievePropertyString(IDebugProperty2 *pPropInfo)
{
    CStringW returnString = L"";
    CComQIPtr<IDebugProperty3> pProp3 = pPropInfo->pProperty;
    If (pProp3 != NULL) {
        ULONG dwStrLen = 0;
        HRESULT hr;
        hr = pProp3->GetStringCharLength(&dwStrLen);
        if (SUCCEEDED(hr) && dwStrLen > 0) {
            ULONG dwRead;
            CStrBufW buf(returnString,dwStrLen,CStrBuf::SET_LENGTH);
            hr = pProp3->GetStringChars(dwStrLen,
                                        reinterpret_cast<WCHAR*>(static_cast<CStringW::PXSTR>(buf)),
                                        &dwRead);
        }
    }
    return(returnString);
}
```

## <a name="see-also"></a>См. также раздел
- [GetStringCharLength](../../../extensibility/debugger/reference/idebugproperty3-getstringcharlength.md)
- [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
