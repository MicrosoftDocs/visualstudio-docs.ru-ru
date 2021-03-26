---
description: Расширяет интерфейс IDebugCodeContext2, чтобы обеспечить получение интерфейсов модуля и процесса.
title: IDebugCodeContext3 | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugCodeContext3 interface
ms.assetid: 524eb882-0ad5-4bfb-95eb-eb3abb3d0237
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4dd0ffb94f25ae8ac9566571a645d706fa224cd8
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105088319"
---
# <a name="idebugcodecontext3"></a>IDebugCodeContext3
Расширяет интерфейс [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) , чтобы обеспечить получение интерфейсов модуля и процесса.

## <a name="syntax"></a>Синтаксис

```
IDebugCodeContext3 : IDebugCodeContext2
```

## <a name="notes-for-implementers"></a>Примечания для разработчиков
 Реализован механизмами отладки и используется [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] пакетом отладки.

## <a name="methods"></a>Методы
 Помимо методов `IDebugCodeContext2` интерфейса, этот интерфейс реализует следующие методы.

|Метод|Описание|
|------------|-----------------|
|[GetModule](../../../extensibility/debugger/reference/idebugcodecontext3-getmodule.md)|Извлекает ссылку на интерфейс модуля отладки.|
|[GetProcess](../../../extensibility/debugger/reference/idebugcodecontext3-getprocess.md)|Извлекает ссылку на интерфейс процесса отладки.|

## <a name="remarks"></a>Remarks
 Это необязательный интерфейс, который обычно не требуется реализовывать.

## <a name="requirements"></a>Требования
 Заголовок: Мсдбг. h

 Пространство имен: Microsoft. VisualStudio. Debugger. Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll
