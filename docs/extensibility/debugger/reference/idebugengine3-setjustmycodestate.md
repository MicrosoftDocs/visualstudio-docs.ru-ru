---
description: Этот метод сообщает модулю отладки о сведениях о состоянии Жустмикоде.
title: 'IDebugEngine3:: Сетжустмикодестате | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine3::SetJustMyCodeState
helpviewer_keywords:
- IDebugEngine3::SetJustMyCodeState
ms.assetid: 8ec17fbf-df93-424a-b2ed-fd1e5ee51256
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a81fa4bda506cf1be27f658b071910e7c8ccd8a7
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102153707"
---
# <a name="idebugengine3setjustmycodestate"></a>IDebugEngine3::SetJustMyCodeState
Этот метод сообщает модулю отладки о сведениях о состоянии Жустмикоде.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT SetJustMyCodeState(
   BOOL           fUpdate,
   DWORD          dwModules,
   JMC_CODE_SPEC* rgJMCSpec
);
```

```csharp
int SetJustMyCodeState(
   int             fUpdate,
   uint            dwModules,
   JMC_CODE_SPEC[] rgJMCSpec
);
```

## <a name="parameters"></a>Параметры
`fUpdate`\
окне Ненулевое значение ( `TRUE` ) для обновления текущей информации, ноль ( `FALSE` ) для сброса всех данных (без учета ранее заданных).

`dwModules`\
окне Количество информационных структур в `rgJMCSpec.`

`rgJMCSpec`\
окне Массив структур [JMC_CODE_SPEC](../../../extensibility/debugger/reference/jmc-code-spec.md) для использования.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает `S_OK` ; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Комментарии
 Жустмикоде — это концепция отладки только кода, относящегося к пользователю, и игнорирования всех промежуточных кодов, таких как системный код, даже если исходный код доступен для этого системного кода.

## <a name="see-also"></a>См. также раздел
- [IDebugEngine3](../../../extensibility/debugger/reference/idebugengine3.md)
- [JMC_CODE_SPEC](../../../extensibility/debugger/reference/jmc-code-spec.md)
