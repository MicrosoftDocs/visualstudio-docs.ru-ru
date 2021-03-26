---
description: Создает перечислитель для свойств, связанных с кадром стека, например локальных переменных.
title: 'IDebugStackFrame2:: Енумпропертиес | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugStackFrame2::EnumProperties
helpviewer_keywords:
- IDebugStackFrame2::EnumProperties
ms.assetid: 334bb95e-c7e0-4008-9f06-8c3999e47ee8
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: bd9494434a8dc3fa2cff9eb28ddea8fb48302ca6
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105071159"
---
# <a name="idebugstackframe2enumproperties"></a>IDebugStackFrame2::EnumProperties
Создает перечислитель для свойств, связанных с кадром стека, например локальных переменных.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT EnumProperties ( 
   DEBUGPROP_INFO_FLAGS      dwFieldSpec,
   UINT                      nRadix,
   REFIID                    refiid,
   DWORD                     dwTimeout,
   ULONG*                    pcelt,
   IEnumDebugPropertyInfo2** ppEnum
);
```

```csharp
int EnumProperties ( 
   enum_DEBUGPROP_INFO_FLAGS   dwFieldSpec,
   uint                        nRadix,
   ref Guid                    refiid,
   uint                        dwTimeout,
   out uint                    pcelt,
   out IEnumDebugPropertyInfo2 ppEnum
);
```

## <a name="parameters"></a>Параметры
`dwFieldSpec`\
окне Сочетание флагов из перечисления [DEBUGPROP_INFO_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md) , которое указывает, какие поля в перечисленных структурах [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) должны быть заполнены.

`nRadix`\
окне Основание системы счисления, используемое при форматировании любой числовой информации.

`refiid`\
окне Идентификатор GUID фильтра, используемый для выбора структур, [подDEBUG_PROPERTY_INFOых](../../../extensibility/debugger/reference/debug-property-info.md) для перечисления, например `guidFilterLocals` .

`dwTimeout`\
окне Максимальное время ожидания (в миллисекундах) перед возвратом из этого метода. Используйте `INFINITE` для бесконечного ожидания.

`pcelt`\
заполняет Возвращает число перечисленных свойств. Это аналогично вызову метода [NOCOUNT](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-getcount.md) .

`ppEnum`\
заполняет Возвращает объект [IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md) , содержащий список требуемых свойств.

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Remarks
 Поскольку этот метод позволяет получать все выбранные свойства с помощью одного вызова, он выполняется быстрее, чем последовательный вызов методов [жетдебугпроперти](../../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md) и [енумчилдрен](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) .

## <a name="see-also"></a>См. также
- [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)
- [DEBUGPROP_INFO_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md)
- [IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md)
- [GetCount](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-getcount.md)
- [GetDebugProperty](../../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md)
- [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)
