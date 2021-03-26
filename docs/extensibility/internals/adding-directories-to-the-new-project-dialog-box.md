---
title: Добавление каталогов в диалоговое окно "новый проект" | Документация Майкрософт
description: Узнайте, как добавлять каталоги в диалоговое окно Новый проект в Visual Studio, чтобы можно было создавать новые типы проектов и отображать их для использования в качестве шаблонов.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- New Project dialog box, extending
ms.assetid: 53b328f5-20bb-49a3-bf9e-1818f4fbdf50
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: ed90ddec0fe8c6cf1941f7e272552882107763a7
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105079115"
---
# <a name="add-directories-to-the-new-project-dialog-box"></a>Добавление каталогов в диалоговое окно "новый проект"
При создании новых типов проектов можно также зарегистрировать новый каталог в диалоговом окне **Новый проект** , чтобы отобразить их для использования в качестве шаблонов. В следующем примере кода показано, как зарегистрировать новый каталог, также известный как узел. В этом примере регистрируются шаблоны, предоставляемые пакетом VSPackage, *CLSID_Package*. В результате в левой части диалогового окна **Новый проект** появится добавленный узел с именем, определенным ресурсом *Folder_Label_ResID* . Этот ресурс загружается из вспомогательной библиотеки DLL VSPackage.

 Значение **папки** представляет идентификатор GUID папки, в которой отображается узел *Folder_Label_ResID* . В этом примере идентификатор GUID представляет папку **другие проекты** на панели **типы проектов** диалогового окна **Новый проект** . Если значение **других проектов** отсутствует, метка располагается на верхнем уровне.

 `TemplatesDir`Значение указывает полный путь к каталогу, содержащему шаблоны проектов. Эти файлы могут представлять собой файлы *. vsz* или обычные файлы шаблонов для клонирования.

 Если указать `TemplatesLocalizedSubDir` , это должен быть идентификатор ресурса строки, которая указывает на подкаталог `TemplatesDir` , содержащий локализованные шаблоны. Поскольку [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] загружает строковый ресурс из вспомогательной библиотеки DLL, если таковой имеется, каждая вспомогательная библиотека DLL может содержать другое имя подкаталога. `SortPriority`Значение указывает приоритет сортировки.

```
NoRemove NewProjectTemplates
{
    NoRemove TemplateDirs
  {
    ForceRemove %CLSID_Package%
    {
      ForceRemove /1 = s '#%Folder_Label_ResID%'
      {
        val Folder = s '{DCF2A94A-45B0-11D1-ADBF-00C04FB6BE4C}'
        val TemplatesDir = s '%Template_Path%'
        val TemplatesLocalizedSubDir = s '#100'
        val SortPriority = d 1000
      }
    }
  }
}
```

## <a name="see-also"></a>См. также
- [Регистрация шаблонов проектов и элементов](../../extensibility/internals/registering-project-and-item-templates.md)
- [Добавление элементов в диалоговое окно "Добавление нового элемента"](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)
- [Добавление каталогов в диалоговое окно "Добавление нового элемента"](../../extensibility/internals/adding-directories-to-the-add-new-item-dialog-box.md)
