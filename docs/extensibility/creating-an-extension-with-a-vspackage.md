---
title: Создание расширения с помощью VSPackage | Документация Майкрософт
description: Узнайте, как создать проект VSIX и добавить элемент проекта VSPackage с помощью VSPackage, чтобы получить службу оболочки пользовательского интерфейса для отображения окна сообщения.
ms.custom: SEO-VS-2020
ms.date: 3/16/2019
ms.topic: how-to
ms.assetid: c0cc5e08-4897-44f2-8309-e3478f1f999e
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: a6c93d90771eeffbfe28ae91781403019743afa9
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105089151"
---
# <a name="create-an-extension-with-a-vspackage"></a>Создание расширения с помощью VSPackage

В этом пошаговом руководстве показано, как создать проект VSIX и добавить элемент проекта VSPackage. Мы будем использовать VSPackage для получения службы оболочки пользовательского интерфейса, чтобы отобразить окно сообщения.

## <a name="prerequisites"></a>Предварительные требования

Начиная с Visual Studio 2015, пакет SDK для Visual Studio не устанавливается из центра загрузки. Он входит в состав программы установки Visual Studio как дополнительный компонент. Пакет SDK для VS можно установить и позже. Дополнительные сведения см. [в статье Установка пакета SDK для Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-vspackage"></a>Создание VSPackage

1. Создайте проект VSIX с именем **фирстпаккаже**. Шаблон проекта VSIX можно найти в диалоговом окне " **Новый проект** ", выполнив поиск по слову "VSIX".

2. Когда откроется проект, добавьте шаблон элемента пакета Visual Studio с именем **фирстпаккаже**. В **Обозреватель решений** щелкните правой кнопкой мыши узел проекта и выберите команду **Добавить**  >  **новый элемент**. В диалоговом окне **Добавление нового элемента** перейдите в раздел расширяемость **Visual C#**  >   и выберите **пакет Visual Studio**. В поле **имя** в нижней части окна измените имя файла команд на *фирстпаккаже. CS*.

3. Выполните сборку решения и запустите отладку.

    Откроется экспериментальный экземпляр Visual Studio. Дополнительные сведения об экспериментальном экземпляре см. [в статье экспериментальный экземпляр](../extensibility/the-experimental-instance.md).

4. В экспериментальном экземпляре откройте окно **инструменты**  >  **расширения и обновления** . Здесь вы увидите расширение **фирстпаккаже** . (Если вы открыли **расширения и обновления** в рабочем экземпляре Visual Studio, вы не увидите **фирстпаккаже**).

## <a name="load-the-vspackage"></a>Загрузка VSPackage

На этом этапе расширение не загружается, так как нет ничего, что приводит к его загрузке. Обычно расширение можно загрузить при взаимодействии с его ИНТЕРФЕЙСом (щелкнув команду меню, открыв окно инструментов) или указав, что пакет VSPackage должен загружаться в определенном контексте пользовательского интерфейса. Дополнительные сведения о загрузке пакетов VSPackage и контекстов пользовательского интерфейса см. в разделе [Загрузка пакетов VSPackage](../extensibility/loading-vspackages.md). В этой процедуре мы покажем, как загрузить VSPackage, когда решение открыто.

1. Откройте файл *фирстпаккаже. CS* . Найдите объявление `FirstPackage` класса. Замените существующие атрибуты следующими атрибутами:

    ```csharp
    [PackageRegistration(UseManagedResourcesOnly = true)]
    [InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)] // Info on this package for Help/About
    [ProvideAutoLoad(UIContextGuids80.SolutionExists)]
    [Guid(FirstPackage.PackageGuidString)]
    public sealed class FirstPackage : Package
    ```

2. Добавим сообщение, которое поможет нам убедиться, что пакет VSPackage загружен. `Initialize()`Для этого мы используем метод VSPackage, так как вы можете получить доступ к службам Visual Studio только после того, как пакет VSPackage установлен на сайте. (Дополнительные сведения о получении служб см. [в разделе как получить службу](../extensibility/how-to-get-a-service.md).) Замените `Initialize()` метод `FirstPackage` на код, который получает <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> службу, получает <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> интерфейс и вызывает его <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ShowMessageBox%2A> метод.

    ```csharp
    protected override void Initialize()
    {
        base.Initialize();

        IVsUIShell uiShell = (IVsUIShell)GetService(typeof(SVsUIShell));
        Guid clsid = Guid.Empty;
        int result;
        Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure(uiShell.ShowMessageBox(
            0,
            ref clsid,
            "FirstPackage",
             string.Format(CultureInfo.CurrentCulture, "Inside {0}.Initialize()", this.GetType().FullName),
            string.Empty,
            0,
            OLEMSGBUTTON.OLEMSGBUTTON_OK,
            OLEMSGDEFBUTTON.OLEMSGDEFBUTTON_FIRST,
            OLEMSGICON.OLEMSGICON_INFO,
            0,
            out result));
    }
    ```

3. Выполните сборку решения и запустите отладку. Откроется экспериментальный экземпляр.

4. Откройте решение в экспериментальном экземпляре. Должно отобразиться окно сообщения, **в котором сначала указывается пакет в разделе Initialize ()**.
