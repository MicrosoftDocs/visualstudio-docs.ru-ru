---
description: Представляет функцию и расширяет интерфейс Идебугфунктионобжект.
title: IDebugFunctionObject2 | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugFunctionObject2 interface
ms.assetid: 56b2fdff-146d-4138-a34c-59a9c65a3ddd
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 012cd3dd0068fe69aae8898a408435340c6b22ee
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105072849"
---
# <a name="idebugfunctionobject2"></a>IDebugFunctionObject2
> [!IMPORTANT]
> В Visual Studio 2015 такой способ реализации оценивающих выражений является устаревшим. Дополнительные сведения о реализации вычислителей выражений CLR см. в разделе средства [оценки выражений CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) и [Пример управляемого средства оценки выражений](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Представляет функцию и расширяет интерфейс [идебугфунктионобжект](../../../extensibility/debugger/reference/idebugfunctionobject.md) .

## <a name="syntax"></a>Синтаксис

```
IDebugFunctionObject2 : IUnknown
```

## <a name="notes-for-implementers"></a>Примечания для разработчиков
 Средство оценки выражений (EE) реализует этот интерфейс для представления функции.

## <a name="notes-for-callers"></a>Примечания для вызывающих объектов
 Методы этого интерфейса откладываются от **идебугфунктионобжект** следующими способами:

- Метод **идебужевалуате** принимает флаги.

- Метод **CreateObject** принимает флаги и время ожидания.

- Метод **креатестрингобжектвисленгс** имеет длину.

## <a name="methods"></a>Методы
 Этот интерфейс реализует следующие методы.

|Метод|Описание|
|------------|-----------------|
|[CreateObject](../../../extensibility/debugger/reference/idebugfunctionobject2-createobject.md)|Создает объект, использующий конструктор заданных параметров флагов оценки и значение времени ожидания.|
|[CreateStringObjectWithLength](../../../extensibility/debugger/reference/idebugfunctionobject2-createstringobjectwithlength.md)|Создает строковый объект, имеющий указанную длину.|
|[Вычислить](../../../extensibility/debugger/reference/idebugfunctionobject2-evaluate.md)|Вызывает функцию и возвращает результирующее значение в виде объекта.|

## <a name="requirements"></a>Требования
 Заголовок: ee. h

 Пространство имен: Microsoft. VisualStudio. Debugger. Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll
