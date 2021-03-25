---
title: Создание базовой системы проектов, часть 2 | Документация Майкрософт
description: Узнайте, как добавить шаблон Visual Studio, страницу свойств и другие возможности в проект, созданный в предыдущей статье.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- writing a project system
- project system
- tutorial
ms.assetid: aee48fc6-a15f-4fd5-8420-7f18824de220
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: a60bdc7a6cbd73e85248f6ea5897ad3e56337113
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105089424"
---
# <a name="create-a-basic-project-system-part-2"></a>Создание базовой системы проектов, часть 2
В первом пошаговом руководстве в этой серии [создается базовая система проектов, часть 1](../extensibility/creating-a-basic-project-system-part-1.md), в которой показано, как создать базовую систему проектов. Это пошаговое руководство строится на базовой системе проектов путем добавления шаблона Visual Studio, страницы свойств и других функций. Прежде чем начать это, необходимо выполнить первое пошаговое руководство.

В этом пошаговом руководстве описывается, как создать тип проекта с расширением имени файла проекта *. мипрож*. Для выполнения этого пошагового руководства не нужно создавать собственный язык, поскольку пошаговое руководство позаимствовано из существующей системы проектов Visual C#.

В этом пошаговом руководстве объясняется, как выполнить эти задачи:

- Создайте шаблон Visual Studio.

- Разверните шаблон Visual Studio.

- Создайте дочерний узел типа проекта в диалоговом окне **Новый проект** .

- Включите подстановку параметров в шаблоне Visual Studio.

- Создание страницы свойств проекта.

> [!NOTE]
> Действия, описанные в этом пошаговом руководстве, основаны на проекте C#. Тем не менее, за исключением особых особенностей, таких как расширения имен файлов и кода, можно использовать те же действия для проекта Visual Basic.

## <a name="create-a-visual-studio-template"></a>Создание шаблона Visual Studio
- [Создание базовой системы проектов, часть 1](../extensibility/creating-a-basic-project-system-part-1.md) показывает, как создать базовый шаблон проекта и добавить его в систему проектов. Здесь также показано, как зарегистрировать этот шаблон в Visual Studio с помощью <xref:Microsoft.VisualStudio.Shell.ProvideProjectFactoryAttribute> атрибута, который записывает полный путь к папке *\\ темплатес\прожектс\симплепрожект \\* в системном реестре.

Используя шаблон Visual Studio (*VSTEMPLATE* -файл) вместо базового шаблона проекта, можно управлять отображением шаблона в диалоговом окне **Новый проект** и о замене параметров шаблона. Файл *VSTEMPLATE* — это XML-файл, описывающий, как следует включать исходные файлы при создании проекта с помощью шаблона системы проектов. Сама система проектов создается путем сбора *VSTEMPLATE* -файла и исходных файлов в *ZIP* -файле и развернутой путем копирования *ZIP* -файла в расположение, известное Visual Studio. Этот процесс более подробно описан далее в этом пошаговом руководстве.

1. В [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] откройте решение симплепрожект, созданное в разделе [Создание базовой системы проектов, часть 1](../extensibility/creating-a-basic-project-system-part-1.md).

2. В файле *симплепрожектпаккаже. CS* Найдите атрибут провидепрожектфактори. Замените второй параметр (имя проекта) на null, а четвертый параметр (путь к папке шаблона проекта) на ". \\ \Нуллпас ", как показано ниже.

    ```
    [ProvideProjectFactory(typeof(SimpleProjectFactory), null,
        "Simple Project Files (*.myproj);*.myproj", "myproj", "myproj",
        ".\\NullPath",
    LanguageVsTemplate = "SimpleProject")]
    ```

3. Добавьте XML-файл с именем *симплепрожект. vstemplate* в папку *\\ темплатес\прожектс\симплепрожект \\* .

4. Замените содержимое файла *симплепрожект. vstemplate* следующим кодом.

    ```xml
    <VSTemplate Version="2.0.0" Type="Project"
        xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
      <TemplateData>
        <Name>SimpleProject Application</Name>
        <Description>
          A project for creating a SimpleProject application
        </Description>
        <Icon>SimpleProject.ico</Icon>
        <ProjectType>SimpleProject</ProjectType>
      </TemplateData>
      <TemplateContent>
        <Project File="SimpleProject.myproj" ReplaceParameters="true">
          <ProjectItem ReplaceParameters="true" OpenInEditor="true">
            Program.cs
          </ProjectItem>
          <ProjectItem ReplaceParameters="true" OpenInEditor="false">
            AssemblyInfo.cs
          </ProjectItem>
        </Project>
      </TemplateContent>
    </VSTemplate>
    ```

