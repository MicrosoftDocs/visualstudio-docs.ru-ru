---
description: Представляет расположение в исходном файле как смещение символа.
title: IDebugDocumentPositionOffset2 | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugDocumentPositionOffset2 interface
ms.assetid: f1b05db3-50d8-453f-a72f-e68b239236a4
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 01815a7dcae5a469db20b9288918b4e2aaf9ffed
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105066325"
---
# <a name="idebugdocumentpositionoffset2"></a>IDebugDocumentPositionOffset2
Представляет расположение в исходном файле как смещение символа.

## <a name="syntax"></a>Синтаксис

```
IDebugDocumentPositionOffset2 : IUnknown
```

## <a name="notes-for-implementers"></a>Примечания для разработчиков
 Реализуется интегрированной средой разработки и используется механизмами отладки.

## <a name="methods"></a>Методы
 В следующей таблице показаны методы `IDebugDocumentPositionOffset2` .

|Метод|Описание|
|------------|-----------------|
|[GetRange](../../../extensibility/debugger/reference/idebugdocumentpositionoffset2-getrange.md)|Извлекает диапазон для текущего расположения документа.|

## <a name="remarks"></a>Remarks
 При этом возвращаются те же сведения [, что](../../../extensibility/debugger/reference/idebugdocumentposition2-getrange.md) и в методе «та», но в `char` смещении от начала документа. Таким образом, документ будет выглядеть так, как если бы он существовал на диске, то есть в одномерном массиве символов вместо сведений о строках и столбцах, которые обычно возвращаются.

## <a name="requirements"></a>Требования
 Заголовок: Мсдбг. h

 Пространство имен: Microsoft. VisualStudio. Debugger. Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)
