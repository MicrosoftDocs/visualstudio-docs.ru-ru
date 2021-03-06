---
description: Представляет возможность создания поля, представляющего тип.
title: Идебугтипефиелдбуилдер | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugTypeFieldBuilder interface
ms.assetid: 2dfed0be-6972-4bec-baec-f0b78df9ef97
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 1bc4f58470792cac8bdb68ede4ddf37567bac208
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102223112"
---
# <a name="idebugtypefieldbuilder"></a>IDebugTypeFieldBuilder
Представляет возможность создания поля, представляющего тип.

## <a name="syntax"></a>Синтаксис

```
IDebugTypeFieldBuilder : IUnknown
```

## <a name="notes-for-callers"></a>Примечания для вызывающих объектов
 Этот интерфейс получается от поставщика символов.

## <a name="methods"></a>Методы
 Этот интерфейс реализует следующие методы.

|Метод|Описание|
|------------|-----------------|
|[CreatePrimitive](../../../extensibility/debugger/reference/idebugtypefieldbuilder-createprimitive.md)|Создает объект, представляющий тип-примитив.|
|[CreatePointerToType](../../../extensibility/debugger/reference/idebugtypefieldbuilder-createpointertotype.md)|Создает указатель на указанный тип.|

## <a name="requirements"></a>Требования
 Заголовок: sh. h

 Пространство имен: Microsoft. VisualStudio. Debugger. Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll
