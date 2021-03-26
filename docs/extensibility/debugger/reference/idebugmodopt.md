---
description: Представляет необязательный модификатор отладки.
title: Идебугмодопт | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugModOpt interface
ms.assetid: ebd525e3-d140-4071-9d8c-41871de4125e
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: ffb235d58c254d130636da0f4b97961c11f9a372
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105087903"
---
# <a name="idebugmodopt"></a>IDebugModOpt
Представляет необязательный модификатор отладки.

## <a name="syntax"></a>Синтаксис

```
IDebugModOpt : IUnknown
```

## <a name="notes-for-callers"></a>Примечания для вызывающих объектов
 Получен из объекта [идебугфиелд](../../../extensibility/debugger/reference/idebugfield.md) , представляющего класс или метод.

## <a name="methods"></a>Методы
 Этот интерфейс реализует следующий метод:

|Метод|Описание|
|------------|-----------------|
|[GetModOpts](../../../extensibility/debugger/reference/idebugmodopt-getmodopts.md)|Извлекает список необязательных модификаторов.|

## <a name="requirements"></a>Требования
 Заголовок: sh. h

 Пространство имен: Microsoft. VisualStudio. Debugger. Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll
