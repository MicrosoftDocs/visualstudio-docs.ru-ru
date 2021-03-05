---
description: Представляет числовой псевдоним для переменной и позволяет средству оценки выражений (EE) получить домен приложения для псевдонима.
title: IDebugAlias2 | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugAlias2 interface
ms.assetid: 5252dcbb-8bfe-4d8a-a8e5-b022b194df19
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: f383e31f43e1e6422892547d66af533c2f4ab87f
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102143861"
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

## <a name="remarks"></a>Комментарии
 Псевдоним представляет собой десятичное число в виде строки, за которым следует символ #, например, 1001 #.

## <a name="requirements"></a>Требования
 Заголовок: ee. h

 Пространство имен: Microsoft. VisualStudio. Debugger. Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll
