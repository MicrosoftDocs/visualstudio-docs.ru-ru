---
description: Этот интерфейс предоставляет возможность изменения значения объекта с помощью визуализатора типов.
title: Иивисуализердатапровидер | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEEVisualizerDataProvider
helpviewer_keywords:
- IEEVisualizerDataProvider interface
ms.assetid: 5fdfe6e3-b94e-4edb-acc5-41d8773d8ca5
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9c2bea2a99b259ac255a4244501ee246fd83e8b5
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102222891"
---
# <a name="ieevisualizerdataprovider"></a>IEEVisualizerDataProvider
> [!IMPORTANT]
> В Visual Studio 2015 такой способ реализации оценивающих выражений является устаревшим. Дополнительные сведения о реализации вычислителей выражений CLR см. в разделе средства [оценки выражений CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) и [Пример управляемого средства оценки выражений](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Этот интерфейс предоставляет возможность изменения значения объекта с помощью визуализатора типов.

## <a name="syntax"></a>Синтаксис

```
IEEVisualizerDataProvider : IUnknown
```

## <a name="notes-for-implementers"></a>Примечания для разработчиков
 Средство оценки выражений реализует этот интерфейс для поддержки изменения данных в объекте свойства с помощью визуализатора типов.

## <a name="notes-for-callers"></a>Примечания для вызывающих объектов
 Этот интерфейс используется при создании объекта [иивисуализерсервице](../../../extensibility/debugger/reference/ieevisualizerservice.md) с помощью вызова [креатевисуализерсервице](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md). Дополнительные сведения см. в разделе [визуализация и просмотр данных](../../../extensibility/debugger/visualizing-and-viewing-data.md) .

## <a name="methods-in-vtable-order"></a>Методы в порядке vtable

|Метод|Описание|
|------------|-----------------|
|[CanSetObjectForVisualizer](../../../extensibility/debugger/reference/ieevisualizerdataprovider-cansetobjectforvisualizer.md)|Определяет, можно ли обновить объект (и впоследствии его значение), который представляет этот визуализатор.|
|[GetNewObjectForVisualizer](../../../extensibility/debugger/reference/ieevisualizerdataprovider-getnewobjectforvisualizer.md)|Вызывает повторное вычисление объекта для этого визуализатора.|
|[GetObjectForVisualizer](../../../extensibility/debugger/reference/ieevisualizerdataprovider-getobjectforvisualizer.md)|Возвращает существующий объект для этого визуализатора (вычисление не выполняется).|
|[SetObjectForVisualizer](../../../extensibility/debugger/reference/ieevisualizerdataprovider-setobjectforvisualizer.md)|Обновляет объект для этого визуализатора, тем самым изменяя значение, представленное визуализатором.|

## <a name="remarks"></a>Комментарии
 Служба визуализатора (представленная интерфейсом [иивисуализерсервице](../../../extensibility/debugger/reference/ieevisualizerservice.md) и возвращаемая методом [креатевисуализерсервице](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md)) сохраняет ссылку на объект, реализующий `IEEVisualizerDataProvider` интерфейс. В результате `IEEVisualizerDataProvider` интерфейс не должен быть реализован на том же объекте, который реализует [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) , если этот объект поддерживает ссылку на `IEEVisualizerService` объект: результаты циклической ссылки и взаимоблокировка возникает при уничтожении объектов. Рекомендуемым подходом является реализация `IEEVisualizerDataProvider` на отдельном объекте, к которому `IDebugProperty2` объект делегируется без вызова `IUnknown::AddRef` .

## <a name="requirements"></a>Требования
 Заголовок: ee. h

 Пространство имен: Microsoft. VisualStudio. Debugger. Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также раздел
- [Интерфейсы вычисления выражений](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md)
- [IEEVisualizerServiceProvider](../../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)
- [Визуализация и просмотр данных](../../../extensibility/debugger/visualizing-and-viewing-data.md)
