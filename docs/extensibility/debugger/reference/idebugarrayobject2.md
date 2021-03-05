---
description: Представляет объект управляемого массива и позволяет средству оценки выражений (EE) определить базовый индекс (нижние границы) для массива.
title: IDebugArrayObject2 | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugArrayObject2 interface
ms.assetid: be6e504d-4ab3-4141-a61b-0953ee0e038e
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 0e6bb73834f53e22df63682663539b5f01685b30
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102174128"
---
# <a name="idebugarrayobject2"></a>IDebugArrayObject2
> [!IMPORTANT]
> В Visual Studio 2015 такой способ реализации оценивающих выражений является устаревшим. Дополнительные сведения о реализации вычислителей выражений CLR см. в разделе средства [оценки выражений CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) и [Пример управляемого средства оценки выражений](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Представляет объект управляемого массива и позволяет средству оценки выражений (EE) определить базовый индекс (нижние границы) для массива.

## <a name="syntax"></a>Синтаксис

```
IDebugArrayObject2 : IDebugArrayObject
```

## <a name="notes-for-implementers"></a>Примечания для разработчиков
 Это реализуется модулем управляемой отладки (DE).

## <a name="methods"></a>Методы
 В дополнение к методам в интерфейсе [идебугаррайобжект](../../../extensibility/debugger/reference/idebugarrayobject.md) этот интерфейс реализует следующие методы:

|Метод|Описание|
|------------|-----------------|
|[GetBaseIndices](../../../extensibility/debugger/reference/idebugarrayobject2-getbaseindices.md)|Получает базовые индексы (нижние границы) для каждого индекса, учитывая количество измерений в массиве.|
|[HasBaseIndices](../../../extensibility/debugger/reference/idebugarrayobject2-hasbaseindices.md)|Определяет, определен ли в массиве базовые индексы (нижние границы).|

## <a name="remarks"></a>Комментарии
 Средство оценки выражений использует этот интерфейс для представления управляемых массивов в дереве синтаксического анализа.

## <a name="requirements"></a>Требования
 Заголовок: ee. h

 Пространство имен: Microsoft. VisualStudio. Debugger. Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll
