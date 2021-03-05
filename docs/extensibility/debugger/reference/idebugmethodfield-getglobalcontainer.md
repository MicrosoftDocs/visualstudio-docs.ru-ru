---
description: Возвращает глобальный контейнер метода.
title: 'Идебугмесодфиелд:: Жетглобалконтаинер | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMethodField::GetGlobalContainer
helpviewer_keywords:
- IDebugMethodField::GetGlobalContainer method
ms.assetid: 041ac5aa-0b80-4310-b9ae-b88f8e7e0e5f
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: eb20551d39f3e876a836ac42906ad9c50e3c6419
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102166298"
---
# <a name="idebugmethodfieldgetglobalcontainer"></a>IDebugMethodField::GetGlobalContainer
Возвращает глобальный контейнер метода.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetGlobalContainer(
   IDebugClassField** ppClass
);
```

```csharp
int GetGlobalContainer(
   out IDebugClassField ppClass
);
```

## <a name="parameters"></a>Параметры
`ppClass`\
заполняет Возвращает [идебугклассфиелд](../../../extensibility/debugger/reference/idebugclassfield.md) , представляющий модуль, в котором определен этот метод.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает S_OK; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Комментарии
 Возвращаемый объект [идебугклассфиелд](../../../extensibility/debugger/reference/idebugclassfield.md) представляет весь модуль и является искусственным объектом, то есть сам модуль не имеет фактического класса, но может быть представлен `IDebugClassField` объектом, что позволяет перечислять и обнаруживать различные элементы модуля.

## <a name="see-also"></a>См. также раздел
- [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
