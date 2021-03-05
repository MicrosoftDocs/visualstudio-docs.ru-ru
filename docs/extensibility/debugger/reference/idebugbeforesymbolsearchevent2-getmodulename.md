---
description: Возвращает имя модуля, в котором выполняется отладка.
title: 'IDebugBeforeSymbolSearchEvent2:: Жетмодуленаме | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- GetModuleName
- IDebugBeforeSymbolSearchEvent2::GetModuleName
ms.assetid: 0b4abeac-2eaf-4b2e-a2d5-c9ec303bc869
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c053bd14949a2688ad332207d07355333814a120
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102167780"
---
# <a name="idebugbeforesymbolsearchevent2getmodulename"></a>IDebugBeforeSymbolSearchEvent2::GetModuleName
Возвращает имя модуля, в котором выполняется отладка.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetModuleName(
    BSTR *pbstrModuleName
);
```

```csharp
public int GetModuleName (
    string pbstrModuleName
);
```

## <a name="parameters"></a>Параметры
`pbstrModuleName`\
заполняет Имя модуля.

## <a name="return-value"></a>Возвращаемое значение
Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="example"></a>Пример
В следующем примере показано, как реализовать этот метод для объекта **кдебугбефоресимболсеарчевентбасе** , предоставляющего интерфейс [IDebugBeforeSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugbeforesymbolsearchevent2.md) .

```cpp
STDMETHODIMP CDebugBeforeSymbolSearchEventBase::GetModuleName(BSTR *pbstrModuleName)
{
    HRESULT hRes = E_FAIL;

    if (m_bstrModuleName)
    {

        *pbstrModuleName = SysAllocString( m_bstrModuleName);

        if (*pbstrModuleName)
        {
            hRes = S_OK;
        }
    }

    return ( hRes );
}
```

## <a name="see-also"></a>См. также раздел
- [IDebugBeforeSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugbeforesymbolsearchevent2.md)
