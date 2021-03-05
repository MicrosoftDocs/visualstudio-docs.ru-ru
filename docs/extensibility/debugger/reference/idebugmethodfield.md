---
description: Этот интерфейс описывает метод.
title: Идебугмесодфиелд | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMethodField
helpviewer_keywords:
- IDebugMethodField interface
ms.assetid: a7dc9030-fc98-4cf1-b943-37a4003300b6
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 05a90252241dd51e1c567847891cf681c88d8fba
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102166311"
---
# <a name="idebugmethodfield"></a>IDebugMethodField
Этот интерфейс описывает метод.

## <a name="syntax"></a>Синтаксис

```
IDebugMethodField : IDebugContainerField
```

## <a name="notes-for-implementers"></a>Примечания для разработчиков
 Поставщик символов реализует этот интерфейс для того же объекта, который реализует интерфейс [идебугконтаинерфиелд](../../../extensibility/debugger/reference/idebugcontainerfield.md) . Этот интерфейс представляет собой специализацию, представляющую метод.

## <a name="notes-for-callers"></a>Примечания для вызывающих объектов
 Используйте [QueryInterface](/cpp/atl/queryinterface) для получения этого интерфейса из интерфейса [идебугконтаинерфиелд](../../../extensibility/debugger/reference/idebugcontainerfield.md) , если метод [Kind](../../../extensibility/debugger/reference/idebugfield-getkind.md) возвращает `FIELD_TYPE_METHOD` . Кроме того, методы, [жетпропертижеттер](../../../extensibility/debugger/reference/idebugpropertyfield-getpropertygetter.md), [жетпропертисеттер](../../../extensibility/debugger/reference/idebugpropertyfield-getpropertysetter.md)и [енумконструкторс](../../../extensibility/debugger/reference/idebugclassfield-enumconstructors.md), возвращают `IDebugMethodField` интерфейс.

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
 Помимо методов в интерфейсах [идебугфиелд](../../../extensibility/debugger/reference/idebugfield.md) и [идебугконтаинерфиелд](../../../extensibility/debugger/reference/idebugcontainerfield.md) , этот интерфейс реализует следующие методы.

|Метод|Описание|
|------------|-----------------|
|[EnumParameters](../../../extensibility/debugger/reference/idebugmethodfield-enumparameters.md)|Создает перечислитель для параметров метода.|
|[GetThis](../../../extensibility/debugger/reference/idebugmethodfield-getthis.md)|Возвращает указатель "this" объекта, содержащего метод.|
|[EnumAllLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumalllocals.md)|Создает перечислитель для всех локальных переменных метода.|
|[EnumLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md)|Создает перечислитель для выбранных локальных переменных метода.|
|[IsCustomAttributeDefined](../../../extensibility/debugger/reference/idebugmethodfield-iscustomattributedefined.md)|Определяет, определен ли определенный настраиваемый атрибут.|
|[EnumStaticLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumstaticlocals.md)|Создает перечислитель для статических локальных переменных метода.|
|[GetGlobalContainer](../../../extensibility/debugger/reference/idebugmethodfield-getglobalcontainer.md)|Возвращает глобальный контейнер метода.|
|[EnumArguments](../../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md)|Создает перечислитель для типа каждого аргумента, необходимого для вызова метода.|

## <a name="remarks"></a>Комментарии
 Метод может содержать параметры, а также локальные переменные.

## <a name="requirements"></a>Требования
 Заголовок: sh. h

 Пространство имен: Microsoft. VisualStudio. Debugger. Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также раздел
- [Интерфейсы поставщика символов](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