5. В окне **Свойства** выберите все пять файлов в папке *\\ Темплатес\прожектс\симплепрожект \\* и задайте для **действия сборки** значение **зиппрожект**.

    ![Простая папка проекта](../extensibility/media/simpproj2.png "SimpProj2")

    В \<TemplateData> разделе определяется расположение и внешний вид типа проекта симплепрожект в диалоговом окне **Новый проект** , как показано ниже.

- \<Name>Элемент называет шаблон проекта Симплепрожект приложением.

- \<Description>Элемент содержит описание, которое отображается в диалоговом окне **Новый проект** при выборе шаблона проекта.

- \<Icon>Элемент задает значок, который отображается вместе с типом проекта симплепрожект.

- \<ProjectType>Элемент называет тип проекта в диалоговом окне **Новый проект** . Это имя заменяет параметр имени проекта атрибута Провидепрожектфактори.

  > [!NOTE]
  > \<ProjectType>Элемент должен соответствовать `LanguageVsTemplate` аргументу `ProvideProjectFactory` атрибута в файле симплепрожектпаккаже. cs.

  В \<TemplateContent> разделе описываются эти файлы, создаваемые при создании нового проекта:

- *Симплепрожект. мипрож*

- *Program.cs*

- *AssemblyInfo.cs*

  Все три файла имеют значение `ReplaceParameters` true, что позволяет подстановку параметров. Файл *Program. CS* имеет значение `OpenInEditor` true, что приводит к открытию файла в редакторе кода при создании проекта.

  Дополнительные сведения об элементах в схеме шаблона Visual Studio см. в [справочнике по схеме шаблонов Visual Studio](../extensibility/visual-studio-template-schema-reference.md).

> [!NOTE]
> Если проект содержит более одного шаблона Visual Studio, каждый шаблон находится в отдельной папке. Для каждого файла в этой папке должно быть задано **действие build** **зиппрожект**.

## <a name="adding-a-minimal-vsct-file"></a>Добавление минимального vsct-файла
 Чтобы распознать новый или измененный шаблон Visual Studio, необходимо запустить Visual Studio в режиме установки. Для режима установки требуется наличие файла *vsct* . Поэтому необходимо добавить в проект минимальный файл *. vsct* .

1. Добавьте XML-файл с именем *симплепрожект. vsct* в проект симплепрожект.

2. Замените содержимое файла *симплепрожект. vsct* следующим кодом.

    ```
    <?xml version="1.0" encoding="utf-8" ?>
    <CommandTable
      xmlns="http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable">
    </CommandTable>
    ```

3. Задайте для **действия сборки** этого файла значение **вскткомпиле**. Это можно сделать только в файле *CSPROJ* , а не в окне " **свойства** ". Убедитесь, что на этом этапе для **действия сборки** этого файла установлено значение **нет** .

    1. Щелкните правой кнопкой мыши узел Симплепрожект и выберите пункт **изменить симплепрожект. csproj**.

    2. В файле *CSPROJ* выберите элемент *симплепрожект. vsct* .

        ```
        <None Include="SimpleProject.vsct" />
        ```

    3. Измените действие сборки на **вскткомпиле**.

        ```
        <VSCTCompile Include="SimpleProject.vsct" />
        ```

    4. файл проекта и закройте редактор.

    5. Сохраните узел Симплепрожект, а затем в **Обозреватель решений** нажмите кнопку **Перезагрузить проект**.

## <a name="examine-the-visual-studio-template-build-steps"></a>Изучите шаги сборки шаблона Visual Studio
 Система сборки проекта VSPackage обычно выполняет Visual Studio в режиме установки при изменении *VSTEMPLATE* -файла или при перестроении проекта, содержащего *VSTEMPLATE* -файл. Вы можете следовать инструкциям, установив уровень детализации для MSBuild в значение "нормальный" или выше.

1. В меню **Сервис** выберите пункт **Параметры**.

