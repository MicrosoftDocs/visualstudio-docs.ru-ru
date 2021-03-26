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
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 426904f777d65a25b92871767649cb26041e2af8
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105071549"
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

## <a name="see-also"></a>См. также
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
