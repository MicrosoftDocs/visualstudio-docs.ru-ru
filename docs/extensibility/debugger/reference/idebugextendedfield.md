---
description: Расширяет типы полей, доступных для поддержки универсальных типов управляемого кода.
title: Идебужекстендедфиелд | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugExtendedField interface
ms.assetid: b491499c-af57-47da-87d6-34b7398f6591
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: d8214703fb1ffc05d3f58f8348870a8505cc8f59
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105077191"
---
# <a name="idebugextendedfield"></a>IDebugExtendedField
Расширяет типы полей, доступных для поддержки универсальных типов управляемого кода.

## <a name="syntax"></a>Синтаксис

```
IDebugExtendedField : IDebugField
```

## <a name="methods"></a>Методы
 В дополнение к методам в интерфейсе [идебугфиелд](../../../extensibility/debugger/reference/idebugfield.md) этот интерфейс реализует следующие методы:

|Метод|Описание|
|------------|-----------------|
|[GetExtendedKind](../../../extensibility/debugger/reference/idebugextendedfield-getextendedkind.md)|Извлекает указанный тип расширенного поля.|
|[IsClosedType](../../../extensibility/debugger/reference/idebugextendedfield-isclosedtype.md)|Определяет, представляет ли поле закрытый тип.|

## <a name="requirements"></a>Требования
 Заголовок: sh. h

 Пространство имен: Microsoft. VisualStudio. Debugger. Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll
