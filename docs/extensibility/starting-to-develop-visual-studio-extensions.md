---
title: Начинается разработка расширений Visual Studio | Документация Майкрософт
description: Узнайте о некоторых распространенных вопросах, которые могут возникнуть при первом запуске для написания расширения Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 09/18/2017
ms.topic: conceptual
helpviewer_keywords:
- getting started, Visual Studio integration
- Visual Studio, integration
ms.assetid: 8fe5e2ab-a424-4173-9d39-dd082c4d58d0
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: d8101640ce3e4a998d0a97fa1d85ded27fa746d0
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105089944"
---
# <a name="starting-to-develop-visual-studio-extensions"></a>Приступая к разработке расширений Visual Studio

Если вы ранее не написали расширение Visual Studio, возможно, у вас есть вопросы. Некоторые из наиболее распространенных из них перечислены здесь. Если вы не видите нужную информацию, воспользуйтесь кнопками обратной связи (**Эта страница полезна** в правом верхнем углу экрана), чтобы запросить нужные сведения.

> [!NOTE]
> Эта статья относится к Visual Studio в Windows. Дополнительные Visual Studio для Mac см. в разделе [расширение Visual Studio для Mac](/visualstudio/mac/extending-visual-studio-mac). Visual Studio Code см. в разделе [API расширения Visual Studio Code](https://code.visualstudio.com/api).

## <a name="what-software-do-i-need-to-develop-visual-studio-extensions"></a>Какое программное обеспечение требуется для разработки расширений Visual Studio?

Для разработки расширений Visual Studio необходимо установить Visual Studio SDK в дополнение к Visual Studio. Вы можете установить пакет SDK для Visual Studio как часть обычной установки или позже. Дополнительные сведения об установке пакета SDK для Visual Studio см. [в статье Установка пакета SDK для Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="what-kinds-of-things-can-i-do-with-visual-studio-extensions"></a>Какие виды действий можно выполнять с расширениями Visual Studio?

Предельное значение перевозки, когда приходится выключать различные расширения Visual Studio. Конечно, большинство расширений имеют что-то, что нужно делать с написанием кода, но это не должно быть так. Ниже приведены некоторые примеры типов расширений, которые можно создать.

- Поддержка языков, не входящих в состав Visual Studio, с использованием цветового выделения синтаксиса, технологии IntelliSense и поддержки компилятора и отладки

- Средства повышения производительности, расширяющие возможности интегрированной среды разработки с дополнительными шаблонами, рефакторинг кода, новые диалоговые окна и окна инструментов

- Зависящие от домена конструкторы для таких сценариев, как проектирование данных или поддержка в облаке

Примеры расширений см. на [Visual Studio Marketplace](https://marketplace.visualstudio.com/vs). Многие расширения открыты с открытым исходным кодом, и в Marketplace имеются ссылки на репозиторий GitHub.

## <a name="which-visual-studio-features-can-i-extend"></a>Какие возможности Visual Studio можно расширить?

Теоретически, вы можете расширить практически любую часть Visual Studio: меню, панели инструментов, команды, окна, решения, проекты, редакторы и т. д.

На практике мы обнаружили, что большинство пользователей хотят расширить возможности команд, меню и панелей инструментов, окон, IntelliSense и проектов. Ниже приведены ссылки на соответствующие разделы.

- [Расширение меню и команд](../extensibility/extending-menus-and-commands.md): Добавление собственных элементов в меню и панели инструментов Visual Studio. Их можно использовать для запуска новых функций Visual Studio или собственных внешних вспомогательных приложений. Можно также указать настраиваемые сочетания клавиш для пунктов меню.

- [Расширение и настройка окон инструментов](../extensibility/extending-and-customizing-tool-windows.md): расширение существующих окон инструментов или создание собственных окон инструментов. Например, можно добавить в **Свойства** новые свойства или создать новое окно инструментов для добавления дополнительных компонентов.

- [Расширения редактора и языковой службы](../extensibility/editor-and-language-service-extensions.md): добавьте собственные настройки в IntelliSense, предоставляемую для языков Visual Studio, или создайте поддержку для новых языков программирования. Можно создавать новые завершения операторов, предложения и новые подсказки краткие сведения. С помощью лампочкй можно добавлять предложения рефакторинга и исправления кода для поддержки новых языков программирования.

- [Расширение проектов](../extensibility/extending-projects.md)

- [Расширение параметров и настроек пользователя](../extensibility/extending-user-settings-and-options.md)

- [Расширение свойств и окна свойств](../extensibility/extending-properties-and-the-property-window.md)

- [Расширение других частей Visual Studio](../extensibility/extending-other-parts-of-visual-studio.md)

- [Изолированная оболочка Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/isolated-shell/)

## <a name="what-project-templates-are-provided-by-the-vssdk"></a><a name="BKMK_ProjectTemplate"></a> Какие шаблоны проектов предоставляются VSSDK?
 Два основных типа расширений — это пакеты VSPackage и расширения MEF. Как правило, расширения VSPackage используются для расширений, которые используют или расширяют команды, окна инструментов и проекты. Расширения MEF используются для расширения или настройки редактора Visual Studio.

 Для расширений Visual C# и Visual Basic VSSDK предоставляет пустой шаблон проекта VSIX, который можно использовать вместе с новыми шаблонами элементов, которые создают команды меню, окна инструментов и расширения редактора. Этот шаблон также можно использовать для упаковки шаблонов проектов, фрагментов кода и других артефактов для распространения другим пользователям.

 Для C++ мастер VSPackage предоставляет код для добавления команд меню, окон инструментов и пользовательских редакторов.

 Шаблон изолированной оболочки используется для упаковки расширения в оболочку Visual Studio, которую можно использовать и распространять самостоятельно. В следующих разделах показано, как приступить к работе с каждым типом расширения.

- Команды меню: [Создание расширения с помощью команды меню](../extensibility/creating-an-extension-with-a-menu-command.md)

- Окна инструментов: [Создание расширения с помощью окна инструментов](../extensibility/creating-an-extension-with-a-tool-window.md)

- Расширения редактора: [Создание расширения с помощью шаблона элемента редактора](../extensibility/creating-an-extension-with-an-editor-item-template.md)

- Основные пакеты VSPackage: [Создание расширения с помощью VSPackage](../extensibility/creating-an-extension-with-a-vspackage.md)

- Шаблон проекта VSIX: [Начало работы с помощью шаблона проекта VSIX](../extensibility/getting-started-with-the-vsix-project-template.md)

## <a name="how-do-i-get-my-extension-to-look-like-visual-studio"></a>Разделы справки получить расширение как Visual Studio?
 Получите советы по проектированию пользовательского интерфейса для расширения в [руководстве пользователя Visual Studio](../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md).

## <a name="where-can-i-find-examples-of-vssdk-code"></a>Где можно найти примеры кода VSSDK?
 Каждая из ссылок, перечисленных в предыдущем разделе, содержит пошаговые пошаговые руководства, демонстрирующие способы реализации конкретных функций. Примеры VSSDK с открытым исходным кодом можно найти на сайте GitHub в [примерах Visual Studio](https://github.com/Microsoft/VSSDK-Extensibility-Samples).

## <a name="how-can-i-distribute-my-extension"></a>Как можно распространить расширение?
 Вы можете установить расширение на другом компьютере или отправить его своим друзьям в виде VSIX-файла, который устанавливается двойным щелчком. Дополнительные сведения о пакетах VSIX см. в статье [Доставка расширений Visual Studio](../extensibility/shipping-visual-studio-extensions.md).

 Вы также можете опубликовать расширение на Visual Studio Marketplace, что делает его видимым для большого числа клиентов Visual Studio. Пример упаковки расширения в Marketplace см. в разделе [Пошаговое руководство. публикация расширения Visual Studio](../extensibility/walkthrough-publishing-a-visual-studio-extension.md). Дополнительные сведения о том, что необходимо сделать для публикации в Marketplace, см. в разделе [Products and Extensions for Visual Studio](/azure/devops/extend/overview?view=vsts&preserve-view=true).

## <a name="see-also"></a>См. также

- [Расширение Visual Studio для Mac](/visualstudio/mac/extending-visual-studio-mac)
- [Расширение Visual Studio Code](https://code.visualstudio.com/api)