---
description: Этот интерфейс представляет средство оценки выражений.
title: Идебужекспрессионевалуатор | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpressionEvaluator
helpviewer_keywords:
- IDebugExpressionEvaluator interface
ms.assetid: 0636d8c3-625a-49fa-94b6-516f22b7e1bc
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: b2e1fb465155bac2aa4be2b0d0a041715bf63bfa
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102152355"
---
# <a name="idebugexpressionevaluator"></a>IDebugExpressionEvaluator
> [!IMPORTANT]
> В Visual Studio 2015 такой способ реализации оценивающих выражений является устаревшим. Дополнительные сведения о реализации вычислителей выражений CLR см. в разделе средства [оценки выражений CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) и [Пример управляемого средства оценки выражений](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

Этот интерфейс представляет средство оценки выражений.

## <a name="syntax"></a>Синтаксис

```
IDebugExpressionEvaluator : IUnknown
```

## <a name="notes-for-implementers"></a>Примечания для разработчиков
Средство оценки выражений должно реализовывать этот интерфейс.

## <a name="notes-for-callers"></a>Примечания для вызывающих объектов
Чтобы получить этот интерфейс, создайте экземпляр средства оценки выражений с помощью `CoCreateInstance` метода, используя идентификатор класса (CLSID) оценщика. См. пример.

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
В следующей таблице показаны методы `IDebugExpressionEvaluator` .

|Метод|Описание|
|------------|-----------------|
|[Анализ](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md)|Преобразует строку выражения в проанализированное выражение.|
|[GetMethodProperty](../../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md)|Возвращает локальные переменные, аргументы и другие свойства метода.|
|[GetMethodLocationProperty](../../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodlocationproperty.md)|Преобразует положение и смещение метода в адрес памяти.|
|[Pragma](../../../extensibility/debugger/reference/idebugexpressionevaluator-setlocale.md)|Определяет, какой язык следует использовать для создания печатных результатов.|
|[SetRegistryRoot](../../../extensibility/debugger/reference/idebugexpressionevaluator-setregistryroot.md)|Задает корень реестра. Используется для параллельной отладки.|

## <a name="remarks"></a>Комментарии
В типичной ситуации модуль отладки (DE) создает экземпляр средства оценки выражений (EE) в результате вызова [парсетекст](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md). Так как язык и поставщик EE, который он хочет использовать, de знает, он получает идентификатор CLSID EE из реестра ( [вспомогательные методы SDK для функции отладки](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) , которые `GetEEMetric` помогают в этом извлечении).

После создания экземпляра EE метод DE вызывает [Parse](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) , чтобы проанализировать выражение и сохранить его в объекте [идебугпарседекспрессион](../../../extensibility/debugger/reference/idebugparsedexpression.md) . Позже при вызове [евалуатесинк](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) вычисляется выражение.

## <a name="requirements"></a>Требования
Заголовок: ee. h

Пространство имен: Microsoft. VisualStudio. Debugger. Interop

Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="example"></a>Пример
В этом примере показано, как создать экземпляр средства оценки выражений, используя поставщик символов и адрес в исходном коде. В этом примере используется функция, `GetEEMetric` из [вспомогательных средств SDK для отладки](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) библиотеки дбгметрик. lib.

```cpp
IDebugExpressionEvaluator GetExpressionEvaluator(IDebugSymbolProvider pSymbolProvider,
                                                 IDebugAddress *pSourceAddress)
{
    // This is typically defined globally but is specified here just
    // for this example.
    static const WCHAR strRegistrationRoot[] = L"Software\\Microsoft\\VisualStudio\\8.0Exp";

    IDebugExpressionEvaluator *pEE = NULL;
    if (pSymbolProvider != NULL && pSourceAddress != NULL) {
        HRESULT hr         = S_OK;
        GUID  languageGuid = { 0 };
        GUID  vendorGuid   = { 0 };

        hr = pSymbolProvider->GetLanguage(pSourceAddress,
                                          &languageGuid,
                                          &vendorGuid);
        if (SUCCEEDED(hr)) {
            CLSID clsidEE = { 0 };
            CComPtr<IDebugExpressionEvaluator> spExpressionEvaluator;
            // Get the expression evaluator's CLSID from the registry.
            ::GetEEMetric(languageGuid,
                          vendorGuid,
                          metricCLSID,
                          &clsidEE,
                          strRegistrationRoot);
            if (!IsEqualGUID(clsidEE,GUID_NULL)) {
                // Instantiate the expression evaluator.
                spExpressionEvaluator.CoCreateInstance(clsidEE);
            }
            if (spExpressionEvaluator != NULL) {
                pEE = spExpressionEvaluator.Detach();
            }
        }
    }
    return pEE;
}
```

## <a name="see-also"></a>См. также раздел
- [Интерфейсы вычисления выражений](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)
- [IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md)
- [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)
- [Вспомогательные пакеты SDK для отладки](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)