2. Разверните узел **проекты и решения** , а затем выберите **Сборка и запуск**.

3. Задайте для параметра **уровень детализации для выходных данных сборки проекта MSBuild** значение **Обычная**. Нажмите кнопку **ОК**.

4. Перестройте проект Симплепрожект.

    Этап сборки для создания *ZIP* -файла проекта должен выглядеть следующим образом.

```
ZipProjects:
1>  Zipping ProjectTemplates
1>  Zipping <path>\SimpleProject\SimpleProject\obj\Debug\SimpleProject.zip...
1>  Copying file from "<path>\SimpleProject\SimpleProject\obj\Debug\SimpleProject.zip" to "<%LOCALAPPDATA%>\Microsoft\VisualStudio\14.0Exp\ProjectTemplates\\\\SimpleProject.zip".
1>  Copying file from "<path>\SimpleProject\SimpleProject\obj\Debug\SimpleProject.zip" to "bin\Debug\\ProjectTemplates\\\\SimpleProject.zip".
1>  SimpleProject -> <path>\SimpleProject\SimpleProject\bin\Debug\ProjectTemplates\SimpleProject.zip
1>ZipItems:
1>  Zipping ItemTemplates
1>  SimpleProject ->
```

## <a name="deploy-a-visual-studio-template"></a>Развертывание шаблона Visual Studio
Шаблоны Visual Studio не содержат сведений о пути. Поэтому *ZIP* -файл шаблона должен быть развернут в расположении, известном Visual Studio. Расположение папки Прожекттемплатес обычно *<% LocalAppData% > \microsoft\visualstudio\14.0exp\projecttemplates*.

Для развертывания фабрики проектов программа установки должна иметь права администратора. Он развертывает шаблоны в узле установки Visual Studio: *. ..\Микрософт Visual Studio версии .\n\n-\ Common7\IDE\ProjectTemplates*.

## <a name="test-a-visual-studio-template"></a>Тестирование шаблона Visual Studio
Проверьте фабрику проекта, чтобы узнать, создает ли она иерархию проектов с помощью шаблона Visual Studio.

1. Сбросьте экспериментальный экземпляр пакета SDK для Visual Studio.

    Вкл [!INCLUDE[win7](../debugger/includes/win7_md.md)] . в меню **Пуск** найдите папку **Microsoft Visual Studio/пакет SDK для Microsoft Visual Studio/Tools** , а затем выберите пункт **сбросить Microsoft Visual Studio экспериментальный экземпляр**.

    В более поздних версиях Windows: на **начальном** экране введите **сбросить Microsoft Visual Studio \<version> экспериментальный экземпляр**.

2. Появится окно командной строки. Если вы видите слова **для продолжения нажмите клавишу** **Ввод**. После закрытия окна откройте Visual Studio.

3. Перестройте проект Симплепрожект и начните отладку. Откроется экспериментальный экземпляр.

4. В экспериментальном экземпляре создайте проект Симплепрожект. В диалоговом окне **Новый проект** выберите **симплепрожект**.

5. Вы увидите новый экземпляр Симплепрожект.

    ![Простой проект новый экземпляр](../extensibility/media/simpproj2_newproj.png "SimpProj2_NewProj")

    ![Мой проект — новый экземпляр](../extensibility/media/simpproj2_myproj.png "SimpProj2_MyProj")

## <a name="create-a-project-type-child-node"></a>Создание дочернего узла типа проекта
Дочерний узел можно добавить в узел типа проекта в диалоговом окне **Новый проект** . Например, для типа проекта Симплепрожект могут существовать дочерние узлы для консольных приложений, оконных приложений, веб-приложений и т. д.

Дочерние узлы создаются путем изменения файла проекта и добавления \<OutputSubPath> дочерних \<ZipProject> элементов в элементы. При копировании шаблона во время сборки или развертывания каждый дочерний узел становится вложенной папкой папки шаблонов проектов.

В этом разделе показано, как создать дочерний узел консоли для типа проекта Симплепрожект.

1. Переименуйте папку *\\ Темплатес\прожектс\симплепрожект \\* в *\\ темплатес\прожектс\консолеапп \\*.

2. В окне **Свойства** выберите все пять файлов в папке *\\ темплатес\прожектс\консолеапп \\* и убедитесь, что для **действия сборки** задано значение **зиппрожект**.

3. В файле Симплепрожект. vstemplate добавьте следующую строку в конце \<TemplateData> раздела непосредственно перед закрывающим тегом.

    ```
    <NumberOfParentCategoriesToRollUp>1</NumberOfParentCategoriesToRollUp>
    ```

    В результате Шаблон консольного приложения будет отображаться как в дочернем узле консоли, так и в родительском узле Симплепрожект, который находится на одном уровне над дочерним узлом.

4. Сохраните файл *симплепрожект. vstemplate* .

5. В файле *CSPROJ* добавьте в \<OutputSubPath> каждый из элементов зиппрожект. Выгрузить проект, как и ранее, и изменить файл проекта.

6. Нахождение \<ZipProject> элементов. К каждому \<ZipProject> элементу добавьте \<OutputSubPath> элемент и присвойте ему консоль value. Зиппрожект

    ```
    <ZipProject Include="Templates\Projects\ConsoleApp\AssemblyInfo.cs">
      <OutputSubPath>Console</OutputSubPath>
    </ZipProject>
    <ZipProject Include="Templates\Projects\ConsoleApp\Program.cs">
      <OutputSubPath>Console</OutputSubPath>
    </ZipProject>
    <ZipProject Include="Templates\Projects\ConsoleApp\SimpleProject.myproj">
      <OutputSubPath>Console</OutputSubPath>
    </ZipProject>
    <ZipProject Include="Templates\Projects\ConsoleApp\SimpleProject.vstemplate">
      <OutputSubPath>Console</OutputSubPath>
    </ZipProject>
    <ZipProject Include="Templates\Projects\ConsoleApp\SimpleProject.ico">
      <OutputSubPath>Console</OutputSubPath>
    </ZipProject>
    ```

7. Добавьте его \<PropertyGroup> в файл проекта:

    ```
    <PropertyGroup>
      <VsTemplateLanguage>SimpleProject</VsTemplateLanguage>
    </PropertyGroup>
    ```

8. Сохраните файл проекта и перезагрузите проект.

## <a name="test-the-project-type-child-node"></a>Тестирование дочернего узла типа проекта
Протестируйте измененный файл проекта, чтобы увидеть, отображается ли дочерний узел **консоли** в диалоговом окне " **Создание проекта** ".

1. Запустите программу **сброса Microsoft Visual Studio экспериментального экземпляра** .

2. Перестройте проект Симплепрожект и начните отладку. Должен отобразиться экспериментальный экземпляр

3. В диалоговом окне **Новый проект** щелкните узел **симплепрожект** . Шаблон **консольного приложения** должен появиться в области **шаблоны** .

4. Разверните узел **симплепрожект** . Должен отобразиться дочерний узел **консоли** . Шаблон **приложения симплепрожект** будет отображаться в области **шаблоны** .

5. Нажмите кнопку **Отмена** и остановить отладку.

    ![Простая свертка проекта](../extensibility/media/simpproj2_rollup.png "SimpProj2_Rollup")

    ![Простой узел консоли проекта](../extensibility/media/simpproj2_subfolder.png "SimpProj2_Subfolder")

## <a name="substitute-project-template-parameters"></a>Замена параметров шаблона проекта
- При [создании базовой системы проектов часть 1](../extensibility/creating-a-basic-project-system-part-1.md) показала, как перезаписать `ProjectNode.AddFileFromTemplate` метод для выполнения базовой разновидности подстановки параметров шаблона. В этом разделе рассказывается, как использовать более сложные параметры шаблона Visual Studio.

При создании проекта с помощью шаблона Visual Studio в диалоговом окне « **Новый проект** » параметры шаблона заменяются строками для настройки проекта. Параметр шаблона — это специальный маркер, который начинается и заканчивается знаком доллара, например $time $. Следующие два параметра особенно полезны для включения настройки в проектах, основанных на шаблоне.

- $GUID [1-10] $ заменяется новым идентификатором GUID. Можно указать до 10 уникальных идентификаторов GUID, например $guid $1.

- $safeprojectname $ — это имя, предоставленное пользователем в диалоговом окне **Новый проект** , изменено для удаления всех незащищенных символов и пробелов.

  Полный список параметров шаблона см. в разделе [Параметры шаблона](../ide/template-parameters.md).

