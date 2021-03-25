---
title: Учебник по расширению Hello World | Документация Майкрософт
description: Узнайте, как добавить новую команду в качестве расширения Visual Studio, которое охватывает создание проекта, добавление команды и изменение исходного кода.
ms.custom: SEO-VS-2020
ms.date: 03/14/2019
ms.topic: tutorial
ms.assetid: f74e1ad1-1ee5-4360-9bd5-d82467b884ca
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: ec465eda5a0bd7d017c3822390d68b43f76b5c47
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105070184"
---
# <a name="tutorial---create-your-first-extension-hello-world"></a>Учебник. Создайте свое первое расширение: Hello World

В этом примере Hello World пошагово показывается, как создать ваше первое расширение для Visual Studio. В этом учебнике показано, как добавить новую команду в Visual Studio.

В процессе изучения вы узнаете, как выполняются следующие задачи:

* **[создание проекта расширения](#create-an-extensibility-project)** ;
* **[добавление пользовательской команды](#add-a-custom-command)** ;
* **[изменение исходного кода](#modify-the-source-code)** ;
* **[Выполните команду.](#run-it)**

В этом примере будет использоваться Visual C# для добавления пользовательской кнопки меню с именем "Say Hello World!", которая выглядит следующим образом:

![Команда Hello World](media/hello-world-say-hello-world.png)

> [!NOTE]
> Эта статья относится к Visual Studio в Windows. Информацию о Visual Studio для Mac см. в статье [Пошаговое руководство по расширяемости в Visual Studio для Mac](/visualstudio/mac/extending-visual-studio-mac-walkthrough).

## <a name="prerequisites"></a>Предварительные требования

Прежде чем начать, убедитесь, что вы установили рабочую нагрузку **разработки расширения Visual Studio**, которая включает нужный шаблон VSIX и пример кода.

> [!NOTE]
> Для создания проекта расширения Visual Studio можно использовать любой выпуск Visual Studio (Community, Professional или Enterprise).

## <a name="create-an-extensibility-project"></a>Создание проекта расширения

::: moniker range="vs-2017"

Шаг 1. В меню **Файл** выберите **Создать**  > **Проект**.

Шаг 2. В поле поиска в правом верхнем углу введите "vsix" и выберите **проект VSIX** Visual C#. Введите "HelloWorld" в поле **Имя** в нижней части диалогового окна и нажмите кнопку **ОК**.

![создание проекта](media/hello-world-new-project.png)

Теперь вы должны увидеть страницу начала работы и некоторые примеры ресурсов.

Если вам понадобится выйти из этого учебника, а затем вернуться к нему, ваш новый проект HelloWorld можно найти на **начальной странице** в разделе **Последние**.

::: moniker-end

::: moniker range=">=vs-2019"

Шаг 1. В меню **Файл** выберите **Создать**  > **Проект**. Выполните поиск "vsix" и выберите **проект VSIX** Visual C#, а затем нажмите **Далее**.

Шаг 2. Введите "HelloWorld" в поле **Имя проекта** и нажмите **Создать**.

![создание проекта](media/hello-world-new-project-2019.png)

Теперь проект HelloWorld должен появиться в **обозревателе решений**.

::: moniker-end

## <a name="add-a-custom-command"></a>Добавление пользовательской команды

Шаг 1. Если выбрать файл манифеста с расширением *VSIXMANIFEST*, можно увидеть, какие параметры могут быть изменены, например описание, автор и версия.

Шаг 2. Щелкните проект (а не решение) правой кнопкой мыши. В контекстном меню выберите **Добавить**, а затем **Создать элемент**.

Шаг 3. Выберите раздел **Расширяемость**, а затем выберите пункт **Команда**.

Шаг 4. Внизу, в поле **Имя**, введите имя файла, например *Command.cs*.

![пользовательская команда](media/hello-world-vsix-command.png)

Теперь ваша новая команда отображается в **обозревателе решений**. В узле **Ресурсы** можно найти другие файлы, связанные с вашей командой. Например, если вы хотите изменить образ, здесь будет находиться PNG-файл.

## <a name="modify-the-source-code"></a>Изменение исходного кода

На этом этапе текст команды и кнопки создается автоматически, и он не слишком информативный. Если вы хотите внести изменения, можно изменить VSCT-файл и CS-файл.

* В VSCT-файле можно переименовать свои команды, а также определить их место в командной системе Visual Studio. Просматривая VSCT-файл, вы увидите комментарии, объясняющие, за что отвечает каждый раздел кода VSCT.

* В CS-файле можно определять действия, например обработчик щелчка мыши.

::: moniker range="vs-2017"

Шаг 1. В **обозревателе решений** найдите VSCT-файл для вашей новой команды. В данном случае он будет называться *CommandPackage.vsct*.

![command package vsct](media/hello-world-command-package-vsct.png)

::: moniker-end

::: moniker range=">=vs-2019"

Шаг 1. В **обозревателе решений** найдите VSCT-файл для вашего пакета расширения VS. В данном случае он будет называться *HelloWorldPackage.vsct*.

::: moniker-end

Шаг 2. Измените значение параметра `ButtonText` на `Say Hello World!`.

```xml
  ...
  <Button guid="guidCommandPackageCmdSet" id="CommandId" priority="0x0100" type="Button">
     <Parent guid="guidCommandPackageCmdSet" id="MyMenuGroup" />
     <Icon guid="guidImages" id="bmpPic1" />
     <Strings>
        <ButtonText>Say Hello World!</ButtonText>
     </Strings>
  </Button>
  ...
```

Шаг 3. Вернитесь в **обозреватель решений** и найдите файл *Command.cs*. В методе `Execute` измените строку `message` с `string.Format(..)` на `Hello World!`.

```csharp
  ...
  private void Execute(object sender, EventArgs e)
  {
    ThreadHelper.ThrowIfNotOnUIThread();
    string message = "Hello World!";
    string title = "Command";

    // Show a message box to prove we were here
    VsShellUtilities.ShowMessageBox(
        this.ServiceProvider,
        message,
        title,
        OLEMSGICON.OLEMSGICON_INFO,
        OLEMSGBUTTON.OLEMSGBUTTON_OK,
        OLEMSGDEFBUTTON.OLEMSGDEFBUTTON_FIRST);
  }
  ...
```

Не забудьте сохранить изменения в каждом файле.

## <a name="run-it"></a>Выполните команду.

Теперь можно запустить исходный код в экспериментальном экземпляре Visual Studio.

Шаг 1. Нажмите клавишу **F5**, чтобы выполнить команду **Начать отладку**. Эта команда выполняет сборку проекта и запускает отладчик, запуская новый экземпляр Visual Studio, который называется **экспериментальным экземпляром**.

::: moniker range="vs-2017"

Вы увидите слова **Экспериментальный экземпляр** в заголовке окна Visual Studio.

![экспериментальный экземпляр, заголовок окна](media/hello-world-exp-instance.png)

::: moniker-end

Шаг 2. В меню **Инструменты** **экспериментального экземпляра** выберите **Say Hello World!** .

![конечный результат](media/hello-world-final-result.png)

Вы должны увидеть результаты новой пользовательской команды. В данном случае это диалоговое окно в центре экрана с сообщением **Hello World!** !".

## <a name="next-steps"></a>Дальнейшие действия

Теперь, после знакомства с основами работы с расширяемостью Visual Studio, вы можете продолжить обучение по следующим ссылкам.

* [Начало разработки расширений Visual Studio](starting-to-develop-visual-studio-extensions.md) — примеры, учебники и публикация расширения
* [Новые возможности пакета SDK для Visual Studio 2017](what-s-new-in-the-visual-studio-2017-sdk.md) — новые функции расширяемости в Visual Studio 2017
* [Новые возможности пакета SDK для Visual Studio 2019](whats-new-visual-studio-2019-sdk.md) — новые функции расширяемости в Visual Studio 2019
* [Компоненты пакета SDK для Visual Studio](internals/inside-the-visual-studio-sdk.md) — подробные сведения о расширяемости Visual Studio
