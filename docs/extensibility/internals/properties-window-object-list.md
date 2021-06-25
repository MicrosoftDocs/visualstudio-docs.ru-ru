---
title: Список объектов окна свойств | Документация Майкрософт
description: Сведения о интерфейсах, используемых для взаимодействия со списком объектов в окно свойств в интегрированной среде разработки Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Properties window, object list
ms.assetid: 6c159c9d-345d-4b23-8ddd-9839d338b62f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 908acf3f8ecad390266c3d085778dc13077a6fa8
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/25/2021
ms.locfileid: "112903441"
---
# <a name="properties-window-object-list"></a>Список объектов окна свойств
Список объектов в окне « **Свойства** » — это раскрывающийся список, позволяющий изменить выделенный фрагмент на другие объекты, доступные в одном или нескольких выбранных окнах. Выбор другого объекта из этого списка вызывает метод, <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.SelectObjects%2A> чтобы сообщить среде о том, что был выбран новый объект. Сведения, отображаемые в окне **Свойства** , изменяются для отображения свойств, связанных с вновь выбранным объектом.

## <a name="the-object-list"></a>Список объектов
 Список объектов состоит из двух полей: имени объекта (отображается полужирным шрифтом) и типа объекта.

 Имя объекта, отображаемое слева от типа объекта полужирным шрифтом, извлекается из самого объекта с помощью `Name` свойства, предоставленного <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo> интерфейсом. <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo.GetClassInfo%2A>, единственный метод в <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo> , возвращает <xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo> для компонентного класса этого интерфейса. В окне **Свойства** используется <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo> для получения имени компонентного класса, который отображается как имя объекта в раскрывающемся списке.

 Если объект не имеет `Name` свойства, имя не отображается в области имен в списке объектов. Если требуется, чтобы имя отображалось в списке объектов, можно добавить в объект свойство Name.

 Если COM-объект не реализует <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo> , в окне **свойства** отображается имя интерфейса вместо имени объекта в левой части списка.

## <a name="see-also"></a>См. также
- [Расширение свойств](../../extensibility/internals/extending-properties.md)
