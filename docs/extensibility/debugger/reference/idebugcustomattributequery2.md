---
description: Определяет существование пользовательского атрибута для этого поля и, если он существует, возвращает сведения об атрибуте.
title: IDebugCustomAttributeQuery2 | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCustomAttributeQuery2
helpviewer_keywords:
- IDebugCustomAttributeQuery interface
- IDebugCustomAttributeQuery2 interface
ms.assetid: 7cfa23e4-a05a-47a3-af6c-bd40c655014b
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 62461cbdbfe373f6c3d45569564e611efdd6f452
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102160229"
---
# <a name="idebugcustomattributequery2"></a>IDebugCustomAttributeQuery2
Определяет существование пользовательского атрибута для этого поля и, если он существует, возвращает сведения об атрибуте.

## <a name="syntax"></a>Синтаксис

```
IDebugCustomAttributeQuery2 : IDebugCustomAttributeQuery
```

## <a name="notes-for-implementers"></a>Примечания для разработчиков
 Поставщик символов реализует этот интерфейс для того же объекта, который реализует [идебугфиелд](../../../extensibility/debugger/reference/idebugfield.md) для поддержки настраиваемых атрибутов.

## <a name="notes-for-callers"></a>Примечания для вызывающих объектов
 Используйте [QueryInterface](/cpp/atl/queryinterface) для получения этого интерфейса из интерфейса [идебугфиелд](../../../extensibility/debugger/reference/idebugfield.md) .

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
 В следующей таблице показаны методы интерфейса **идебугкустоматтрибутекуери** .

|Метод|Описание|
|------------|-----------------|
|[IsCustomAttributeDefined](../../../extensibility/debugger/reference/idebugcustomattributequery2-iscustomattributedefined.md)|Определяет, существует ли настраиваемый атрибут по имени.|
|[GetCustomAttributeByName](../../../extensibility/debugger/reference/idebugcustomattributequery2-getcustomattributebyname.md)|Возвращает сведения об атрибуте для заданного пользовательского атрибута.|

 В дополнение к методам **идебугкустоматтрибутекуери** `IDebugCustomAttributeQuery2` реализует следующий метод:

|Метод|Описание|
|------------|-----------------|
|[EnumCustomAttributes](../../../extensibility/debugger/reference/idebugcustomattributequery2-enumcustomattributes.md)|Возвращает перечислитель для всех настраиваемых атрибутов, прикрепленных к этому полю.|

## <a name="remarks"></a>Комментарии
 Метод [иенумдебугкустоматтрибутес](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md) может возвращать перечислитель для всех пользовательских атрибутов, определенных для этого поля.

## <a name="requirements"></a>Требования
 Заголовок: sh. h

 Пространство имен: Microsoft. VisualStudio. Debugger. Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также раздел
- [Интерфейсы поставщика символов](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md)
