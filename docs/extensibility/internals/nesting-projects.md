---
title: Вложенные проекты | Документация Майкрософт
description: Сведения о вложении проектов, позволяющих разработчикам приложений, которые используют VSPackage для группировки схожих типов проектов в Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project nesting
- nested projects
- projects [Visual Studio SDK], child projects
- projects [Visual Studio SDK], nesting
ms.assetid: 12cce037-9840-4761-845e-5abd5fb317b0
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 30b562cac794b7ab960f055fe67a5d0cc4ec871f
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105063228"
---
# <a name="nesting-projects"></a>Проекты вложения
Разработчики корпоративных приложений, использующие пакет VS, могут группировать схожие типы проектов вместе с [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] помощью *вложений проектов*. Например, проект корпоративного шаблона использует вложенные проекты для группировки проектов по категориям. Проекты Business фасадной, проекты пользовательского веб-интерфейса и т. д. группируются в одной категории.

 В этом сценарии нет ограничений на количество проектов, которые разработчик может вкладывать в каждый родительский проект, хотя разработчик может программно предоставлять ограничения. Этот тип группирования можно также сделать рекурсивным. в этом случае проекты того же типа, что и дочерний проект, могут быть вложены в дочерний проект дочернего проекта, который является подпроектом родительского.

 Вложенность проектов не является встроенной частью [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . Необходимо написать код для включения вложенности и вложенных проектов в дочерних проектах. Родительский проект — это особый пакет VSPackage или тип проекта, созданный и зарегистрированный с собственным идентификатором GUID, включающий код, необходимый для реализации вложенности проекта.

 Пример вложения проектов см. в этом посвящении [: Реализация вложенных проектов](../../extensibility/internals/how-to-implement-nested-projects.md).

## <a name="nested-projects-example"></a>Пример вложенных проектов
 ![Решение вложенных проектов](../../extensibility/internals/media/vsnestedprojects.gif "вснестедпрожектс") Пример вложенных проектов

## <a name="see-also"></a>См. также
- [Рекомендации по выгрузке и перезагрузке вложенных проектов](../../extensibility/internals/considerations-for-unloading-and-reloading-nested-projects.md)
- [Поддержка мастера для вложенных проектов](../../extensibility/internals/wizard-support-for-nested-projects.md)
- [Регистрация шаблонов проектов и элементов](../../extensibility/internals/registering-project-and-item-templates.md)
- [Реализация обработки команд для вложенных проектов](../../extensibility/internals/implementing-command-handling-for-nested-projects.md)
- [Фильтрация диалогового окна AddItem для вложенных проектов](../../extensibility/internals/filtering-the-additem-dialog-box-for-nested-projects.md)
- [Контрольный список. Создание новых типов проектов](../../extensibility/internals/checklist-creating-new-project-types.md)
- [Параметры контекста](../../extensibility/internals/context-parameters.md)
- [Файл мастера (VSZ-файл)](../../extensibility/internals/wizard-dot-vsz-file.md)
