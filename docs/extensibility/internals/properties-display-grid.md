---
title: Отображение сетки свойств | Документация Майкрософт
description: Сведения о том, где поля имен свойств и значений свойств находятся в сетке в окно свойств и как работать с сеткой в расширении свойств.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- properties [Visual Studio SDK], grid
ms.assetid: 318e41b0-acf5-4842-b85e-421c9d5927c5
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: ee3d7d8d6277f9cfa0352cb4961644e4860b46bb
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/25/2021
ms.locfileid: "112899658"
---
# <a name="properties-display-grid"></a>Сетка "Отображение свойств"

В окне **Свойства** отображаются поля в сетке. Левый столбец содержит имена свойств; правый столбец содержит значения свойств.

## <a name="work-with-the-grid"></a>Работа с сеткой

В списке из двух столбцов отображаются свойства, независимые от конфигурации, которые можно изменить во время разработки и их текущие параметры. Обратите внимание, что все свойства могут не отображаться. Свойство может быть задано как скрытое, например, путем реализации <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.HideProperty%2A> метода. В частности, для скрытия свойств, имеющих дочерние свойства:

1. Установите `pfDisplay` параметр в <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.DisplayChildProperties%2A> значение `FALSE` .

2. Установите `pfHide` параметр в <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.HideProperty%2A> значение `TRUE` .

Для отправки сведений в окно **свойств** в интегрированной среде разработки используется <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> . <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> вызывается пакетами VSPackage для каждого окна, содержащего выбираемые объекты со связанными свойствами, которые должны отображаться в окне **Свойства** . Реализация вызовов **Обозреватель решений** <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> `GetProperty` с помощью [__VSHPROPID. VSHPROPID_BrowseObject](<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_BrowseObject>) в иерархии проекта для получения просматриваемых объектов в иерархии.

Если пакет VSPackage не поддерживает [__VSHPROPID. VSHPROPID_BrowseObject](<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_BrowseObject>), интегрированная среда разработки пытается использовать <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> значение для [__VSHPROPID. VSHPROPID_SelContainer](<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_SelContainer>) , что элемент или элементы иерархии являются предоставленными.

Не требуется создавать <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> пакет VSPackage, так как предоставляемый интегрированной средой разработки комплект (например, **Обозреватель решений**) создает его от <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> имени.

<xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> состоит из трех методов, вызываемых интегрированной средой разработки:

- <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.CountObjects%2A> содержит число объектов, выбранных для отображения в окне **Свойства** .

- <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.GetObjects%2A> Возвращает `IDispatch` объекты, выбранные для отображения в окне " **свойства** ".

- <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.SelectObjects%2A> делает возможным выбор любого из объектов, возвращаемых <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.GetObjects%2A> пользователем. Это позволяет VSPackage визуально обновлять выбор, отображаемый пользователю в пользовательском интерфейсе.

Окно **Свойства** извлекает из `IDispatch` объектов сведения для получения просматриваемых свойств. Браузер свойств использует, `IDispatch` чтобы запросить у объекта, какие свойства он поддерживает, выполнив запросы `ITypeInfo` , полученные из `IDispatch::GetTypeInfo` . Затем в браузере используются эти значения для заполнения окна **Свойства** и изменения значений отдельных свойств, отображаемых в сетке. Сведения о свойствах хранятся в самом объекте.

Так как возвращаемые объекты поддерживают `IDispatch` , вызывающий объект может получить такие сведения, как имя объекта, вызвав либо `IDispatch::Invoke` `ITypeInfo::Invoke` с заранее определенным идентификатором диспетчеризации (DISPID), представляющим нужную информацию. Объявленные идентификаторы DISPID являются отрицательными, чтобы гарантировать, что они не конфликтуют с определяемыми пользователем идентификаторами.

В окне **Свойства** отображаются различные типы полей в зависимости от атрибутов конкретных свойств выбранного объекта. К этим полям относятся поля редактирования, раскрывающиеся списки и ссылки на диалоговые окна настраиваемого редактора.

- Значения, содержащиеся в списке перечисления, извлекаются <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.GetObjects%2A> запросом к `IDispatch` . Значения, полученные из перечислимого списка, можно изменить в сетке свойства, дважды щелкнув имя поля или щелкнув значение и выбрав новое значение из раскрывающегося списка. Для свойств, которые имеют предопределенные параметры из перечисленных списков, дважды щелкните имя свойства в списке свойств, чтобы просмотреть доступные варианты. Для предопределенных свойств с двумя вариантами, такими как true/false, дважды щелкните имя свойства для переключения между вариантами.

- Если <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.HasDefaultValue%2A> имеет `false` значение, то есть изменение значения, значение отображается полужирным шрифтом. <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.CanResetPropertyValue%2A> используется для определения возможности сброса значения к исходному значению. Если это так, можно вернуться к значению по умолчанию, щелкнув его правой кнопкой мыши и выбрав пункт **Сброс** в открывшемся меню. В противном случае необходимо вернуть значение по умолчанию вручную. <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing> также позволяет локализовать и скрывать имена свойств, отображаемых во время разработки, но не влияет на имена свойств, отображаемые во время выполнения.

- Нажатие кнопки с многоточием (...) приводит к отображению списка значений свойств, из которых пользователь может выбрать (например, выбор цвета или список шрифтов). <xref:Microsoft.VisualStudio.Shell.Interop.IProvidePropertyBuilder> предоставляет эти значения.

## <a name="see-also"></a>См. также

- [Расширение свойств](../../extensibility/internals/extending-properties.md)
