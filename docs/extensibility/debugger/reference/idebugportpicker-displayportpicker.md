---
description: Отображает указанное диалоговое окно, позволяющее пользователю выбрать порт.
title: Идебугпортпиккер::D Исплайпортпиккер | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- DisplayPortPicker
- IDebugPortPicker::DisplayPortPicker
ms.assetid: 08511ef5-be64-4069-b169-a569cc94bc64
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9c07e95343521692d41d045a89a4038f5ff64e7b
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102142561"
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

## <a name="see-also"></a>См. также раздел
- [IDebugPortPicker](../../../extensibility/debugger/reference/idebugportpicker.md)
