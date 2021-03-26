---
description: Создает перечислитель для интерфейсов, реализуемых этим классом.
title: 'Идебугклассфиелд:: Енуминтерфацесимплементед | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugClassField::EnumInterfacesImplemented
helpviewer_keywords:
- IDebugClassField::EnumInterfacesImplemented method
ms.assetid: e5523e45-d350-491e-a92c-fe0ca97d2052
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1763cbcd0a1c61150a054752c94a42f10127251a
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105088618"
---
# <a name="idebugclassfieldenuminterfacesimplemented"></a>IDebugClassField::EnumInterfacesImplemented
Создает перечислитель для интерфейсов, реализуемых этим классом.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT EnumInterfacesImplemented( 
   IEnumDebugFields** ppEnum
);
```

```csharp
int EnumInterfacesImplemented(
   out IEnumDebugFields ppEnum
);
```

## <a name="parameters"></a>Параметры
`ppEnum`\
заполняет Возвращает объект [иенумдебугфиелдс](../../../extensibility/debugger/reference/ienumdebugfields.md) , представляющий список реализованных интерфейсов. Возвращает значение null, если интерфейсы отсутствуют.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает S_OK или возвращает S_FALSE, если в этом классе не реализованы интерфейсы. В противном случае возвращается код ошибки.

## <a name="remarks"></a>Remarks
 Каждый элемент перечисления — это объект [идебугклассфиелд](../../../extensibility/debugger/reference/idebugclassfield.md) , описывающий интерфейс. Обратите внимание, что неуправляемый [!INCLUDE[vcprvc](../../../code-quality/includes/vcprvc_md.md)] код не использует интерфейсы как дискретную сущность, поэтому этот метод всегда возвращает значение NULL для неуправляемого [!INCLUDE[vcprvc](../../../code-quality/includes/vcprvc_md.md)] кода.

## <a name="see-also"></a>См. также
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
