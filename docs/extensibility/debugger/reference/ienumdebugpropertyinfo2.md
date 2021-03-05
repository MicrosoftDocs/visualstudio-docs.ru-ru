---
description: Этот интерфейс перечисляет структуры DEBUG_PROPERTY_INFO.
title: IEnumDebugPropertyInfo2 | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugPropertyInfo2
helpviewer_keywords:
- IEnumDebugPropertyInfo2
ms.assetid: fdea8262-40b8-473e-88ba-639e4c4648e6
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: fea2dc5cf958f87463af9dfca9f29bec5d01a82b
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102224191"
---
# <a name="ienumdebugpropertyinfo2"></a>IEnumDebugPropertyInfo2
Этот интерфейс перечисляет структуры [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) .

## <a name="syntax"></a>Синтаксис

```
IEnumDebugPropertyInfo2 : IUnknown
```

## <a name="notes-for-implementers"></a>Примечания для разработчиков
 Модуль отладки (DE) реализует этот интерфейс для представления сведений о конкретном свойстве.

## <a name="notes-for-callers"></a>Примечания для вызывающих объектов
 Вызовите [енумчилдрен](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) , чтобы получить этот интерфейс, представляющий дочерние элементы определенного свойства. Вызовите [енумпропертиес](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md) , чтобы получить этот интерфейс, представляющий свойства определенного кадра стека.

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
 В следующей таблице показаны методы `IEnumDebugPropertyInfo2` .

|Метод|Описание|
|------------|-----------------|
|[Вперед](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-next.md)|Извлекает указанное число структур [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) в последовательности перечисления.|
|[Skip](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-skip.md)|Пропускает указанное число структур [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) в последовательности перечисления.|
|[Сброс](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-reset.md)|Сбрасывает последовательность перечислений в начало.|
|[Клонировать](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-clone.md)|Создает перечислитель, который содержит то же состояние перечисления, что и текущий перечислитель.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-getcount.md)|Возвращает число структур [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) в перечислителе.|

## <a name="remarks"></a>Комментарии
 Как правило, свойство представляет собой иерархию данных, которая может включать имя, значение, адрес и тип, а также любые другие сведения, соответствующие связанному объекту свойства или кадру стека. Дополнительные сведения см. в разделе [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) .

## <a name="requirements"></a>Требования
 Заголовок: мсдбг. h

 Пространство имен: Microsoft. VisualStudio. Debugger. Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также раздел
- [Базовые интерфейсы](../../../extensibility/debugger/reference/core-interfaces.md)
- [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)
- [EnumProperties](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md)
