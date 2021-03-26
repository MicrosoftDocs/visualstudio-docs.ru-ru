---
description: Возвращает список выбранных потомков ссылки.
title: 'IDebugReference2:: Енумчилдрен | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugReference2::EnumChildren
helpviewer_keywords:
- IDebugReference2::EnumChildren
ms.assetid: 35b3c2f3-69f4-4013-b555-f847221f62e8
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 92f55f511a68cca6685579eeb6d686108bf70799
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105071458"
---
# <a name="idebugreference2enumchildren"></a>IDebugReference2::EnumChildren
Возвращает список выбранных потомков ссылки. Зарезервировано для последующего использования.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT EnumChildren ( 
   DEBUGREF_INFO_FLAGS        dwFields,
   DWORD                      dwRadix,
   DBG_ATTRIB_FLAGS           dwAttribFilter,
   LPCOLESTR                  pszNameFilter,
   DWORD                      dwTimeout,
   IEnumDebugReferenceInfo2** ppEnum
);
```

```csharp
int EnumChildren ( 
   enum_DEBUGREF_INFO_FLAGS     dwFields,
   uint                         dwRadix,
   enum_DBG_ATTRIB_FLAGS        dwAttribFilter,
   string                       pszNameFilter,
   uint                         dwTimeout,
   out IEnumDebugReferenceInfo2 ppEnum
);
```

## <a name="parameters"></a>Параметры
`dwFields`\
окне Сочетание флагов из перечисления [DEBUGREF_INFO_FLAGS](../../../extensibility/debugger/reference/debugref-info-flags.md) , которое указывает, какие поля в перечисленных структурах [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) должны быть заполнены.

`dwRadix`\
окне Основание системы счисления, используемое при форматировании любой числовой информации.

`dwAttribFilter`\
окне Сочетание флагов из перечисления [DBG_ATTRIB_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md) , которое используется в качестве фильтра в сочетании с `pszNameFilter` параметром для выбора структур для перечисления.

`pszNameFilter`\
окне Строка, указывающая фильтр, например "микс", используемый в сочетании с `dwAttribFilter` параметром для выбора структур для перечисления.

`dwTimeout`\
окне Максимальное время ожидания (в миллисекундах) перед возвратом из этого метода. Используйте `INFINITE` для бесконечного ожидания.

`ppEnum`\
заполняет Возвращает объект [IEnumDebugReferenceInfo2](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2.md) , содержащий список запрошенных дочерних свойств.

## <a name="return-value"></a>Возвращаемое значение
 Всегда возвращает значение `E_NOTIMPL`.

## <a name="see-also"></a>См. также
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
- [DEBUGREF_INFO_FLAGS](../../../extensibility/debugger/reference/debugref-info-flags.md)
- [DBG_ATTRIB_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md)
- [IEnumDebugReferenceInfo2](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2.md)
