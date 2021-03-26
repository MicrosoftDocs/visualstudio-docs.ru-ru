---
title: Вклад в диалоговое окно "Добавление нового элемента" | Документация Майкрософт
description: Сведения о том, как вносить изменения в диалоговое окно Добавление нового элемента в Visual Studio путем регистрации добавления шаблонов элементов в подразделе реестра Projects.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Add New Item dialog box, contributing to
ms.assetid: b2e53175-9372-4d17-8c2b-9264c9e51e9c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 8186f25f8e1631f0e13aa7a8f43620812c4c7693
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105057056"
---
# <a name="contribute-to-the-add-new-item-dialog-box"></a>Участие в диалоговом окне "Добавление нового элемента"
Подтип проекта может предоставлять полный новый каталог элементов для диалогового окна **Добавление нового элемента** путем регистрации **добавления шаблонов элементов** в подразделе реестра **Projects** .

## <a name="register-add-new-item-templates"></a>Регистрация добавления новых шаблонов элементов
 Этот раздел находится в разделе **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0\Projects** в реестре. Приведенные ниже записи реестра предполагают, что [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] проект агрегирован по гипотетическому подтипу проекта. Ниже перечислены записи для [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] проекта.

```
[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0\Projects\{F184B08F-C81C-45F6-A57F-5ABD9991F28F}]
@="#2143"
"DefaultProjectExtension"="vbproj"
"PossibleProjectExtensions"="vbproj;vbp"
"ProjectTemplatesDir"="visualStudioInstallPath\\Vb\\.\\VBProjects"

[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0\Projects\{F184B08F-C81C-45F6-A57F-5ABD9991F28F}\AddItemTemplates\TemplateDirs\{12345678-1234-1234-1122334455667788}\/1]
@="#100"
"TemplatesDir"="projectSubTypeTemplatesDir\\VBProjectItems"
```

 Подраздел **аддитемтемплатес\темплатедирс** содержит записи реестра с путем к каталогу, в который помещаются элементы, доступные в диалоговом окне **Добавление нового элемента** .

 Среда автоматически загружает все данные **аддитемтемплатес** из подраздела реестра **Projects** . Эти данные могут включать данные для базовых реализаций проекта, а также данные для конкретных типов подтипов проектов. Каждый подтип проекта определяется **идентификатором GUID** типа проекта. Подтип проекта может указывать, что для конкретного экземпляра проекта с установленным флагом следует использовать альтернативный набор шаблонов **добавления элементов** , поддерживая `VSHPROPID_ AddItemTemplatesGuid` Перечисление <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> в <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> реализации, чтобы вернуть значение идентификатора GUID подтипа проекта. Если `VSHPROPID_AddItemTemplatesGuid` свойство не задано, используется базовый идентификатор проекта.

 Можно отфильтровать элементы в диалоговом окне **Добавление нового элемента** , реализовав <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg> интерфейс для объекта агрегатора подтипа проекта. Например, подтип проекта, который реализует проект базы данных путем статистической обработки [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] проекта, может фильтровать [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] определенные элементы в диалоговом окне **Добавление нового элемента** путем реализации фильтрации, а в свою очередь может добавлять элементы, относящиеся к проекту базы данных, посредством поддержки `VSHPROPID_ AddItemTemplatesGuid` в <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> . Дополнительные сведения о фильтрации и добавлении элементов в диалоговом окне " **Добавление нового элемента** " см. в разделе [Добавление элементов в диалоговое окно Добавление нового](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)элемента.

## <a name="see-also"></a>См. также
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>
- [CATID для объектов, которые обычно используются для расширения проектов](../../extensibility/internals/catids-for-objects-that-are-typically-used-to-extend-projects.md)
