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
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 0114d0cf51769d6162563f6c60d51a3f031e19e2
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102159956"
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

## <a name="remarks"></a>Комментарии
 Свойства, возвращаемые этим методом, относятся только к программе. Если программе необходимо вернуть более одного свойства, то объект [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) , возвращаемый этим методом, является контейнером дополнительных свойств и вызовом метода [енумчилдрен](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) возвращает список всех свойств.

 Программа может предоставлять любое количество и тип дополнительных свойств, которые можно описать через `IDebugProperty2` интерфейс. Интегрированная среда разработки может отображать дополнительные свойства программы через пользовательский интерфейс обозревателя универсальных свойств.

## <a name="see-also"></a>См. также раздел
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)
