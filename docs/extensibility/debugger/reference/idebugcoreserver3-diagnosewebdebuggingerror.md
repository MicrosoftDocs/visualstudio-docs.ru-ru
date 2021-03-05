---
description: Пытается определить причину сбоя автоматического подключения.
title: IDebugCoreServer3::D Иагносевебдебуггинжеррор | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCoreServer3::DiagnoseWebDebuggingError
helpviewer_keywords:
- IDebugCoreServer3::DiagnoseWebDebuggingError
ms.assetid: 8c4570ca-ae55-42f2-bbaa-8d8e75d2fa19
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 95e54add3616fa0ec97f4114b4cd628213e752f9
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102154695"
---
# <a name="idebugcoreserver3diagnosewebdebuggingerror"></a>IDebugCoreServer3::DiagnoseWebDebuggingError
Пытается определить причину сбоя автоматического подключения.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT DiagnoseWebDebuggingError(
   LPCWSTR pszUrl
);
```

```csharp
int DiagnoseWebDebuggingError(
   string pszUrl
);
```

## <a name="parameters"></a>Параметры
`pszUrl`\
окне В настоящее время не используется; всегда должно быть задано значение null.

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки. Ниже приведены другие стандартные коды возврата.

|Код|Описание|
|----------|-----------------|
|`S_WEBDBG_UNABLE_TO_DIAGNOSE`|Не удается определить, почему удаленному серверу не удалось запустить отладку.|
|`S_WEBDBG_DEBUG_VERB_BLOCKED`|Не удается выполнить отладку на удаленном сервере, возможно, из-за недостаточных разрешений или если команда отладки не включена.|
|`E_WEBDBG_DEBUG_VERB_BLOCKED`|Веб-сервер заблокирован и блокирует команду DEBUG, которая необходима для включения отладки.|

## <a name="see-also"></a>См. также раздел
- [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)
