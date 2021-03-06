---
description: Этот интерфейс предоставляет прокси-интерфейс для просмотра и изменения данных объекта.
title: Ипропертипроксипровидер | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IPropertyProxyProvider
helpviewer_keywords:
- IPropertyProxyProvider interface
ms.assetid: 52e9f7fc-6fe0-4d23-890b-5673dca8c3cb
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 87bc0bfa11c54f8eade595f6bf0bfaba1fa277ca
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105058096"
---
# <a name="ipropertyproxyprovider"></a>IPropertyProxyProvider
Этот интерфейс предоставляет прокси-интерфейс для просмотра и изменения данных объекта.

## <a name="syntax"></a>Синтаксис

```
IPropertyProxyProvider : IUnknown
```

## <a name="notes-for-implementers"></a>Примечания для разработчиков
 Средство оценки выражений (EE) реализует этот интерфейс для того же объекта, который реализует интерфейс [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) как часть поддержки визуализаторов типов в ee.

## <a name="notes-for-callers"></a>Примечания для вызывающих объектов
 Вызовите [QueryInterface](/cpp/atl/queryinterface) для `IDebugProperty3` интерфейса, чтобы получить этот интерфейс.

## <a name="methods-in-vtable-order"></a>Методы в порядке vtable
 `IPropertyProxyProvider`Интерфейс реализует следующий метод:

|Метод|Описание|
|------------|-----------------|
|[GetPropertyProxy](../../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md)|Извлекает интерфейс прокси-сервера свойства для просмотра данных в объекте.|

## <a name="remarks"></a>Remarks
 Несмотря на то, что EE реализует этот интерфейс, реализация [жетпропертипрокси](../../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md) обычно обрабатывается с помощью [жетпропертипрокси](../../../extensibility/debugger/reference/ieevisualizerservice-getpropertyproxy.md). Дополнительные сведения о получении интерфейса Иивисуализерсервице см. в разделе [визуализация и просмотр данных](../../../extensibility/debugger/visualizing-and-viewing-data.md) .

## <a name="requirements"></a>Требования
 Заголовок: мсдбг. h

 Пространство имен: Microsoft. VisualStudio. Debugger. Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Основные интерфейсы](../../../extensibility/debugger/reference/core-interfaces.md)
- [GetPropertyProxy](../../../extensibility/debugger/reference/ieevisualizerservice-getpropertyproxy.md)
- [Визуализатор типов и пользовательское средство просмотра](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)
- [Визуализация и просмотр данных](../../../extensibility/debugger/visualizing-and-viewing-data.md)
