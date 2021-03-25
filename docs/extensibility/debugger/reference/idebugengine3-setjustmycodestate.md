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
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 6e527dbaeb9c04171bf26ea00e550eac336ac6a8
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105066127"
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

## <a name="remarks"></a>Remarks
 Жустмикоде — это концепция отладки только кода, относящегося к пользователю, и игнорирования всех промежуточных кодов, таких как системный код, даже если исходный код доступен для этого системного кода.

## <a name="see-also"></a>См. также
- [IDebugEngine3](../../../extensibility/debugger/reference/idebugengine3.md)
- [JMC_CODE_SPEC](../../../extensibility/debugger/reference/jmc-code-spec.md)
