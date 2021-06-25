---
title: Подписка на событие | Документация Майкрософт
description: Узнайте, как создать окно инструментов, которое реагирует на события в выполняющейся таблице документов в пакете SDK для Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- running document table (RDT), responding to events
- running document table (RDT), subscribing to events
ms.assetid: e94a4fea-94df-488e-8560-9538413422bc
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 01271016eed9a4a157b333a2f0435589b0a028d5
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/25/2021
ms.locfileid: "112899397"
---
# <a name="subscribing-to-an-event"></a>Подписка на событие
В этом пошаговом руководстве объясняется, как создать окно инструментов, которое реагирует на события в выполняющейся таблице документов (РДТ). В окне инструментов размещается пользовательский элемент управления, реализующий интерфейс <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents> . <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.AdviseRunningDocTableEvents%2A>Метод подключает интерфейс к событиям.

## <a name="prerequisites"></a>Предварительные требования
 Начиная с Visual Studio 2015, пакет SDK для Visual Studio не устанавливается из центра загрузки. Он входит в состав программы установки Visual Studio как дополнительный компонент. Пакет SDK для VS можно установить и позже. Дополнительные сведения см. [в разделе Установка пакета SDK для Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="subscribing-to-rdt-events"></a>Подписка на события РДТ

#### <a name="to-create-an-extension-with-a-tool-window"></a>Создание расширения с помощью окна инструментов

1. Создайте проект с именем **рдтексплорер** с помощью шаблона VSIX и добавьте пользовательский шаблон элемента окна инструментов с именем **рдтексплорервиндов**.

     Дополнительные сведения о создании расширения с помощью окна инструментов см. в разделе [Создание расширения с помощью окна инструментов](../extensibility/creating-an-extension-with-a-tool-window.md).

#### <a name="to-subscribe-to-rdt-events"></a>Подписка на события РДТ

1. Откройте файл Рдтексплорервиндовконтрол. XAML и удалите кнопку с именем `button1` . Добавьте <xref:System.Windows.Forms.ListBox> элемент управления и примите имя по умолчанию. Элемент Grid должен выглядеть следующим образом:

    ```xml
    <Grid>
        <StackPanel Orientation="Vertical" Margin="-10,10,10,0">
            <TextBlock Margin="10" HorizontalAlignment="Center">RDTExplorerWindow</TextBlock>
            <ListBox x:Name="listBox" Height="100" />
        </StackPanel>
    </Grid>
    ```

2. Откройте файл Рдтексплорервиндов. cs в представлении кода. Добавьте следующие директивы using в начало файла.

    ```csharp
    using Microsoft.VisualStudio;
    using Microsoft.VisualStudio.Shell;
    using Microsoft.VisualStudio.Shell.Interop;
    ```

3. Измените `RDTExplorerWindow` класс, чтобы в дополнение к наследованию от <xref:Microsoft.VisualStudio.Shell.ToolWindowPane> класса он реализовал <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents> интерфейс.

    ```csharp
    public class RDTExplorerWindow : ToolWindowPane, IVsRunningDocTableEvents
    {. . .}
    ```

4. Реализуйте расширение <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents>.

    - Реализуйте интерфейс. Поместите курсор на имя Ивсруннингдоктабливентс. В левом поле появится лампочка лампочки. Щелкните стрелку вниз справа от лампочки и выберите команду **реализовать интерфейс**.

5. В каждом методе в интерфейсе замените строку `throw new NotImplementedException();` следующим:

    ```csharp
    return VSConstants.S_OK;
    ```

6. Добавьте поле cookie в класс Рдтексплорервиндов.

    ```csharp
    private uint rdtCookie;
    ```

     Он содержит файл cookie, возвращаемый <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.AdviseRunningDocTableEvents%2A> методом.

7. Переопределите метод Initialize () Рдтексплорервиндов для регистрации событий РДТ. Всегда следует получать службы в методе Initialize () ToolWindowPane, а не в конструкторе.

    ```csharp
    protected override void Initialize()
    {
        IVsRunningDocumentTable rdt = (IVsRunningDocumentTable)
        this.GetService(typeof(SVsRunningDocumentTable));
        rdt.AdviseRunningDocTableEvents(this, out rdtCookie);
    }
    ```

     <xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable>Для получения интерфейса вызывается служба <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable> . <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.AdviseRunningDocTableEvents%2A>Метод подключает события РДТ к объекту, реализующему <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents> в данном случае объект рдтексплорер.

8. Обновите метод Dispose () Рдтексплорервиндов.

    ```csharp
    protected override void Dispose(bool disposing)
    {
        // Release the RDT cookie.
        IVsRunningDocumentTable rdt = (IVsRunningDocumentTable)
            Package.GetGlobalService(typeof(SVsRunningDocumentTable));
        rdt.UnadviseRunningDocTableEvents(rdtCookie);

        base.Dispose(disposing);
    }
    ```

     <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.UnadviseRunningDocTableEvents%2A>Метод удаляет соединение между `RDTExplorer` и РДТ уведомления о событии.

9. Добавьте следующую строку в тело <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents.OnBeforeLastDocumentUnlock%2A> обработчика непосредственно перед `return` инструкцией.

    ```csharp
    public int OnBeforeLastDocumentUnlock(uint docCookie, uint dwRDTLockType, uint dwReadLocksRemaining, uint dwEditLocksRemaining)
    {
        ((RDTExplorerWindowControl)this.Content).listBox.Items.Add("Entering OnBeforeLastDocumentUnlock");
        return VSConstants.S_OK;
    }
    ```

10. Добавьте аналогичную строку в текст <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents.OnAfterFirstDocumentLock%2A> обработчика и в другие события, которые необходимо просмотреть в списке.

    ```csharp
    public int OnAfterFirstDocumentLock(uint docCookie, uint dwRDTLockType, uint dwReadLocksRemaining, uint dwEditLocksRemaining)
    {
        ((RDTExplorerWindowControl)this.Content).listBox.Items.Add("Entering OnAfterFirstDocumentLock");
        return VSConstants.S_OK;
    }
    ```

11. Выполните сборку решения и запустите отладку. Откроется экспериментальный экземпляр Visual Studio.

12. Откройте **рдтексплорервиндов** (**представление/другие окна или рдтексплорервиндов**).

     Откроется окно **рдтексплорервиндов** с пустым списком событий.

13. Откройте или создайте решение.

     `OnBeforeLastDocument`События AS и `OnAfterFirstDocument` запускаются, поэтому в списке событий отображаются уведомления о каждом событии.
