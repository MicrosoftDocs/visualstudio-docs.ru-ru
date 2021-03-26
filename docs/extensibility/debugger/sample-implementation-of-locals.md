---
title: Пример реализации локальных переменных | Документация Майкрософт
description: Узнайте, как Visual Studio получает локальные переменные для метода из средства оценки выражений в этой статье.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], local variables
- expression evaluation, local variables
ms.assetid: 66a2e00a-f558-4e87-96b8-5ecf5509e04c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 4bf07dc6f47391af14c878021c742c2cb461bc85
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105070418"
---
# <a name="sample-implementation-of-locals"></a>Пример реализации локальных переменных
> [!IMPORTANT]
> В Visual Studio 2015 такой способ реализации оценивающих выражений является устаревшим. Дополнительные сведения о реализации вычислителей выражений CLR см. в разделе средства [оценки выражений CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) и [Пример управляемого средства оценки выражений](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Ниже приведены общие сведения о том, как Visual Studio получает локальные переменные для метода из средства оценки выражений (EE):

1. Visual Studio вызывает [жетдебугпроперти](../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md) модуля отладки (de) для получения объекта [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) , который представляет все свойства кадра стека, включая локальные переменные.

2. `IDebugStackFrame2::GetDebugProperty` вызывает [жетмесодпроперти](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md) , чтобы получить объект, описывающий метод, в котором произошла точка останова. В параметре DE предоставляется поставщик символов ([идебугсимболпровидер](../../extensibility/debugger/reference/idebugsymbolprovider.md)), адрес ([идебугаддресс](../../extensibility/debugger/reference/idebugaddress.md)) и связыватель ([идебугбиндер](../../extensibility/debugger/reference/idebugbinder.md)).

3. `IDebugExpressionEvaluator::GetMethodProperty` вызывает [жетконтаинерфиелд](../../extensibility/debugger/reference/idebugsymbolprovider-getcontainerfield.md) с переданным `IDebugAddress` объектом для получения [идебугконтаинерфиелд](../../extensibility/debugger/reference/idebugcontainerfield.md) , представляющего метод, содержащий указанный адрес.

4. `IDebugContainerField`Интерфейс запрашивает интерфейс [идебугмесодфиелд](../../extensibility/debugger/reference/idebugmethodfield.md) . Это интерфейс, предоставляющий доступ к локальным переменным метода.

5. `IDebugExpressionEvaluator::GetMethodProperty` создает экземпляр класса (вызываемого `CFieldProperty` в примере), который запускает `IDebugProperty2` интерфейс для представления локальных переменных метода. `IDebugMethodField`Объект помещается в этот `CFieldProperty` объект вместе с `IDebugSymbolProvider` объектами, `IDebugAddress` и `IDebugBinder` .

6. При `CFieldProperty` инициализации объекта вызывается [](../../extensibility/debugger/reference/idebugfield-getinfo.md) метод `IDebugMethodField` GetObject для объекта, чтобы получить структуру [FIELD_INFO](../../extensibility/debugger/reference/field-info.md) , содержащую все сведения о самом методе.

7. `IDebugExpressionEvaluator::GetMethodProperty` Возвращает `CFieldProperty` объект в виде `IDebugProperty2` объекта.

8. Visual Studio вызывает [енумчилдрен](../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) для возвращенного `IDebugProperty2` объекта с фильтром `guidFilterLocalsPlusArgs` , который возвращает объект [IEnumDebugPropertyInfo2](../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md) , содержащий локальные переменные метода. Это перечисление заполняется вызовами [енумлокалс](../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md) и [енумаргументс](../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md).

9. Visual Studio вызывает [Next](../../extensibility/debugger/reference/ienumdebugpropertyinfo2-next.md) , чтобы получить структуру [DEBUG_PROPERTY_INFO](../../extensibility/debugger/reference/debug-property-info.md) для каждого локального элемента. Эта структура содержит указатель на `IDebugProperty2` интерфейс для локального объекта.

10. Visual Studio вызывает [GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) для каждого локального объекта, чтобы получить имя, значение и тип локального компьютера. Эти сведения отображаются в окне **локальные** .

## <a name="in-this-section"></a>Содержание раздела
 [Реализация жетмесодпроперти](../../extensibility/debugger/implementing-getmethodproperty.md) Описывает реализацию [жетмесодпроперти](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md).

 [Перечислить локальные переменные](../../extensibility/debugger/enumerating-locals.md) Описывает, как модуль отладки (DE) выполняет вызов для перечисления локальных переменных или аргументов.

 [Получить локальные свойства](../../extensibility/debugger/getting-local-properties.md) Описывает, как DE вызывает метод, чтобы получить имя, тип и значение одной или нескольких локальных переменных.

 [Получить локальные значения](../../extensibility/debugger/getting-local-values.md) Обсуждается получение значения Local, для которого требуются службы объекта связывателя, заданные контекстом оценки.

 [Оценка локальных переменных](../../extensibility/debugger/evaluating-locals.md) Объясняет, как оцениваются локальные переменные.

## <a name="related-sections"></a>Связанные разделы
 [Контекст оценки](../../extensibility/debugger/evaluation-context.md) Предоставляет аргументы, которые передаются, когда метод DE вызывает средство оценки выражений (EE).

 [Пример мицее](/previous-versions/) Демонстрируется один подход к реализации для создания средства оценки выражений для языка Мик.

## <a name="see-also"></a>См. также
- [Отображение локальных переменных](../../extensibility/debugger/displaying-locals.md)