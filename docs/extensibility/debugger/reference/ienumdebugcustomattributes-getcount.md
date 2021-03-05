---
description: Возвращает число настраиваемых атрибутов в перечислителе.
title: 'Иенумдебугкустоматтрибутес:: NOCOUNT | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumCustomAttributes::GetCount
helpviewer_keywords:
- IEnumDebugCustomAttributes::GetCount
ms.assetid: fafe826f-4ebf-4572-b2a3-d5dd2916c12f
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e89525982cf912238038a3c6bf2616407d7af803
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102226947"
---
# <a name="ienumdebugcustomattributesgetcount"></a>IEnumDebugCustomAttributes::GetCount
Возвращает число настраиваемых атрибутов в перечислителе.

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
 Этот метод не является частью пользовательского интерфейса перечисления com, который указывает, что `Next` необходимо реализовать только,, `Clone` `Skip` и `Reset` .

## <a name="see-also"></a>См. также раздел
- [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md)
