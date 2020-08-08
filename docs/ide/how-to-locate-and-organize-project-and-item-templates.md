---
title: Локальные шаблоны
ms.date: 01/02/2018
ms.topic: how-to
helpviewer_keywords:
- project templates [Visual Studio], locations
- item templates [Visual Studio], locations
- template locations [Visual Studio]
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: ecbc5421562ca79466ace0d93a16ac4e3635ddfb
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/23/2020
ms.locfileid: "85284247"
---
# <a name="how-to-locate-and-organize-project-and-item-templates"></a>Практическое руководство. Размещение и упорядочение шаблонов проектов и элементов

Чтобы файлы шаблонов отображались в диалоговых окнах "Новый проект" и "Новый элемент", эти файлы должны находиться в известном расположении.

::: moniker range="vs-2017"

Можно также создать пользовательские подкатегории в расположении с пользовательскими шаблонами. Категории будут отображаться в диалоговых окнах **Новый проект** и **Добавление нового элемента**.

::: moniker-end

## <a name="locate-templates"></a>Локальные шаблоны

Установленные шаблоны и пользовательские шаблоны хранятся в двух различных местах.

### <a name="installed-templates"></a>Установленные шаблоны

По умолчанию шаблоны, установленные с Visual Studio, находятся в следующих расположениях:

::: moniker range="vs-2017"

- *%ProgramFiles(x86)%\\Microsoft Visual Studio\\2017\\\<edition>\\Common7\IDE\ProjectTemplates\\<язык\>\\<код языка\>*

- *%ProgramFiles(x86)%\\Microsoft Visual Studio\\2017\\\<edition>\Common7\IDE\ItemTemplates\\<язык\>\\<код языка\>*

Например, следующий каталог содержит шаблоны элементов Visual Basic для английского языка (LCID 1033):

*C:\\Program Files (x86)\\Microsoft Visual Studio\\2017\\Community\\Common7\\IDE\\ItemTemplates\\VisualBasic\\1033*

::: moniker-end

::: moniker range=">=vs-2019"

- *%ProgramFiles(x86)%\\Microsoft Visual Studio\\2019\\\<edition>\\Common7\IDE\ProjectTemplates\\<язык\>\\<код языка\>*

- *%ProgramFiles(x86)%\\Microsoft Visual Studio\\2019\\\<edition>\Common7\IDE\ItemTemplates\\<язык\>\\<код языка\>*

Например, следующий каталог содержит шаблоны элементов Visual Basic для английского языка (LCID 1033):

*C:\\Program Files (x86)\\Microsoft Visual Studio\\2019\\Community\\Common7\\IDE\\ItemTemplates\\VisualBasic\\1033*

::: moniker-end

### <a name="user-templates"></a>Шаблоны пользователя

Если добавить сжатый файл (*ZIP*), содержащий *VSTEMPLATE*-файл, в каталог с пользовательскими шаблонами, этот шаблон будет отображаться в диалоговом окне "Новый проект" или "Новый элемент". По умолчанию пользовательские шаблоны находятся в следующих расположениях:

::: moniker range="vs-2017"

- *%USERPROFILE%\Documents\Visual Studio 2017\Templates\ProjectTemplates*

- *%USERPROFILE%\Documents\Visual Studio 2017\Templates\ItemTemplates*

Например, следующий каталог содержит шаблоны проектов пользователя на C#:

- *C:\Users\Имя_пользователя\Documents\Visual Studio 2017\Templates\ProjectTemplates\Visual C#*

::: moniker-end

::: moniker range=">=vs-2019"

- *%USERPROFILE%\Documents\Visual Studio 2019\Templates\ProjectTemplates*

- *%USERPROFILE%\Documents\Visual Studio 2019\Templates\ItemTemplates*

Например, следующий каталог содержит шаблоны проектов пользователя на C#:

- *C:\Users\Имя_пользователя\Documents\Visual Studio 2019\Templates\ProjectTemplates\Visual C#*

::: moniker-end

> [!TIP]
> Известное расположение пользовательских шаблонов можно изменить, последовательно выбрав **Средства** > **Параметры** > **Проекты и решения** > **Расположения**.

::: moniker range="vs-2017"

## <a name="organize-templates"></a>Упорядочивание шаблонов

Категории в диалоговых окнах **Новый проект** и **Добавление нового элемента** отражают структуры каталогов, которые существуют в расположениях установленных и пользовательских шаблонов. Пользовательские шаблоны можно упорядочить по собственным категориям путем добавления новых папок в каталог с пользовательскими шаблонами. Диалоговые окна **Новый проект** и **Добавление нового элемента** отражают все изменения, вносимые в категории шаблонов пользователя.

> [!NOTE]
> Вы не можете создать новую категорию на уровне языка программирования. Новые категории можно создавать только в рамках каждого отдельного языка.

### <a name="create-new-user-project-template-categories"></a>Создание категорий пользовательских шаблонов проектов

1. Создайте папку в папке языка программирования, находящейся в каталоге пользовательских шаблонов проектов. Например, чтобы создать категорию **HelloWorld** для шаблонов проектов C#, необходимо создать следующий каталог:

    - *\%USERPROFILE%\Documents\Visual Studio \<Version\>\Templates\ProjectTemplates\Visual C#\HelloWorld*

1. Поместите все шаблоны для этой категории в новую папку.

1. В меню **Файл** щелкните **Создать** > **Проект**.

   Категория **HelloWorld** отображается в диалоговом окне **Новый проект** в разделе **Установленные** > **Visual C#** .

### <a name="create-new-user-item-template-categories"></a>Создание категорий пользовательских шаблонов элементов

1. Создайте папку в папке языка программирования, находящейся в каталоге пользовательских шаблонов элементов. Например, чтобы создать категорию **HelloWorld** для шаблонов элементов C#, необходимо создать следующий каталог:

    - *\%USERPROFILE%\Documents\Visual Studio \<Version\>\Templates\ItemTemplates\Visual C#\HelloWorld*

1. Поместите все шаблоны для этой категории в новую папку.

1. Создайте новый проект или откройте уже имеющийся. Затем в меню **Проект** выберите пункт **Добавить новый элемент**.

   Категория **HelloWorld** отображается в диалоговом окне **Добавление нового элемента** в разделе **Установленные** > **Элементы Visual C#** .

### <a name="display-templates-in-parent-categories"></a>Отображение шаблонов в родительских категориях

Можно включить шаблоны в подкатегориях, чтобы они отображались в их родительских категориях, с помощью элемента `NumberOfParentCategoriesToRollUp` в *VSTEMPLATE*-файле. Эти действия одинаковы как для шаблонов проектов, так и для шаблонов элементов.

1. Найдите *ZIP*-файл, содержащий шаблон.

1. Извлеките содержимое *ZIP*-файла.

1. Откройте *VSTEMPLATE*-файл в Visual Studio.

1. В элементе `TemplateData` добавьте элемент `NumberOfParentCategoriesToRollUp`. Например, следующий код делает шаблон видимым в родительской категории, но не на более высоких уровнях.

    ```xml
    <TemplateData>
        ...
        <NumberOfParentCategoriesToRollUp>
            1
        </NumberOfParentCategoriesToRollUp>
        ...
    </TemplateData>
    ```

1. Сохраните *VSTEMPLATE*-файл и закройте его.

1. Выберите файлы в шаблоне, щелкните выделение правой кнопкой мыши и выберите пункты **Отправить** > **Сжатая ZIP-папка**.

   Файлы сжимаются в *ZIP*-файл.

1. Удалите извлеченные файлы шаблона и *ZIP*-файл старого шаблона.

1. Поместите новый *ZIP*-файл в каталог, где находился удаленный *ZIP*-файл.

::: moniker-end

## <a name="see-also"></a>См. также

- [Настройка шаблонов](../ide/customizing-project-and-item-templates.md)
- [Справочник по схемам шаблонов Visual Studio (расширяемость)](../extensibility/visual-studio-template-schema-reference.md)
- [Элемент NumberOfParentCategoriesToRollUp (шаблоны Visual Studio)](../extensibility/numberofparentcategoriestorollup-visual-studio-templates.md)
- [Практическое руководство. создание шаблонов проектов](../ide/how-to-create-project-templates.md)
- [Практическое руководство. создание шаблонов элементов](../ide/how-to-create-item-templates.md)
