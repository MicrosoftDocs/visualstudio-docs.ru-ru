---
title: Как предоставить асинхронную службу Visual Studio | Документация Майкрософт
description: Узнайте, как предоставить асинхронную службу Visual Studio. Такой подход позволяет получить службу, не блокируя поток пользовательского интерфейса.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 0448274c-d3d2-4e12-9d11-8aca78a1f3f5
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: f9973bb86296442f4b936ddb54ff645d74d7ab74
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105074942"
---
# <a name="how-to-provide-an-asynchronous-visual-studio-service"></a>Как предоставить асинхронную службу Visual Studio
Если вы хотите получить службу, не блокируя поток пользовательского интерфейса, следует создать асинхронную службу и загрузить пакет в фоновом потоке. Для этой цели можно использовать <xref:Microsoft.VisualStudio.Shell.AsyncPackage> вместо <xref:Microsoft.VisualStudio.Shell.Package> , а также добавить службу с особыми асинхронными методами асинхронного пакета.

 Сведения о предоставлении синхронных служб Visual Studio см. [в разделе руководство. предоставление службы](../extensibility/how-to-provide-a-service.md).

## <a name="implement-an-asynchronous-service"></a>Реализация асинхронной службы

1. Создание проекта VSIX (**файл**  >  **создать**  >  **проект**  >  **Visual C#**  >  **расширяемости**  >  **VSIX**). Назовите проект **тестасинк**.

2. Добавьте VSPackage в проект. Выберите узел проекта в **Обозреватель решений** и щелкните **Добавить**  >  **новый элемент**  >  **Visual C# элементы**  >  **расширяемость**  >  **пакет Visual Studio**. Назовите этот файл *тестасинкпаккаже. CS*.

3. В *тестасинкпаккаже. CS* Измените пакет, чтобы он наследовал от, `AsyncPackage` а не от `Package` :

    ```csharp
    public sealed class TestAsyncPackage : AsyncPackage
    ```

4. Чтобы реализовать службу, необходимо создать три типа:

    - Интерфейс, идентифицирующий службу. Многие из этих интерфейсов пусты, т. е. они не имеют методов, так как они используются только для запроса службы.

    - Интерфейс, описывающий интерфейс службы. Этот интерфейс включает методы, которые должны быть реализованы.

    - Класс, реализующий как службу, так и интерфейс службы.

5. В следующем примере показана базовая реализация трех типов. Конструктор класса службы должен задать поставщик службы. В этом примере мы просто добавим службу в файл кода пакета.

6. Добавьте следующие директивы using в файл пакета:

    ```csharp
    using System.Threading;
    using System.Threading.Tasks;
    using System.Runtime.CompilerServices;
    using System.IO;
    using Microsoft.VisualStudio.Threading;
    using IAsyncServiceProvider = Microsoft.VisualStudio.Shell.IAsyncServiceProvider;
    using Task = System.Threading.Tasks.Task;
    ```

7. Ниже приведена реализация асинхронной службы. Обратите внимание, что вместо синхронного поставщика служб в конструкторе необходимо задать поставщик асинхронной службы:

    ```csharp
    public class TextWriterService : STextWriterService, ITextWriterService
    {
        private IAsyncServiceProvider asyncServiceProvider;

        public TextWriterService(IAsyncServiceProvider provider)
        {
            // constructor should only be used for simple initialization
            // any usage of Visual Studio service, expensive background operations should happen in the
            // asynchronous InitializeAsync method for best performance
            asyncServiceProvider = provider;
        }

        public async Task InitializeAsync(CancellationToken cancellationToken)
        {
            await TaskScheduler.Default;
            // do background operations that involve IO or other async methods

            await ThreadHelper.JoinableTaskFactory.SwitchToMainThreadAsync(cancellationToken);
            // query Visual Studio services on main thread unless they are documented as free threaded explicitly.
            // The reason for this is the final cast to service interface (such as IVsShell) may involve COM operations to add/release references.

            IVsShell vsShell = this.asyncServiceProvider.GetServiceAsync(typeof(SVsShell)) as IVsShell;
            // use Visual Studio services to continue initialization
        }

        public async Task WriteLineAsync(string path, string line)
        {
            StreamWriter writer = new StreamWriter(path);
            await writer.WriteLineAsync(line);
            writer.Close();
        }
    }

    public interface STextWriterService
    {
    }

    public interface ITextWriterService
    {
        System.Threading.Tasks.Task WriteLineAsync(string path, string line);
    }
    ```

## <a name="register-a-service"></a>Регистрация службы
 Чтобы зарегистрировать службу, добавьте в <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> пакет, предоставляющий службу. Для регистрации синхронной службы необходимо убедиться, что оба пакета и службы поддерживают асинхронную загрузку:

- Необходимо добавить поле **алловсбаккграундлоадинг = true** в, <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute> чтобы обеспечить возможность асинхронной инициализации пакета для получения дополнительных сведений о паккажерегистратионаттрибуте, см. раздел [Регистрация и Отмена регистрации пакетов VSPackage](../extensibility/registering-and-unregistering-vspackages.md).

- Чтобы гарантировать, что экземпляр службы можно инициализировать асинхронно, необходимо добавить поле **исасинккуерябле = true** в параметр <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> .

  Ниже приведен пример `AsyncPackage` с регистрацией асинхронной службы:

```csharp
[ProvideService((typeof(STextWriterService)), IsAsyncQueryable = true)]
[ProvideAutoLoad(UIContextGuids80.SolutionExists, PackageAutoLoadFlags.BackgroundLoad)]
[PackageRegistration(UseManagedResourcesOnly = true, AllowsBackgroundLoading = true)]
[Guid(TestAsyncPackage.PackageGuidString)]
public sealed class TestAsyncPackage : AsyncPackage
{. . . }
```

## <a name="add-a-service"></a>Добавление службы

1. В *тестасинкпаккаже. CS* удалите `Initialize()` метод и переопределите `InitializeAsync()` метод. Добавьте службу и добавьте метод обратного вызова для создания служб. Ниже приведен пример асинхронного инициализатора, который добавляет службу:

    ```csharp
    protected override async Task InitializeAsync(CancellationToken cancellationToken, IProgress<ServiceProgressData> progress)
    {
        await base.InitializeAsync(cancellationToken, progress);
        this.AddService(typeof(STextWriterService), CreateTextWriterService);
    }

    ```
    Чтобы эта служба стала видимой за пределами этого пакета, установите для флага Promote значение *true* в качестве последнего параметра:  `this.AddService(typeof(STextWriterService), CreateTextWriterService, true);`

2. Добавьте ссылку на *Microsoft.VisualStudio.Shell.Interop.14.0.DesignTime.dll*.

3. Реализуйте метод обратного вызова в качестве асинхронного метода, который создает и возвращает службу.

    ```csharp
    public async Task<object> CreateTextWriterService(IAsyncServiceContainer container, CancellationToken cancellationToken, Type serviceType)
    {
        TextWriterService service = new TextWriterService(this);
        await service.InitializeAsync(cancellationToken);
        return service;
    }

    ```

## <a name="use-a-service"></a>Использование службы
 Теперь вы можете получить службу и использовать ее методы.

1. Мы покажем это в инициализаторе, но вы можете получить службу в любом месте, где вы хотите использовать службу.

    ```csharp
    protected override async System.Threading.Tasks.Task InitializeAsync(CancellationToken cancellationToken, IProgress<ServiceProgressData> progress)
    {
        await base.InitializeAsync(cancellationToken, progress);
        this.AddService(typeof(STextWriterService), CreateTextWriterService);

        ITextWriterService textService = await this.GetServiceAsync(typeof(STextWriterService)) as ITextWriterService;
        string userpath = @"C:\MyDir\MyFile.txt";
        await textService.WriteLineAsync(userpath, "this is a test");
    }

    ```

     Не забудьте перейти `userpath` к имени файла и пути, которые имеют смысл на вашем компьютере!

2. Выполните сборку и запустите код. Когда появится экспериментальный экземпляр Visual Studio, откройте решение. Это приводит `AsyncPackage` к автозагрузкиу. При запуске инициализатора необходимо найти файл в указанном расположении.

## <a name="use-an-asynchronous-service-in-a-command-handler"></a>Использование асинхронной службы в обработчике команд
 Ниже приведен пример использования асинхронной службы в команде меню. Приведенную здесь процедуру можно использовать для использования службы в других неасинхронных методах.

1. Добавьте команду меню в проект. (В **Обозреватель решений** выберите узел проекта, щелкните его правой кнопкой мыши и выберите Добавить.   >  **Новый элемент**  >  **Расширяемость**  >  **Пользовательская команда**.) Назовите командный файл *тестасинккомманд. CS*.

2. Пользовательский шаблон команды повторно добавляет `Initialize()` метод в файл *тестасинкпаккаже. CS* , чтобы инициализировать команду. В `Initialize()` методе скопируйте строку, которая инициализирует команду. Он должен выглядеть так:

    ```csharp
    TestAsyncCommand.Initialize(this);
    ```

     Переместите эту строку в `InitializeAsync()` метод в файле *асинкпаккажефорсервице. CS* . Так как это асинхронная инициализация, необходимо переключиться на основной поток перед инициализацией команды с помощью <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A> . Результат будет выглядеть так:

    ```csharp

    protected override async System.Threading.Tasks.Task InitializeAsync(CancellationToken cancellationToken, IProgress<ServiceProgressData> progress)
    {
        await base.InitializeAsync(cancellationToken, progress);
        this.AddService(typeof(STextWriterService), CreateTextWriterService);

        ITextWriterService textService =
           await this.GetServiceAsync(typeof(STextWriterService)) as ITextWriterService;
        
        string userpath = @"C:\MyDir\MyFile.txt";
        await textService.WriteLineAsync(userpath, "this is a test");

        await this.JoinableTaskFactory.SwitchToMainThreadAsync(cancellationToken);
        TestAsyncCommand.Initialize(this);
    }

    ```

3. Удалите `Initialize()` метод.

4. Найдите метод в файле *тестасинккомманд. CS* `MenuItemCallback()` . Удалите текст метода.

5. Добавьте директиву using:

    ```csharp
    using System.IO;
    ```

6. Добавьте асинхронный метод с именем `UseTextWriterAsync()` , который получает службу и использует ее методы:

    ```csharp
    private async System.Threading.Tasks.Task UseTextWriterAsync()
    {
        // Query text writer service asynchronously to avoid a blocking call.
        ITextWriterService textService =
           await AsyncServiceProvider.GlobalProvider.GetServiceAsync(typeof(STextWriterService))
              as ITextWriterService;

        string userpath = @"C:\MyDir\MyFile.txt";
        await textService.WriteLineAsync(userpath, "this is a test");
       }

    ```

7. Вызовите этот метод из `MenuItemCallback()` метода:

    ```csharp
    private void MenuItemCallback(object sender, EventArgs e)
    {
        UseTextWriterAsync();
    }

    ```

8. Постройте решение и запустите отладку. Когда появится экспериментальный экземпляр Visual Studio, перейдите в меню **Сервис** и найдите пункт меню **вызвать тестасинккомманд** . Если щелкнуть его, Текствритерсервице запишет в указанный файл. (Не нужно открывать решение, так как вызов команды также вызывает загрузку пакета.)

## <a name="see-also"></a>См. также
- [Использование и предоставление служб](../extensibility/using-and-providing-services.md)
