---
description: Создает перечислитель для полей контейнера.
title: 'Идебугконтаинерфиелд:: EnumFields | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugContainerField::EnumFields
helpviewer_keywords:
- IDebugContainerField::EnumFields method
ms.assetid: 9e5e681b-ad49-4c62-bd95-4afa11d61a57
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 63ce34fc9eddec84326982cf7d30fda919817040
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105077932"
---
# <a name="idebugcontainerfieldenumfields"></a>IDebugContainerField::EnumFields
Создает перечислитель для полей контейнера.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT EnumFields( 
   FIELD_KIND         dwKindFilter,
   FIELD_MODIFIERS    dwModifiersFilter,
   LPCOLESTR          pszNameFilter,
   NAME_MATCH         nameMatch,
   IEnumDebugFields** ppEnum
);
```

```csharp
int EnumFields(
   enum_ FIELD_KIND      dwKindFilter,
   enum_ FIELD_MODIFIERS dwModifiersFilter,
   string                pszNameFilter,
   NAME_MATCH            nameMatch,
   out IEnumDebugFields  ppEnum
);
```

## <a name="parameters"></a>Параметры
`dwKindFilter`\
окне Сочетание [FIELD_KIND](../../../extensibility/debugger/reference/field-kind.md) констант, которые выбирают поля для перечисления. Виды полей могут описывать типы хранения, например класс или примитив, или конкретные сведения, такие как локальный, параметр или указатель.

`dwModifiersFilter`\
окне Сочетание [FIELD_MODIFIERS](../../../extensibility/debugger/reference/field-modifiers.md) констант, которые выбирают поля для перечисления. Модификаторы полей могут иметь разрешения на доступ, такие как открытые или закрытые данные или сведения о хранении, например виртуальные, статические или окончательные.

`pszNameFilter`\
окне Имя поля для перечисления. Это может быть значение null, если должны возвращаться все поля.

`nameMatch`\
окне Значение из перечисления [NAME_MATCH](../../../extensibility/debugger/reference/name-match.md) , которое определяет, учитывается ли регистр при поиске.

`ppEnum`\
заполняет Возвращает объект [иенумдебугфиелдс](../../../extensibility/debugger/reference/ienumdebugfields.md) , представляющий список полей. Возвращает значение null, если нет полей.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает S_OK или S_FALSE, если нет полей. В противном случае возвращается код ошибки.

## <a name="remarks"></a>Remarks
 `dwKindFilter`Параметры, `dwModifiersFilter` и `pszNameFilter` можно комбинировать, например, чтобы выбрать все открытые виртуальные методы с именем MyMethod.

## <a name="see-also"></a>См. также
- [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
- [FIELD_KIND](../../../extensibility/debugger/reference/field-kind.md)
- [FIELD_MODIFIERS](../../../extensibility/debugger/reference/field-modifiers.md)
- [NAME_MATCH](../../../extensibility/debugger/reference/name-match.md)
