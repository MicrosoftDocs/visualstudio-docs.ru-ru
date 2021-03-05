---
description: Возвращает язык, связанный с этим контекстом документа.
title: 'IDebugDocumentContext2:: Жетлангуажеинфо | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentContext2::GetLanguageInfo
helpviewer_keywords:
- IDebugDocumentContext2::GetLanguageInfo
ms.assetid: 6a212ee5-414c-4eb5-ab11-19db1786943d
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: cd7bc00a0be242f66ff47ac5318753d81237c63a
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102160216"
---
# <a name="idebugdocumentcontext2getlanguageinfo"></a>IDebugDocumentContext2::GetLanguageInfo
Возвращает язык, связанный с этим контекстом документа.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetLanguageInfo(
    BSTR* pbstrLanguage,
    GUID* pguidLanguage
);
```

```csharp
int GetLanguageInfo(
    out string pbstrLanguage,
    out Guid   pguidLanguage
);
```

## <a name="parameters"></a>Параметры
`pbstrLanguage`\
заполняет Возвращает имя языка, реализующего код в данном контексте документа.

`pguidLanguage`\
заполняет Возвращает идентификатор GUID языка, реализующего код в данном контексте документа. Например, `guidVBScriptLang` или `guidCPPLang`. Этот идентификатор GUID не ограничивается языками, предоставляемыми [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] .

## <a name="return-value"></a>Возвращаемое значение
Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="example"></a>Пример
В следующем примере показано, как реализовать этот метод для простого `CDebugContext` объекта, предоставляющего интерфейс [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) .

```cpp
HRESULT CDebugContext::GetLanguageInfo(BSTR* pbstrLanguage, GUID* pguidLanguage)
{
    HRESULT hr;

    // Check for a valid language argument pointers.
    if (pbstrLanguage && pguidLanguage)
    {
        *pguidLanguage = GUID_NULL;
        *pbstrLanguage = SysAllocString(L"Batch File");
        if (*pbstrLanguage)
        {
            *pguidLanguage = guidBatLang;
            hr = S_OK;
        }
        else
        {
            hr = E_OUTOFMEMORY;
        }
    }
    else
    {
        hr = E_INVALIDARG;
    }

    return hr;
}
```

## <a name="see-also"></a>См. также раздел
- [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)
