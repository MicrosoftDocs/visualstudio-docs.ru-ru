---
description: Этот метод вызывается для вывода указанного значения.
title: Идебугкустомвиевер::D Исплайвалуе | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCustomViewer::DisplayValue
helpviewer_keywords:
- IDebugCustomViewer::DisplayValue
ms.assetid: 7a538248-5ced-450e-97cd-13fabe35fb1c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 11a93ba7a3367a9ff61debfe338c349549ee429d
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105077581"
---
# <a name="idebugcustomviewerdisplayvalue"></a>IDebugCustomViewer::DisplayValue
Этот метод вызывается для вывода указанного значения.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT DisplayValue(
   HWND             hwnd,
   DWORD            dwID,
   IUnknown *       pHostServices,
   IDebugProperty3* pDebugProperty);
);
```

```csharp
int DisplayValue(
   IntPtr          hwnd,
   uint            dwID,
   object          pHostServices,
   IDebugProperty3 pDebugProperty
);
```

## <a name="parameters"></a>Параметры
`hwnd`\
окне Родительское окно

`dwID`\
окне Идентификатор для пользовательских средств просмотра, поддерживающих более одного типа.

`pHostServices`\
[in] Зарезервировано. Всегда имеет значение null.

`pDebugProperty`\
окне Интерфейс, который можно использовать для получения отображаемого значения.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает `S_OK` ; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Remarks
 Экран является "модальным" тем, что этот метод создает необходимое окно, отображает значение, ждет ввода и перед возвратом в вызывающий объект закрывает окно. Это означает, что метод должен управлять всеми аспектами отображения значения свойства, от создания окна для вывода, ожидающего ввода данных пользователем, для уничтожения окна.

 Для поддержки изменения значения в заданном объекте [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) можно использовать метод [сетвалуеасстрингвисеррор](../../../extensibility/debugger/reference/idebugproperty3-setvalueasstringwitherror.md) , если значение может быть выражено в виде строки. В противном случае необходимо создать настраиваемый интерфейс — исключительно для средства оценки выражений, реализующего этот `DisplayValue` метод, в том же объекте, который реализует `IDebugProperty3` интерфейс. Этот пользовательский интерфейс предоставляет методы для изменения данных произвольного размера или сложности.

## <a name="see-also"></a>См. также
- [IDebugCustomViewer](../../../extensibility/debugger/reference/idebugcustomviewer.md)
- [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)
- [SetValueAsStringWithError](../../../extensibility/debugger/reference/idebugproperty3-setvalueasstringwitherror.md)
