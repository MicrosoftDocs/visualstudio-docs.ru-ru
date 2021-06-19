---
title: Использование ModelBus в текстовом шаблоне
description: Узнайте, как разрешить ссылки на целевые модели доступа при написании текстовых шаблонов, считывающих модель, содержащую ссылки Visual Studio ModelBus.
ms.date: 11/04/2016
ms.topic: how-to
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 2afe8de66b109793a4e15e8320c3f498a08b25ec
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2021
ms.locfileid: "112388390"
---
# <a name="using-visual-studio-modelbus-in-a-text-template"></a>Использование Visual Studio ModelBus в текстовом шаблоне

При написании текстовых шаблонов, считывающих модель, содержащую ссылки Visual Studio ModelBus, может потребоваться разрешить ссылки для доступа к целевым моделям. В этом случае необходимо адаптировать текстовые шаблоны и упоминаемые доменные языки (DSL):

- У DSL, который является целью ссылок, должен быть адаптер ModelBus, настроенный для доступа из текстовых шаблонов. Если вы также обращаетесь к DSL из другого кода, Перенастроенный адаптер требуется в дополнение к стандартному адаптеру ModelBus.

     Диспетчер адаптеров должен наследовать от [встексттемплатингмоделингадаптерманажер](/previous-versions/ee844317(v=vs.140)) и должен иметь атрибут `[HostSpecific(HostName)]` .

- Шаблон должен наследовать от [моделбусенабледтексттрансформатион](/previous-versions/ee844263(v=vs.140)).

> [!NOTE]
> Если вы хотите читать модели DSL, не содержащие ссылок ModelBus, можно использовать обработчики директив, созданные в проектах DSL. Дополнительные сведения см. в разделе [доступ к моделям из текстовых шаблонов](../modeling/accessing-models-from-text-templates.md).

Дополнительные сведения о текстовых шаблонах см. в разделе [Создание кода во время разработки с помощью текстовых шаблонов T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md).

## <a name="create-a-model-bus-adapter-for-access-from-text-templates"></a>Создание адаптера шины модели для доступа из текстовых шаблонов

Чтобы разрешить ссылку ModelBus в текстовом шаблоне, целевой DSL должен иметь совместимый адаптер. Текстовые шаблоны выполняются в отдельном AppDomain из редакторов документов Visual Studio, поэтому адаптеру необходимо загрузить модель, а не обращаться к ней через DTE.

