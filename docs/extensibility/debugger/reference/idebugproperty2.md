---
description: Этот интерфейс представляет свойство кадра стека, свойство документа программы или другое свойство.
title: IDebugProperty2 | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty2
helpviewer_keywords:
- IDebugProperty2 interface
ms.assetid: a7d5c70f-a1a5-4120-9f70-184e01c25bff
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 42cdd3f9e5fd1d92e007bb9a15cf9e1fa5e44e83
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102171456"
---
# <a name="idebugproperty2"></a>IDebugProperty2
Этот интерфейс представляет свойство кадра стека, свойство документа программы или другое свойство. Свойство обычно является результатом вычисления выражения.

> [!NOTE]
> Использование "Свойства" не следует путать с тем, что это означает переменную-член класса, хотя `IDebugProperty2` может представлять такую сущность.

## <a name="syntax"></a>Синтаксис

```
IDebugProperty2 : IUnknown
```

## <a name="notes-for-implementers"></a>Примечания для разработчиков
 Метод DE реализует этот интерфейс, чтобы представить определенный тип значения. Например, значение может быть числовым значением в результате вычисления выражения, контекста памяти, используемого для отображения памяти, или списка регистров и их значений.

## <a name="notes-for-callers"></a>Примечания для вызывающих объектов
 Вызовите [евалуатесинк](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) или [евалуатеасинк](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) , чтобы получить этот интерфейс, который представляет результат вычисления. `IDebugExpression2::EvaluateAsync` Возвращает этот интерфейс путем отправки интерфейса [IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md) в SDM, который, в свою очередь, вызывает метод [result](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getresult.md) для получения свойства.

- [Жетдебугпроперти](../../../extensibility/debugger/reference/idebugpropertycreateevent2-getdebugproperty.md) возвращает этот интерфейс, чтобы предоставить связанный документ скрипта.

- [Жетретурнвалуе](../../../extensibility/debugger/reference/idebugreturnvalueevent2-getreturnvalue.md) возвращает этот интерфейс, чтобы представить возвращаемое значение функции.

- [Жетдебугпроперти](../../../extensibility/debugger/reference/idebugprogram2-getdebugproperty.md) возвращает этот интерфейс для представления различных свойств программы, таких как имя или контекст памяти.

- [Жетдебугпроперти](../../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md) возвращает этот интерфейс для представления различных свойств кадра стека, например локальных переменных.

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
 В следующей таблице показаны методы `IDebugProperty2` .

|Метод|Описание|
|------------|-----------------|
|[GetPropertyInfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)|Заполняет структуру [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) , описывающую свойство.|
|[SetValueAsString](../../../extensibility/debugger/reference/idebugproperty2-setvalueasstring.md)|Задает значение свойства из строки.|
|[SetValueAsReference](../../../extensibility/debugger/reference/idebugproperty2-setvalueasreference.md)|Задает значение свойства из значения заданной ссылки.|
|[EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)|Перечисляет дочерние элементы свойства.|
|[GetParent](../../../extensibility/debugger/reference/idebugproperty2-getparent.md)|Возвращает родителя свойства.|
|[GetDerivedMostProperty](../../../extensibility/debugger/reference/idebugproperty2-getderivedmostproperty.md)|Возвращает свойство, описывающее наиболее производное свойство свойства.|
|[GetMemoryBytes](../../../extensibility/debugger/reference/idebugproperty2-getmemorybytes.md)|Возвращает байты памяти, составляющие значение свойства.|
|[GetMemoryContext](../../../extensibility/debugger/reference/idebugproperty2-getmemorycontext.md)|Возвращает контекст памяти для значения свойства.|
|[GetSize](../../../extensibility/debugger/reference/idebugproperty2-getsize.md)|Возвращает размер значения свойства в байтах.|
|[GetReference](../../../extensibility/debugger/reference/idebugproperty2-getreference.md)|Возвращает ссылку на значение этого свойства.|
|[GetExtendedInfo](../../../extensibility/debugger/reference/idebugproperty2-getextendedinfo.md)|Возвращает расширенные сведения о свойстве.|

## <a name="remarks"></a>Комментарии
 Свойство, представленное `IDebugProperty2` интерфейсом, может рассматриваться как значение с именем, типом и адресом. В общих чертах объект `IDebugProperty2` может представлять все, имеющее иерархическую структуру, с родительскими и дочерними узлами.

 Свойство обычно является транзитным, исходящим только до текущего кадра стека, например. С другой стороны, ссылка, представленная интерфейсом [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) , продолжается до тех пор, пока значение остается в памяти.

 Интегрированная среда разработки может использовать `IDebugProperty2` интерфейс, чтобы позволить пользователям просматривать и изменять свойства во время выполнения.

## <a name="requirements"></a>Требования
 Заголовок: мсдбг. h

 Пространство имен: Microsoft. VisualStudio. Debugger. Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также раздел
- [Базовые интерфейсы](../../../extensibility/debugger/reference/core-interfaces.md)
- [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
