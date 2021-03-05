---
description: Этот метод получает контекст памяти или объект, который содержит текущее значение символа.
title: 'Идебугбиндер:: BIND | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBinder::Bind
helpviewer_keywords:
- IDebugBinder::Bind method
ms.assetid: 15a11ad7-0fcc-4e80-ae34-8a7dd7bae3c3
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c373fbdae030de30544c67c1509eb812b746b7f1
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102143664"
---
# <a name="idebugbinderbind"></a>IDebugBinder::Bind
Этот метод получает контекст памяти или объект, который содержит текущее значение символа.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT Bind( 
   IDebugObject*  pContainer,
   IDebugField*   pField,
   IDebugObject** ppObject
);
```

```csharp
int Bind(
   IDebugObject     pContainer,
   IDebugField      pField,
   out IDebugObject ppObject
);
```

## <a name="parameters"></a>Параметры
`pContainer`\
окне [Идебугобжект](../../../extensibility/debugger/reference/idebugobject.md) , содержащий дочерний элемент, на который ссылается `pField` .

`pField`\
окне [Идебугфиелд](../../../extensibility/debugger/reference/idebugfield.md) , представляющий символ.

`ppObject`\
заполняет Возвращает объект `IDebugObject` , представляющий экземпляр символа.

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="see-also"></a>См. также раздел
- [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
