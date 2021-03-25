---
description: Извлекает диапазон для текущего расположения документа.
title: 'IDebugDocumentPositionOffset2:: Range | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugDocumentPositionOffset2::GetRange
ms.assetid: 27da7130-0932-4f97-abde-05e6fb018606
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 66184ba67dd0623a886ca37e28d311aebc6633bd
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105066351"
---
# <a name="idebugdocumentpositionoffset2getrange"></a>IDebugDocumentPositionOffset2::GetRange
Извлекает диапазон для текущего расположения документа.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetRange(
   DWORD* pdwBegOffset,
   DWORD* pdwEndOffset
);
```

```csharp
public int GetRange(
   ref uint pdwBegOffset,
   ref uint pdwEndOffset
);
```

## <a name="parameters"></a>Параметры
`pdwBegOffset`\
[вход, выход] Смещение начальной позиции диапазона. Если эти сведения не требуются, присвойте этому параметру значение null.

`pdwEndOffset`\
[вход, выход] Смещение конечной позиции диапазона. Если эти сведения не требуются, присвойте этому параметру значение null.

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Remarks
 Диапазон, указанный в позиции документа для точки останова расположения, используется модулем отладки (DE) для поиска оператора, который фактически участвует в коде. Рассмотрим следующий пример кода:

```
Line 5: // comment
Line 6: x = 1;
```

 Строка 5 не вносит код в отлаживаемую программу. Если отладчику, устанавливающему точку останова в строке 5, требуется, чтобы DE выполнял поиск первой строки, которая участвует в коде, отладчик укажет диапазон, включающий дополнительные строки-кандидаты, где точка останова может быть правильно размещена. После этого команда «DE» будет выполнять поиск вперед по этим строкам, пока не найдет строку, которая может принять точку останова.

## <a name="see-also"></a>См. также
- [IDebugDocumentPositionOffset2](../../../extensibility/debugger/reference/idebugdocumentpositionoffset2.md)
- [GetRange](../../../extensibility/debugger/reference/idebugdocumentposition2-getrange.md)
