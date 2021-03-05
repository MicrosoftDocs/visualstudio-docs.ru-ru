---
description: Возвращает количество элементов в перечислении Ports.
title: 'IEnumDebugPorts2:: NOCOUNT | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugPorts2::GetCount
helpviewer_keywords:
- IEnumDebugPorts2::GetCount
ms.assetid: d714455c-e4fc-48dc-a6d4-7e8b5d7c1bce
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 22550fa1ba700a77564f6da666d6300335427e1a
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102226323"
---
# <a name="ienumdebugports2getcount"></a>IEnumDebugPorts2::GetCount
Возвращает количество элементов в перечислении.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetCount(
   ULONG* pcelt
);
```

```csharp
int GetCount(
   out uint pcelt
);
```

## <a name="parameters"></a>Параметры
`pcelt`\
заполняет Возвращает количество элементов в перечислении.

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Комментарии
 Этот метод не является частью пользовательского интерфейса перечисления com, который указывает, что `Next` `Clone` необходимо реализовать только методы,, `Skip` и `Reset` .

## <a name="see-also"></a>См. также раздел
- [IEnumDebugPorts2](../../../extensibility/debugger/reference/ienumdebugports2.md)