1. Если целевое решение DSL не имеет проекта **ModelBusAdapter** , создайте его с помощью мастера расширения ModelBus:

    1. Скачайте и установите расширение Visual Studio ModelBus, если вы еще не сделали этого. Дополнительные сведения см. в разделе [SDK визуализации и моделирования](https://devblogs.microsoft.com/devops/the-visual-studio-modeling-sdk-is-now-available-with-visual-studio-2017/).

    2. Откройте файл определения DSL. Щелкните правой кнопкой мыши область конструктора и выберите команду **включить ModelBus**.

    3. В диалоговом окне выберите **я хочу предоставить этот DSL для ModelBus**. Вы можете выбрать оба варианта, если вы хотите, чтобы этот DSL предоставлял свои модели и использовал ссылки на другой домен.

    4. Нажмите кнопку **OK**. В решение DSL будет добавлен новый проект ModelBusAdapter.

    5. Щелкните **преобразовать все шаблоны**.

    6. Выполните повторную сборку решения.

2. Если вы хотите получить доступ к DSL как из текстового шаблона, так и из другого кода, например команды, скопируйте проект **ModelBusAdapter** :

    1. В проводнике Windows скопируйте и вставьте папку, содержащую **ModelBusAdapter. csproj**.

    2. Переименуйте файл проекта (например, в **T4ModelBusAdapter. csproj**).

    3. В **Обозреватель решений** щелкните правой кнопкой мыши узел решения, наведите указатель на пункт **Добавить** и выберите пункт **существующий проект**. Выберите новый проект адаптера **T4ModelBusAdapter. csproj**.

    4. В каждом `*.tt` файле нового проекта измените пространство имен.

    5. Щелкните правой кнопкой мыши новый проект в **Обозреватель решений** и выберите пункт **свойства**. В редакторе свойств измените имена создаваемой сборки и пространства имен по умолчанию.

    6. В проекте DslPackage добавьте ссылку на новый проект адаптера, чтобы он ссылался на оба адаптера.

    7. В Дслпаккаже\саурце.екстенсион.ТТ добавьте строку, которая ссылается на новый проект адаптера.

        ```
        <MefComponent>|T4ModelBusAdapter|</MefComponent>
        ```

    8. **Преобразуйте все шаблоны** и перестройте решение. Ошибки сборки не возникнет.

3. В новом проекте адаптера добавьте ссылки на следующие сборки:

    - Microsoft. VisualStudio. TextTemplating. 11.0
    - Microsoft. VisualStudio. TextTemplating. моделирование. 11.0

4. В AdapterManager.tt:

    - Измените объявление Адаптерманажербасе, чтобы оно наследовалось от [встексттемплатингмоделингадаптерманажер](/previous-versions/ee844317(v=vs.140)).

         `public partial class <#= dslName =>AdapterManagerBase :`

         `Microsoft.VisualStudio.TextTemplating.Modeling.VsTextTemplatingModelingAdapterManager { ...`

    - Ближе к концу файла замените атрибут HostSpecific до класса AdapterManager. Удалите следующую строку:

         `[DslIntegration::HostSpecific(DslIntegrationShell::VsModelingAdapterManager.HostName)]`

         Вставьте следующую строку:

         `[Microsoft.VisualStudio.Modeling.Integration.HostSpecific(HostName)]`

         Этот атрибут фильтрует набор адаптеров, доступных, когда потребитель ModelBus ищет адаптер.

5. **Преобразуйте все шаблоны** и перестройте решение. Ошибки сборки не возникнет.

## <a name="write-a-text-template-that-can-resolve-modelbus-references"></a>Написание текстового шаблона, который может разрешать ссылки на ModelBus

Как правило, начинается с шаблона, который считывает и создает файлы из исходного DSL. Этот шаблон использует директиву, созданную в проекте DSL исходного кода, для считывания файлов исходной модели способом, описанным в статье [доступ к моделям из текстовых шаблонов](../modeling/accessing-models-from-text-templates.md). Однако исходный DSL-код содержит ссылки ModelBus на "целевой" DSL. Поэтому необходимо включить код шаблона для разрешения ссылок и доступа к целевому DSL. Поэтому необходимо адаптировать шаблон, выполнив следующие действия.

- Измените базовый класс шаблона на [моделбусенабледтексттрансформатион](/previous-versions/ee844263(v=vs.140)).

- Включите `hostspecific="true"` в директиву template.

- Добавьте ссылки на сборку в целевом DSL и его адаптере, а также для включения ModelBus.

- Не требуется директива, которая создается как часть целевого DSL.

```
<#@ template debug="true" hostspecific="true" language="C#"
inherits="Microsoft.VisualStudio.TextTemplating.Modeling.ModelBusEnabledTextTransformation" #>
<#@ SourceDsl processor="SourceDslDirectiveProcessor" requires="fileName='Sample.source'" #>
<#@ output extension=".txt" #>
<#@ assembly name = "Microsoft.VisualStudio.Modeling.Sdk.Integration.11.0" #>
<#@ assembly name = "Company.TargetDsl.Dsl.dll" #>
<#@ assembly name = "Company.TargetDsl.T4ModelBusAdapter.dll" #>
<#@ assembly name = "System.Core" #>
<#@ import namespace="Microsoft.VisualStudio.Modeling.Integration" #>
<#@ import namespace="Company.TargetDsl" #>
<#@ import namespace="Company.TargetDsl.T4ModelBusAdapters" #>
<#@ import namespace="System.Linq" #>
<#
  SourceModelRoot source = this.ModelRoot; // Usual access to source model.
  // In the source DSL Definition, the root element has a model reference:
  using (TargetAdapter adapter = this.ModelBus.CreateAdapter(source.ModelReference) as TargetAdapter)
  {if (adapter != null)
   {
      // Get the root of the target model:
      TargetRoot target = adapter.ModelRoot;
    // The source DSL Definition has a class "SourceElement" embedded under the root.
    // (Let's assume they're all in the same model file):
    foreach (SourceElement sourceElement in source.Elements)
    {
      // In the source DSL Definition, each SourceElement has a MBR property:
      ModelBusReference elementReference = sourceElement.ReferenceToTarget;
      // Resolve the target model element:
      TargetElement element = adapter.ResolveElementReference<TargetElement>(elementReference);
#>
     The source <#= sourceElement.Name #> is linked to: <#= element.Name #> in target model: <#= target.Name #>.
<#
    }
  }}
  // Other useful code: this.Host.ResolvePath(filename) gets an absolute filename
  // from a path that is relative to the text template.
#>
```

 При выполнении этого текстового шаблона `SourceDsl` директива загружает файл `Sample.source` . Шаблон может обращаться к элементам этой модели, начиная с `this.ModelRoot` . Код может использовать доменные классы и свойства этого DSL.

 Кроме того, шаблон может разрешать ссылки ModelBus. Если ссылки указывают на целевую модель, директивы сборки позволяют коду использовать доменные классы и свойства DSL этой модели.

- Если директива, созданная проектом DSL, не используется, необходимо также включить следующее.

    ```
    <#@ assembly name = "Microsoft.VisualStudio.Modeling.Sdk.11.0" #>
    <#@ assembly name = "Microsoft.VisualStudio.TextTemplating.Modeling.11.0" #>
    ```

- Используйте `this.ModelBus` для получения доступа к ModelBus.

## <a name="walkthrough-testing-a-text-template-that-uses-modelbus"></a>Пошаговое руководство. Тестирование текстового шаблона, использующего ModelBus
 В этом пошаговом руководстве вы выполните следующие действия:

1. Создайте два DSL. Один домен DSL, *потребитель*, имеет `ModelBusReference` свойство, которое может ССЫЛАТЬСЯ на другой DSL, *поставщик*.

2. Создайте два адаптера ModelBus в поставщике: один для доступа по текстовым шаблонам, другой — для обычного кода.

3. Создание моделей экземпляров DSL в одном экспериментальном проекте.

4. Установите свойство домена в одной модели, чтобы оно указывало на другую модель.

5. Напишите обработчик двойного щелчка, открывающий модель, на которую указывает.

6. Напишите текстовый шаблон, который может загрузить первую модель, перейдите по ссылке на другую модель и прочтите другую модель.

### <a name="construct-a-dsl-that-is-accessible-to-modelbus"></a>Создание DSL, доступного для ModelBus

1. Создайте новое решение DSL. В этом примере выберите шаблон решения для потока задач. Задайте для имени языка `MBProvider` и расширения имя файла значение. Укажите.

2. На схеме определения DSL щелкните правой кнопкой мыши пустую часть диаграммы, которая не находится ближе к верхней, и выберите пункт **включить ModelBus**.

   Если вы не видите параметр **Enable ModelBus**, скачайте и установите расширение VMSDK ModelBus.

3. В диалоговом окне **Включение ModelBus** выберите **предоставить этот DSL для ModelBus** и нажмите кнопку **ОК**.

    В `ModelBusAdapter` решение добавляется новый проект.

Теперь у вас есть DSL, доступ к которому можно получить с помощью текстовых шаблонов с помощью ModelBus. Ссылки на него можно разрешить в коде команд, обработчиков событий или правил, которые работают в домене приложения редактора файлов модели. Однако текстовые шаблоны выполняются в отдельном домене приложения и не могут получить доступ к модели при редактировании. Если требуется получить доступ к ссылкам ModelBus на этот DSL из текстового шаблона, необходимо иметь отдельный ModelBusAdapter.

### <a name="create-a-modelbus-adapter-that-is-configured-for-text-templates"></a>Создание адаптера ModelBus, настроенного для текстовых шаблонов

1. В проводнике скопируйте и вставьте папку, содержащую *ModelBusAdapter. csproj*.

    Назовите папку **T4ModelBusAdapter**.

    Переименуйте файл проекта *T4ModelBusAdapter. csproj*.

2. В обозреватель решений добавьте T4ModelBusAdapter в решение Мбпровидер. Щелкните правой кнопкой мыши узел решения, наведите указатель на пункт **Добавить** и выберите пункт **существующий проект**.

3. Щелкните правой кнопкой мыши узел проекта T4ModelBusAdapter и выберите пункт Свойства. В окне Свойства проекта измените **имя сборки** и **пространство имен по умолчанию** на `Company.MBProvider.T4ModelBusAdapters` .

4. В каждом файле *. tt в T4ModelBusAdapter вставьте "T4" в последнюю часть пространства имен, чтобы строка была похожа на следующую.

    `namespace <#= CodeGenerationUtilities.GetPackageNamespace(this.Dsl) #>.T4ModelBusAdapters`

5. В `DslPackage` проекте добавьте ссылку на проект `T4ModelBusAdapter` .

6. В Дслпаккаже\саурце.екстенсион.ТТ добавьте следующую строку в разделе `<Content>` .

    `<MefComponent>|T4ModelBusAdapter|</MefComponent>`

7. В `T4ModelBusAdapter` проекте добавьте ссылку на: **Microsoft. VisualStudio. TextTemplating. моделирование. 11.0** .

8. Откройте T4ModelBusAdapter\AdapterManager.tt:

   1. Измените базовый класс Адаптерманажербасе на [встексттемплатингмоделингадаптерманажер](/previous-versions/ee844317(v=vs.140)). Эта часть файла теперь выглядит примерно так:

       ```
       namespace <#= CodeGenerationUtilities.GetPackageNamespace(this.Dsl) #>.T4ModelBusAdapters
       {
           /// <summary>
           /// Adapter manager base class (double derived pattern) for the <#= dslName #> Designer
           /// </summary>
           public partial class <#= dslName #>AdapterManagerBase
           : Microsoft.VisualStudio.TextTemplating.Modeling.VsTextTemplatingModelingAdapterManager
           {
       ```

   2. Рядом с концом файла вставьте следующий дополнительный атрибут перед классом AdapterManager.

        `[Microsoft.VisualStudio.Modeling.Integration.HostSpecific(HostName)]`

        Результат будет выглядеть следующим образом.

       ```
       /// <summary>
       /// ModelBus modeling adapter manager for a <#= dslName #>Adapter model adapter
       /// </summary>
       [Mef::Export(typeof(DslIntegration::ModelBusAdapterManager))]
       [Mef::ExportMetadata(DslIntegration::CompositionAttributes.AdapterIdKey,<#= dslName #>Adapter.AdapterId)]
       [DslIntegration::HostSpecific(DslIntegrationShell::VsModelingAdapterManager.HostName)]
       [Microsoft.VisualStudio.Modeling.Integration.HostSpecific(HostName)]
       public partial class <#= dslName #>AdapterManager : <#= dslName #>AdapterManagerBase
       {
       }
       ```

9. Щелкните **преобразовать все шаблоны** в заголовке окна Обозреватель решений.

10. Нажмите клавишу **F5**.

11. Убедитесь, что DSL работает. В экспериментальном проекте откройте `Sample.provider` . Закройте экспериментальный экземпляр Visual Studio.

    Ссылки ModelBus на этот DSL теперь можно разрешить в текстовых шаблонах, а также в обычном коде.

### <a name="construct-a-dsl-with-a-modelbus-reference-domain-property"></a>Создание DSL с помощью свойства домена ссылок ModelBus

1. Создайте новый домен DSL с помощью шаблона минимального языкового решения. Присвойте языку имя Мбконсумер и задайте для расширения имени файла значение ". потреблено".

2. В проекте DSL Добавьте ссылку на сборку DSL Мбпровидер. Щелкните правой кнопкой мыши  `MBConsumer\Dsl\References` и выберите команду **Добавить ссылку**. На вкладке **Обзор** найдите `MBProvider\Dsl\bin\Debug\Company.MBProvider.Dsl.dll`

    Это позволяет создавать код, использующий другой DSL. Если необходимо создать ссылки на несколько доменных языков, добавьте их также.

3. На схеме определения DSL щелкните правой кнопкой мыши диаграмму и выберите команду **включить ModelBus**. В диалоговом окне выберите **включить этот DSL для использования ModelBus**.

4. В классе `ExampleElement` добавьте новое свойство домена `MBR` и в окно свойств задайте для его типа значение `ModelBusReference` .

5. Щелкните правой кнопкой мыши свойство предметной области на схеме и выберите пункт **изменить специальные свойства моделбусреференце**. В диалоговом окне выберите **элемент модели**.

    Задайте для фильтра диалогового окна файла следующее значение.

    `Provider File|*.provide`

    Подстрока после «&#124;» является фильтром для диалогового окна «Выбор файла». Можно задать, чтобы разрешить любые файлы с помощью *.\*

    В списке **тип элемента модели** введите имена одного или нескольких доменных классов в поставщике DSL (например, Company. Мбпровидер. Task). Они могут быть абстрактными классами. Если оставить список пустым, пользователь может задать ссылку на любой элемент.

6. Закройте диалоговое окно и **преобразуйте все шаблоны**.

   Вы создали DSL, которое может содержать ссылки на элементы в другом DSL.

### <a name="create-a-modelbus-reference-to-another-file-in-the-solution"></a>Создание ссылки ModelBus на другой файл в решении

1. В решении Мбконсумер нажмите клавиши CTRL + F5. В проекте **мбконсумер\дебуггинг** откроется экспериментальный экземпляр Visual Studio.

2. Добавьте копию примера. Предоставьте в проект **мбконсумер\дебуггинг** . Это необходимо потому, что ссылка ModelBus должна ссылаться на файл в том же решении.

   1. Щелкните правой кнопкой мыши проект отладки, наведите указатель на пункт **Добавить** и выберите пункт **существующий элемент**.

   2. В диалоговом окне **Добавление элемента** задайте фильтр для **всех файлов ( \* . \* )**.

   3. Перейдите к `MBProvider\Debugging\Sample.provide` и нажмите кнопку **Добавить**.

3. Откройте `Sample.consume`.

4. Щелкните один пример фигуры, а затем в окно свойств щелкните **[...]** в свойстве MBR. В диалоговом окне нажмите кнопку **Обзор** и выберите `Sample.provide` . В окне элементы разверните задачу тип и выберите один из элементов.

5. Сохраните файл. (Еще не закрывайте экспериментальный экземпляр Visual Studio.)

   Вы создали модель, содержащую ссылку ModelBus на элемент в другой модели.

### <a name="resolve-a-modelbus-reference-in-a-text-template"></a>Разрешение ссылки ModelBus в текстовом шаблоне

1. В экспериментальном экземпляре Visual Studio откройте пример файла текстового шаблона. Задайте его содержимое следующим образом.

    ```
    <#@ template debug="true" hostspecific="true" language="C#"
    inherits="Microsoft.VisualStudio.TextTemplating.Modeling.ModelBusEnabledTextTransformation" #>
    <#@ MBConsumer processor="MBConsumerDirectiveProcessor" requires="fileName='Sample.consume'" #>
    <#@ output extension=".txt" #>
    <#@ assembly name = "Microsoft.VisualStudio.Modeling.Sdk.Integration.11.0" #>
    <#@ assembly name = "Company.MBProvider.Dsl.dll" #>
    <#@ import namespace="Microsoft.VisualStudio.Modeling.Integration" #>
    <#@ import namespace="Company.MBProvider" #>
    <#
      // Property provided by the Consumer directive processor:
      ExampleModel consumerModel = this.ExampleModel;
      // Iterate through Consumer model, listing the elements:
      foreach (ExampleElement element in consumerModel.Elements)
      {
    #>
       <#= element.Name #>
    <#
        if (element.MBR != null)
      using (ModelBusAdapter adapter = this.ModelBus.CreateAdapter(element.MBR))
      {
              // If we allowed multiple types or DSLs in the MBR, discover type here.
        Task task = adapter.ResolveElementReference<Task>(element.MBR);
    #>
            <#= element.Name #> is linked to Task: <#= task==null ? "(null)" : task.Name #>
    <#
          }
      }
    #>

    ```

     Обратите внимание на следующие моменты.

    - `hostSpecific` `inherits` `template` Необходимо задать атрибуты и директивы.

    - Доступ к модели потребителя осуществляется обычным образом с помощью процессора директив, созданного в этом DSL.

    - Директивы Assembly и Import должны иметь возможность доступа к ModelBus и типам поставщика DSL.

    - Если известно, что многие Мбрс связаны с одной и той же моделью, лучше вызывать Креатеадаптер только один раз.

2. при сохранении шаблона; Убедитесь, что полученный текстовый файл выглядит следующим образом.

    ```
    ExampleElement1
    ExampleElement2
         ExampleElement2 is linked to Task: Task2
    ```

### <a name="resolve-a-modelbus-reference-in-a-gesture-handler"></a>Разрешение ссылки ModelBus в обработчике жестов

1. Закройте экспериментальный экземпляр Visual Studio, если он работает.

2. Добавьте файл с именем *мбконсумер\дсл\кустом.КС* и задайте для него следующее содержимое:

    ```csharp
    namespace Company.MB2Consume
    {
      using Microsoft.VisualStudio.Modeling.Integration;
      using Company.MB3Provider;

      public partial class ExampleShape
      {
        public override void OnDoubleClick(Microsoft.VisualStudio.Modeling.Diagrams.DiagramPointEventArgs e)
        {
          base.OnDoubleClick(e);
          ExampleElement element = this.ModelElement as ExampleElement;
          if (element.MBR != null)
          {
            IModelBus modelbus = this.Store.GetService(typeof(SModelBus)) as IModelBus;
            using (ModelBusAdapter adapter = modelbus.CreateAdapter(element.MBR))
            {
              Task task = adapter.ResolveElementReference<Task>(element.MBR);
              // Open a window on this model:
              ModelBusView view = adapter.GetDefaultView();
              view.Show();
              view.SetSelection(element.MBR);
            }
          }
        }
      }
    }
    ```

3. Нажмите клавиши **CTRL** + **F5**.

4. В экспериментальном экземпляре Visual Studio откройте `Debugging\Sample.consume` .

5. Дважды щелкните одну фигуру.

    Если для этого элемента задана основная загрузочная запись, то открывается указанная модель и выбирается элемент, на который указывает ссылка.

## <a name="see-also"></a>См. также

- [Интеграция моделей с помощью Visual Studio Modelbus](../modeling/integrating-models-by-using-visual-studio-modelbus.md)
- [Создание кода и текстовые шаблоны T4](../modeling/code-generation-and-t4-text-templates.md)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]
