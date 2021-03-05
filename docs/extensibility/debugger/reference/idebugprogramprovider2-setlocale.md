---
description: Устанавливает языковой стандарт, используемый для всех ресурсов, зависящих от языкового стандарта.
title: 'IDebugProgramProvider2:: SetLocale | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramProvider2::SetLocale
helpviewer_keywords:
- IDebugProgramProvider2::SetLocale
ms.assetid: b41d20a7-ba40-4c42-a450-16f413d6a04f
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f23a6cc5b2724e925efcb9b7f4d6f272fc808121
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102167013"
---
# <a name="idebugprogramprovider2setlocale"></a>IDebugProgramProvider2::SetLocale
Устанавливает языковой стандарт, используемый для всех ресурсов, зависящих от языкового стандарта.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT SetLocale(
   WORD wLangID
);
```

```csharp
int SetLocale(
   ushort wLangID
);
```

## <a name="parameters"></a>Параметры
`wLangID`\
окне Идентификатор языка для установки. Например, 1033 для английского языка.

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="see-also"></a>См. также раздел
- [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)
