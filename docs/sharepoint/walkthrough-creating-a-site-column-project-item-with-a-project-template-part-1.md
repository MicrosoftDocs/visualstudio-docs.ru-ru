---
title: Создание элемента проекта столбца сайта с помощью шаблона проекта, часть 1
titleSuffix: ''
description: Определите тип элемента проекта для создания столбца сайта, а затем создайте шаблон проекта, который будет использоваться для создания проекта SharePoint, содержащего элемент проекта.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint project items, defining your own types
- project items [SharePoint development in Visual Studio], defining your own types
- SharePoint projects, creating custom templates
- SharePoint development in Visual Studio, defining new project item types
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 07f3b90df070eca4e17e5bba9fa6a9e3582bd238
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/02/2021
ms.locfileid: "106217803"
---
# <a name="walkthrough-create-a-site-column-project-item-with-a-project-template-part-1"></a>Пошаговое руководство. Создание элемента проекта столбца сайта с помощью шаблона проекта, часть 1
  Проекты SharePoint — это контейнеры для одного или нескольких элементов проектов SharePoint. Вы можете расширить систему проектов SharePoint в Visual Studio, создав собственные типы элементов проектов SharePoint и связав их с шаблоном проекта. В этом пошаговом руководстве будет определен тип элемента проекта для создания столбца сайта, а затем будет создан шаблон проекта, который можно использовать для создания нового проекта, содержащего элемент проекта столбца сайта.

 В этом пошаговом руководстве описаны следующие задачи.

- Создание расширения Visual Studio, определяющего новый тип элемента проекта SharePoint для столбца сайта. Тип элемента проекта включает в себя простое пользовательское свойство, которое отображается в окне " **Свойства** ".

- Создание [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] шаблона проекта для элемента проекта.

- Создание [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] пакета расширения (VSIX) для развертывания шаблона проекта и сборки расширения.

- Отладка и тестирование элемента проекта.

  Это автономное пошаговое руководство. После завершения этого пошагового руководства можно усовершенствовать элемент проекта, добавив мастер в шаблон проекта. Дополнительные сведения см. в разделе [Пошаговое руководство. Создание элемента проекта столбца сайта с помощью шаблона проекта, часть 2](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md).

> [!NOTE]
> Ряд примеров рабочих процессов см. в разделе [примеры рабочих процессов SharePoint](/sharepoint/dev/general-development/sharepoint-workflow-samples).

## <a name="prerequisites"></a>Предварительные требования
 Для выполнения этого пошагового руководства на компьютере разработчика потребуются следующие компоненты:

