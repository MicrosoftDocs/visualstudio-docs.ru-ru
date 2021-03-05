---
description: Этот интерфейс представляет пользовательский атрибут и может предоставить имя, родительский объект и тип класса атрибута.
title: Идебугкустоматтрибуте | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCustomAttribute
helpviewer_keywords:
- IDebugCustomAttribute interface
ms.assetid: c5ae41e9-00b9-4cca-871d-b8de9ef390d1
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 724aedb41a11607f89193b51f41e403a6da7dd45
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102154500"
---
# <a name="idebugcustomattribute"></a>IDebugCustomAttribute
Этот интерфейс представляет пользовательский атрибут и может предоставить имя, родительский объект и тип класса атрибута.

## <a name="syntax"></a>Синтаксис

```
IDebugCustomAttribute : IUnknown
```

## <a name="notes-for-implementers"></a>Примечания для разработчиков
 Поставщик символов реализует этот интерфейс для поддержки настраиваемых атрибутов, связанных с символом. Обычно он реализуется для собственного объекта.

## <a name="notes-for-callers"></a>Примечания для вызывающих объектов
 Вызов функции [Next](../../../extensibility/debugger/reference/ienumdebugcustomattributes-next.md) возвращает этот интерфейс. Вызов метода [EnumCustomAttributes](../../../extensibility/debugger/reference/idebugcustomattributequery2-enumcustomattributes.md) возвращает интерфейс [иенумдебугкустоматтрибутес](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md) .

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
 В следующей таблице показаны методы `IDebugCustomAttribute` .

|Метод|Описание|
|------------|-----------------|
|[GetParentField](../../../extensibility/debugger/reference/idebugcustomattribute-getparentfield.md)|Возвращает поле, к которому присоединен текущий атрибут.|
|[GetAttributeTypeField](../../../extensibility/debugger/reference/idebugcustomattribute-getattributetypefield.md)|Возвращает тип класса настраиваемого атрибута.|
|[GetName](../../../extensibility/debugger/reference/idebugcustomattribute-getname.md)|Возвращает имя настраиваемого атрибута.|
|[GetAttributeBytes](../../../extensibility/debugger/reference/idebugcustomattribute-getattributebytes.md)|Возвращает сведения об атрибуте в виде большого двоичного объекта в байтах.|

## <a name="remarks"></a>Комментарии
 Настраиваемый атрибут — это структура C#, которая предоставляет пользовательские метаданные, связанные с определенным классом или методом.

## <a name="requirements"></a>Требования
 Заголовок: sh. h

 Пространство имен: Microsoft. VisualStudio. Debugger. Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также раздел
- [Интерфейсы поставщика символов](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [IDebugCustomAttributeQuery2](../../../extensibility/debugger/reference/idebugcustomattributequery2.md)
- [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md)
