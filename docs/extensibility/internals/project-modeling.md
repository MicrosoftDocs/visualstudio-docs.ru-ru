---
title: Моделирование проекта | Документация Майкрософт
description: Сведения о стандартных объектах проекта, необходимых для создания автоматизации для нового типа проекта, и пути, которым следует автоматизация проекта.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK], implementing project objects
- project models, automation
ms.assetid: c8db8fdb-88c1-4b12-86fe-f3c30a18f9ee
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 506606291996c94ff10514c6c57f83c6e1133862
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105062828"
---
# <a name="project-modeling"></a>Моделирование проекта
Следующим шагом в предоставлении автоматизации для проекта является реализация стандартных объектов проекта: <xref:EnvDTE.Projects> коллекций и, `ProjectItems` `Project` объектов и, <xref:EnvDTE.ProjectItem> а также оставшихся объектов, уникальных для вашей реализации. Эти стандартные объекты определены в файле Дтеинтернал. h. Реализация стандартных объектов представлена в примере Бскпрж. Эти классы можно использовать в качестве моделей для создания собственных объектов стандартных проектов, которые будут изолированы параллельно с объектами проекта из других типов проектов.

 Потребитель автоматизации предполагает возможность вызова <xref:EnvDTE.Solution> (" `<UniqueProjName>")` and <xref:EnvDTE.ProjectItems> ()", `n` где n — номер индекса для получения конкретного проекта в решении. В результате этого вызова службы автоматизации среда вызывается <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.GetProperty%2A> в соответствующей иерархии проекта, передавая VSITEMID_ROOT в качестве параметра itemId и VSHPROPID_ExtObject в качестве параметра вшпропид. `IVsHierarchy::GetProperty` Возвращает `IDispatch` указатель на объект автоматизации `Project` , предоставляющий реализуемый базовый интерфейс.

 Ниже приведен синтаксис `IVsHierarchy::GetProperty` .

 `HRESULT GetProperty (`

 `VSITEMID` `itemid`,

 `VSHPROPID` `propid`,

 `VARIANT` `*pvar`

 `);`

 Проекты, предназначенные для вложенности и использования коллекций для создания групп элементов проекта. Иерархия выглядит следующим образом.

```
Projects
  |- Project
      |- ProjectItems (a collection of ProjectItem)
          |- ProjectItem (single object) or ProjectItems (another collection)
```

 Вложение означает, что <xref:EnvDTE.ProjectItem> объект может быть <xref:EnvDTE.ProjectItems> собран одновременно, так как `ProjectItems` коллекция может содержать вложенные объекты. Пример базового проекта не демонстрирует такое вложение. Реализуя `Project` объект, вы участвуете в древовидной структуре, которая характеризует структуру общей модели автоматизации.

 Автоматизация проекта соответствует пути на следующей схеме.

 ![Объекты проектов Visual Studio](../../extensibility/internals/media/projectobjects.gif "прожектобжектс") Автоматизация проектов

 Если объект не реализуется `Project` , среда по-прежнему будет возвращать универсальный `Project` объект, содержащий только имя проекта.

## <a name="see-also"></a>См. также
- <xref:EnvDTE.Projects>
- <xref:EnvDTE.ProjectItem>
- <xref:EnvDTE.ProjectItems>
