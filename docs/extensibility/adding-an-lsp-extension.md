---
title: Добавление расширения протокола языкового сервера | Документация Майкрософт
description: Узнайте, как создать расширение Visual Studio, которое интегрирует языковой сервер на основе протокола Language Server (LSP).
ms.custom: SEO-VS-2020
ms.date: 11/14/2017
ms.topic: conceptual
ms.assetid: 52f12785-1c51-4c2c-8228-c8e10316cd83
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: accf054cbf0b58066568124a3f35e064ce3cba78
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105094995"
---
# <a name="add-a-language-server-protocol-extension"></a>Добавление расширения протокола языкового сервера

Протокол Language Server (LSP) — это общий протокол в формате JSON RPC версии 2.0, используемый для предоставления функций языковой службы различным редакторам кода. Используя протокол, разработчики могут создавать сервер с одним языком для предоставления таких функций языковой службы, как IntelliSense, диагностика ошибок, поиск всех ссылок и т. д. в различных редакторах кода, поддерживающих LSP. Традиционно языковые службы в Visual Studio можно добавить с помощью файлов грамматики TextMate, чтобы обеспечить основные функциональные возможности, такие как выделение синтаксиса или написание пользовательских языковых служб, использующих полный набор API расширяемости Visual Studio для предоставления более подробных данных. С поддержкой Visual Studio для LSP существует третий вариант.

![Служба протокола языкового сервера в Visual Studio](media/lsp-service-in-VS.png)

## <a name="language-server-protocol"></a>Протокол языкового сервера

![Реализация протокола серверного языка](media/lsp-implementation.png)

В этой статье описывается, как создать расширение Visual Studio, которое использует серверный язык, основанный на LSP. Предполагается, что вы уже разработали серверный язык, основанный на LSP, и просто хотите интегрировать его в Visual Studio.

Для поддержки в Visual Studio языковые серверы могут взаимодействовать с клиентом (Visual Studio) с помощью любого механизма передачи на основе потока, например:

* Стандартные потоки ввода-вывода
* Именованные каналы
* Сокеты (только TCP)

