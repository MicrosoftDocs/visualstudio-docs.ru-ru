---
title: Визуализация и просмотр данных | Документация Майкрософт
description: Узнайте, как визуализаторы типов и пользовательские средства просмотра предоставляют данные разработчику. Средство оценки выражений поддерживает средства визуализации типов сторонних разработчиков.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], viewing data
- debugging [Debugging SDK], visualizing data
ms.assetid: 699dd0f5-7569-40b3-ade6-d0fe53e832bc
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 4fd87ba5af069a923853c18e43a1c8ba4943c91d
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105091426"
---
# <a name="visualizing-and-viewing-data"></a>Визуализация и просмотр данных
Визуализаторы типов и пользовательские средства просмотра представляют данные в удобном для разработчика виде. Средство оценки выражений (EE) может поддерживать визуализаторы типов сторонних производителей, а также предоставлять собственные пользовательские средства просмотра.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Определяет, сколько визуализаторов типов и пользовательских средств просмотра связаны с типом объекта путем вызова метода [жеткустомвиеверкаунт](../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md) . Если имеется хотя бы один визуализатор типов или пользовательское средство просмотра, Visual Studio вызывает метод [жеткустомвиеверлист](../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) для получения списка этих визуализаторов и средств просмотра (на самом деле, списка, который реализует визуализаторы и средства просмотра) и представляет их пользователю.

## <a name="supporting-type-visualizers"></a>Вспомогательные визуализаторы типов
 Существует ряд интерфейсов, которые должны быть реализованы в EE для поддержки визуализаторов типов. Эти интерфейсы можно разделить на две широкие категории: интерфейсы, в которых перечисляются визуализаторы типов и интерфейсы, обращающиеся к данным свойства.

### <a name="listing-type-visualizers"></a>Список визуализаторов типов
 EE поддерживает вывод списка визуализаторов типов в его реализации `IDebugProperty3::GetCustomViewerCount` и `IDebugProperty3::GetCustomViewerList` . Эти методы передают вызов соответствующим методам [жеткустомвиеверкаунт](../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewercount.md) и [жеткустомвиеверлист](../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md).

 [Иивисуализерсервице](../../extensibility/debugger/reference/ieevisualizerservice.md) получается путем вызова [креатевисуализерсервице](../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md). Для этого метода требуется интерфейс [IDebugBinder3](../../extensibility/debugger/reference/idebugbinder3.md) , полученный из интерфейса [идебугбиндер](../../extensibility/debugger/reference/idebugbinder.md) , переданного в [евалуатесинк](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md). `IEEVisualizerServiceProvider::CreateVisualizerService` также требуются интерфейсы [идебугсимболпровидер](../../extensibility/debugger/reference/idebugsymbolprovider.md) и [идебугаддресс](../../extensibility/debugger/reference/idebugaddress.md) , которые были переданы в `IDebugParsedExpression::EvaluateSync` . Последним интерфейсом, необходимым для создания `IEEVisualizerService` интерфейса, является интерфейс [иивисуализердатапровидер](../../extensibility/debugger/reference/ieevisualizerdataprovider.md) , который реализуется в ee. Этот интерфейс позволяет вносить изменения в свойство визуализации. Все данные свойств инкапсулируются в интерфейсе [идебугобжект](../../extensibility/debugger/reference/idebugobject.md) , который также реализуется в ee.

### <a name="accessing-property-data"></a>Доступ к данным свойств
 Доступ к данным свойства осуществляется через интерфейс [ипропертипроксеесиде](../../extensibility/debugger/reference/ipropertyproxyeeside.md) . Чтобы получить этот интерфейс, Visual Studio вызывает [QueryInterface](/cpp/atl/queryinterface) для объекта Property, чтобы получить интерфейс [ипропертипроксипровидер](../../extensibility/debugger/reference/ipropertyproxyprovider.md) (реализованный в том же объекте, который реализует интерфейс [IDebugProperty3](../../extensibility/debugger/reference/idebugproperty3.md) ), а затем вызывает метод [жетпропертипрокси](../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md) для получения `IPropertyProxyEESide` интерфейса.

 Все данные, передаваемые в интерфейс и из него `IPropertyProxyEESide` , инкапсулируются в интерфейсе [иидатастораже](../../extensibility/debugger/reference/ieedatastorage.md) . Этот интерфейс представляет массив байтов и реализуется как в Visual Studio, так и в EE. При изменении данных свойства Visual Studio создает `IEEDataStorage` объект, содержащий новые данные, и вызывает [функция createreplacementobject](../../extensibility/debugger/reference/ipropertyproxyeeside-createreplacementobject.md) с этим объектом данных, чтобы получить новый `IEEDataStorage` объект, который, в свою очередь, передается в [инплацеупдатеобжект](../../extensibility/debugger/reference/ipropertyproxyeeside-inplaceupdateobject.md) для обновления данных свойства. `IPropertyProxyEESide::CreateReplacementObject` позволяет компоненту EE создать экземпляр собственного класса, реализующего `IEEDataStorage` интерфейс.

## <a name="supporting-custom-viewers"></a>Поддержка пользовательских средств просмотра
 Флаг `DBG_ATTRIB_VALUE_CUSTOM_VIEWER` задается в `dwAttrib` поле структуры [DEBUG_PROPERTY_INFO](../../extensibility/debugger/reference/debug-property-info.md) (возвращается вызовом [GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)), чтобы указать, что с объектом связано пользовательское средство просмотра. Если этот флаг установлен, Visual Studio получает интерфейс [IDebugProperty3](../../extensibility/debugger/reference/idebugproperty3.md) из интерфейса [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) с помощью [QueryInterface](/cpp/atl/queryinterface).

 Если пользователь выбирает пользовательское средство просмотра, Visual Studio создает экземпляр пользовательского средства просмотра с помощью средства просмотра, `CLSID` предоставленного `IDebugProperty3::GetCustomViewerList` методом. Затем Visual Studio вызывает [дисплайвалуе](../../extensibility/debugger/reference/idebugcustomviewer-displayvalue.md) , чтобы отобразить значение для пользователя.

 Обычно `IDebugCustomViewer::DisplayValue` представляет собой представление данных, доступное только для чтения. Чтобы разрешить изменения данных, в EE должен быть реализован пользовательский интерфейс, поддерживающий изменение данных в объекте свойства. `IDebugCustomViewer::DisplayValue`Метод использует этот пользовательский интерфейс для поддержки изменения данных. Метод выполняет поиск пользовательского интерфейса в `IDebugProperty2` интерфейсе, переданном в качестве `pDebugProperty` аргумента.

## <a name="supporting-both-type-visualizers-and-custom-viewers"></a>Поддержка визуализаторов типов и пользовательских средств просмотра
 EE может поддерживать как визуализаторы типов, так и пользовательские средства просмотра в методах [жеткустомвиеверкаунт](../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md) и [жеткустомвиеверлист](../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) . Во-первых, EE добавляет число пользовательских средств просмотра, которые он передает, в значение, возвращаемое методом [жеткустомвиеверкаунт](../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewercount.md) . Во вторых, EE добавляет к `CLSID` списку, возвращенному методом [жеткустомвиеверлист](../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md) , собственные пользовательские средства просмотра.

## <a name="see-also"></a>См. также
- [Задачи отладки](../../extensibility/debugger/debugging-tasks.md)
- [Визуализатор типов и пользовательское средство просмотра](../../extensibility/debugger/type-visualizer-and-custom-viewer.md)