### <a name="to-substitute-project-template-parameters"></a>Замена параметров шаблона проекта

1. В файле *симплепрожектноде. CS* удалите `AddFileFromTemplate` метод.

2. В файле *\\ темплатес\прожектс\консолеапп\симплепрожект.мипрож* выберите \<RootNamespace> свойство и измените его значение на $safeprojectname $.

    ```
    <RootNamespace>$safeprojectname$</RootNamespace>
    ```

3. В файле *\\ темплатес\прожектс\симплепрожект\програм.КС* замените содержимое файла следующим кодом:

    ```
    using System;
    using System.Collections.Generic;
    using System.Text;
    using System.Runtime.InteropServices;    // Guid

    namespace $safeprojectname$
    {
        [Guid("$guid1$")]
        public class $safeprojectname$
        {
            static void Main(string[] args)
            {
                Console.WriteLine("Hello VSX!!!");
                Console.ReadKey();
            }
        }
    }
    ```

4. Перестройте проект Симплепрожект и начните отладку. Должен отобразиться экспериментальный экземпляр.

5. Создайте новое консольное приложение Симплепрожект. (В области **типы проектов** выберите **симплепрожект**. В разделе **Установленные шаблоны Visual Studio** выберите **консольное приложение**.)

6. В созданном проекте откройте *программу Program. CS*. Он должен выглядеть примерно следующим образом (значения GUID в файле будут отличаться):

    ```csharp
    using System;
    using System.Collections.Generic;
    using System.Text;
    using System.Runtime.InteropServices;    // Guid

    namespace Console_Application1
    {
        [Guid("00000000-0000-0000-00000000-00000000)"]
        public class Console_Application1
        {
            static void Main(string[] args)
            {
                Console.WriteLine("Hello VSX!!!");
                Console.ReadKey();
            }
        }
    }
    ```

## <a name="create-a-project-property-page"></a>Страница «Создание свойства проекта»
Можно создать страницу свойств для типа проекта, чтобы пользователи могли просматривать и изменять свойства в проектах, основанных на шаблоне. В этом разделе показано, как создать страницу свойств, не зависящую от конфигурации. Эта основная страница свойств использует сетку свойств для отображения открытых свойств, предоставляемых в классе страницы свойств.

Создайте класс страницы свойств, производный от `SettingsPage` базового класса. Сетка свойств, предоставляемая `SettingsPage` классом, учитывает большинство типов данных-примитивов и знает, как их отображать. Кроме того, `SettingsPage` класс знает, как сохранять значения свойств в файле проекта.

Страница свойств, созданная в этом разделе, позволяет изменять и сохранять следующие свойства проекта:

- AssemblyName

- OutputType

- RootNamespace.

1. В файле *симплепрожектпаккаже. CS* добавьте этот `ProvideObject` атрибут к `SimpleProjectPackage` классу:

    ```
    [ProvideObject(typeof(GeneralPropertyPage))]
    public sealed class SimpleProjectPackage : ProjectPackage
    ```

    Он регистрирует класс страницы свойств `GeneralPropertyPage` в com.

2. В файле *симплепрожектноде. CS* добавьте следующие два переопределенных метода в `SimpleProjectNode` класс:

    ```csharp
    protected override Guid[] GetConfigurationIndependentPropertyPages()
    {
        Guid[] result = new Guid[1];
        result[0] = typeof(GeneralPropertyPage).GUID;
        return result;
    }
    protected override Guid[] GetPriorityProjectDesignerPages()
    {
        Guid[] result = new Guid[1];
        result[0] = typeof(GeneralPropertyPage).GUID;
        return result;
    }
    ```

    Оба этих метода возвращают массив идентификаторов GUID страницы свойств. Идентификатор GUID Женералпропертипаже является единственным элементом массива, поэтому в диалоговом окне **страницы свойств** будет отображаться только одна страница.

3. Добавьте файл класса с именем *женералпропертипаже. CS* в проект симплепрожект.

