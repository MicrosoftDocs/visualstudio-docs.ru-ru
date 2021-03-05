---
description: Этот метод определяет, может ли поставщик порта сохранять порты (путем записи на диск) между вызовами отладчика.
title: 'IDebugPortSupplier3:: Канперсистпортс | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortSupplier3::CanPersistPorts
helpviewer_keywords:
- IDebugPortSupplier3::CanPersistPorts
ms.assetid: 4127760c-e602-4e86-9232-457e382a52c7
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 092f6e372d8f98e731ad90a7d261fe015d019656
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102172013"
---
# <a name="idebugportsupplier3canpersistports"></a>IDebugPortSupplier3::CanPersistPorts
Этот метод определяет, может ли поставщик порта сохранять порты (путем записи на диск) между вызовами отладчика.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT CanPersistPorts();
```

```csharp
int CanPersistPorts();
```

## <a name="parameters"></a>Параметры
 Нет.

## <a name="return-value"></a>Возвращаемое значение
 `S_OK` Если порты можно сохранить или `S_FALSE` указать, что порты не могут быть сохранены.

## <a name="remarks"></a>Комментарии
 Если поставщик порта может сохранять порты, он должен сделать это, когда он будет уничтожен, а затем перезагрузить его при повторном создании экземпляра.

## <a name="see-also"></a>См. также раздел
- [IDebugPortSupplier3](../../../extensibility/debugger/reference/idebugportsupplier3.md)
