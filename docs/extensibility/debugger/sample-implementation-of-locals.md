---
title: Пример реализации локальных переменных | Документация Майкрософт
description: В этой статье вы узнаете, как Visual Studio получает для метода локальные переменные от вычислителя выражений.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: sample
helpviewer_keywords:
- debugging [Debugging SDK], local variables
- expression evaluation, local variables
ms.assetid: 66a2e00a-f558-4e87-96b8-5ecf5509e04c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: ac52f1524c4be2e4a7afcbd21fb437977fb663e3
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/25/2021
ms.locfileid: "112902284"
---
# <a name="sample-implementation-of-locals"></a>Пример реализации локальных переменных
> [!IMPORTANT]
> В Visual Studio 2015 такая реализация вычислителя выражений была сделана нерекомендуемой. Сведения о реализации вычислителей выражений в среде CLR см. на страницах [CLR expression evaluators](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) (Вычислители выражений CLR) и [Managed expression evaluator sample](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample) (Пример управляемого вычислителя выражений).

 Ниже приведен обзор того, каким образом Visual Studio получает для метода локальные переменные от вычислителя выражений.

1. Visual Studio вызывает метод модуля отладки [GetDebugProperty](../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md) и получает объект [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md), который представляет все свойства кадра стека, в том числе локальные переменные.

2. `IDebugStackFrame2::GetDebugProperty` вызывает метод [GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md) и получает объект, описывающий метод, в котором сработала точка останова. Модуль отладки предоставляет поставщик символов ([IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md)), адрес ([IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md)) и модуль привязки ([IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)).

3. `IDebugExpressionEvaluator::GetMethodProperty` вызывает [GetContainerField](../../extensibility/debugger/reference/idebugsymbolprovider-getcontainerfield.md) и предоставляет объект `IDebugAddress`, чтобы получить интерфейс [IDebugContainerField](../../extensibility/debugger/reference/idebugcontainerfield.md), который представляет метод, содержащий указанный адрес.

4. Интерфейс `IDebugContainerField` запрашивается для получения интерфейса [IDebugMethodField](../../extensibility/debugger/reference/idebugmethodfield.md), который и предоставляет доступ к локальным переменным анализируемого метода.

5. `IDebugExpressionEvaluator::GetMethodProperty` создает экземпляр класса (называемого в примере `CFieldProperty`), который использует интерфейс `IDebugProperty2` для представления локальных переменных метода. Объект `IDebugMethodField` помещается в объект `CFieldProperty` вместе с объектами `IDebugSymbolProvider`, `IDebugAddress` и `IDebugBinder`.

6. После инициализации объекта `CFieldProperty` вызывается метод [GetInfo](../../extensibility/debugger/reference/idebugfield-getinfo.md) для объекта `IDebugMethodField`, чтобы получить структуру [FIELD_INFO](../../extensibility/debugger/reference/field-info.md), содержащую все доступные для отображения сведения непосредственно о методе.

7. `IDebugExpressionEvaluator::GetMethodProperty` возвращает объект `CFieldProperty` в виде объекта `IDebugProperty2`.

8. Visual Studio вызывает для возвращенного объекта `IDebugProperty2` метод [EnumChildren](../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) с фильтром `guidFilterLocalsPlusArgs`, который возвращает объект [IEnumDebugPropertyInfo2](../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md), содержащий локальные переменные метода. Это перечисление заполняется вызовами [EnumLocals](../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md) и [EnumArguments](../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md).

9. Visual Studio вызывает метод [Next](../../extensibility/debugger/reference/ienumdebugpropertyinfo2-next.md), чтобы получить структуру [DEBUG_PROPERTY_INFO](../../extensibility/debugger/reference/debug-property-info.md) для каждой локальной переменной. Эта структура содержит для локальной переменной указатель на интерфейс `IDebugProperty2`.

10. Visual Studio вызывает для каждой локальной переменной метод [GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) и получает ее имя, значение и тип. Эти сведения отображаются в окне **Локальные переменные**.

## <a name="in-this-section"></a>В этом разделе
 [Реализация GetMethodProperty](../../extensibility/debugger/implementing-getmethodproperty.md) — описывает реализацию метода [GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md).

 [Перечисление локальных переменных](../../extensibility/debugger/enumerating-locals.md) — описывает, как модуль отладки совершает вызов для перечисления локальных переменных или аргументов.

 [Получение свойств локальных элементов](../../extensibility/debugger/getting-local-properties.md) — описывает, как модуль отладки совершает вызов для получения имени, типа и значений локальных переменных.

 [Получение значений локальных переменных](../../extensibility/debugger/getting-local-values.md) — описывает получение значения локальной переменной с помощью объекта модуля привязки, предоставляемого контекстом вычислений.

 [Вычисление локальных переменных](../../extensibility/debugger/evaluating-locals.md) — поясняет принципы вычисления локальных переменных.

## <a name="related-sections"></a>Связанные разделы
 [Контекст вычислений](../../extensibility/debugger/evaluation-context.md) — указывает аргументы, передаваемые при вызове вычислителя выражений из модуля отладки.

 [Пример для MyCEE](/previous-versions/) — демонстрирует один из подходов к реализации создания вычислителя выражений на языке MyC.

## <a name="see-also"></a>См. также
- [Отображение локальных переменных](../../extensibility/debugger/displaying-locals.md)