Целью LSP и его поддержки в Visual Studio является внедрение языковых служб, которые не являются частью продукта Visual Studio. Он не предназначен для расширения существующих языковых служб (например, C#) в Visual Studio. Дополнительные сведения о расширении существующих языков см. в руководстве по расширению языковой службы (например, ["Roslyn" .NET Compiler Platform](../extensibility/dotnet-compiler-platform-roslyn-extensibility.md)) или [в разделе Расширение возможностей редактора и языковых служб](../extensibility/extending-the-editor-and-language-services.md).

Дополнительные сведения о самом протоколе см. в документации [здесь](https://github.com/Microsoft/language-server-protocol).

Дополнительные сведения о создании образца языкового сервера или интеграции существующего языкового сервера в Visual Studio Code см. в документации [здесь](https://code.visualstudio.com/docs/extensions/example-language-server).

## <a name="language-server-protocol-supported-features"></a>Поддерживаемые функции протокола сервера языка

В следующих таблицах показано, какие функции LSP поддерживаются в Visual Studio:

Сообщение | Имеет поддержку в Visual Studio
--- | ---
устанавливает | да
инициализирован | да
shutdown | да
exit | да
/Канцелрекуест | да
окно или showMessage | да
окно или Шовмессажерекуест | да
окно или logMessage | да
данные телеметрии и события |
Клиент/Регистеркапабилити |
Клиент/Унрегистеркапабилити |
Рабочая область или Дидчанжеконфигуратион | да
Рабочая область или Дидчанжеватчедфилес | да
Рабочая область или символ | да
Рабочая область/executeCommand | да
Рабочая область или Аппледит | да
textDocument/Публишдиагностикс | да
textDocument/Дидопен | да
textDocument/Дидчанже | да
textDocument/Виллсаве |
textDocument/Виллсавеваитунтил |
textDocument/Дидсаве | да
textDocument/Дидклосе | да
textDocument/завершение | да
завершение и разрешение | да
textDocument/наведение указателя мыши | да
textDocument/Сигнатурехелп | да
textDocument и ссылки | да
textDocument/Докуменсигхлигхт | да
textDocument/Документсимбол | да
textDocument/форматирование | да
textDocument/Ранжеформаттинг | да
textDocument/Онтипеформаттинг |
textDocument/определение | да
textDocument/Кодеактион | да
textDocument/codeLens |
codeLens/разрешение |
textDocument/Документлинк |
Документлинк/разрешить |
textDocument/переименовать | да

## <a name="get-started"></a>Приступая к работе

> [!NOTE]
> Начиная с Visual Studio 2017 версии 15,8, поддержка протокола общего языка сервера встроена в Visual Studio. Если вы создали расширения LSP с помощью [клиентской версии VSIX на языке](https://marketplace.visualstudio.com/items?itemName=vsext.LanguageServerClientPreview) , они перестанут работать после обновления до версии 15,8 или более поздней. Для повторной работы расширений LSP необходимо выполнить следующие действия.
>
> 1. Удалите версию VSIX для протокола сервера Microsoft Visual Studio Language.
>
>    Начиная с версии 15,8 при каждом выполнении обновления в Visual Studio предварительный просмотр VSIX автоматически обнаруживается и удаляется.
>
> 2. Обновите ссылку NuGet до последней версии [пакета LSP](https://www.nuget.org/packages/Microsoft.VisualStudio.LanguageServer.Client), не являющейся предварительной.
>
> 3. Удалите зависимость для предварительной версии протокола сервера Microsoft Visual Studio Language. VSIX в манифесте VSIX.
>
> 4. Убедитесь, что в VSIX указана версия Visual Studio 2017 версии 15,8 3 в качестве нижней границы для целевого объекта установки.
>
> 5. заново собрать или повторно развернуть ресурс.

### <a name="create-a-vsix-project"></a>Создание проекта VSIX

Чтобы создать расширение языковой службы с помощью серверного языка на основе LSP, сначала убедитесь, что у вас установлена рабочая нагрузка **разработки расширения Visual Studio** для экземпляра vs.

Затем создайте новый проект VSIX, перейдя к **файлу**  >  **Новый** проект  >    >  **расширяемость** Visual C# проект  >  **VSIX**:

![Создание проекта VSIX](media/lsp-vsix-project.png)

### <a name="language-server-and-runtime-installation"></a>Языковой сервер и установка среды выполнения

По умолчанию расширения, созданные для поддержки серверных языков на основе LSP в Visual Studio, не содержат сами языковые серверы или среды выполнения, необходимые для их выполнения. Разработчики расширений несут ответственность за распространение языковых серверов и необходимых сред выполнения. Это можно сделать несколькими способами:

* Языковые серверы можно внедрять в VSIX как файлы содержимого.
* Создайте MSI-файл для установки языкового сервера и (или) требуемых сред выполнения.
* Предоставьте инструкции в Marketplace, информирующее пользователей о том, как получить среды выполнения и языковые серверы.

### <a name="textmate-grammar-files"></a>Файлы грамматики TextMate

LSP не включает спецификацию того, как обеспечить цветовую цветопередачу текста для языков. Чтобы обеспечить пользовательскую цветовую раскраску для языков в Visual Studio, разработчики расширений могут использовать файл грамматики TextMate. Чтобы добавить пользовательские файлы грамматики или темы TextMate, выполните следующие действия.

1. Создайте папку с именем "грамматики" в расширении (или это может быть любое имя, которое вы выбираете).

2. В папке " *грамматики* " Включите любые файлы *\* тмлангуаже*, *\* plist*, *\* . тмсеме* или *\* . JSON* , которые вам нужны, чтобы обеспечить пользовательскую цветовую раскраску.

   > [!TIP]
   > *Тмсеме* -файл определяет, как области сопоставляются с классификациями Visual Studio (именованными ключами цвета). Чтобы получить рекомендации, можно сослаться на глобальный файл *тмсеме* в каталоге *% ProgramFiles (x86)% \ Microsoft Visual Studio \\ \<version> \\ \<SKU> \Common7\IDE\CommonExtensions\Microsoft\TextMate\Starterkit\Themesg* .

3. Создайте файл *pkgdef* и добавьте строку, аналогичную следующей:

    ```
    [$RootKey$\TextMate\Repositories]
    "MyLang"="$PackageFolder$\Grammars"
    ```

4. Щелкните файлы правой кнопкой мыши и выберите пункт **Свойства**. Измените действие **сборки** на **содержимое** и измените значение свойства **включить в VSIX** на **true**.

После выполнения описанных выше действий в каталог установки пакета добавляется папка *грамматики* в качестве источника репозитория с именем "миланг" ("миланг" — это просто имя для устранения неоднозначности и может быть любой уникальной строкой). Все грамматики (*тмлангуаже* -файлы) и файлы тем (*тмсеме* -файлы) в этом каталоге выбираются как потенциальные и заменяют встроенные грамматики, предоставленные TextMate. Если объявленные расширения файла грамматики соответствуют расширению открываемого файла, TextMate будет выполнен Шаг с заходом.

## <a name="create-a-simple-language-client"></a>Создание клиента простого языка

### <a name="main-interface---ilanguageclient"></a>Основной интерфейс — [илангуажеклиент](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient?view=visualstudiosdk-2017&preserve-view=true)

После создания проекта VSIX добавьте в проект следующие пакеты NuGet:

* [Microsoft. VisualStudio. Лангуажесервер. Client](https://www.nuget.org/packages/Microsoft.VisualStudio.LanguageServer.Client)

> [!NOTE]
> При зависимости от пакета NuGet после выполнения описанных выше действий в проект также добавляются Newtonsoft.Jsи пакеты Стреамжсонрпк. **Не обновляйте эти пакеты, если не уверены, что эти новые версии будут установлены в версии Visual Studio, для которой предназначено расширение**. Сборки не будут включаться в VSIX; Вместо этого они будут отобраны из каталога установки Visual Studio. Если вы ссылаетесь на более новую версию сборок, чем установленное на компьютере пользователя, расширение работать не будет.

Затем можно создать новый класс, реализующий интерфейс [илангуажеклиент](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient?view=visualstudiosdk-2017&preserve-view=true) , который является основным интерфейсом, необходимым для клиентских клиентов, подключающихся к серверному языковому интерфейсу.

Ниже приведен пример:

```csharp
namespace MockLanguageExtension
{
    [ContentType("bar")]
    [Export(typeof(ILanguageClient))]
    public class BarLanguageClient : ILanguageClient
    {
        public string Name => "Bar Language Extension";

        public IEnumerable<string> ConfigurationSections => null;

        public object InitializationOptions => null;

        public IEnumerable<string> FilesToWatch => null;

        public event AsyncEventHandler<EventArgs> StartAsync;
        public event AsyncEventHandler<EventArgs> StopAsync;

        public async Task<Connection> ActivateAsync(CancellationToken token)
        {
            await Task.Yield();

            ProcessStartInfo info = new ProcessStartInfo();
            info.FileName = Path.Combine(Path.GetDirectoryName(Assembly.GetExecutingAssembly().Location), "Server", @"MockLanguageServer.exe");
            info.Arguments = "bar";
            info.RedirectStandardInput = true;
            info.RedirectStandardOutput = true;
            info.UseShellExecute = false;
            info.CreateNoWindow = true;

            Process process = new Process();
            process.StartInfo = info;

            if (process.Start())
            {
                return new Connection(process.StandardOutput.BaseStream, process.StandardInput.BaseStream);
            }

            return null;
        }

        public async Task OnLoadedAsync()
        {
            await StartAsync.InvokeAsync(this, EventArgs.Empty);
        }

        public Task OnServerInitializeFailedAsync(Exception e)
        {
            return Task.CompletedTask;
        }

        public Task OnServerInitializedAsync()
        {
            return Task.CompletedTask;
        }
    }
}
```

Основные методы, которые необходимо реализовать, — это [онлоадедасинк](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.onloadedasync?view=visualstudiosdk-2017&preserve-view=true) и [активатеасинк](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.activateasync?view=visualstudiosdk-2017&preserve-view=true). [Онлоадедасинк](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.onloadedasync?view=visualstudiosdk-2017&preserve-view=true) вызывается, когда Visual Studio загрузил расширение, и Ваш языковой сервер готов к запуску. В этом методе можно немедленно вызвать делегат [стартасинк](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.startasync?view=visualstudiosdk-2017&preserve-view=true) , чтобы сообщить о том, что должен быть запущен языковой сервер, или можно выполнить дополнительную логику и вызвать [стартасинк](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.startasync?view=visualstudiosdk-2017&preserve-view=true) позже. **Чтобы активировать языковой сервер, необходимо вызвать Стартасинк в некоторый момент.**

[Активатеасинк](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.activateasync?view=visualstudiosdk-2017&preserve-view=true) — это метод, который в конечном итоге вызывается путем вызова делегата [стартасинк](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.startasync?view=visualstudiosdk-2017&preserve-view=true) . Он содержит логику для запуска языкового сервера и установления подключения к нему. Должен возвращаться объект соединения, содержащий потоки для записи на сервер и чтения с сервера. Все исключения, созданные здесь, перехватываются и отображаются для пользователя с помощью сообщения информационной панели в Visual Studio.

### <a name="activation"></a>Активация

После реализации класса языкового клиента необходимо определить два атрибута, чтобы определить, как он будет загружен в Visual Studio и активирован:

```csharp
  [Export(typeof(ILanguageClient))]
  [ContentType("bar")]
```

### <a name="mef"></a>MEF

Visual Studio использует [MEF](https://github.com/Microsoft/vs-mef/blob/master/doc/index.md) (Managed Extensibility Framework) для управления точками расширения. Атрибут [Export](/dotnet/api/system.componentmodel.composition.exportattribute) указывает Visual Studio, что этот класс следует выбрать в качестве точки расширения и загрузить в соответствующее время.

Чтобы использовать MEF, необходимо также определить MEF в качестве ресурса в манифесте VSIX.

Откройте конструктор манифеста VSIX и перейдите на вкладку **Assets (активы** ):

![Добавить ресурс MEF](media/lsp-add-asset.png)

Щелкните **создать** , чтобы создать новый ресурс:

![Определение ресурса MEF](media/lsp-define-asset.png)

* **Тип**: Microsoft. VisualStudio. MefComponent
* **Источник**: проект в текущем решении
* **Проект**: [ваш проект]

### <a name="content-type-definition"></a>Определение типа содержимого

Сейчас единственный способ загрузить расширение серверного языка на основе LSP — это тип содержимого файла. То есть при определении клиентского класса языка (который реализует [илангуажеклиент](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient?view=visualstudiosdk-2017&preserve-view=true)) необходимо определить типы файлов, которые при открытии приведут к загрузке расширения. Если не открыто ни одного файла, соответствующего определенному типу содержимого, расширение не будет загружено.

Это делается путем определения одного или нескольких `ContentTypeDefinition` классов:

```csharp
namespace MockLanguageExtension
{
    public class BarContentDefinition
    {
        [Export]
        [Name("bar")]
        [BaseDefinition(CodeRemoteContentDefinition.CodeRemoteContentTypeName)]
        internal static ContentTypeDefinition BarContentTypeDefinition;

        [Export]
        [FileExtension(".bar")]
        [ContentType("bar")]
        internal static FileExtensionToContentTypeDefinition BarFileExtensionDefinition;
    }
}
```

В предыдущем примере для файлов, заканчивающихся расширением *. Bar* , создается определение типа содержимого. Определение типа содержимого получает имя "Bar" и должно быть производным от [кодеремотеконтенттипенаме](/dotnet/api/microsoft.visualstudio.languageserver.client.coderemotecontentdefinition.coderemotecontenttypename?view=visualstudiosdk-2017&preserve-view=true).

После добавления определения типа содержимого можно определить, когда следует загружать расширение клиента языка в класс Language Client:

```csharp
    [ContentType("bar")]
    [Export(typeof(ILanguageClient))]
    public class BarLanguageClient : ILanguageClient
    {
    }
```

Для добавления поддержки для серверных языков LSP не требуется реализовывать собственную систему проектов в Visual Studio. Клиенты могут открыть один файл или папку в Visual Studio, чтобы начать работу с языковой службой. По сути, поддержка серверных языковых серверов разработана для работы только в сценариях открытия файлов и папок. Если реализуется пользовательская система проектов, некоторые функции (такие как параметры) не будут работать.

## <a name="advanced-features"></a>Дополнительные функции

### <a name="settings"></a>Параметры

Поддержка настраиваемых языковых параметров для конкретного языка доступна, но она по-прежнему находится в процессе улучшения. Параметры зависят от того, что поддерживает языковой сервер, и обычно управляют тем, как языковый сервер выдает данные. Например, языковой сервер может иметь параметр для максимального числа ошибок, о которых сообщается. Авторы расширений определяют значение по умолчанию, которое может быть изменено пользователями для конкретных проектов.

Чтобы добавить поддержку параметров в расширение службы языка LSP, выполните следующие действия.

1. Добавьте JSON-файл (например, *MockLanguageExtensionSettings.json*) в проект, содержащий параметры и их значения по умолчанию. Пример:

    ```json
    {
        "foo.maxNumberOfProblems": -1
    }
    ```

2. Щелкните правой кнопкой мыши JSON-файл и выберите пункт **Свойства**. Измените действие **сборки** на "содержимое", а свойство "включить в VSIX" в **значение true**.

3. Реализуйте Конфигуратионсектионс и верните список префиксов для параметров, определенных в JSON-файле (в Visual Studio Code это будет сопоставлено с именем раздела конфигурации в package.json):

    ```csharp
    public IEnumerable<string> ConfigurationSections
    {
        get
        {
            yield return "foo";
        }
    }
    ```

4. Добавьте pkgdef-файл в проект (добавить новый текстовый файл и измените расширение файла на pkgdef). Файл pkgdef должен содержать следующие сведения:

    ```
    [$RootKey$\OpenFolder\Settings\VSWorkspaceSettings\[settings-name]]
    @="$PackageFolder$\[settings-file-name].json"
    ```

    Образец.

    ```
    [$RootKey$\OpenFolder\Settings\VSWorkspaceSettings\MockLanguageExtension]
    @="$PackageFolder$\MockLanguageExtensionSettings.json"
    ```

5. Щелкните файл pkgdef правой кнопкой мыши и выберите пункт **Свойства**. Измените действие **сборки** на **содержимое** , а для свойства **включить в VSIX —** на **true**.

6. Откройте файл *source. extension. vsixmanifest* и добавьте ресурс на вкладке **актив** :

   ![Изменение ресурса VSPackage](media/lsp-add-vspackage-asset.png)

   * **Тип**: Microsoft. VisualStudio. VSPackage
   * **Источник**: файл в файловой системе
   * **Путь**: [путь к файлу *pkgdef* ]

### <a name="user-editing-of-settings-for-a-workspace"></a>Изменение параметров рабочей области пользователем

1. Пользователь открывает рабочую область, содержащую файлы, которыми владеет сервер.
2. Пользователь добавляет файл в папку *. VS* с именем *VSWorkspaceSettings.json*.
3. Пользователь добавляет строку в *VSWorkspaceSettings.jsв* файле для параметра, предоставляемого сервером. Пример:

    ```json
    {
        "foo.maxNumberOfProblems": 10
    }
    ```

### <a name="enable-diagnostics-tracing"></a>Включить трассировку диагностики

Трассировка диагностики может быть включена для вывода всех сообщений между клиентом и сервером, что может быть полезно при отладке проблем. Чтобы включить диагностическую трассировку, выполните следующие действия.

1. Откройте или создайте файл параметров рабочей области *VSWorkspaceSettings.jsна* странице (см. раздел "изменение параметров пользователя для рабочей области").
2. Добавьте следующую строку в файл параметров JSON:

```json
{
    "foo.trace.server": "Off"
}
```

Существует три возможных значения детализации трассировки:

* "OFF": трассировка полностью отключена
* "Сообщения": трассировка включена, но отслеживаются только имя метода и идентификатор ответа.
* "Verbose": трассировка включена; будет выполнен трассировка всего сообщения RPC.

Когда трассировка включена, содержимое записывается в файл в каталоге *%темп%\висуалстудио\лсп* . Журнал соответствует формату имени *[лангуажеклиентнаме]-[метка времени]. log*. В настоящее время трассировка может быть включена только для сценариев с открытыми папками. Открытие одного файла для активации языкового сервера не поддерживает трассировку диагностики.

### <a name="custom-messages"></a>Пользовательские сообщения

Существуют API-интерфейсы для упрощения передачи и получения сообщений от языкового сервера, не входящего в стандартный протокол сервера языка. Для работы с пользовательскими сообщениями реализуйте интерфейс [илангуажеклиенткустоммессаже](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage?view=visualstudiosdk-2017&preserve-view=true) в клиентском классе языка. Библиотека [VS-стреамжсонрпк](https://github.com/Microsoft/vs-streamjsonrpc/blob/master/doc/index.md) используется для передачи пользовательских сообщений между языковым клиентом и языковым сервером. Так как расширение клиента на языке LSP аналогично любому другому расширению Visual Studio, можно добавить дополнительные компоненты (которые не поддерживаются этим LSP) в Visual Studio (с помощью других API-интерфейсов Visual Studio) в расширении с помощью пользовательских сообщений.

#### <a name="receive-custom-messages"></a>Получение пользовательских сообщений

Для получения пользовательских сообщений от языкового сервера реализуйте свойство [кустоммессажетаржет](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage.custommessagetarget?view=visualstudiosdk-2017&preserve-view=true) в [илангуажеклиенткустоммессаже](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage?view=visualstudiosdk-2017&preserve-view=true) и Возвратите объект, который знает, как работать с пользовательскими сообщениями. См. пример ниже.

```csharp
internal class MockCustomLanguageClient : MockLanguageClient, ILanguageClientCustomMessage
{
    private JsonRpc customMessageRpc;

    public MockCustomLanguageClient() : base()
    {
        CustomMessageTarget = new CustomTarget();
    }

    public object CustomMessageTarget
    {
        get;
        set;
    }

    public class CustomTarget
    {
        public void OnCustomNotification(JToken arg)
        {
            // Provide logic on what happens OnCustomNotification is called from the language server
        }

        public string OnCustomRequest(string test)
        {
            // Provide logic on what happens OnCustomRequest is called from the language server
        }
    }
}
```

#### <a name="send-custom-messages"></a>Отправка пользовательских сообщений

Чтобы отправить пользовательские сообщения на сервер языка, реализуйте метод [аттачфоркустоммессажеасинк](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage.attachforcustommessageasync?view=visualstudiosdk-2017&preserve-view=true) в [илангуажеклиенткустоммессаже](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage?view=visualstudiosdk-2017&preserve-view=true). Этот метод вызывается при запуске языкового сервера и готовности к получению сообщений. Объект [жсонрпк](https://github.com/Microsoft/vs-streamjsonrpc/blob/master/src/StreamJsonRpc/JsonRpc.cs) передается в качестве параметра, который затем можно оставаться на отправку сообщений на сервер языка с помощью API [VS-стреамжсонрпк](https://github.com/Microsoft/vs-streamjsonrpc/blob/master/doc/index.md) . См. пример ниже.

```csharp
internal class MockCustomLanguageClient : MockLanguageClient, ILanguageClientCustomMessage
{
    private JsonRpc customMessageRpc;

    public MockCustomLanguageClient() : base()
    {
        CustomMessageTarget = new CustomTarget();
    }

    public async Task AttachForCustomMessageAsync(JsonRpc rpc)
    {
        await Task.Yield();

        this.customMessageRpc = rpc;
    }

    public async Task SendServerCustomNotification(object arg)
    {
        await this.customMessageRpc.NotifyWithParameterObjectAsync("OnCustomNotification", arg);
    }

    public async Task<string> SendServerCustomMessage(string test)
    {
        return await this.customMessageRpc.InvokeAsync<string>("OnCustomRequest", test);
    }
}
```

### <a name="middle-layer"></a>Средний слой

Иногда разработчику расширений может потребоваться перехват сообщений, отправляемых и получаемых с языкового сервера. Например, разработчику расширений может потребоваться изменить параметр сообщения, отправленный для конкретного LSP-сообщения, или изменить результаты, возвращенные сервером языка для функции LSP (например, завершения). При необходимости разработчики расширений могут использовать API Миддлелайер для перехвата сообщений LSP.

Каждое LSP сообщение имеет собственный интерфейс промежуточного слоя для перехвата. Чтобы перехватить конкретное сообщение, создайте класс, реализующий интерфейс среднего уровня для этого сообщения. Затем реализуйте интерфейс [илангуажеклиенткустоммессаже](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage?view=visualstudiosdk-2017&preserve-view=true) в клиентском классе языка и возвратите экземпляр объекта в свойстве [миддлелайер](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage.middlelayer?view=visualstudiosdk-2017&preserve-view=true) . См. пример ниже.

```csharp
public class MockLanguageClient: ILanguageClient, ILanguageClientCustomMessage
{
    public object MiddleLayer => MiddleLayerProvider.Instance;

    private class MiddleLayerProvider : ILanguageClientWorkspaceSymbolProvider
    {
        internal readonly static MiddleLayerProvider Instance = new MiddleLayerProvider();

        private MiddleLayerProvider()
        {
        }

        public async Task<SymbolInformation[]> RequestWorkspaceSymbols(WorkspaceSymbolParams param, Func<WorkspaceSymbolParams, Task<SymbolInformation[]>> sendRequest)
        {
            // Send along the request as given
            SymbolInformation[] symbols = await sendRequest(param);

            // Only return symbols that are "files"
            return symbols.Where(sym => string.Equals(new Uri(sym.Location.Uri).Scheme, "file", StringComparison.OrdinalIgnoreCase)).ToArray();
        }
    }
}
```

Функция среднего уровня все еще находится в разработке, но еще не является исчерпывающей.

## <a name="sample-lsp-language-server-extension"></a>Пример расширения сервера для LSP

Исходный код примера расширения с помощью клиентского API LSP в Visual Studio см. в разделе VSSDK-Extensibility-Samples [LSP Sample](https://github.com/Microsoft/VSSDK-Extensibility-Samples/tree/master/LanguageServerProtocol).

## <a name="faq"></a>Вопросы и ответы

**Я хотел бы создать пользовательскую систему проектов, чтобы дополнить мой языковой сервер для обеспечения расширенной поддержки функций в Visual Studio, как это сделать?**

Поддержка серверных языков, основанных на LSP в Visual Studio, зависит от [функции открытой папки](https://devblogs.microsoft.com/visualstudio/open-any-folder-with-visual-studio-15-preview/) и не требует специальной системы проектов. Вы можете создать собственную пользовательскую систему проектов, следуя указаниям [здесь](https://github.com/Microsoft/VSProjectSystem), но некоторые функции, например параметры, могут не работать. Логика инициализации по умолчанию для LSP-языковых серверов заключается в том, чтобы передать расположение корневой папки открываемой в данный момент папки, поэтому при использовании пользовательской системы проектов может потребоваться указать пользовательскую логику во время инициализации, чтобы убедиться, что Ваш языковой сервер может быть запущен правильно.

**Разделы справки добавить поддержку отладчика?**

Мы предоставляем поддержку [общего протокола отладки](https://code.visualstudio.com/docs/extensionAPI/api-debugging) в будущем выпуске.

**Если на компьютере уже установлена поддерживаемая языковая служба VS (например, JavaScript), можно ли по-прежнему установить расширение сервера LSP, предлагающее дополнительные функции (например, linting)?**

Да, но не все функции будут работать должным образом. Основная цель для серверных расширений LSP-языка — Включение языковых служб, изначально не поддерживаемых Visual Studio. Вы можете создавать расширения, которые обеспечивают дополнительную поддержку с помощью серверов языковой поддержки, но некоторые функции (например, IntelliSense) не будут работать гладко. Как правило, рекомендуется использовать серверные расширения LSP для предоставления новых языков программирования, а не расширения существующих.

**Где опубликовать завершенный VSIX языкового сервера?**

См. инструкции по Marketplace [здесь](walkthrough-publishing-a-visual-studio-extension.md).

## <a name="see-also"></a>См. также

- [Добавление поддержки редактора Visual Studio для других языков](../ide/adding-visual-studio-editor-support-for-other-languages.md)
