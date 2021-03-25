---
title: Расширение строки состояния | Документация Майкрософт
description: Узнайте, как расширить строку состояния Visual Studio в нижней части интегрированной среды разработки, которая отображает сведения.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- status bars, about status bars
- status bars, overview
ms.assetid: f955115c-4c5f-45ec-b41b-365868c5ec0c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 5ab87f9c8b54d9c31466068668eb8dd5a1857a06
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105070106"
---
# <a name="extend-the-status-bar"></a>Расширение строки состояния
Для отображения сведений можно использовать строку состояния Visual Studio в нижней части интегрированной среды разработки.

 При расширении строки состояния можно отобразить сведения и пользовательский интерфейс в четырех регионах: область обратной связи, индикатор выполнения, область анимации и область конструктора. Область отзывов позволяет отображать текст и выделять отображаемый текст. Индикатор выполнения показывает последовательный ход выполнения для коротких операций, таких как сохранение файла. В области анимации отображается непрерывная анимация для длительно выполняющихся операций или операция неопределенной длины, например создание нескольких проектов в решении. В области конструктора отображается номер строки и столбца расположения курсора.

 Строку состояния можно получить с помощью <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbar> интерфейса (из <xref:Microsoft.VisualStudio.Shell.Interop.SVsStatusbar> службы). Кроме того, любой объект, нарасположенный в кадре окна, может зарегистрировать в качестве клиентского объекта строки состояния, реализовав <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser> интерфейс. Всякий раз при активации окна Visual Studio запрашивает объект, расположенный в этом окне, для `IVsStatusbarUser` интерфейса. При обнаружении он вызывает <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A> метод для возвращенного интерфейса, и объект может обновить строку состояния в этом методе. Например, окна документов могут использовать <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A> метод для обновления сведений в области конструктора, когда они становятся активными.

 В следующих процедурах предполагается, что вы понимаете, как создать проект VSIX и добавить пользовательскую команду меню. Дополнительные сведения см. в разделе [Создание расширения с помощью команды меню](../extensibility/creating-an-extension-with-a-menu-command.md).

## <a name="modify-the-status-bar"></a>Изменение строки состояния
 В этой процедуре показано, как задать и получить текст, отобразить статический текст и выделить отображаемый текст в области обратной связи в строке состояния.

### <a name="read-and-write-to-the-status-bar"></a>Чтение строки состояния и запись в нее

1. Создайте проект VSIX с именем **тестстатусбарекстенсион** и добавьте команду меню с именем **тестстатусбаркомманд**.

2. В *тестстатусбаркомманд. CS* замените код метода обработчика команд ( `MenuItemCallback` ) следующим кодом:

    ```csharp
    private void MenuItemCallback(object sender, EventArgs e)
    {
        IVsStatusbar statusBar = (IVsStatusbar)ServiceProvider.GetService(typeof(SVsStatusbar));

        // Make sure the status bar is not frozen
        int frozen;

        statusBar.IsFrozen(out frozen);

        if (frozen != 0)
        {
            statusBar.FreezeOutput(0);
        }

        // Set the status bar text and make its display static.
        statusBar.SetText("We just wrote to the status bar.");

        // Freeze the status bar.
        statusBar.FreezeOutput(1);

        // Get the status bar text.
        string text;
        statusBar.GetText(out text);
        System.Windows.Forms.MessageBox.Show(text);

        // Clear the status bar text.
        statusBar.FreezeOutput(0);
        statusBar.Clear();
    }
    ```

3. Скомпилируйте код и начните отладку.

4. Откройте меню **Сервис** в экспериментальном экземпляре Visual Studio. Нажмите кнопку **вызвать тестстатусбаркомманд** .

     Вы увидите, что текст в строке состояния теперь считывает **только что записанное в строку состояния.** и отображаемое окно сообщения имеет тот же текст.

### <a name="update-the-progress-bar"></a>Обновление индикатора выполнения

1. В этой процедуре будет показано, как инициализировать и обновить индикатор выполнения.

2. Откройте файл *тестстатусбаркомманд. CS* и замените `MenuItemCallback` метод следующим кодом:

    ```csharp
    private void MenuItemCallback(object sender, EventArgs e)
    {
        IVsStatusbar statusBar = (IVsStatusbar)ServiceProvider.GetService(typeof(SVsStatusbar));
        uint cookie = 0;
        string label = "Writing to the progress bar";

        // Initialize the progress bar.
        statusBar.Progress(ref cookie, 1, "", 0, 0);

        for (uint i = 0, total = 20; i <= total; i++)
        {
            // Display progress every second.
            statusBar.Progress(ref cookie, 1, label, i, total);
            System.Threading.Thread.Sleep(1000);
        }

        // Clear the progress bar.
        statusBar.Progress(ref cookie, 0, "", 0, 0);
    }
    ```

3. Скомпилируйте код и начните отладку.

4. Откройте меню **Сервис** в экспериментальном экземпляре Visual Studio. Нажмите кнопку **Invoke тестстатусбаркомманд (вызвать** ).

     Вы увидите, что текст в строке состояния теперь считывает **запись на индикатор выполнения.** Вы также увидите, что индикатор выполнения обновляется каждую секунду в течение 20 секунд. После этого строка состояния и индикатор выполнения будут удалены.

### <a name="display-an-animation"></a>Отображение анимации

1. В строке состояния отображается циклическая анимация, которая указывает на выполнение длительной операции (например, создание нескольких проектов в решении). Если вы не видите эту анимацию, убедитесь, что у вас есть правильные параметры **инструментов**  >   :

     Перейдите на вкладку **Сервис**  >  **Параметры**  >  **Общие** и снимите флажок **автоматически настраивать визуальный интерфейс на основе производительности клиента**. Затем установите флажок **доработать многофункциональное визуальное взаимодействие с клиентами**. Теперь вы сможете увидеть анимацию при построении проекта в экспериментальном экземпляре Visual Studio.

     В этой процедуре мы отображаем стандартную анимацию Visual Studio, которая представляет собой сборку проекта или решения.

2. Откройте файл *тестстатусбаркомманд. CS* и замените `MenuItemCallback` метод следующим кодом:

    ```csharp
    private void MenuItemCallback(object sender, EventArgs e)
    {
        IVsStatusbar statusBar =(IVsStatusbar)ServiceProvider.GetService(typeof(SVsStatusbar));

        // Use the standard Visual Studio icon for building.
        object icon = (short)Microsoft.VisualStudio.Shell.Interop.Constants.SBAI_Build;

        // Display the icon in the Animation region.
        statusBar.Animation(1, ref icon);

        // The message box pauses execution for you to look at the animation.
        System.Windows.Forms.MessageBox.Show("showing?");

        // Stop the animation.
        statusBar.Animation(0, ref icon);
    }
    ```

3. Скомпилируйте код и начните отладку.

4. Откройте меню **Сервис** в экспериментальном экземпляре Visual Studio и выберите команду **вызвать тестстатусбаркомманд**.

     Когда появится окно сообщения, вы также увидите анимацию в строке состояния в правом углу. Если закрыть окно сообщения, анимация исчезнет.
