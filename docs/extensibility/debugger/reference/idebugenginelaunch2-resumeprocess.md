---
description: Возобновляет выполнение процесса.
title: 'IDebugEngineLaunch2:: Ресумепроцесс | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngineLaunch2::ResumeProcess
helpviewer_keywords:
- IDebugEngineLaunch2::ResumeProcess
ms.assetid: 61ccc14e-75c6-44e7-aae4-57a9aac52089
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e868d81647e85e90728d0de73143a89fb8e0b0f0
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102153577"
---
# <a name="idebugenginelaunch2resumeprocess"></a>IDebugEngineLaunch2::ResumeProcess
Возобновляет выполнение процесса.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT ResumeProcess ( 
   IDebugProcess2* pProcess
);
```

```csharp
int ResumeProcess ( 
   IDebugProcess2 pProcess
);
```

## <a name="parameters"></a>Параметры
`pProcess`\
окне Объект [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) , представляющий процесс, который должен быть возобновлен.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает `S_OK` ; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Комментарии
 Этот метод вызывается после запуска процесса с вызовом метода [лаунчсуспендед](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md) .

## <a name="see-also"></a>См. также раздел
- [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
- [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)
