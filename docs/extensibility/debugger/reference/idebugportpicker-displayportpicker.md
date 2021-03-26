---
description: Отображает указанное диалоговое окно, позволяющее пользователю выбрать порт.
title: Идебугпортпиккер::D Исплайпортпиккер | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- DisplayPortPicker
- IDebugPortPicker::DisplayPortPicker
ms.assetid: 08511ef5-be64-4069-b169-a569cc94bc64
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a49c1379d2bb3946f75eddd9d80bdccdb370d3ab
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105072316"
---
# <a name="idebugportpickerdisplayportpicker"></a>IDebugPortPicker::DisplayPortPicker
Отображает указанное диалоговое окно, позволяющее пользователю выбрать порт.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT DisplayPortPicker(
   HWND hwndParentDialog,
   BSTR* pbstrPortId
);
```

```csharp
public int DisplayPortPicker(
   int hwndParentDialog,
   out string pbstrPortId
);
```

## <a name="parameters"></a>Параметры
`hwndParentDialog`\
окне Обработчик для родительского диалогового окна.

`pbstrPortId`\
заполняет Строка идентификатора порта.

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки. Возвращаемое значение `S_FALSE` (или возвращаемое значение со значением `S_OK` `BSTR` `NULL` ) указывает, что пользователь щелкнул кнопку **Отмена**.

## <a name="see-also"></a>См. также
- [IDebugPortPicker](../../../extensibility/debugger/reference/idebugportpicker.md)
