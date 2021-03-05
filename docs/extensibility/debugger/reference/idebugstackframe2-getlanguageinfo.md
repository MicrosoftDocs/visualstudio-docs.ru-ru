---
description: Возвращает язык, связанный с этим кадром стека.
title: 'IDebugStackFrame2:: Жетлангуажеинфо | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugStackFrame2::GetLanguageInfo
helpviewer_keywords:
- IDebugStackFrame2::GetLanguageInfo
ms.assetid: 0e12fd92-f155-46a7-8272-cda279388cfb
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 38d9cfcab6748aad2166bfddfb48e9a0c0dc90c0
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102159826"
---
# <a name="idebugstackframe2getlanguageinfo"></a>IDebugStackFrame2::GetLanguageInfo

Возвращает язык, связанный с этим кадром стека.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetLanguageInfo ( 
   BSTR* pbstrLanguage,
   GUID* pguidLanguage
);
```

```csharp
int GetLanguageInfo ( 
   ref string pbstrLanguage,
   ref Guid   pguidLanguage
);
```

## <a name="parameters"></a>Параметры

`pbstrLanguage`\
заполняет Возвращает имя языка, реализующего метод, связанный с этим кадром стека.

`pguidLanguage`\
заполняет Возвращает `GUID` язык. Например, для [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] языков можно вернуть следующее:

- `guidVBScriptLang`\

- `guidJScriptLang`\

- `guidCPPLang`\

- `guidVBLang`\

- `guidSQLLang`\

- `guidScriptLang`\

## <a name="return-value"></a>Возвращаемое значение

 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="see-also"></a>См. также раздел

- [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)
