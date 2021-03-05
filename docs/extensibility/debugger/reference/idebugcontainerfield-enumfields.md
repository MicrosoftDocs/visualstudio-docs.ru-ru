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
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 68ec12cd97318fc41b97c5a7701dff2346524101
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102143172"
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

## <a name="remarks"></a>Комментарии
 `dwKindFilter`Параметры, `dwModifiersFilter` и `pszNameFilter` можно комбинировать, например, чтобы выбрать все открытые виртуальные методы с именем MyMethod.

## <a name="see-also"></a>См. также раздел
- [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
- [FIELD_KIND](../../../extensibility/debugger/reference/field-kind.md)
- [FIELD_MODIFIERS](../../../extensibility/debugger/reference/field-modifiers.md)
- [NAME_MATCH](../../../extensibility/debugger/reference/name-match.md)
