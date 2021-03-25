---
description: Извлекает список дочерних элементов свойства.
title: 'IDebugProperty2:: Енумчилдрен | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty2::EnumChildren
helpviewer_keywords:
- IDebugProperty2::EnumChildren
ms.assetid: cf79f666-65d1-417c-af7c-9271bac9a267
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 58378b04589c7e55272eeb3c2ce761516835a77c
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105065051"
---
# <a name="idebugproperty2enumchildren"></a>IDebugProperty2::EnumChildren
Извлекает список дочерних элементов свойства.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT EnumChildren ( 
   DEBUGPROP_INFO_FLAGS      dwFields,
   DWORD                     dwRadix,
   REFGUID                   guidFilter,
   DBG_ATTRIB_FLAGS          dwAttribFilter,
   LPCOLESTR                 pszNameFilter,
   DWORD                     dwTimeout,
   IEnumDebugPropertyInfo2** ppEnum
);
```

```csharp
int EnumChildren ( 
   enum_DEBUGPROP_INFO_FLAGS   dwFields,
   uint                        dwRadix,
   ref Guid                    guidFilter,
   uint                        dwAttribFilter,
   string                      pszNameFilter,
   uint                        dwTimeout,
   out IEnumDebugPropertyInfo2 ppEnum
);
```

## <a name="parameters"></a>Параметры
`dwFields`\
окне Сочетание флагов из перечисления [DEBUGPROP_INFO_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md) , которое указывает, какие поля в перечисленных структурах [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) должны быть заполнены.

`dwRadix`\
окне Указывает основание системы счисления, используемое при форматировании любых числовых данных.

`guidFilter`\
окне Идентификатор GUID фильтра, используемого с `dwAttribFilter` параметрами и, `pszNameFilter` для выбора `DEBUG_PROPERTY_INFO` дочерних элементов для перечисления. Например, `guidFilterLocals` фильтры для локальных переменных.

`dwAttribFilter`\
окне Сочетание флагов из перечисления [DBG_ATTRIB_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md) , которое указывает тип объектов для перечисления, например `DBG_ATTRIB_METHOD` для всех методов, которые могут быть дочерними для данного свойства. Используется в сочетании с `guidFilter` параметрами и `pszNameFilter` .

`pszNameFilter`\
окне Имя фильтра, используемого с `guidFilter` параметрами и, `dwAttribFilter` для выбора `DEBUG_PROPERTY_INFO` дочерних элементов для перечисления. Например, при присвоении этому параметру фильтров "микс" для всех дочерних элементов с именем "микс".

`dwTimeout`\
окне Указывает максимальное время ожидания (в миллисекундах) перед возвратом из этого метода. Используйте `INFINITE` для бесконечного ожидания.

`ppEnum`\
заполняет Возвращает объект [IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md) , содержащий список дочерних свойств.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает `S_OK` ; в противном случае возвращает код ошибки.

## <a name="see-also"></a>См. также
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [DEBUGPROP_INFO_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md)
- [DBG_ATTRIB_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md)
- [IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md)
