---
title: Реализация визуализаторов типов и пользовательских средств просмотра | Документация Майкрософт
description: Сведения о реализации визуализаторов типов и пользовательских средств просмотра, позволяющих пользователю просматривать данные так, чтобы они были более осмысленными, чем дампы чисел.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], custom viewer
- debugging [Debugging SDK], type visualizer
ms.assetid: abef18c0-8272-4451-b82a-b4624edaba7d
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 79df5f6c7bf11c791f8de415f7cf1532321ed57a
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105059786"
---
# <a name="implement-type-visualizers-and-custom-viewers"></a>Реализация визуализаторов типов и пользовательских средств просмотра
> [!IMPORTANT]
> В Visual Studio 2015 такой способ реализации оценивающих выражений является устаревшим. Дополнительные сведения о реализации вычислителей выражений CLR см. в разделе средства [оценки выражений CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) и [Пример управляемого средства оценки выражений](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Визуализаторы типов и пользовательские средства просмотра позволяют пользователю просматривать данные определенного типа так, чтобы они были более осмысленными, чем простой шестнадцатеричный дамп чисел. Средство оценки выражений (EE) может связывать пользовательские средства просмотра с конкретными типами данных или переменных. Эти пользовательские средства просмотра реализуются с помощью EE. EE также может поддерживать внешние визуализаторы типов, которые могут поступать у другого стороннего поставщика или даже для конечного пользователя.

## <a name="discussion"></a>Разговор

### <a name="type-visualizers"></a>Визуализаторы типов
 Visual Studio запрашивает список визуализаторов типов и пользовательских средств просмотра для каждого объекта, отображаемого в окне контрольных значений. Средство оценки выражений (EE) предоставляет такой список для каждого типа, для которого требуется поддержка визуализаторов типов и пользовательских средств просмотра. Вызовы [жеткустомвиеверкаунт](../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md) и [жеткустомвиеверлист](../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) запускают весь процесс доступа к визуализаторам типов и пользовательским средствам просмотра (см. статью [визуализация и просмотр данных](../../extensibility/debugger/visualizing-and-viewing-data.md) для получения подробных сведений о вызывающей последовательности).

### <a name="custom-viewers"></a>Пользовательские средства просмотра
 Пользовательские средства просмотра реализуются в EE для определенного типа данных и представлены интерфейсом [идебугкустомвиевер](../../extensibility/debugger/reference/idebugcustomviewer.md) . Пользовательское средство просмотра не так гибко, как визуализатор типов, так как оно доступно только при выполнении в EE, реализующем это конкретное пользовательское средство просмотра. Реализация пользовательского средства просмотра проще, чем реализация поддержки визуализаторов типов. Однако поддерживающие визуализаторы типов обеспечивают максимальную гибкость для пользователя при визуализации своих данных. Оставшаяся часть этого обсуждения касается только визуализаторов типов.

## <a name="interfaces"></a>Интерфейсы
 EE реализует следующие интерфейсы для поддержки визуализаторов типов, которые будут использоваться в Visual Studio:

- [IEEVisualizerDataProvider](../../extensibility/debugger/reference/ieevisualizerdataprovider.md)

- [IPropertyProxyEESide](../../extensibility/debugger/reference/ipropertyproxyeeside.md)

- [IPropertyProxyProvider](../../extensibility/debugger/reference/ipropertyproxyprovider.md)

- [IEEDataStorage](../../extensibility/debugger/reference/ieedatastorage.md)

- [IDebugProperty3](../../extensibility/debugger/reference/idebugproperty3.md)

- [IDebugObject](../../extensibility/debugger/reference/idebugobject.md)

  EE использует следующие интерфейсы для поддержки визуализаторов типов:

- [IEEVisualizerService](../../extensibility/debugger/reference/ieevisualizerservice.md)

- [IEEVisualizerServiceProvider](../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)

- [IDebugBinder3](../../extensibility/debugger/reference/idebugbinder3.md)

## <a name="see-also"></a>См. также
- [Написание вычислителя выражений CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
- [Визуализация и просмотр данных](../../extensibility/debugger/visualizing-and-viewing-data.md)
- [IDebugCustomViewer](../../extensibility/debugger/reference/idebugcustomviewer.md)
