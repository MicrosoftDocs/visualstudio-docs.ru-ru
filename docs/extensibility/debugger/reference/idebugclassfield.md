---
description: Этот интерфейс представляет класс как тип.
title: Идебугклассфиелд | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugClassField
helpviewer_keywords:
- IDebugClassField interface
ms.assetid: 49358cbc-8973-4862-9dcc-79b1248e6712
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: dfb07f066d65ed48678c814444881cb004f14697
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105088475"
---
# <a name="idebugclassfield"></a>IDebugClassField
Этот интерфейс представляет класс как тип.

## <a name="syntax"></a>Синтаксис

```
IDebugClassField : IDebugContainerField
```

## <a name="notes-for-implementers"></a>Примечания для разработчиков
 Поставщик символов реализует этот интерфейс для того же объекта, который реализует интерфейс [идебугконтаинерфиелд](../../../extensibility/debugger/reference/idebugcontainerfield.md) . Этот интерфейс является специализацией, представляющей тип класса.

## <a name="notes-for-callers"></a>Примечания для вызывающих объектов
 Ряд интерфейсов имеет методы, которые могут возвращать этот интерфейс, включая [идебугсимболпровидер](../../../extensibility/debugger/reference/idebugsymbolprovider.md), [идебугмесодфиелд](../../../extensibility/debugger/reference/idebugmethodfield.md)и [идебугкустоматтрибуте](../../../extensibility/debugger/reference/idebugcustomattribute.md). Кроме того, можно использовать [QueryInterface](/cpp/atl/queryinterface) для получения этого интерфейса из интерфейса [идебугконтаинерфиелд](../../../extensibility/debugger/reference/idebugcontainerfield.md) , если метод [Kind](../../../extensibility/debugger/reference/idebugfield-getkind.md) Возвращает флаг `FIELD_TYPE_CLASS` .

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
 Помимо методов в интерфейсах [идебугфиелд](../../../extensibility/debugger/reference/idebugfield.md) и [идебугконтаинерфиелд](../../../extensibility/debugger/reference/idebugcontainerfield.md) , этот интерфейс реализует следующее:

|Метод|Описание|
|------------|-----------------|
|[EnumBaseClasses](../../../extensibility/debugger/reference/idebugclassfield-enumbaseclasses.md)|Создает перечислитель для базовых классов этого класса.|
|[DoesInterfaceExist](../../../extensibility/debugger/reference/idebugclassfield-doesinterfaceexist.md)|Определяет, определен ли в классе определенный интерфейс.|
|[EnumNestedClasses](../../../extensibility/debugger/reference/idebugclassfield-enumnestedclasses.md)|Создает перечислитель для вложенных классов этого класса.|
|[GetEnclosingClass](../../../extensibility/debugger/reference/idebugclassfield-getenclosingclass.md)|Возвращает класс, который заключает в себя этот класс.|
|[EnumInterfacesImplemented](../../../extensibility/debugger/reference/idebugclassfield-enuminterfacesimplemented.md)|Создает перечислитель для интерфейсов, реализуемых этим классом.|
|[EnumConstructors](../../../extensibility/debugger/reference/idebugclassfield-enumconstructors.md)|Создает перечислитель для конструкторов этого класса.|
|[GetDefaultIndexer](../../../extensibility/debugger/reference/idebugclassfield-getdefaultindexer.md)|Возвращает имя индексатора по умолчанию.|
|[EnumNestedEnums](../../../extensibility/debugger/reference/idebugclassfield-enumnestedenums.md)|Создает перечислитель для вложенных перечислителей этого класса.|

## <a name="requirements"></a>Требования
 Заголовок: sh. h

 Пространство имен: Microsoft. VisualStudio. Debugger. Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Интерфейсы поставщика символов](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)
