---
title: Добавление каталогов в диалоговое окно "Добавление нового элемента" | Документация Майкрософт
description: Сведения о добавлении каталогов в диалоговое окно Добавление нового элемента в Visual Studio с помощью сценария реестра для регистрации каталогов.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- Add New Item dialog box, extending
ms.assetid: 67ae8af6-3752-49e8-8ce3-007aca5f7982
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: dab135f8e8632755674d7b3ddf5972592f74d315
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/25/2021
ms.locfileid: "112904364"
---
# <a name="add-directories-to-the-add-new-item-dialog-box"></a>Добавление каталогов в диалоговое окно "Добавление нового элемента"
В следующем примере кода показано, как зарегистрировать новый набор каталогов для диалогового окна " **Добавление нового элемента** ". Каталоги для диалогового окна « **Добавление нового элемента** » для каждого проекта различаются. Поэтому каталоги регистрируются в подразделе " **проекты** ", который находится в **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\Projects**.

## <a name="registry-script"></a>Сценарий реестра

```
NoRemove Projects
{
  NoRemove %GUID_Project%
  {
    NoRemove AddItemTemplates
    {
      NoRemove TemplateDirs
      {
        ForceRemove %CLSID_Package%
        {
      ForceRemove /1 = s '#%Folder_Label_ResID%'
          {
            val TemplatesDir = s '%Template_Path%'
            val SortPriority = d 2000
          }
        }
      }
    }
  }
}
```

 `%Template_Path%`Значение указывает полный путь к каталогу, содержащему шаблоны проектов. Эти шаблоны могут представлять собой файлы *. vsz* или файлы шаблонов прототипные для клонирования.

 `SortPriority`Значение указывает приоритет сортировки.

## <a name="add-items-to-an-existing-project"></a>Добавление элементов в существующий проект
 Кроме того, можно добавлять элементы в существующий проект. Например, для [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] проекта можно добавить элементы в папку *\<root> \Program Files\Microsoft Visual студио\вк # \кшарппрожектитемс\локалпрожектитемс* . В этом случае `%GUID_Project%` — это идентификатор GUID для проекта C# ({FAE04EC0-301F-11D3-BF4B-00C04F79EFBC}).

 Можно также расширить существующий проект путем программирования подтипа проекта. С помощью подтипа проекта можно расширить проект, не написав новый тип проекта. Дополнительные сведения о подтипах проектов см. в разделе [Project подтипы](../../extensibility/internals/project-subtypes.md).

## <a name="see-also"></a>См. также
- [Регистрация шаблонов проектов и элементов](../../extensibility/internals/registering-project-and-item-templates.md)
- [Добавление элементов в диалоговое окно "Добавление нового элемента"](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)
- [Добавление каталогов в диалоговое окно "новый проект"](../../extensibility/internals/adding-directories-to-the-new-project-dialog-box.md)