4. Замените содержимое этого файла, используя следующий код:

    ```csharp
    using System;
    using System.Runtime.InteropServices;
    using Microsoft.VisualStudio;
    using Microsoft.VisualStudio.Project;
    using System.ComponentModel;

    namespace SimpleProject
    {
        [ComVisible(true)]
        [Guid("6BC7046B-B110-40d8-9F23-34263D8D2936")]
        public class GeneralPropertyPage : SettingsPage
        {
            private string assemblyName;
            private OutputType outputType;
            private string defaultNamespace;

            public GeneralPropertyPage()
            {
                this.Name = "General";
            }

            [Category("AssemblyName")]
            [DisplayName("AssemblyName")]
            [Description("The output file holding assembly metadata.")]
            public string AssemblyName
            {
                get { return this.assemblyName; }
            }
            [Category("Application")]
            [DisplayName("OutputType")]
            [Description("The type of application to build.")]
            public OutputType OutputType
            {
                get { return this.outputType; }
                set { this.outputType = value; this.IsDirty = true; }
            }
            [Category("Application")]
            [DisplayName("DefaultNamespace")]
            [Description("Specifies the default namespace for added items.")]
            public string DefaultNamespace
            {
                get { return this.defaultNamespace; }
                set { this.defaultNamespace = value; this.IsDirty = true; }
            }

            protected override void BindProperties()
            {
                this.assemblyName = this.ProjectMgr.GetProjectProperty("AssemblyName", true);
                this.defaultNamespace = this.ProjectMgr.GetProjectProperty("RootNamespace", false);

                string outputType = this.ProjectMgr.GetProjectProperty("OutputType", false);
                this.outputType = (OutputType)Enum.Parse(typeof(OutputType), outputType);
            }

            protected override int ApplyChanges()
            {
                this.ProjectMgr.SetProjectProperty("AssemblyName", this.assemblyName);
                this.ProjectMgr.SetProjectProperty("OutputType", this.outputType.ToString());
                this.ProjectMgr.SetProjectProperty("RootNamespace", this.defaultNamespace);
                this.IsDirty = false;

                return VSConstants.S_OK;
            }
        }
    }
    ```

    `GeneralPropertyPage`Класс предоставляет три общедоступных свойства AssemblyName, OutputType и rootNamespace. Поскольку AssemblyName не имеет метода Set, он отображается как свойство только для чтения. OutputType является перечислимой константой, поэтому он отображается в виде раскрывающегося списка.

    `SettingsPage`Базовый класс предоставляет `ProjectMgr` для сохранения свойств. `BindProperties`Метод использует `ProjectMgr` для извлечения значений материализованных свойств и установки соответствующих свойств. `ApplyChanges`Метод использует `ProjectMgr` для получения значений свойств и их сохранения в файле проекта. Метод Set свойства задает `IsDirty` значение true, чтобы указать, что свойства должны быть сохранены. Сохраняемость происходит при сохранении проекта или решения.

5. Перестройте решение Симплепрожект и начните отладку. Должен отобразиться экспериментальный экземпляр.

6. В экспериментальном экземпляре создайте новое приложение Симплепрожект.

7. Visual Studio вызывает фабрику проектов для создания проекта с помощью шаблона Visual Studio. В редакторе кода откроется новый файл *Program. CS* .

8. Щелкните правой кнопкой мыши узел проекта в **Обозреватель решений** и выберите пункт **свойства**. Откроется диалоговое окно **Страницы свойств**.

    ![Страница свойств простого проекта](../extensibility/media/simpproj2_proppage.png "SimpProj2_PropPage")

## <a name="test-the-project-property-page"></a>Тестирование страницы свойств проекта
Теперь можно проверить, можно ли изменять и изменять значения свойств.

1. В диалоговом окне **страницы свойств миконсолеаппликатион** измените **свойство DefaultNamespace** на **MyApplication**.

2. Выберите свойство **OutputType** , а затем выберите **Библиотека классов**.

3. Щелкните **Применить** и нажмите кнопку **ОК**.

4. Снова откройте диалоговое окно **страницы свойств** и убедитесь, что изменения сохранены.

5. Закройте экспериментальный экземпляр Visual Studio.

6. Повторно откройте экспериментальный экземпляр.

7. Снова откройте диалоговое окно **страницы свойств** и убедитесь, что изменения сохранены.

8. Закройте экспериментальный экземпляр Visual Studio.
    ![Закрыть экспериментальный экземпляр](../extensibility/media/simpproj2_proppage2.png "SimpProj2_PropPage2")