- Поддерживаемые выпуски Microsoft Windows, SharePoint и [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

- [!include[vssdk_current_long](../sharepoint/includes/vssdk-current-long-md.md)]. В этом пошаговом руководстве используется шаблон **проекта VSIX** в пакете SDK для создания пакета VSIX для развертывания элемента проекта. Дополнительные сведения см. [в разделе Расширение инструментов SharePoint в Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md).

  Знания следующего понятия полезны, но не требуются для выполнения этого пошагового руководства.

- Столбцы сайта в SharePoint. Дополнительные сведения см. в разделе [столбцы](/previous-versions/office/developer/sharepoint-2010/ms196085(v=office.14)).

- Шаблоны проектов в Visual Studio. Дополнительные сведения см. в статье [Creating Project and Item Templates](../ide/creating-project-and-item-templates.md) (Создание шаблонов проектов и элементов).

## <a name="create-the-projects"></a>Создание проектов
 Для выполнения этого пошагового руководства необходимо создать три проекта:

- Проект VSIX. Этот проект создает пакет VSIX для развертывания элемента проекта столбца сайта и шаблона проекта.

- Проект шаблона проекта. Этот проект создает шаблон проекта, который можно использовать для создания нового проекта SharePoint, содержащего элемент проекта столбца сайта.

- Проект библиотеки классов. Этот проект, реализующий расширение Visual Studio, которое определяет поведение элемента проекта столбца сайта.

  Начните пошаговое руководство, создав проекты.

#### <a name="to-create-the-vsix-project"></a>Создание проекта VSIX

1. Запустите среду [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

2. В строке меню выберите **Файл** > **Создать** > **Проект**.

3. В верхней части диалогового окна **Новый проект** убедитесь, что **платформа .NET Framework 4,5** выбран в списке версий платформа .NET Framework.

4. Разверните узлы **Visual Basic** или **Visual C#** , а затем выберите узел **расширяемость** .

    > [!NOTE]
    > Узел **расширяемости** доступен только при установке пакета SDK для Visual Studio. Дополнительные сведения см. в разделе Предварительные требования ранее в этом разделе.

5. В списке шаблонов проектов выберите **проект VSIX**.

6. В поле **имя** введите **ситеколумнпрожектитем**, а затем нажмите кнопку **ОК** .

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Добавляет проект **ситеколумнпрожектитем** в **Обозреватель решений**.

#### <a name="to-create-the-project-template-project"></a>Создание проекта шаблона проекта

1. В **Обозреватель решений** откройте контекстное меню узла решения, выберите **Добавить**, а затем выберите **Новый проект**.

2. В верхней части диалогового окна **Новый проект** убедитесь, что **платформа .NET Framework 4,5** выбран в списке версий платформа .NET Framework.

3. Разверните узел **Visual C#** или **Visual Basic** , а затем выберите узел **расширяемость** .

4. В списке шаблонов проектов выберите шаблон **проекта C#** или шаблон **шаблона проекта Visual Basic** .

5. В поле **имя** введите **ситеколумнпрожекттемплате**, а затем нажмите кнопку **ОК** .

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Добавляет проект **ситеколумнпрожекттемплате** в решение.

6. Удалите файл кода Class1 из проекта.

7. Если вы создали Visual Basic проект, также удалите следующие файлы из проекта:

    - *MyApplication. Designer. vb*

    - MyApplication. MyApp

    - *Resources. Designer. vb*

    - *Resources. resx*

    - *Settings. Designer. vb*

    - Settings. Settings

#### <a name="to-create-the-extension-project"></a>Создание проекта расширения

1. В **Обозреватель решений** откройте контекстное меню узла решения, выберите **Добавить**, а затем выберите **Новый проект**.

2. В верхней части диалогового окна **Новый проект** убедитесь, что **платформа .NET Framework 4,5** выбран в списке версий платформа .NET Framework.

3. Разверните узлы **Visual C#** или **Visual Basic** , выберите узел **Windows** , а затем шаблон **Библиотека классов** .

4. В поле **имя** введите **прожектитемтипедефинитион** , а затем нажмите кнопку **ОК** .

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Добавляет проект **прожектитемтипедефинитион** в решение и открывает файл кода Class1 по умолчанию.

5. Удалите файл кода Class1 из проекта.

## <a name="configure-the-extension-project"></a>Настройка проекта расширения
 Добавьте файлы кода и ссылки на сборки для настройки проекта расширения.

#### <a name="to-configure-the-project"></a>Настройка проекта

1. В проекте Прожектитемтипедефинитион добавьте файл кода с именем **ситеколумнпрожектитемтипепровидер**.

2. В строке меню выберите **Проект** > **Добавить ссылку**.

3. В диалоговом окне **Диспетчер ссылок — прожектитемтипедефинитион** разверните узел **сборки** , выберите узел **платформа** , а затем установите флажок System. ComponentModel. композиция.

4. Выберите узел **расширения** , установите флажок рядом с сборкой Microsoft. VisualStudio. SharePoint, а затем нажмите кнопку **ОК** .

## <a name="define-the-new-sharepoint-project-item-type"></a>Определение нового типа элемента проекта SharePoint
 Создайте класс, реализующий <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> интерфейс для определения поведения нового типа элемента проекта. Реализуйте этот интерфейс всякий раз, когда нужно определить новый тип элемента проекта.

#### <a name="to-define-the-new-sharepoint-project-item-type"></a>Определение типа нового элемента проекта SharePoint

1. В файле кода **ситеколумнпрожектитемтипепровидер** замените код по умолчанию следующим кодом, а затем сохраните файл.

     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/projectitemtypedefinition/sitecolumnprojectitemtypeprovider.cs" id="Snippet1":::
     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/projectitemtypedefinition/sitecolumnprojectitemtypeprovider.vb" id="Snippet1":::

## <a name="create-a-visual-studio-project-template"></a>Создание шаблона проекта Visual Studio
 Создав шаблон проекта, вы разрешите другим разработчикам создавать проекты SharePoint, содержащие элементы проекта столбца сайта. Шаблон проекта SharePoint включает файлы, необходимые для всех проектов в Visual Studio, таких как *CSPROJ* -или *VBPROJ* -и *VSTEMPLATE* -файлы, а также файлы, относящиеся к проектам SharePoint. Дополнительные сведения см. в разделе [Создание шаблонов элементов и шаблонов проектов для элементов проектов SharePoint](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).

 В этой процедуре создается пустой проект SharePoint для создания файлов, относящихся к проектам SharePoint. Затем добавьте эти файлы в проект Ситеколумнпрожекттемплате, чтобы они включались в шаблон, созданный из этого проекта. Вы также настроите файл проекта Ситеколумнпрожекттемплате, чтобы указать, где будет отображаться шаблон проекта в диалоговом окне **Новый проект** .

#### <a name="to-create-the-files-for-the-project-template"></a>Создание файлов для шаблона проекта

1. Запустите второй экземпляр [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] с учетными данными администратора.

2. Создайте проект SharePoint 2010 с именем **басешарепоинтпрожект**.

   > [!IMPORTANT]
   > В **мастере настройки SharePoint** не выбирайте параметр **Развернуть как решение фермы** .

3. Добавьте пустой элемент элемента в проект, а затем назовите элемент **field1**.

4. Сохраните проект, а затем закройте второй экземпляр [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

5. В экземпляре [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , в котором открыто решение ситеколумнпрожектитем, в **Обозреватель решений** откройте контекстное меню узла проекта **ситеколумнпрожекттемплате** , выберите **Добавить**, а затем щелкните **существующий элемент**.

6. В диалоговом окне **Добавление существующего элемента** откройте список расширений файлов и выберите **все файлы ( \* . \* )**.

7. В каталоге, содержащем проект Басешарепоинтпрожект, выберите файл key. snk, а затем нажмите кнопку **Добавить** .

   > [!NOTE]
   > В этом пошаговом руководстве создаваемый шаблон проекта использует один и тот же файл key. snk для подписывания каждого проекта, созданного с помощью шаблона. Сведения о том, как развернуть этот пример, чтобы создать другой файл key. snk для каждого экземпляра проекта, см. в разделе [Пошаговое руководство. Создание элемента проекта столбца сайта с помощью шаблона проекта, часть 2](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md).

8. Повторите шаги 5-8, чтобы добавить следующие файлы из указанных вложенных папок в каталоге Басешарепоинтпрожект:

   - *\Field1\Elements.xml*

   - *\Field1\SharePointProjectItem.spdata*

   - *\Features\Feature1\Feature1.feature*

   - *\Features\Feature1\Feature1.Template.xml*

   - *\паккаже\паккаже.паккаже*

   - *\Package\Package.Template.xml*

     Добавьте эти файлы непосредственно в проект Ситеколумнпрожекттемплате. не создавайте заново подпапки field1, Features или Package в проекте. Дополнительные сведения об этих файлах см. в разделе [Создание шаблонов элементов и шаблонов проектов для элементов проектов SharePoint](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).

#### <a name="to-configure-how-developers-discover-the-project-template-in-the-new-project-dialog-box"></a>Настройка способа обнаружения шаблона проекта разработчиками в диалоговом окне "Создание проекта"

1. В **Обозреватель решений** откройте контекстное меню для узла проекта **ситеколумнпрожекттемплате** и выберите команду **Выгрузить проект**. Если будет предложено сохранить изменения в файлах, нажмите кнопку **Да** .

2. Снова откройте контекстное меню для узла **ситеколумнпрожекттемплате** , а затем выберите **изменить ситеколумнпрожекттемплате. csproj** или **изменить ситеколумнпрожекттемплате. vbproj**.

3. В файле проекта выберите следующий `VSTemplate` элемент.

    ```xml
    <VSTemplate Include="SiteColumnProjectTemplate.vstemplate">
    ```

4. Замените этот элемент следующим XML-кодом.

    ```xml
    <VSTemplate Include="SiteColumnProjectTemplate.vstemplate">
      <OutputSubPath>SharePoint\SharePoint14</OutputSubPath>
    </VSTemplate>
    ```

     `OutputSubPath`Элемент задает дополнительные папки в пути, по которому создается шаблон проекта при построении проекта. Указанные здесь папки гарантируют, что шаблон проекта будет доступен только тогда, когда клиенты открывают диалоговое окно **Новый проект** , разверните узел **SharePoint** , а затем выберите узел **2010** .

5. Сохраните файл и закройте его.

6. В **Обозреватель решений** откройте контекстное меню проекта **ситеколумнпрожекттемплате** и выберите **Перезагрузить проект**.

## <a name="edit-the-project-template-files"></a>Изменение файлов шаблонов проектов
 В проекте Ситеколумнпрожекттемплате измените следующие файлы, чтобы определить поведение шаблона проекта:

- *AssemblyInfo. CS* или *AssemblyInfo. vb*

- *Elements.xml*

- *Шарепоинтпрожектитем. данные*

- *Компонент Feature1. feature*

- *Package. Package*

- *Ситеколумнпрожекттемплате. vstemplate*

- *ProjectTemplate. csproj* или *ProjectTemplate. vbproj*

  В следующих процедурах вы добавите в некоторые из этих файлов заменяемые параметры. Заменяемый параметр — это маркер, который начинается и заканчивается знаком доллара ($). Когда пользователь использует этот шаблон проекта для создания проекта, Visual Studio автоматически заменяет эти параметры в новом проекте на конкретные значения. Дополнительные сведения см. в разделе [Заменяемые параметры](../sharepoint/replaceable-parameters.md).

#### <a name="to-edit-the-assemblyinfocs-or-assemblyinfovb-file"></a>Изменение файла AssemblyInfo. cs или AssemblyInfo. vb

1. В проекте Ситеколумнпрожекттемплате откройте файл *AssemblyInfo. CS* или *AssemblyInfo. vb* , а затем добавьте следующий оператор в его верхнюю часть:

    ```vb
    Imports System.Security
    ```

    ```csharp
    using System.Security;
    ```

     Если свойство **"изолированное решение"** проекта SharePoint имеет значение **true**, Visual Studio добавляет в <xref:System.Security.AllowPartiallyTrustedCallersAttribute> файл кода AssemblyInfo. Однако файл кода AssemblyInfo в шаблоне проекта не импортирует <xref:System.Security> пространство имен по умолчанию. Чтобы избежать ошибок компиляции, необходимо добавить инструкцию **using** или **Imports** .

2. Сохраните файл и закройте его.

#### <a name="to-edit-the-elementsxml-file"></a>Изменение файла Elements.xml

1. В проекте Ситеколумнпрожекттемплате замените содержимое файла *Elements.xml* следующим XML-кодом.

    ```xml
    <?xml version="1.0" encoding="utf-8"?>
    <Elements xmlns="http://schemas.microsoft.com/sharepoint/">
      <Field ID="{$guid5$}"
          Name="$safeprojectname$"
          DisplayName="$projectname$"
          Type="Text"
          Group="Custom Columns">
      </Field>
    </Elements>
    ```

     Новый XML-файл добавляет `Field` элемент, определяющий имя столбца сайта, его базовый тип и группу, в которой будет перечисляться столбец сайта в коллекции. Дополнительные сведения о содержимом этого файла см. в разделе [схема определения поля](/previous-versions/office/developer/sharepoint-2010/ms196289(v=office.14)).

2. Сохраните файл и закройте его.

#### <a name="to-edit-the-sharepointprojectitemspdata-file"></a>Изменение файла Шарепоинтпрожектитем. данных

1. В проекте Ситеколумнпрожекттемплате замените содержимое файла *шарепоинтпрожектитем. данных* следующим XML-кодом.

   ```xml
   <?xml version="1.0" encoding="utf-8"?>
   <ProjectItem Type="Contoso.SiteColumn" DefaultFile="Elements.xml"
                xmlns="http://schemas.microsoft.com/VisualStudio/2010/SharePointTools/SharePointProjectItemModel">
     <Files>
       <ProjectItemFile Source="Elements.xml" Target="$safeprojectname$\" Type="ElementManifest" />
     </Files>
   </ProjectItem>
   ```

    Новый XML вносит в файл следующие изменения:

   - Изменяет `Type` атрибут `ProjectItem` элемента на ту же строку, которая передается в <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute> Определение элемента проекта ( `SiteColumnProjectItemTypeProvider` класс, созданный ранее в этом пошаговом руководстве).

   - Удаляет `SupportedTrustLevels` атрибуты и `SupportedDeploymentScopes` из `ProjectItem` элемента. Эти значения атрибутов не нужны, так как уровни доверия и области развертывания указаны в `SiteColumnProjectItemTypeProvider` классе в проекте прожектитемтипедефинитион.

     Дополнительные сведения о содержимом файлов *данных с данными* см. в разделе [Справочник по схеме элементов проекта SharePoint](../sharepoint/sharepoint-project-item-schema-reference.md).

2. Сохраните файл и закройте его.

#### <a name="to-edit-the-feature1feature-file"></a>Изменение файла Feature1. feature

1. В проекте Ситеколумнпрожекттемплате замените содержимое файла *Feature1. Feature* следующим XML-кодом.

   ```xml
   <?xml version="1.0" encoding="utf-8"?>
   <feature xmlns:dm0="http://schemas.microsoft.com/VisualStudio/2008/DslTools/Core" dslVersion="1.0.0.0" Id="$guid4$" featureId="$guid4$"
            imageUrl="" solutionId="00000000-0000-0000-0000-000000000000" title="Site Column Feature1" version=""
            deploymentPath="$SharePoint.Project.FileNameWithoutExtension$_$SharePoint.Feature.FileNameWithoutExtension$"
            xmlns="http://schemas.microsoft.com/VisualStudio/2008/SharePointTools/FeatureModel">
     <projectItems>
       <projectItemReference itemId="$guid2$" />
     </projectItems>
   </feature>
   ```

    Новый XML вносит в файл следующие изменения:

   - Изменяет значения `Id` `featureId` атрибутов и `feature` элемента на `$guid4$` .

   - Изменяет значения `itemId` атрибута `projectItemReference` элемента на `$guid2$` .

     Дополнительные сведения о файлах *Feature* см. в разделе [Создание шаблонов элементов и шаблонов проектов для элементов проектов SharePoint](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).

2. Сохраните файл и закройте его.

#### <a name="to-edit-the-packagepackage-file"></a>Изменение файла пакета. Package

1. В проекте Ситеколумнпрожекттемплате замените содержимое файла *Package. Package* следующим XML-кодом.

   ```xml
   <?xml version="1.0" encoding="utf-8"?>
   <package xmlns:dm0="http://schemas.microsoft.com/VisualStudio/2008/DslTools/Core" dslVersion="1.0.0.0"
            Id="$guid3$" solutionId="$guid3$" resetWebServer="false" name="$safeprojectname$"
            xmlns="http://schemas.microsoft.com/VisualStudio/2008/SharePointTools/PackageModel">
     <features>
       <featureReference itemId="$guid4$" />
     </features>
   </package>
   ```

    Новый XML вносит в файл следующие изменения:

   - Изменяет значения `Id` `solutionId` атрибутов и `package` элемента на `$guid3$` .

   - Изменяет значения `itemId` атрибута `featureReference` элемента на `$guid4$` .

     Дополнительные сведения о *пакетных* файлах см. в разделе [Создание шаблонов элементов и шаблонов проектов для элементов проектов SharePoint](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).

2. Сохраните файл и закройте его.

#### <a name="to-edit-the-sitecolumnprojecttemplatevstemplate-file"></a>Изменение файла ситеколумнпрожекттемплате. vstemplate

1. В проекте Ситеколумнпрожекттемплате замените содержимое файла Ситеколумнпрожекттемплате. vstemplate одним из следующих разделов XML.

   - Если вы создаете шаблон проекта Visual C#, используйте следующий код XML.

   ```xml
   <?xml version="1.0" encoding="utf-8"?>
   <VSTemplate Version="3.0.0" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005" Type="Project">
     <TemplateData>
       <Name>Site Column</Name>
       <Description>Creates a new site column in SharePoint</Description>
       <FrameworkVersion>3.5</FrameworkVersion>
       <ProjectType>CSharp</ProjectType>
       <CreateNewFolder>true</CreateNewFolder>
       <CreateInPlace>true</CreateInPlace>
       <ProvideDefaultName>true</ProvideDefaultName>
       <DefaultName>SiteColumn</DefaultName>
       <LocationField>Enabled</LocationField>
       <EnableLocationBrowseButton>true</EnableLocationBrowseButton>
       <PromptForSaveOnCreation>true</PromptForSaveOnCreation>
       <NumberOfParentCategoriesToRollUp>1</NumberOfParentCategoriesToRollUp>
       <Icon>SiteColumnProjectTemplate.ico</Icon>
       <SortOrder>1000</SortOrder>
     </TemplateData>
     <TemplateContent>
       <Project TargetFileName="SharePointProject1.csproj" File="ProjectTemplate.csproj" ReplaceParameters="true">
         <ProjectItem ReplaceParameters="true" TargetFileName="Properties\AssemblyInfo.cs">AssemblyInfo.cs</ProjectItem>
         <ProjectItem ReplaceParameters="true" TargetFileName="Features\Feature1\Feature1.feature">Feature1.feature</ProjectItem>
         <ProjectItem ReplaceParameters="true" TargetFileName="Features\Feature1\Feature1.Template.xml">Feature1.template.xml</ProjectItem>
         <ProjectItem ReplaceParameters="true" TargetFileName="Package\Package.package">Package.package</ProjectItem>
         <ProjectItem ReplaceParameters="true" TargetFileName="Package\Package.Template.xml">Package.Template.xml</ProjectItem>
         <ProjectItem ReplaceParameters="true" TargetFileName="Field1\SharePointProjectItem.spdata">SharePointProjectItem.spdata</ProjectItem>
         <ProjectItem ReplaceParameters="true" TargetFileName="Field1\Elements.xml" OpenInEditor="true">Elements.xml</ProjectItem>
         <ProjectItem ReplaceParameters="false" TargetFileName="key.snk">key.snk</ProjectItem>
       </Project>
     </TemplateContent>
   </VSTemplate>
   ```

   - Если вы создаете шаблон проекта Visual Basic, используйте следующий код XML.

   ```xml
   <?xml version="1.0" encoding="utf-8"?>
   <VSTemplate Version="3.0.0" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005" Type="Project">
     <TemplateData>
       <Name>Site Column</Name>
       <Description>Creates a new site column in SharePoint</Description>
       <FrameworkVersion>3.5</FrameworkVersion>
       <ProjectType>VisualBasic</ProjectType>
       <CreateNewFolder>true</CreateNewFolder>
       <CreateInPlace>true</CreateInPlace>
       <ProvideDefaultName>true</ProvideDefaultName>
       <DefaultName>SiteColumn</DefaultName>
       <LocationField>Enabled</LocationField>
       <EnableLocationBrowseButton>true</EnableLocationBrowseButton>
       <PromptForSaveOnCreation>true</PromptForSaveOnCreation>
       <NumberOfParentCategoriesToRollUp>1</NumberOfParentCategoriesToRollUp>
       <Icon>SiteColumnProjectTemplate.ico</Icon>
       <SortOrder>1000</SortOrder>
     </TemplateData>
     <TemplateContent>
       <Project TargetFileName="SharePointProject1.vbproj" File="ProjectTemplate.vbproj" ReplaceParameters="true">
         <ProjectItem ReplaceParameters="true" TargetFileName="My Project\AssemblyInfo.vb">AssemblyInfo.vb</ProjectItem>
         <ProjectItem ReplaceParameters="true" TargetFileName="Features\Feature1\Feature1.feature">Feature1.feature</ProjectItem>
         <ProjectItem ReplaceParameters="true" TargetFileName="Features\Feature1\Feature1.Template.xml">Feature1.template.xml</ProjectItem>
         <ProjectItem ReplaceParameters="true" TargetFileName="Package\Package.package">Package.package</ProjectItem>
         <ProjectItem ReplaceParameters="true" TargetFileName="Package\Package.Template.xml">Package.Template.xml</ProjectItem>
         <ProjectItem ReplaceParameters="true" TargetFileName="Field1\SharePointProjectItem.spdata">SharePointProjectItem.spdata</ProjectItem>
         <ProjectItem ReplaceParameters="true" TargetFileName="Field1\Elements.xml" OpenInEditor="true">Elements.xml</ProjectItem>
         <ProjectItem ReplaceParameters="false" TargetFileName="key.snk">key.snk</ProjectItem>
       </Project>
     </TemplateContent>
   </VSTemplate>
   ```

    Новый XML вносит в файл следующие изменения:

   - Задает `Name` элемент в **столбце значение сайта**. (Это имя отображается в диалоговом окне **Новый проект** ).

   - Добавляет `ProjectItem` элементы для каждого филесат, входящего в каждый экземпляр проекта.

   - Использует пространство имен `http://schemas.microsoft.com/developer/vstemplate/2005` . Другие файлы проекта в этом решении используют `http://schemas.microsoft.com/developer/msbuild/2003` пространство имен. Поэтому будут созданы предупреждающие сообщения схемы XML, но их можно игнорировать в этом пошаговом руководстве.

     Дополнительные сведения о содержимом *VSTEMPLATE* файлов см. в разделе [Справочник по схеме шаблонов Visual Studio](../extensibility/visual-studio-template-schema-reference.md).

2. Сохраните файл и закройте его.

#### <a name="to-edit-the-projecttemplatecsproj-or-projecttemplatevbproj-file"></a>Изменение файла projecttemplate. csproj или projecttemplate. vbproj

1. В проекте Ситеколумнпрожекттемплате замените содержимое файла *ProjectTemplate. csproj* или *ProjectTemplate. vbproj* одним из следующих разделов XML.

    - Если вы создаете шаблон проекта Visual C#, используйте следующий код XML.

    ```xml
    <?xml version="1.0" encoding="utf-8"?>
    <Project ToolsVersion="4.0" DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
      <PropertyGroup>
        <Configuration Condition=" '$(Configuration)' == '' ">Debug</Configuration>
        <Platform Condition=" '$(Platform)' == '' ">AnyCPU</Platform>
        <SchemaVersion>2.0</SchemaVersion>
        <ProjectGuid>{$guid1$}</ProjectGuid>
        <OutputType>Library</OutputType>
        <AppDesignerFolder>Properties</AppDesignerFolder>
        <RootNamespace>$safeprojectname$</RootNamespace>
        <AssemblyName>$safeprojectname$</AssemblyName>
        <TargetFrameworkVersion>v3.5</TargetFrameworkVersion>
        <FileAlignment>512</FileAlignment>
        <ProjectTypeGuids>{BB1F664B-9266-4fd6-B973-E1E44974B511};{14822709-B5A1-4724-98CA-57A101D1B079};{FAE04EC0-301F-11D3-BF4B-00C04F79EFBC}</ProjectTypeGuids>
      </PropertyGroup>
      <PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Debug|AnyCPU' ">
        <DebugSymbols>true</DebugSymbols>
        <DebugType>full</DebugType>
        <Optimize>false</Optimize>
        <OutputPath>bin\Debug\</OutputPath>
        <DefineConstants>DEBUG;TRACE</DefineConstants>
        <ErrorReport>prompt</ErrorReport>
        <WarningLevel>4</WarningLevel>
        <UseVSHostingProcess>false</UseVSHostingProcess>
      </PropertyGroup>
      <PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Release|AnyCPU' ">
        <DebugType>pdbonly</DebugType>
        <Optimize>true</Optimize>
        <OutputPath>bin\Release\</OutputPath>
        <DefineConstants>TRACE</DefineConstants>
        <ErrorReport>prompt</ErrorReport>
        <WarningLevel>4</WarningLevel>
      </PropertyGroup>
      <PropertyGroup>
        <SignAssembly>true</SignAssembly>
        <AssemblyOriginatorKeyFile>key.snk</AssemblyOriginatorKeyFile>
      </PropertyGroup>
      <ItemGroup>
        <Reference Include="System" />
        <Reference Include="System.Core" />
        <Reference Include="System.Data" />
        <Reference Include="System.Data.DataSetExtensions" />
        <Reference Include="System.Web" />
        <Reference Include="System.Xml" />
        <Reference Include="System.Xml.Linq" />
        <Reference Include="Microsoft.SharePoint" />
        <Reference Include="Microsoft.SharePoint.Security" />
      </ItemGroup>
      <ItemGroup>
        <Compile Include="Properties\AssemblyInfo.cs" />
      </ItemGroup>
      <ItemGroup>
        <None Include="Field1\SharePointProjectItem.spdata">
          <SharePointProjectItemId>{$guid2$}</SharePointProjectItemId>
        </None>
        <None Include="Field1\Elements.xml" />
      </ItemGroup>
      <ItemGroup>
        <None Include="key.snk" />
        <None Include="Package\Package.package">
          <PackageId>{$guid3$}</PackageId>
        </None>
        <None Include="Package\Package.Template.xml">
          <DependentUpon>Package.package</DependentUpon>
        </None>
        <None Include="Features\Feature1\Feature1.feature">
          <FeatureId>{$guid4$}</FeatureId>
        </None>
        <None Include="Features\Feature1\Feature1.Template.xml">
          <DependentUpon>Feature1.feature</DependentUpon>
        </None>
      </ItemGroup>
      <Import Project="$(MSBuildToolsPath)\Microsoft.CSharp.targets" />
      <Import Project="$(MSBuildExtensionsPath32)\Microsoft\VisualStudio\v10.0\SharePointTools\Microsoft.VisualStudio.SharePoint.targets" />
    </Project>
    ```

    1. Если вы создаете шаблон проекта Visual Basic, используйте следующий код XML.

    ```xml
    <?xml version="1.0" encoding="utf-8"?>
    <Project ToolsVersion="4.0" DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
      <PropertyGroup>
        <Configuration Condition=" '$(Configuration)' == '' ">Debug</Configuration>
        <Platform Condition=" '$(Platform)' == '' ">AnyCPU</Platform>
        <ProductVersion>
        </ProductVersion>
        <SchemaVersion>
        </SchemaVersion>
        <ProjectGuid>{$guid1$}</ProjectGuid>
        <OutputType>Library</OutputType>
        <RootNamespace>$safeprojectname$</RootNamespace>
        <AssemblyName>$safeprojectname$</AssemblyName>
        <TargetFrameworkVersion>v3.5</TargetFrameworkVersion>
        <FileAlignment>512</FileAlignment>
        <ProjectTypeGuids>{BB1F664B-9266-4fd6-B973-E1E44974B511};{D59BE175-2ED0-4C54-BE3D-CDAA9F3214C8};{F184B08F-C81C-45F6-A57F-5ABD9991F28F}</ProjectTypeGuids>
        <OptionExplicit>On</OptionExplicit>
        <OptionCompare>Binary</OptionCompare>
        <OptionStrict>Off</OptionStrict>
        <OptionInfer>On</OptionInfer>
      </PropertyGroup>
      <PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Debug|AnyCPU' ">
        <DebugSymbols>true</DebugSymbols>
        <DebugType>full</DebugType>
        <DefineDebug>true</DefineDebug>
        <DefineTrace>true</DefineTrace>
        <OutputPath>bin\Debug\</OutputPath>
        <WarningLevel>4</WarningLevel>
        <UseVSHostingProcess>false</UseVSHostingProcess>
      </PropertyGroup>
      <PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Release|AnyCPU' ">
        <DebugType>pdbonly</DebugType>
        <DefineDebug>false</DefineDebug>
        <DefineTrace>true</DefineTrace>
        <Optimize>true</Optimize>
        <OutputPath>bin\Release\</OutputPath>
        <UseVSHostingProcess>false</UseVSHostingProcess>
      </PropertyGroup>
      <PropertyGroup>
        <SignAssembly>true</SignAssembly>
        <AssemblyOriginatorKeyFile>key.snk</AssemblyOriginatorKeyFile>
      </PropertyGroup>
      <ItemGroup>
        <Reference Include="System" />
        <Reference Include="System.Core" />
        <Reference Include="System.Data" />
        <Reference Include="System.Data.DataSetExtensions" />
        <Reference Include="System.Xml" />
        <Reference Include="System.Xml.Linq" />
        <Reference Include="Microsoft.SharePoint" />
        <Reference Include="Microsoft.SharePoint.Security" />
      </ItemGroup>
      <ItemGroup>
        <Import Include="Microsoft.VisualBasic" />
        <Import Include="System" />
        <Import Include="System.Collections" />
        <Import Include="System.Collections.Generic" />
        <Import Include="System.Data" />
        <Import Include="System.Diagnostics" />
        <Import Include="System.Linq" />
        <Import Include="System.Xml.Linq" />
        <Import Include="Microsoft.SharePoint" />
        <Import Include="Microsoft.SharePoint.Security" />
      </ItemGroup>
      <ItemGroup>
        <Compile Include="My Project\AssemblyInfo.vb" />
      </ItemGroup>
      <ItemGroup>
        <AppDesigner Include="My Project\" />
      </ItemGroup>
      <ItemGroup>
        <None Include="Features\Feature1\Feature1.feature">
          <FeatureId>{$guid4$}</FeatureId>
        </None>
        <None Include="Field1\SharePointProjectItem.spdata">
          <SharePointProjectItemId>{$guid2$}</SharePointProjectItemId>
        </None>
        <None Include="key.snk" />
        <None Include="Package\Package.package">
          <PackageId>{$guid3$}</PackageId>
        </None>
        <None Include="Package\Package.Template.xml">
          <DependentUpon>Package.package</DependentUpon>
        </None>
      </ItemGroup>
      <ItemGroup>
        <None Include="Features\Feature1\Feature1.Template.xml">
          <DependentUpon>Feature1.feature</DependentUpon>
        </None>
        <None Include="Field1\Elements.xml" />
      </ItemGroup>
      <Import Project="$(MSBuildToolsPath)\Microsoft.VisualBasic.targets" />
      <Import Project="$(MSBuildExtensionsPath32)\Microsoft\VisualStudio\v10.0\SharePointTools\Microsoft.VisualStudio.SharePoint.targets" />
    </Project>
    ```

     Новый XML вносит в файл следующие изменения:

    - Использует `TargetFrameworkVersion` элемент для указания платформа .NET Framework 3,5, а не 4,5.

    - Добавляет `SignAssembly` `AssemblyOriginatorKeyFile` элементы и для подписания выходных данных проекта.

    - Добавляет `Reference` элементы для ссылок на сборки, используемые проектами SharePoint.

    - Добавляет элементы для каждого файла по умолчанию в проекте, например *Elements.xml* и *шарепоинтпрожектитем. данных*.

2. Сохраните файл и закройте его.

## <a name="create-a-vsix-package-to-deploy-the-project-template"></a>Создание пакета VSIX для развертывания шаблона проекта
 Чтобы развернуть расширение, используйте проект VSIX в решении **ситеколумнпрожектитем** для создания пакета VSIX. Сначала настройте пакет VSIX, изменив файл Source. extension. vsixmanifest, который включен в проект VSIX. Затем создайте пакет VSIX, создав решение.

#### <a name="to-configure-and-create-the-vsix-package"></a>Настройка и создание пакета VSIX

1. В **Обозреватель решений** в проекте **ситеколумнпрожектитем** откройте файл Source. extension. vsixmanifest в редакторе манифестов.

     Файл Source. extension. vsixmanifest является основанием для файла Extension. vsixmanifest, который требуются для всех пакетов VSIX. Дополнительные сведения об этом файле см. в разделе [Справочник по схеме расширения VSIX 1,0](/previous-versions/dd393700(v=vs.110)).

2. В поле **Название продукта** введите **столбец сайта**.

3. В поле **Author (автор** ) введите **contoso**.

4. В поле **Описание** введите **проект SharePoint для создания столбцов сайта**.

5. Перейдите на вкладку **активы** и нажмите кнопку **создать** .

     Откроется диалоговое окно **Добавление нового ресурса** .

6. В списке **тип** выберите **Microsoft. VisualStudio. ProjectTemplate**.

    > [!NOTE]
    > Это значение соответствует `ProjectTemplate` элементу в файле Extension. vsixmanifest. Этот элемент определяет вложенную папку в пакете VSIX, который содержит шаблон проекта. Дополнительные сведения см. в разделе [элемент ProjectTemplate (Схема VSX)](/previous-versions/visualstudio/visual-studio-2010/dd393735\(v\=vs.100\)).

7. В списке **источник** выберите **проект в текущем решении**.

8. В списке **проект** выберите **ситеколумнпрожекттемплате**, а затем нажмите кнопку **ОК** .

9. Снова нажмите кнопку **создать** .

     Откроется диалоговое окно **Добавление нового ресурса** .

10. В списке **тип** выберите **Microsoft. VisualStudio. MefComponent**.

    > [!NOTE]
    > Это значение соответствует `MefComponent` элементу в файле Extension. vsixmanifest. Этот элемент задает имя сборки расширения в пакете VSIX. Дополнительные сведения см. в разделе [элемент MEFComponent (Схема VSX)](/previous-versions/visualstudio/visual-studio-2010/dd393736\(v\=vs.100\)).

11. В списке **источник** выберите **проект в текущем решении**.

12. В списке **проект** выберите **прожектитемтипедефинитион**, а затем нажмите кнопку **ОК** .

13. В строке меню выберите **Сборка**  >  **сборка решения**, а затем убедитесь, что проект компилируется без ошибок.

## <a name="test-the-project-template"></a>Тестирование шаблона проекта
 Теперь вы готовы к тестированию шаблона проекта. Сначала начните отладку решения Ситеколумнпрожектитем в экспериментальном экземпляре Visual Studio. Затем протестируйте проект **столбца сайта** в экспериментальном экземпляре Visual Studio. Наконец, создайте и запустите проект SharePoint, чтобы убедиться, что столбец сайта работает ожидаемым образом.

#### <a name="to-start-debugging-the-solution"></a>Запуск отладки решения

1. Перезапустите Visual Studio с учетными данными администратора, а затем откройте решение Ситеколумнпрожектитем.

2. В файле кода Ситеколумнпрожектитемтипепровидер добавьте точку останова в первую строку кода в `InitializeType` методе, а затем нажмите клавишу **F5** , чтобы начать отладку.

     Visual Studio устанавливает расширение в%UserProfile%\AppData\Local\Microsoft\VisualStudio\10.0Exp\Extensions\Contoso\Site Column\1.0 и запускает экспериментальный экземпляр Visual Studio. Вы проверите элемент проекта в этом экземпляре Visual Studio.

#### <a name="to-test-the-project-in-visual-studio"></a>Тестирование проекта в Visual Studio

1. В экспериментальном экземпляре Visual Studio в строке меню выберите **файл**  >  **создать**  >  **проект**.

2. Разверните узел **Visual C#** или **Visual Basic** (в зависимости от языка, поддерживаемого шаблоном проекта), разверните узел **SharePoint** , а затем выберите узел **2010** .

3. В списке шаблонов проектов выберите шаблон **столбец сайта** .

4. В поле **имя** введите **ситеколумнтест** , а затем нажмите кнопку **ОК** .

     В **Обозреватель решений** откроется новый проект с элементом проекта с именем **field1**.

5. Убедитесь, что код в другом экземпляре Visual Studio остановлен в точке останова, заданной ранее в `InitializeType` методе, а затем нажмите клавишу **F5** , чтобы продолжить отладку проекта.

6. В **Обозреватель решений** выберите узел **field1** , а затем нажмите клавишу **F4** .

     Откроется окно **Свойства**.

7. Убедитесь, что в списке свойств отображается **свойство пример** свойства.

#### <a name="to-test-the-site-column-in-sharepoint"></a>Тестирование столбца сайта в SharePoint

1. В **Обозреватель решений** выберите узел **ситеколумнтест** .

2. В окне **Свойства** в текстовом поле рядом со свойством **URL-адрес сайта** введите **http://localhost** .

     На этом шаге указывается локальный сайт SharePoint на компьютере разработчика, который будет использоваться для отладки.

    > [!NOTE]
    > Свойство **URL-адрес сайта** по умолчанию пусто, так как шаблон проекта столбца сайта не предоставляет мастер для сбора этого значения при создании проекта. Чтобы узнать, как добавить мастер, который запрашивает у разработчика это значение, а затем настроит это свойство в новом проекте, см. раздел [Пошаговое руководство. Создание элемента проекта столбца сайта с помощью шаблона проекта, часть 2](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md).

3. Нажмите клавишу **F5**.

     Столбец сайта упаковывается и развертывается на сайте SharePoint, который указан в свойстве **URL-адрес сайта** проекта. В веб-браузере откроется страница по умолчанию этого сайта.

    > [!NOTE]
    > Если откроется диалоговое окно **Отладка скрипта отключено** , нажмите кнопку **Да** , чтобы продолжить отладку проекта.

4. В меню **действия сайта** выберите пункт **Параметры сайта**.

5. На странице **Параметры сайта** в списке **коллекции** выберите ссылку **столбцы сайта** .

6. В списке столбцов сайта убедитесь, что группа **пользовательских столбцов** содержит столбец с именем **ситеколумнтест**.

7. Закройте веб-браузер.

## <a name="clean-up-the-development-computer"></a>Очистка компьютера разработчика
 После завершения тестирования проекта удалите шаблон проекта из экспериментального экземпляра Visual Studio.

#### <a name="to-clean-up-the-development-computer"></a>Очистка компьютера разработки

1. В экспериментальном экземпляре Visual Studio в строке меню выберите **инструменты**  >  **расширения и обновления**.

     Появится диалоговое окно **Расширения и обновления**.

2. В списке расширений выберите расширение **столбца сайта** , а затем нажмите кнопку **Удалить** .

3. В появившемся диалоговом окне нажмите кнопку **Да** , чтобы подтвердить удаление расширения.

4. Нажмите кнопку **Закрыть** , чтобы завершить удаление.

5. Закройте оба экземпляра Visual Studio (экспериментальный экземпляр и экземпляр Visual Studio, в котором открыто решение Ситеколумнпрожектитем).

## <a name="next-steps"></a>Дальнейшие действия
 После завершения этого пошагового руководства можно добавить мастер в шаблон проекта. Когда пользователь создает проект столбца сайта, мастер запрашивает у пользователя URL-адрес сайта, который будет использоваться для отладки, а также указывает, является ли новое решение изолированным, и мастер настроит новый проект с этими сведениями. Мастер также собирает сведения о столбце (например, базовый тип и группу, в которой будет перечисляться столбец в коллекции столбцов сайта) и добавляет эти сведения в файл *Elements.xml* в новом проекте. Дополнительные сведения см. в разделе [Пошаговое руководство. Создание элемента проекта столбца сайта с помощью шаблона проекта, часть 2](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md).

## <a name="see-also"></a>См. также раздел

- [Пошаговое руководство. Создание элемента проекта столбца сайта с помощью шаблона проекта, часть 2](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)
- [Определение пользовательских типов элементов проектов SharePoint](../sharepoint/defining-custom-sharepoint-project-item-types.md)
- [Создание шаблонов элементов и проектов для элементов проектов SharePoint](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)
- [Сохранение данных в расширениях системы проектов SharePoint](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md)
- [Связывание пользовательских данных с помощью расширений инструментов SharePoint](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)