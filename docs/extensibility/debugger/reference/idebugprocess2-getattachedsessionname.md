---
description: Возвращает имя сеанса, в котором выполняется отладка этого процесса.
title: 'IDebugProcess2:: Жетаттачедсессионнаме | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess2::GetAttachedSessionName
helpviewer_keywords:
- IDebugProcess2::GetAttachedSessionName
ms.assetid: 7e5e116f-2c0c-4bc8-ad3f-e9fd2318a7e4
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 63d83a9d5f89ea06744454b790d988f1881c193b
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102142548"
---
# <a name="idebugprocess2getattachedsessionname"></a>IDebugProcess2::GetAttachedSessionName
Возвращает имя сеанса, в котором выполняется отладка этого процесса. Интегрированная среда разработки может отображать эту информацию для пользователя, выполняющего отладку определенного процесса на определенном компьютере.

> [!NOTE]
> Этот метод является устаревшим, и его реализация всегда должна возвращать `E_NOTIMPL` .

## <a name="syntax"></a>Синтаксис

```
HRESULT GetAttachedSessionName(
   BSTR* pbstrSessionName
);
```

## <a name="parameters"></a>Параметры
`pbstrSessionName`\

## <a name="return-value"></a>Возвращаемое значение
 Этот метод всегда должен возвращать `E_NOTIMPL` .

## <a name="see-also"></a>См. также раздел
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
