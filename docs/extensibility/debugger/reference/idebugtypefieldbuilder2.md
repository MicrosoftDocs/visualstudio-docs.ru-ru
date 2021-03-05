---
description: Расширяет Идебугтипефиелдбуилдер, чтобы иметь возможность создавать типы массивов.
title: IDebugTypeFieldBuilder2 | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugTypeFieldBuilder2 interface
ms.assetid: 23911c5b-2bbf-4734-9976-87a0bd6ea36c
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: e73642024cb379e804559ba8dd55eb44722cf580
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102223008"
---
# <a name="idebugtypefieldbuilder2"></a>IDebugTypeFieldBuilder2
Расширяет **идебугтипефиелдбуилдер** , чтобы иметь возможность создавать типы массивов.

## <a name="syntax"></a>Синтаксис

```
IDebugTypeFieldBuilder2 : IDebugTypeFieldBuilder
```

## <a name="notes-for-callers"></a>Примечания для вызывающих объектов
 Этот интерфейс можно получить от поставщика символов.

## <a name="methods"></a>Методы
 В дополнение к методам в интерфейсе [идебугтипефиелдбуилдер](../../../extensibility/debugger/reference/idebugtypefieldbuilder.md) этот интерфейс реализует следующий метод:

|Метод|Описание|
|------------|-----------------|
|[CreateArrayOfType](../../../extensibility/debugger/reference/idebugtypefieldbuilder2-createarrayoftype.md)|Создает массив указанного типа и размера.|

## <a name="requirements"></a>Требования
 Заголовок: sh. h

 Пространство имен: Microsoft. VisualStudio. Debugger. Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll
