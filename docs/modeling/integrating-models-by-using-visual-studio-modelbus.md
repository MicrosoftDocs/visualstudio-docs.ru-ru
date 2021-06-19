---
title: Интеграция моделей с помощью ModelBus
description: Узнайте, что Visual Studio ModelBus предоставляет метод для создания ссылок между моделями и из других средств в модели.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 350398d91d73a722956d195b300311f313ff34db
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2021
ms.locfileid: "112391066"
---
# <a name="integrate-models-by-using-visual-studio-modelbus"></a>Интеграция моделей с помощью Visual Studio ModelBus

Visual Studio ModelBus предоставляет метод для создания связей между моделями и из других средств в модели. Например, можно связать модели доменного языка (DSL) с моделями UML или создать интегрированный набор DSL.

ModelBus позволяет создать уникальную ссылку на модель или на определенный элемент внутри модели. Эта ссылка может храниться вне модели, например в элементе другой модели. Если впоследствии средству потребуется доступ к элементу, инфраструктура ModelBus загрузит соответствующую модель и вернет элемент. При необходимости модель можно отобразить для пользователя. Если доступ к файлу в его прежнем расположении невозможен, ModelBus предложит пользователю его найти. Если пользователь найдет файл, ModelBus исправит все ссылки на этот файл.

> [!NOTE]
> В текущей реализации ModelBus в Visual Studio связанные модели должны быть элементами в одном решении Visual Studio.

Дополнительные сведения и образец кода см. здесь:

- [Практическое руководство. Добавление обработчика перетаскивания](../modeling/how-to-add-a-drag-and-drop-handler.md)

- [Пакет SDK моделирования для Visual Studio](https://www.microsoft.com/download/details.aspx?id=48148)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

## <a name="providing-access-to-a-dsl"></a><a name="provide"></a> Предоставление доступа к DSL
 Перед созданием ссылок ModelBus на модель или ее элементы необходимо определить ModelBusAdapter для DSL. Самый простой способ сделать это — использовать расширение "Шина модели Visual Studio", которое добавляет команды в Конструктор DSL.

### <a name="to-expose-a-dsl-definition-to-model-bus"></a><a name="expose"></a> Предоставление определения DSL для шины модели

1. Откройте файл определения DSL. Щелкните правой кнопкой мыши область конструктора и выберите команду **включить ModelBus**.

2. В диалоговом окне выберите **я хочу предоставить этот DSL для ModelBus**. Если вы хотите, чтобы DSL предоставил свои модели и использовал ссылки на другие DSL, выберите оба параметра.

3. Нажмите кнопку **OK**. В решение DSL будет добавлен новый проект ModelBusAdapter.

4. Если вам необходимо получить доступ к DSL из текстового шаблона, измените файл AdapterManager.tt в новом проекте. Пропустите этот шаг, если доступ к DSL необходимо получить из другого кода, например из обработчика команд и событий. Дополнительные сведения см. [в разделе использование Visual Studio ModelBus в текстовом шаблоне](../modeling/using-visual-studio-modelbus-in-a-text-template.md).

   1. Измените базовый класс Адаптерманажербасе на [встексттемплатингмоделингадаптерманажер](/previous-versions/ee844317(v=vs.140)).

   2. Ближе к концу файла вставьте перед классом AdapterManager следующий дополнительный атрибут:

       `[Microsoft.VisualStudio.Modeling.Integration.HostSpecific(HostName)]`

   3. В ссылках проекта ModelBusAdapter добавьте **Microsoft. VisualStudio. TextTemplating. моделирование. 11.0**.

      Если доступ к DSL должен предоставляться как из текстовых шаблонов, так и из другого кода, необходимо указать два адаптера — один измененный и один неизмененный.

5. Щелкните **преобразовать все шаблоны**.

6. Выполните повторную сборку решения.

   Теперь ModelBus может открывать экземпляры этого DSL.

   В папке `ModelBusAdapters\bin\*` содержатся сборки, построенные проектом `Dsl` и проектом `ModelBusAdapters`. Чтобы сослаться на этот DSL из другого DSL, импортируйте эти сборки.

### <a name="ensure-that-elements-can-be-referenced"></a>Убедитесь, что на элементы можно ссылаться

Visual Studio ModelBus адаптеры по умолчанию используют идентификатор GUID элемента для его однозначного обнаружения. Это значит, что такие идентификаторы должны храниться в файле модели.

Чтобы обеспечить сохранение идентификаторов элементов, выполните следующие действия.

1. Откройте файл DslDefinition.dsl.

2. В обозревателе DSL разверните узел **поведение сериализации XML**, а затем — **данные класса**.

3. Для каждого класса, к которому необходимо создать ссылки ModelBus, сделайте следующее:

    Щелкните узел класса и в окно свойств убедитесь, что для параметра **СЕРИАЛИЗОВАТЬ ID** задано значение `true` .

   Кроме того, если требуется использовать имена элементов для определения элементов вместо идентификаторов GUID, можно переопределить части созданных адаптеров. Переопределите следующие методы в классе адаптера.

- Метод `GetElementId`, чтобы вернуть необходимый для использования идентификатор. Этот метод вызывается при создании ссылок.

- Метод `ResolveElementReference`, чтобы найти правильный элемент по ссылке ModelBus.

## <a name="accessing-a-dsl-from-another-dsl"></a><a name="editRef"></a> Доступ к DSL из другого DSL

Ссылки ModelBus можно сохранять в свойство домена в DSL, написав специальный код, который будет их использовать. Также можно позволить пользователю создавать ссылки ModelBus, выбирая файлы модели и элементы в нем.

Чтобы разрешить DSL использовать ссылки на другой домен DSL, необходимо сначала сделать его *потребителем* ссылок на шину модели.

### <a name="to-enable-a-dsl-to-consume-references-to-an-exposed-dsl"></a>Предоставление DSL возможности получать ссылки на предоставляемый DSL

1. На схеме определения DSL щелкните правой кнопкой мыши основную часть диаграммы и выберите пункт **включить ModelBus**.

2. В диалоговом окне выберите **я хочу включить эту модель для использования ссылок на шины модели**.

3. В проекте Dsl принимающего DSL к ссылкам проекта добавьте указанные ниже сборки (файлы .DLL). Эти сборки (.dll файлы) находятся в \\ каталоге моделбусадаптер\бин * предоставленного DSL.

    - Предоставленная сборка DSL, например **Fabrikam.FamilyTree.Dsl.dll**

    - Предоставленная Сборка адаптера шины, например **Fabrikam.FamilyTree.ModelBusAdapter.dll**

4. Добавьте следующие сборки платформы .NET к ссылкам проекта получающего DSL:

    1. **Microsoft.VisualStudio.Modeling.Sdk.Integration.11.0.dll**

    2. **Microsoft.VisualStudio.Modeling.Sdk.Integration.Shell.11.0.dll**

### <a name="to-store-a-model-bus-reference-in-a-domain-property"></a>Сохранение ссылки ModelBus в свойстве домена

1. В схеме "Определение DSL" принимающего DSL добавьте к классу домена свойство домена и присвойте ему имя.

2. В окно свойств с выбранным свойством домен задайте для параметра **тип** значение `ModelBusReference` .

   На данном этапе программный код может определять значение свойства, но в окне "Свойства" он доступен только для чтения.

   Можно разрешить пользователям устанавливать свойство с помощью специализированного редактора ссылок ModelBus. Существует две версии этого редактора или *средства выбора:* один позволяет пользователям выбрать файл модели, а другой позволяет пользователям выбрать файл модели и элемент в пределах модели.

### <a name="to-allow-the-user-to-set-a-model-bus-reference-in-a-domain-property"></a>Разрешение пользователю устанавливать ссылку ModelBus в свойстве домена

1. Щелкните правой кнопкой мыши свойство домена и выберите пункт **изменить специальные свойства моделбусреференце**. Откроется диалоговое окно. Это *средство выбора шины модели*.

2. Выберите соответствующий **тип моделбусреференце**: для модели или для элемента внутри модели.

3. В строке фильтра диалогового окна выбора файла введите строку вида `Family Tree files |*.ftree`. Замените расширение файла предоставленного DSL.

4. Если выбрана ссылка на элемент в модели, можно добавить список типов, доступных для выбора пользователем, например Company.FamilyTree.Person.

5. Нажмите кнопку **ОК**, а затем выберите **преобразовать все шаблоны** на панели инструментов **Обозреватель решений** .

    > [!WARNING]
    > Если допустимая модель или сущность не выбрана, нажатие кнопки "ОК" не будет иметь никакого действия, даже если выглядит активной.

6. При указании списка целевых типов, таких как Company.FamilyTree.Person, необходимо также добавить ссылку на сборку проекта DSL, ссылающуюся на DLL целевого DSL, например Company.FamilyTree.Dsl.dll

### <a name="to-test-a-model-bus-reference"></a>Проверка ссылки ModelBus

1. Постройте предоставляемый и принимающий DSL.

2. Запустите один из DSL в экспериментальном режиме, нажав клавишу F5 или сочетание клавиш CTRL + F5.

3. В проекте отладки в экспериментальном экземпляре Visual Studio добавьте файлы, которые являются экземплярами каждого DSL.

    > [!NOTE]
    > Visual Studio ModelBus может разрешать ссылки только на модели, которые являются элементами в одном решении Visual Studio. Например, создать ссылку на файл модели, расположенный в другой части файловой системы, нельзя.

4. Создайте и сохраните несколько элементов и связей в экземпляре предоставляемого DSL.

5. Откройте экземпляр принимающего DSL и выберите элемент модели, имеющий свойство ссылки ModelBus.

6. В окне "Свойства" дважды щелкните свойство ссылки ModelBus. Откроется диалоговое окно выбора.

7. Нажмите кнопку **Обзор** и выберите экземпляр предоставленного DSL.

     Средство выбора позволяет также выбрать элемент в модели в том случае, если был указан определенный тип элемента ссылки ModelBus.

## <a name="creating-references-in-program-code"></a>Создание ссылок в программном коде

Если ссылку необходимо сохранить в модели или в элементе внутри модели, создается объект `ModelBusReference`. Существует два вида объектов `ModelBusReference`: ссылки на модель и ссылки на элемент.

Чтобы создать ссылку на модель, требуется AdapterManager DSL, в котором модель является экземпляром, а также имя файла или элемент проекта Visual Studio модели.

Для создания ссылки на элемент требуется адаптер для файла модели и элемент, на который необходимо сослаться.

> [!NOTE]
> С помощью Visual Studio ModelBus можно создавать ссылки только на элементы в одном решении Visual Studio.

### <a name="import-the-exposed-dsl-assemblies"></a>Импорт предоставляемых сборок DSL

В принимающем проекте добавьте ссылки проекта на сборки DSL и ModelBusAdapter предоставляемого DSL.

Например, предположим, что ссылки ModelBus необходимо сохранить в элементах DSL библиотеки MusicLibrary. Ссылки ModelBus будут ссылаться на элементы DSL FamilyTree. В проекте `Dsl` решения MusicLibrary и в узле "Ссылки" добавьте ссылки на следующие сборки:

- Fabrikam.FamilyTree.Dsl.dll — предоставляемый DSL;

- Fabrikam.FamilyTree.ModelBusAdapters.dll — адаптер ModelBus предоставляемого DSL;

- Microsoft.VisualStudio.Modeling.Sdk.Integration.11.0;

- Microsoft.VisualStudio.Modeling.Sdk.Integration.Shell.11.0.

  Эти сборки находятся в проекте `ModelBusAdapters` предоставляемого DSL в папке `bin\*`.

  В файл кода, предназначенного для создания ссылок, как правило, импортируются следующие пространства имен:

```csharp
// The namespace of the DSL you want to reference:
using Fabrikam.FamilyTree;  // Exposed DSL
using Fabrikam.FamilyTree.ModelBusAdapters;
using Microsoft.VisualStudio.Modeling.Integration;
using System.Linq;
...
```

### <a name="to-create-a-reference-to-a-model"></a>Создание ссылки на модель

Чтобы создать ссылку на модель, необходимо получить сначала доступ к AdapterManager для предоставляемого DSL, а затем использовать его для создания ссылки на модель. Можно указать либо путь к файлу, либо `EnvDTE.ProjectItem`.

Из AdapterManager можно получить адаптер, который предоставляет доступ к отдельным элементам в модели.

> [!NOTE]
> После использования адаптер необходимо ликвидировать. Наиболее удобным способом достижения этой цели является использование оператора `using`. Это показано в следующем примере.

```csharp
// The file path of a model instance of the FamilyTree DSL:
string targetModelFile = "TudorFamilyTree.ftree";
// Get the ModelBus service:
IModelBus modelBus =
    this.Store.GetService(typeof(SModelBus)) as IModelBus;
// Get an adapterManager for the target DSL:
FamilyTreeAdapterManager manager =
    (modelbus.GetAdapterManager(FamilyTreeAdapter.AdapterId)
     as FamilyTreeAdapterManager;
// or: (modelBus.FindAdapterManagers(targetModelFile).First())
// or could provide an EnvDTE.ProjectItem

// Create a reference to the target model:
// NOTE: the target model must be a file in this project.
ModelBusReference modelReference =
     manager.CreateReference(targetModelFile);
// or can use an EnvDTE.ProjectItem instead of the filename

// Get the root element of this model:
using (FamilyTreeAdapter adapter =
     modelBus.CreateAdapter(modelReference) as FamilyTreeAdapter)
{
  FamilyTree modelRoot = adapter.ModelRoot;
  // Access elements under the root in the usual way:
  foreach (Person p in modelRoot.Persons) {...}
  // You can create adapters for individual elements:
  ModelBusReference elementReference =
     adapter.GetElementReference(person);
  ...
} // Dispose adapter
```

Чтобы `modelReference` можно было использовать позднее, ее можно сохранить в свойстве домена, имеющем ссылку `ModelBusReference` внешнего типа:

```csharp
using Transaction t = this.Store.TransactionManager
    .BeginTransaction("keep reference"))
{
  artist.FamilyTreeReference = modelReference;
  t.Commit();
}
```

Чтобы разрешить пользователям изменять свойство домена, используйте `ModelReferenceEditor` в качестве параметра атрибута Editor ("Редактор"). Дополнительные сведения см. в разделе [разрешение пользователю на изменение ссылки](#editRef).

### <a name="to-create-a-reference-to-an-element"></a>Создание ссылки на элемент

Созданный для модели адаптер можно использовать для создания и разрешения ссылок.

```csharp
// person is an element in the FamilyTree model:
ModelBusReference personReference =
  adapter.GetElementReference(person);
```

Чтобы `elementReference` можно было использовать позднее, ее можно сохранить в свойстве домена, имеющем ссылку `ModelBusReference` внешнего типа: Чтобы разрешить пользователям изменять эту ссылку, используйте `ModelElementReferenceEditor` в качестве параметра атрибута Editor ("Редактор"). Дополнительные сведения см. в разделе [разрешение пользователю на изменение ссылки](#editRef).

### <a name="resolving-references"></a>Разрешение ссылок

Наличие ссылки `ModelBusReference` (MBR) позволяет получить модель или элемент модели, к которой она относится. Если элемент представлен на схеме или в другом представлении, откройте это представление и выберите нужный элемент.

Из MBR можно создать адаптер. Из адаптера можно получить корень модели. Также можно разрешить MBR, ссылающиеся на определенные элементы внутри модели.

```csharp
using Microsoft.VisualStudio.Modeling.Integration; ...
ModelBusReference elementReference = ...;

// Get the ModelBus service:
IModelBus modelBus =
    this.Store.GetService(typeof(SModelBus)) as IModelBus;
// Use a model reference or an element reference
// to obtain an adapter for the target model:
using (FamilyTreeAdapter adapter =
   modelBus.CreateAdapter(elementReference) as FamilyTreeAdapter)
   // or CreateAdapter(modelReference)
{
  // Get the root of the model:
  FamilyTree tree = adapter.ModelRoot;

  // Get a model element:
  MyDomainClass mel =
    adapter.ResolveElementReference<MyDomainClass>(elementReference);
  if (mel != null) {...}

  // Get the diagram or other view, if there is one:
  ModelBusView view = adapter.GetDefaultView();
  if (view != null)
  {
   view.Open();
   // Display the diagram:
   view.Show();
   // Attempt to select the shape that presents the element:
   view.SetSelection(elementReference);
  }
} // Dispose the adapter.
```

#### <a name="to-resolve-modelbus-references-in-a-text-template"></a>Разрешение ссылок ModelBus в текстовом шаблоне

1. DSL, к которому необходимо получить доступ, должен иметь адаптер ModelBus, настроенный с помощью текстовых шаблонов на получение доступа. Дополнительные сведения см. в разделе [предоставление доступа к домену DSL](#provide).

2. Как правило, получение доступа к целевому DSL осуществляется с помощью ссылки ModelBus (MBR), которая хранится в исходном DSL. В связи с этим шаблон включает директиву исходного DSL и код, необходимый для разрешения MBR. Дополнительные сведения о текстовых шаблонах см. в разделе [Создание кода на основе языка Domain-Specific](../modeling/generating-code-from-a-domain-specific-language.md).

   ```
   <#@ template debug="true" hostspecific="true"
   inherits="Microsoft.VisualStudio.TextTemplating.Modeling.ModelBusEnabledTextTransformation" #>
   <#@ SourceDsl processor="SourceDslDirectiveProcessor" requires="fileName='Sample.source'" #>
   <#@ output extension=".txt" #>
   <#@ assembly name = "Microsoft.VisualStudio.Modeling.Sdk.Integration.11.0" #>
   <#@ assembly name = "System.Core" #>
   <#@ assembly name = "Company.CompartmentDragDrop.Dsl.dll" #>
   <#@ assembly name = "Company.CompartmentDragDrop.ModelBusAdapter.dll" #>
   <#@ import namespace="Microsoft.VisualStudio.Modeling.Integration" #>
   <#@ import namespace="System.Linq" #>
   <#@ import namespace="Company.CompartmentDragDrop" #>
   <#@ import namespace="Company.CompartmentDragDrop.ModelBusAdapters" #>
   <# // Get source root from directive processor:
     ExampleModel source = this.ExampleModel;
     // This DSL has a MBR in its root:
   using (ModelBusAdapter adapter = this.ModelBus.CreateAdapter(source.ModelReference) as ModelBusAdapter)
     {
     ModelBusAdapterManager manager = this.ModelBus.FindAdapterManagers(this.Host.ResolvePath("Sample.compDD1")).FirstOrDefault();
     ModelBusReference modelReference =
       manager.CreateReference(this.Host.ResolvePath("Sample.compDD1"));

     // Get the root element of this model:
     using (CompartmentDragDropAdapter adapter =
        this.ModelBus.CreateAdapter(modelReference) as CompartmentDragDropAdapter)
     {
       ModelRoot root = adapter.ModelRoot;
   #>
   [[<#= root.Name #>]]
   <#
     }
   #>
   ```

   Дополнительные сведения и пошаговое руководство см. в разделе [использование Visual Studio ModelBus в текстовом шаблоне](../modeling/using-visual-studio-modelbus-in-a-text-template.md) .

## <a name="serializing-a-modelbusreference"></a>Сериализация ссылки ModelBus (ModelBusReference)

Если `ModelBusReference` (MBR) необходимо сохранить в виде строки, ее можно сериализовать:

```csharp
string serialized = modelBus.SerializeReference(elementReference);
// Store it anywhere, then get it back again:
ModelBusReference elementReferenceRestored =
    modelBus.DeserializeReference(serialized, null);
```

MBR, сериализованная подобным образом, не зависит от контекста. При использовании простого файлового адаптера ModelBus MBR содержит абсолютный путь к файлу. Этого достаточно, если файлы модели экземпляра никогда не перемещаются. Тем не менее файлы модели обычно являются элементами в проекте Visual Studio. Пользователи будут рассчитывать на возможность перемещать весь проект в различные части файловой системы, а также сохранять исходный контроль над проектом и открывать его на разных компьютерах. В связи с этим пути следует сериализовать относительно расположения проекта, содержащего файлы.

### <a name="serializing-relative-to-a-specified-file-path"></a>Сериализация относительно указанного пути к файлу

`ModelBusReference` содержит `ReferenceContext` — словарь, в котором можно хранить такую информацию, как путь к файлу, относительно которого его следует сериализовать.

Сериализация относительно пути:

```csharp
elementReference.ReferenceContext.Add(
   ModelBusReferencePropertySerializer.FilePathSaveContextKey,
   currentProjectFilePath);
string serialized = modelBus.SerializeReference(elementReference);
```

Получение ссылки из строки:

```csharp
ReferenceContext context = new ReferenceContext();
context.Add(ModelBusReferencePropertySerializer.FilePathLoadContextKey,
    currentProjectFilePath);
ModelBusReference elementReferenceRestored =
    modelBus.DeserializeReference(serialized, context);
```

### <a name="modelbusreferences-created-by-other-adapters"></a>Ссылки ModelBus, созданные другими адаптерами
 Приведенные ниже сведения будут полезны при создании собственного адаптера.

 `ModelBusReference` (MBR) состоит из двух частей: заголовка MBR, десериализованого шиной модели, и адаптера, который обрабатывается специальным диспетчером адаптеров. Это позволяет обеспечить собственный формат сериализации адаптера. Например, можно ссылаться на базу данных, а не на файл, или хранить дополнительные сведения в ссылке на адаптер. Собственный адаптер может помещать дополнительные сведения в `ReferenceContext`.

 При десериализации MBR необходимо указать контекст ссылки (ReferenceContext), который сохраняется в объекте MBR. При сериализации MBR, сохраненное значение ReferenceContext используется адаптером для создания строки. Десериализованная строка не содержит все сведения, указанные в ReferenceContext. Например, в простом файловом адаптере ReferenceContext содержит корневой путь к файлу, который не хранится в сериализованной строке MBR.

 MBR десериализуется в два этапа.

- `ModelBusReferencePropertySerializer` — Это Стандартный сериализатор, который работает с заголовком MBR. Он использует стандартный для DSL контейнер свойств `SerializationContext`, который сохраняется в `ReferenceContext` с помощью ключа `ModelBusReferencePropertySerializer.ModelBusLoadContextKey`. В частности, `SerializationContext` должен содержать экземпляр `ModelBus`.

- Адаптер ModelBus работает с адаптерной частью MBR. Он может использовать дополнительные сведения, сохраненные в значении ReferenceContext ссылки ModelBus. Простой адаптер на основе файлов сохраняет пути к корневым файлам с помощью ключей `FilePathLoadContextKey` и `FilePathSaveContextKey` .

     Ссылка на адаптер в файле модели десериализуется только в случае ее использования.

## <a name="to-create-a-model"></a>Создание модели

### <a name="creating-opening-and-editing-a-model"></a>Создание, открытие и изменение модели
 Следующий фрагмент взят из примера конечного автомата на веб-сайте VMSDK. В нем показывается использование ссылок ModelBus для создания и открытия модели, а также для получения связанной с моделью схемы.

 В данном примере целевой DSL имеет имя StateMachine. От него наследуются несколько имен, например имя класса модели и имя ModelBusAdapter.

```csharp
using Fabrikam.StateMachine.ModelBusAdapters;
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Diagrams;
using Microsoft.VisualStudio.Modeling.Integration;
using Microsoft.VisualStudio.Modeling.Integration.Shell;
using Microsoft.VisualStudio.Modeling.Shell;
...
// Create a new model.
ModelBusReference modelReference =
   StateMachineAdapterManager    .CreateStateMachineModel(modelName, fileName);
//Keep reference of new model in this model.
using (Transaction t = ...)
{
  myModelElement.ReferenceProperty = modelReference;
  t.Commit();
}
// Get the ModelBus service from Visual Studio.
IModelBus modelBus = Microsoft.VisualStudio.Shell.Package.
    GetGlobalService(typeof(SModelBus)) as IModelBus;
// Get a modelbus adapter on the new model.
ModelBusAdapter modelBusAdapter;
modelBus.TryCreateAdapter(modelReference,
    this.ServiceProvider, out modelBusAdapter);
using (StateMachineAdapter adapter =
      modelBusAdapter as StateMachineAdapter)
{
    if (adapter != null)
    {
        // Obtain a Diagram from the adapter.
        Diagram targetDiagram =
           ((StandardVsModelingDiagramView)
                 adapter.GetDefaultView()
            ).Diagram;

        using (Transaction t =
             targetDiagram.Store.TransactionManager
                .BeginTransaction("Update diagram"))
        {
            DoUpdates(targetDiagram);
            t.Commit();
        }

        // Display the new diagram.
        adapter.GetDefaultView().Show();
    }
}
```

## <a name="validating-references"></a>Проверка ссылок
 BrokenReferenceDetector проверяет все свойства домена в хранилище (Store), которое может содержать ссылки ModelBus (ModelBusReference). Он вызывает действие, которое определяет место выполнения любого действия. Это особенно полезно для методов проверки. Следующий метод проверки тестирует хранилище, пытаясь сохранить модель, и сообщает в окне ошибок о "битых" ссылках:

```csharp
[ValidationMethod(ValidationCategories.Save)]
public void ValidateModelBusReferences(ValidationContext context)
{
  BrokenReferenceDetector.DetectBrokenReferences(this.Store,
    delegate(ModelElement element, // parent of property
             DomainPropertyInfo property, // identifies property
             ModelBusReference reference) // invalid reference
    {
      context.LogError(string.Format(INVALID_REF_FORMAT,
             property.Name,
             referenceState.Name,
             new ModelBusReferenceTypeConverter().
                 ConvertToInvariantString(reference)),
         "Reference",
         element);
      });
}}
private const string INVALID_REF_FORMAT =
    "The '{0}' domain property of ths ReferenceState instance "
  + "named '{1}' contains reference value '{2}' which is invalid";
```

## <a name="actions-performed-by-the-modelbus-extension"></a>Действия, выполняемые расширением ModelBus

Следующая информация не является существенно важной, но может пригодиться при широком использовании ModelBus.

Расширение ModelBus вносит в решение DSL описанные ниже изменения.

При щелчке правой кнопкой мыши на схеме определения DSL щелкните **включить ModelBus**, а затем выберите **включить этот DSL для использования ModelBus**:

- В проекте DSL добавляется ссылка на **Microsoft.VisualStudio.Modeling.Sdk.Integration.11.0.dll**

- В окне "Определение DSL" добавляется ссылка внешнего типа: `Microsoft.VisualStudio.Modeling.Integration.ModelBusReference`.

   Ссылку можно просмотреть в **обозревателе DSL** в разделе **типы доменов**. Чтобы добавить ссылки внешнего типа вручную, щелкните корневой узел правой кнопкой мыши.

- Добавляется новый файл шаблона, **дсл\женератедкоде\моделбусреференцессериализатион.ТТ**.

Если для свойства домена задано значение Моделбусреференце, щелкните правой кнопкой мыши свойство и выберите пункт **включить специальные свойства моделбусреференце**:

- В свойство домена будут добавлены несколько атрибутов CLR. Их можно увидеть в поле "Пользовательские атрибуты" окна "Свойства". В **дсл\женератедкоде\домаинклассес.КС** можно увидеть атрибуты в объявлении свойства:

  ```csharp
  [System.ComponentModel.TypeConverter(typeof(
  Microsoft.VisualStudio.Modeling.Integration.ModelBusReferenceTypeConverter))]
  [System.ComponentModel.Editor(typeof(
    Microsoft.VisualStudio.Modeling.Integration.Picker
    .ModelReferenceEditor // or ModelElementReferenceEditor
    ), typeof(System.Drawing.Design.UITypeEditor))]
  [Microsoft.VisualStudio.Modeling.Integration.Picker
    .SupplyFileBasedBrowserConfiguration
    ("Choose a model file", "Target model|*.target")]
  ```

При щелчке правой кнопкой мыши на схеме определения DSL щелкните **включить ModelBus** и выберите **открыть этот DSL для ModelBus**:

- Новый проект `ModelBusAdapter` будет добавлен в решение.

- Ссылка на `ModelBusAdapter` будет добавлена в проект `DslPackage`. `ModelBusAdapter` содержит ссылку на `Dsl` проект.

- В **дслпаккаже\саурце.екстентион.ТТ** `|ModelBusAdapter|` добавляется как компонент MEF.

## <a name="see-also"></a>См. также

- [Практическое руководство. Открытие модели из файла в коде программы](../modeling/how-to-open-a-model-from-file-in-program-code.md)
- [Практическое руководство. Добавление обработчика перетаскивания](../modeling/how-to-add-a-drag-and-drop-handler.md)
- [Использование Visual Studio ModelBus в текстовом шаблоне](../modeling/using-visual-studio-modelbus-in-a-text-template.md)
