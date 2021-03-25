---
description: Этот интерфейс реализует ключевые методы, которые предоставляют функциональные возможности для интерфейсов IDebugProperty3 и Ипропертипроксеесиде.
title: Иивисуализерсервице | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEEVisualizerService
helpviewer_keywords:
- IEEVisualizerService interface
ms.assetid: 3bdb124b-c582-47ba-b465-13c6a1cdb702
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: cc712d0c86613d0ee6b30d754b759c17e3ab9bdc
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105086772"
---
# <a name="ieevisualizerservice"></a>IEEVisualizerService
> [!IMPORTANT]
> В Visual Studio 2015 такой способ реализации оценивающих выражений является устаревшим. Дополнительные сведения о реализации вычислителей выражений CLR см. в разделе средства [оценки выражений CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) и [Пример управляемого средства оценки выражений](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Этот интерфейс реализует ключевые методы, которые предоставляют функциональные возможности для интерфейсов [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) и [ипропертипроксеесиде](../../../extensibility/debugger/reference/ipropertyproxyeeside.md) .

## <a name="syntax"></a>Синтаксис

```
IEEVisualizerService : IUnknown
```

## <a name="notes-for-implementers"></a>Примечания для разработчиков
 Visual Studio реализует этот интерфейс, чтобы использовать средство оценки выражений (EE) для поддержки визуализаторов типов.

## <a name="notes-for-callers"></a>Примечания для вызывающих объектов
 EE вызывает [креатевисуализерсервице](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md) для получения этого интерфейса в рамках поддержки визуализаторов типов.

## <a name="methods-in-vtable-order"></a>Методы в порядке vtable

|Метод|Описание|
|------------|-----------------|
|[GetCustomViewerCount](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewercount.md)|Возвращает число пользовательских средств просмотра, о которых знает эта служба.|
|[GetCustomViewerList](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md)|Возвращает список пользовательских средств просмотра.|
|[GetPropertyProxy](../../../extensibility/debugger/reference/ieevisualizerservice-getpropertyproxy.md)|Возвращает прокси-объект для свойства.|
|[GetValueDisplayStringCount](../../../extensibility/debugger/reference/ieevisualizerservice-getvaluedisplaystringcount.md)|Извлекает количество строк значений, отображаемых для указанного свойства или поля.|

## <a name="remarks"></a>Remarks
 Интегрированная среда разработки использует интерфейс [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) , чтобы определить наличие пользовательских средств просмотра или визуализаторов типов для свойства. Создав службу визуализатора (с [креатевисуализерсервице](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md)), ee может предоставить функции `IDebugProperty3` и [ипропертипроксеесиде](../../../extensibility/debugger/reference/ipropertyproxyeeside.md) (который поддерживает просмотр и изменение интерфейсов значений свойств) и, таким образом, поддерживать визуализаторы типов.

 Если у EE имеется пользовательское средство просмотра, которое само реализует, то EE может добавить в `CLSID` конец списка, возвращенного [жеткустомвиеверлист](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md). Это позволяет элементу EE поддерживать как визуализаторы типов, так и собственные пользовательские средства просмотра. Просто убедитесь, что [жеткустомвиеверкаунт](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md) отражает добавление любых пользовательских средств просмотра.

 Обсуждение различий между визуализаторами и читателями см. в разделе [Визуализатор типов и пользовательское средство просмотра](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md) .

## <a name="requirements"></a>Требования
 Заголовок: ee. h

 Пространство имен: Microsoft. VisualStudio. Debugger. Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Интерфейсы вычисления выражений](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)
- [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)
- [CreateVisualizerService](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md)
- [Визуализатор типов и пользовательское средство просмотра](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)
