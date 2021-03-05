---
description: Расширяет типы полей, доступных для поддержки универсальных типов управляемого кода.
title: Идебужекстендедфиелд | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugExtendedField interface
ms.assetid: b491499c-af57-47da-87d6-34b7398f6591
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 5da66ddab0f485587ac5779187384a749459419e
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102152108"
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
