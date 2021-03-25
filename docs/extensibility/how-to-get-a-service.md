---
title: Руководство. Получение службы | Документация Майкрософт
description: Узнайте, как получить доступ к различным функциям в службах Visual Studio. Большинство служб можно получить с помощью VSPackage.
ms.custom: SEO-VS-2020
ms.date: 3/16/2019
ms.topic: how-to
helpviewer_keywords:
- services, consuming
ms.assetid: 1f000020-8fb7-4e39-8e1e-2e38c7fec3d4
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 9096250f72e6bf64b2c6b76eeaa313ee7769dd51
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105070093"
---
# <a name="how-to-get-a-service"></a>Руководство. Получение службы

Для доступа к различным функциям часто требуется получить доступ к службам Visual Studio. Как правило, служба Visual Studio предоставляет один или несколько интерфейсов, которые можно использовать. Большинство служб можно получить из VSPackage.

Любой пакет VSPackage, производный от <xref:Microsoft.VisualStudio.Shell.Package> и, который был правильно помещен в сайт, может запросить любую глобальную службу. Поскольку `Package` класс реализует <xref:System.IServiceProvider> , любой пакет VSPackage, производный от, `Package` также является поставщиком службы.

При загрузке Visual Studio <xref:Microsoft.VisualStudio.Shell.Package> объект передается в <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> метод во время инициализации. Это называется *заблокировано* VSPackage. `Package`Класс служит оболочкой этого поставщика услуг и предоставляет <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> метод для получения служб.

## <a name="getting-a-service-from-an-initialized-vspackage"></a>Получение службы из инициализированного пакета VSPackage

1. Каждое расширение Visual Studio начинается с проекта развертывания VSIX, который будет содержать ресурсы расширения. Создайте [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] проект VSIX с именем `GetServiceExtension` . Шаблон проекта VSIX можно найти в диалоговом окне " **Новый проект** ", выполнив поиск по слову "VSIX".

2. Теперь добавьте пользовательский шаблон элемента команды с именем **жетсервицекомманд**. В диалоговом окне **Добавление нового элемента** перейдите в раздел расширяемость **Visual C#**  >   и выберите пункт **пользовательская команда**. В поле **имя** в нижней части окна измените имя файла команд на *жетсервицекомманд. CS*. Дополнительные сведения о создании настраиваемой команды см. в статье [Создание расширения с помощью команды меню](../extensibility/creating-an-extension-with-a-menu-command.md) .

3. В *жетсервицекомманд. CS* удалите текст `MenuItemCommand` метода и добавьте следующий код:

   ```csharp
   IVsActivityLog activityLog = ServiceProvider.GetService(typeof(SVsActivityLog)) as IVsActivityLog;
   if (activityLog == null) return;
   System.Windows.Forms.MessageBox.Show("Found the activity log service.");

   ```

    Этот код получает службу Свсактивитилог и приводит ее к <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog> интерфейсу, который можно использовать для записи в журнал действий. Пример см. в разделе [как использовать журнал действий](../extensibility/how-to-use-the-activity-log.md).

4. Выполните сборку решения и запустите отладку. Откроется экспериментальный экземпляр.

5. В меню **Сервис** экспериментального экземпляра найдите кнопку **вызвать жетсервицекомманд** . При нажатии этой кнопки должно отобразиться окно с сообщением о том, что **Служба журнала действий найдена.**

## <a name="getting-a-service-from-a-tool-window-or-control-container"></a>Получение службы из окна инструментов или контейнера элемента управления

Иногда может потребоваться получить службу из окна инструментов или контейнера элемента управления, который не был добавлен в узел, или в другом месте с поставщиком услуг, который не знает о нужной службе. Например, может потребоваться запись в журнал действий из элемента управления.

Статический <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> метод основан на кэшированном поставщике служб, который инициализируется в первый раз, когда любой из VSPackage, производный от <xref:Microsoft.VisualStudio.Shell.Package> , находится на сайте.

Так как конструктор VSPackage вызывается до того, как VSPackage размещается в узле, глобальные службы обычно недоступны из конструктора VSPackage. Дополнительные сведения см. в статье [Устранение неполадок служб](../extensibility/how-to-troubleshoot-services.md) .

Ниже приведен пример способа получения службы в окне инструментов или в другом элементе, не являющемся VSPackage.

```csharp
IVsActivityLog log = Package.GetGlobalService(typeof(SVsActivityLog)) as IVsActivityLog;
if (log == null) return;
```

## <a name="getting-a-service-from-the-dte-object"></a>Получение службы из объекта DTE

Также можно получить службы из <xref:EnvDTE.DTEClass> объекта. Однако необходимо получить объект DTE как службу из VSPackage или путем вызова статического <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> метода.

Объект DTE реализует <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> , который можно использовать для запроса службы с помощью <xref:Microsoft.VisualStudio.Shell.ServiceProvider.GetService%2A> .

Вот как можно получить службу из объекта DTE.

```csharp
// Start with the DTE object, for example: 
// using EnvDTE;
// DTE dte = (DTE)GetService(typeof(DTE));

ServiceProvider sp = new ServiceProvider((Microsoft.VisualStudio.OLE.Interop.IServiceProvider)dte);
if (sp != null)
{
    IVsActivityLog log = sp.GetService(typeof(SVsActivityLog)) as IVsActivityLog;
    if (log != null)
    {
        System.Windows.Forms.MessageBox.Show("Found the activity log service.");
    }
}
```

## <a name="see-also"></a>См. также

- [Руководство. предоставление службы](../extensibility/how-to-provide-a-service.md)
- [Использование и предоставление служб](../extensibility/using-and-providing-services.md)
- [Основные компоненты службы](../extensibility/internals/service-essentials.md)
