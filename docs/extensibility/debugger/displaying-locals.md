---
title: Отображение локальных переменных | Документация Майкрософт
description: Сведения о списке локальных переменных и аргументов, которые в совокупности называются локальными переменными метода, которые отображаются при приостановке выполнения.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation, displaying locals
ms.assetid: 62264cec-845b-4233-aed7-0b038fa79250
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 564b42a15e1420027b79cb5f00c70f61649ad4f9
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105097270"
---
# <a name="display-locals"></a>Отобразить локальные переменные
> [!IMPORTANT]
> В Visual Studio 2015 такой способ реализации оценивающих выражений является устаревшим. Дополнительные сведения о реализации вычислителей выражений CLR см. в разделе средства [оценки выражений CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) и [Пример управляемого средства оценки выражений](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Выполнение всегда происходит в контексте метода, также известного как содержащий метод или текущий метод. Когда выполнение приостанавливается, Visual Studio вызывает модуль отладки (DE) для получения списка локальных переменных и аргументов, которые вместе называются локальными переменными метода. Visual Studio отображает эти локальные переменные и их значения в окне **локальные** .

 Чтобы отобразить локальные переменные, метод DE обращается к [жетмесодпроперти](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md) , входящему в ee, и передает ему контекст вычисления, то есть поставщик символов (SP), текущий адрес выполнения и объект связывателя. Дополнительные сведения см. в разделе [контекст оценки](../../extensibility/debugger/evaluation-context.md). Если вызов завершается с ошибкой, `IDebugExpressionEvaluator::GetMethodProperty` метод возвращает объект [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) , который представляет метод, содержащий текущий адрес выполнения.

 Метод DE вызывает [енумчилдрен](../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) для получения объекта [IEnumDebugPropertyInfo2](../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md) , который фильтруется для возврата только локальных переменных и перечисления для получения списка структур [DEBUG_PROPERTY_INFO](../../extensibility/debugger/reference/debug-property-info.md) . Каждая структура содержит имя, тип и значение локального объекта. Тип и значение хранятся в виде форматированных строк, подходящих для вывода. Имя, тип и значение обычно отображаются вместе в одной строке окна **локальные переменные** .

> [!NOTE]
> Окна " **Быстрая проверка** " и " **Контрольные значения** " также отображают переменные с одинаковым форматом имени, значения и типа. Однако эти значения получаются путем вызова [GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) вместо `IDebugProperty2::EnumChildren` .

## <a name="in-this-section"></a>Содержание раздела
 [Пример реализации локальных переменных](../../extensibility/debugger/sample-implementation-of-locals.md) Использует примеры для пошагового выполнения процесса реализации локальных переменных.

## <a name="related-sections"></a>Связанные разделы
 [Контекст оценки](../../extensibility/debugger/evaluation-context.md) Объясняется, что когда модуль отладки (DE) вызывает средство оценки выражений (EE), оно передает три аргумента.

## <a name="see-also"></a>См. также
 [Написание вычислителя выражений CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
