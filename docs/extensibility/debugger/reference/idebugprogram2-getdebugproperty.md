---
description: Возвращает свойства программы.
title: 'IDebugProgram2:: Жетдебугпроперти | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::GetDebugProperty
helpviewer_keywords:
- IDebugProgram2::GetDebugProperty
ms.assetid: d194224e-f0e6-46ab-85d4-9e2639e28946
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 60e551829a1f424a9bb7f89642f1d692db8d8032
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105075982"
---
# <a name="idebugprogram2getdebugproperty"></a>IDebugProgram2::GetDebugProperty
Возвращает свойства программы.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetDebugProperty( 
   IDebugProperty2** ppProperty
);
```

```csharp
int GetDebugProperty( 
   out IDebugProperty2 ppProperty
);
```

## <a name="parameters"></a>Параметры
`ppProperty`\
заполняет Возвращает объект [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) , представляющий свойства программы.

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Remarks
 Свойства, возвращаемые этим методом, относятся только к программе. Если программе необходимо вернуть более одного свойства, то объект [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) , возвращаемый этим методом, является контейнером дополнительных свойств и вызовом метода [енумчилдрен](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) возвращает список всех свойств.

 Программа может предоставлять любое количество и тип дополнительных свойств, которые можно описать через `IDebugProperty2` интерфейс. Интегрированная среда разработки может отображать дополнительные свойства программы через пользовательский интерфейс обозревателя универсальных свойств.

## <a name="see-also"></a>См. также
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)
