---
description: Представляет числовой псевдоним для переменной и позволяет средству оценки выражений (EE) получить домен приложения для псевдонима.
title: IDebugAlias2 | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugAlias2 interface
ms.assetid: 5252dcbb-8bfe-4d8a-a8e5-b022b194df19
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: f6ca97fbe23e9b0c84c39e591c0fd9cfb997fca5
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105059045"
---
# <a name="idebugalias2"></a>IDebugAlias2
> [!IMPORTANT]
> В Visual Studio 2015 такой способ реализации оценивающих выражений является устаревшим. Дополнительные сведения о реализации вычислителей выражений CLR см. в разделе средства [оценки выражений CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) и [Пример управляемого средства оценки выражений](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Представляет числовой псевдоним для переменной и позволяет средству оценки выражений (EE) получить домен приложения для псевдонима.

## <a name="syntax"></a>Синтаксис

```
IDebugAlias2 : IDebugAlias
```

## <a name="notes-for-implementers"></a>Примечания для разработчиков
 Этот интерфейс реализуется управляемым модулем отладки (DE).

## <a name="methods"></a>Методы
 В дополнение к методам в интерфейсе [идебугалиас](../../../extensibility/debugger/reference/idebugalias.md) этот интерфейс реализует следующий метод:

|Метод|Описание|
|------------|-----------------|
|[GetAppDomainId](../../../extensibility/debugger/reference/idebugalias2-getappdomainid.md)|Возвращает идентификатор для домена приложения.|

## <a name="remarks"></a>Remarks
 Псевдоним представляет собой десятичное число в виде строки, за которым следует символ #, например, 1001 #.

## <a name="requirements"></a>Требования
 Заголовок: ee. h

 Пространство имен: Microsoft. VisualStudio. Debugger. Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll
