---
description: Представляет указатель в дереве синтаксического анализа и расширяет интерфейс Идебугпоинтеробжект.
title: IDebugPointerObject3 | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugPointerObject3 interface
ms.assetid: 11d26af4-1079-435e-96fa-d5269cbea8eb
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: f40003c04b7b0b4e480aff8057582f998e092079
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102142830"
---
# <a name="idebugpointerobject3"></a>IDebugPointerObject3
> [!IMPORTANT]
> В Visual Studio 2015 такой способ реализации оценивающих выражений является устаревшим. Дополнительные сведения о реализации вычислителей выражений CLR см. в разделе средства [оценки выражений CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) и [Пример управляемого средства оценки выражений](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Представляет указатель в дереве синтаксического анализа и расширяет интерфейс **идебугпоинтеробжект** .

## <a name="syntax"></a>Синтаксис

```
IDebugPointerObject3 : IDebugPointerObject
```

## <a name="notes-for-implementers"></a>Примечания для разработчиков
 Средство оценки выражений (EE) реализует этот интерфейс.

## <a name="methods"></a>Методы
 В дополнение к методам в интерфейсе [идебугпоинтеробжект](../../../extensibility/debugger/reference/idebugpointerobject.md) этот интерфейс реализует следующие методы:

|Метод|Описание|
|------------|-----------------|
|[GetPointerAddress](../../../extensibility/debugger/reference/idebugpointerobject3-getpointeraddress.md)|Получает адрес указателя.|

## <a name="requirements"></a>Требования
 Заголовок: ee. h

 Пространство имен: Microsoft. VisualStudio. Debugger. Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll
