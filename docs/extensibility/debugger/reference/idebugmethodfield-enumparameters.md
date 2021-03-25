---
description: Создает перечислитель для параметров метода.
title: 'Идебугмесодфиелд:: Енумпараметерс | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMethodField::EnumParameters
helpviewer_keywords:
- IDebugMethodField::EnumParameters method
ms.assetid: d77b1197-deb6-4144-8d1b-8b09949ccfac
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 0f2085b6a2aff6b41456f47a01c446b1c646f353
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105058395"
---
# <a name="idebugmethodfieldenumparameters"></a>IDebugMethodField::EnumParameters
Создает перечислитель для параметров метода.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT EnumParameters( 
   IEnumDebugFields** ppParams
);
```

```csharp
int EnumParameters(
   out IEnumDebugFields ppParams
);
```

## <a name="parameters"></a>Параметры
`ppParams`\
заполняет Возвращает объект [иенумдебугфиелдс](../../../extensibility/debugger/reference/ienumdebugfields.md) , представляющий список параметров метода. в противном случае возвращает значение null, если нет параметров.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает S_OK или возвращает S_FALSE, если нет параметров. В противном случае возвращается код ошибки.

## <a name="remarks"></a>Remarks
 Каждый элемент является объектом [идебугфиелд](../../../extensibility/debugger/reference/idebugfield.md) , представляющим различные типы параметров. Вызовите метод [Kind](../../../extensibility/debugger/reference/idebugfield-getkind.md) для каждого объекта, чтобы точно определить, какой тип параметра представляет объект.

 Параметр включает как имя переменной, так и ее тип. Первый параметр метода класса обычно является указателем this.

 Если требуются только типы параметров, вызовите метод [енумаргументс](../../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md) .

## <a name="see-also"></a>См. также
- [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [EnumArguments](../../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md)
