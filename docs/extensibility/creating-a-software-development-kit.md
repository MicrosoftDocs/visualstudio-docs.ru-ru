---
title: Создание пакета средств разработки программного обеспечения | Документация Майкрософт
description: Узнайте об общей инфраструктуре пакетов SDK и о том, как создать пакет SDK для платформы и пакет SDK для расширений.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 8496afb4-1573-4585-ac67-c3d58b568a12
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: bc762912abdc58b33e49406dd46cadd152f732b6
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105089372"
---
# <a name="create-a-software-development-kit"></a>Создание пакета средств разработки программного обеспечения

Пакет средств разработки программного обеспечения (SDK) — это коллекция интерфейсов API, на которые можно ссылаться как на один элемент в Visual Studio. В диалоговом окне **Диспетчер ссылок** перечислены все пакеты SDK, относящиеся к проекту. При добавлении пакета SDK в проект интерфейсы API доступны в Visual Studio.

Существует два типа пакетов SDK:

- Пакеты SDK для платформы являются обязательными компонентами для разработки приложений для платформы. Например, [!INCLUDE[win81](../debugger/includes/win81_md.md)] пакет SDK необходим для разработки [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] приложений.

- Пакеты SDK расширения — это дополнительные компоненты, которые расширяют платформу, но не являются обязательными для разработки приложений для этой платформы.

В следующих разделах описывается общая инфраструктура пакетов SDK и создание пакета SDK для платформы и пакета SDK для расширений.

## <a name="platform-sdks"></a>Пакеты SDK для платформ

Для разработки приложений для платформы требуются пакеты SDK для платформы. Например, [!INCLUDE[win81](../debugger/includes/win81_md.md)] пакет SDK необходим для разработки приложений для [!INCLUDE[win81](../debugger/includes/win81_md.md)] .

### <a name="installation"></a>Установка

Все пакеты SDK для платформы будут установлены в пакетах *SDK для HKLM\Software\Microsoft\Microsoft \\ [ТПИ] \V [ТПВ] \\ @InstallationFolder = [корень пакета SDK]*. Соответственно, [!INCLUDE[win81](../debugger/includes/win81_md.md)] пакет SDK устанавливается на сайте *HKLM\Software\Microsoft\Microsoft SDKs\Windows\v8.1*.

### <a name="layout"></a>Layout

Пакеты SDK для платформы имеют следующий вид:

```
\[InstallationFolder root]
            SDKManifest.xml
            \References
                  \[config]
                        \[arch]
            \DesignTime
                  \[config]
                        \[arch]
```

| Узел | Описание |
|------------------------| - |
| Папка *ссылок* | Содержит двоичные файлы, которые содержат интерфейсы API, которые можно закодировать. К ним могут относиться файлы метаданных Windows (WinMD) или сборки. |
| Папка *DesignTime* | Содержит файлы, которые необходимы только во время предварительного запуска или отладки. К ним могут относиться XML-документы, библиотеки, заголовки, двоичные файлы времени разработки, артефакты MSBuild и т. д.<br /><br /> Документы XML, в идеале, будут помещены в папку *\DesignTime)* , но документы XML для ссылок будут по-прежнему размещаться вместе с файлом ссылки в Visual Studio. Например, XML-документ для ссылки <em>\референцес \\ [config] \\ [Arch] \sample.dll</em> будет *\референцес \\ [config] \\ [Arch] \sample.xml*, а локализованная версия этого документа будет *\референцес \\ [config] \\ [Arch] \\ [locale] \sample.xml*. |
| Папка *конфигурации* | Может быть только три папки: *Debug*, *Retail* и *CommonConfiguration*. Авторы пакетов SDK могут размещать свои файлы в папке *CommonConfiguration* , если необходимо использовать один и тот же набор файлов SDK независимо от конфигурации, которую будет ориентировать потребитель пакета SDK. |
| Папка *архитектуры* | Может существовать любая поддерживаемая папка *архитектуры* . Visual Studio поддерживает следующие архитектуры: x86, x64, ARM и Neutral. Примечание. Win32 сопоставляется с платформой x86, а AnyCPU сопоставляется с нейтральным.<br /><br /> MSBuild ищет только в *\коммонконфигуратион\неутрал* для пакетов SDK для платформы. |
| *SDKManifest.xml* | В этом файле описывается, как Visual Studio должен использовать пакет SDK. Просмотрите манифест пакета SDK для [!INCLUDE[win81](../debugger/includes/win81_md.md)] :<br /><br /> `<FileList             DisplayName = "Windows"             PlatformIdentity = "Windows, version=8.1"             TargetFramework = ".NET for Windows Store apps, version=v4.5.1; .NET Framework, version=v4.5.1"             MinVSVersion = "14.0">              <File Reference = "Windows.winmd">                <ToolboxItems VSCategory = "Toolbox.Default" />             </File> </FileList>`<br /><br /> **Отображаемое имя:** Значение, которое обозреватель объектов отображает в списке просмотра.<br /><br /> **Платформидентити:** Наличие этого атрибута указывает Visual Studio и MSBuild, что пакет SDK является Platform SDK, а ссылки, добавленные из нее, не должны копироваться локально.<br /><br /> **TargetFramework:** Этот атрибут используется в Visual Studio, чтобы гарантировать, что только проекты, предназначенные для тех же платформ, которые указаны в значении этого атрибута, могут использовать пакет SDK.<br /><br /> **MinVSVersion:** Этот атрибут используется в Visual Studio для использования только пакетов SDK, которые применяются к нему.<br /><br /> **Справочные материалы:** Этот атрибут должен быть указан только для тех ссылок, которые содержат элементы управления. Сведения о том, как указать, содержит ли ссылка элементы управления, см. ниже. |

## <a name="extension-sdks"></a>Пакеты SDK расширения

В следующих разделах описаны действия, которые необходимо выполнить для развертывания пакета SDK расширения.

### <a name="installation"></a>Установка

Пакеты SDK расширения можно установить для конкретного пользователя или для всех пользователей без указания раздела реестра. Чтобы установить пакет SDK для всех пользователей, используйте следующий путь:

*% Program Files%\Microsoft SDK \<target platform\> \v<номер версии платформы \> \екстенсионсдкс*

Для установки конкретного пользователя используйте следующий путь:

*%Усерпрофиле%\аппдата\локал\микрософт пакеты SDK \<target platform\> \v<номер версии платформы \> \екстенсионсдкс*

Если вы хотите использовать другое расположение, необходимо выполнить одно из двух действий.

1. Укажите его в разделе реестра:

     **HKLM\Software\Microsoft\Microsoft пакеты SDK \<target platform> \v<номер версии платформы \> \екстенсионсдкс\<SDKName>\<SDKVersion>**\

     и добавьте подраздел (по умолчанию) со значением `<path to SDK><SDKName><SDKVersion>` .

2. Добавьте свойство MSBuild `SDKReferenceDirectoryRoot` в файл проекта. Значение этого свойства представляет собой разделенный точками с запятой список каталогов, в которых находятся пакеты SDK расширений, на которые вы хотите ссылаться.

### <a name="installation-layout"></a>Макет установки

Пакеты SDK расширения имеют следующий макет установки:

```
\<ExtensionSDKs root>
           \<SDKName>
                 \<SDKVersion>
                        SDKManifest.xml
                        \References
                              \<config>
                                    \<arch>
                        \Redist
                              \<config>
                                    \<arch>
                        \DesignTime
                               \<config>
                                     \<arch>

```

1. \\<Сдкнаме \> \\<сдкверсион \> : имя и версия пакета SDK расширения являются производными от имен соответствующих папок в пути к корню пакета SDK. MSBuild использует это удостоверение для поиска пакета SDK на диске, и Visual Studio отображает это удостоверение в окне " **Свойства** " и в диалоговом окне " **Диспетчер ссылок** ".

2. Папка *ссылок* : двоичные файлы, содержащие API-интерфейсы. Это могут быть файлы метаданных Windows (WinMD) или сборки.

3. Папка *Redist* : файлы, необходимые для выполнения и отладки, которые должны быть упакованы в состав приложения пользователя. Все двоичные файлы должны размещаться под *\redist \\<config \> \\<Arch \>*, а двоичные имена должны иметь следующий формат для обеспечения уникальности: *]* \<company> .. \<product> \<purpose> . \<extension> <em>. Например, * Microsoft.Cpp.Build.dll</em>. Все файлы с именами, которые могут конфликтовать с именами других пакетов SDK (например, файлы JavaScript, CSS, PRI, XAML, PNG и JPG), должны размещаться под <em>\redist \\<config \> \\<Arch \> \\<сдкнаме \> \* , за исключением файлов, связанных с элементами управления XAML. Эти файлы должны находиться под названием * \Redist \\<config \> \\<Arch \> \\<\> \\ ComponentName</em>.

4. Папка *DesignTime* . файлы, которые необходимы только во время предварительной установки или отладки и не должны упаковываться как часть приложения пользователя. Это могут быть XML-документы, библиотеки, заголовки, двоичные файлы времени разработки, артефакты MSBuild и т. д. Любой пакет SDK, предназначенный для использования в собственном проекте, должен иметь файл *сдкнаме. props* . Ниже показан пример файла этого типа.

   ```xml
   <?xml version="1.0" encoding="utf-8"?>
   <Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
     <PropertyGroup>
       <ExecutablePath>C:\Temp\ExecutablePath;$(ExecutablePath)</ExecutablePath>
       <IncludePath>$(FrameworkSDKRoot)\..\v8.1\ExtensionSDKs\cppimagingsdk\1.0\DesignTime\CommonConfiguration\Neutral\include;$(IncludePath)</IncludePath>
       <AssemblyReferencePath>C:\Temp\AssemblyReferencePath;(AssemblyReferencePath)</AssemblyReferencePath>
       <LibraryPath>$(FrameworkSDKRoot)\..\v8.1\ExtensionSDKs\cppimagingsdk\1.0\DesignTime\Debug\ARM;$(LibraryPath)</LibraryPath>
       <SourcePath>C:\Temp\SourcePath\X64;$(SourcePath)</SourcePath>
       <ExcludePath>C:\Temp\ExcludePath\X64;$(ExcludePath)</ExcludePath>
       <_PropertySheetDisplayName>DevILSDK, 1.0</_PropertySheetDisplayName>
     </PropertyGroup>
   </Project>

   ```

    Справочные документы XML помещаются вместе с файлом ссылки. Например, XML-документ ссылки для *\референцес \\<config \> \\<Arch \>\sample.dll* сборка — *\референцес \\<config \> \\<Arch \>\sample.xml*, а локализованная версия документа — *\референцес \\<config \> \\<Arch<\> \\ языкового стандарта \>\sample.xml*.

5. Папка *конфигурации* : три вложенных папки: *Debug*, *Retail* и *CommonConfiguration*. Авторы пакета SDK могут поместить свои файлы в *CommonConfiguration* , когда необходимо использовать один и тот же набор файлов SDK, независимо от конфигурации, для которой предназначен потребитель SDK.

6. Папка *архитектуры* : поддерживаются следующие архитектуры: x86, x64, ARM, Neutral. Win32 сопоставляется с платформой x86, а AnyCPU сопоставляется с нейтральным.

### <a name="sdkmanifestxml"></a>SDKManifest.xml

В файле *SDKManifest.xml* описывается, как Visual Studio должен использовать пакет SDK. Ниже представлен пример такого кода:

```
<FileList>
DisplayName = "My SDK"
ProductFamilyName = "My SDKs"
TargetFramework = ".NETCore, version=v4.5.1; .NETFramework, version=v4.5.1"
MinVSVersion = "14.0"
MaxPlatformVersion = "8.1"
AppliesTo = "WindowsAppContainer + WindowsXAML"
SupportPrefer32Bit = "True"
SupportedArchitectures = "x86;x64;ARM"
SupportsMultipleVersions = "Error"
CopyRedistToSubDirectory = "."
DependsOn = "SDKB, version=2.0"
MoreInfo = "https://msdn.microsoft.com/MySDK">
<File Reference = "MySDK.Sprint.winmd" Implementation = "XNASprintImpl.dll">
<Registration Type = "Flipper" Implementation = "XNASprintFlipperImpl.dll" />
<Registration Type = "Flexer" Implementation = "XNASprintFlexerImpl.dll" />
<ToolboxItems VSCategory = "Toolbox.Default" />
</File>
</FileList>
```

В следующем списке приводятся элементы файла:

1. DisplayName: значение, которое отображается в диспетчере ссылок, обозреватель решений, обозревателе объектов и других расположениях в пользовательском интерфейсе для Visual Studio.

2. Продуктфамилинаме: общее название продукта пакета SDK. Например, [!INCLUDE[winjs_long](../debugger/includes/winjs_long_md.md)] пакет SDK называется «Microsoft. WinJS. 1.0» и «Microsoft. WinJS. 2.0», который относится к семейству продуктов пакета SDK «Microsoft. WinJS». Этот атрибут позволяет Visual Studio и MSBuild сделать это подключение. Если этот атрибут не существует, в качестве имени семейства продуктов используется имя пакета SDK.

3. FrameworkIdentity: определяет зависимость от одной или нескольких библиотек компонентов Windows. Значение этого атрибута помещается в манифест приложения для использования. Этот атрибут применим только к библиотекам компонентов Windows.

4. TargetFramework: указывает пакеты SDK, доступные в диспетчере ссылок и на панели элементов. Это разделенный точками с запятой список моникеров целевой платформы, например "платформа .NET Framework, Version = v 2.0; платформа .NET Framework, Version = v 4.5.1". Если указаны несколько версий одной и той же целевой платформы, Диспетчер ссылок использует самую раннюю версию для фильтрации. Например, если задано значение "платформа .NET Framework, Version = v 2.0; платформа .NET Framework, версия = v 4.5.1", то Диспетчер ссылок будет использовать "платформа .NET Framework, Version = v 2.0". Если указан определенный профиль целевой платформы, Диспетчер ссылок будет использовать только этот профиль для целей фильтрации. Например, если задано значение "Silverlight, Version = v 4.0, профиль = WindowsPhone", Диспетчер ссылок будет фильтровать только профиль Windows Phone; проект, предназначенный для полной платформы Silverlight 4,0, не увидит пакет SDK в диспетчере ссылок.

5. MinVSVersion: Минимальная версия Visual Studio.

6. Максплатформверсон: Максимальная версия целевой платформы должна использоваться для указания версий платформы, на которых ваш пакет SDK расширения не будет работать. Например, на пакет среды выполнения Microsoft Visual C++ версии 11.0 должны ссылаться только проекты Windows 8. Таким же Максплатформверсион проекта Windows 8 является 8,0. Это означает, что диспетчер ссылок фильтрует пакет среды выполнения Microsoft Visual C++ для Windows 8.1 проекта, а MSBuild выдает ошибку, когда [!INCLUDE[win81](../debugger/includes/win81_md.md)] проект ссылается на него. Примечание. Этот элемент поддерживается начиная с [!INCLUDE[vs_dev12](../extensibility/includes/vs_dev12_md.md)] .

7. AppliesTo: указывает пакеты SDK, доступные в диспетчере ссылок, путем указания применимых типов проектов Visual Studio. Распознаются девять значений: Виндовсаппконтаинер, VisualC, VB, CSharp, Виндовсксамл, JavaScript, Managed и Native. Автор пакета SDK может использовать и ("+") или ("&#124;"), а не ("!"). операторы для указания области применения типов проектов, применимых к пакету SDK.

    Виндовсаппконтаинер определяет проекты для [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] приложений.

8. SupportPrefer32Bit: поддерживаются значения "true" и "false". Значение по умолчанию — true. Если задано значение "false", MSBuild возвращает ошибку для [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] проектов (или предупреждение для проектов для настольных систем), если в проекте, который ссылается на пакет SDK, включен Prefer32Bit. Дополнительные сведения о Prefer32Bit см. в разделе [Страница "сборка", конструктор проектов (C#)](../ide/reference/build-page-project-designer-csharp.md) или [Страница "компиляция" в конструкторе проектов (Visual Basic)](../ide/reference/compile-page-project-designer-visual-basic.md).

9. Суппортедарчитектурес: разделенный точками с запятой список архитектур, поддерживаемых пакетом SDK. MSBuild выводит предупреждение, если целевая архитектура пакета SDK в проекте, используемом для использования, не поддерживается. Если этот атрибут не указан, MSBuild никогда не отображает этот тип предупреждения.

10. Суппортсмултиплеверсионс: Если для этого атрибута задано значение " **Ошибка** " или " **предупреждение**", MSBuild указывает, что один и тот же проект не может ссылаться на несколько версий одного семейства пакетов SDK. Если этот атрибут не существует или имеет значение **allow**, MSBuild не отображает этот тип ошибки или предупреждения.

11. AppX: указывает путь к пакетам приложений для библиотеки компонентов Windows на диске. Это значение передается компоненту регистрации библиотеки компонентов Windows во время локальной отладки. Для имени файла используется соглашение об именовании *\<Company> . \<Product> . \<Architecture> . \<Configuration> \<Version> . appx*. Конфигурация и архитектура являются необязательными в имени атрибута и значении атрибута, если они не применяются к библиотеке компонентов Windows. Это значение применимо только к библиотекам компонентов Windows.

12. Копиредисттосубдиректори: указывает, куда должны копироваться файлы в папке *\Redist* относительно корневого каталога пакета приложения (т. е. **расположения пакета** , выбранного в мастере **создания пакета приложения** ) и корня макета среды выполнения. Расположением по умолчанию является корень пакета приложения и раскладка **F5** .

13. DependsOn: список удостоверений SDK, определяющих пакеты SDK, от которых зависит этот пакет SDK. Этот атрибут отображается в области сведений диспетчера ссылок.

14. Мореинфо: URL-адрес страницы, предоставляющей справку и дополнительные сведения. Это значение используется в ссылке "Дополнительные сведения" в правой области диспетчера ссылок.

15. Тип регистрации: указывает регистрацию WinMD в манифесте приложения и требуется для собственного WinMD-файла, который имеет библиотеку DLL реализации аналога.

16. Ссылка на файл: задается только для тех ссылок, которые содержат элементы управления или являются собственными WinMD-файлами. Сведения о том, как указать, содержит ли ссылка элементы управления, см. [в разделе Указание расположения элементов панели элементов](#ToolboxItems) ниже.

## <a name="specify-the-location-of-toolbox-items"></a><a name="ToolboxItems"></a> Укажите расположение элементов панели элементов

Элемент **тулбокситемс** схемы *SDKManifest.xml* указывает категорию и расположение элементов панели элементов в пакетах SDK для платформы и расширений. В следующих примерах показано, как указать различные расположения. Это относится либо к WinMD, либо к ссылкам DLL.

1. Располагать элементы управления в категории панели элементов по умолчанию.

    ```xml
    <File Reference = "sample.winmd">
        <ToolboxItems VSCategory = "Toolbox.Default"/>
    </File>
    ```

2. Разместите элементы управления под определенным именем категории.

    ```xml
    <File Reference = "sample.winmd">
        <ToolboxItems VSCategory= "MyCategoryName"/>
    </File>
    ```

3. Разместите элементы управления под определенными именами категорий.

    ```xml
    <File Reference = "sample.winmd">
        <ToolboxItems VSCategory = "Graph">
        <ToolboxItems/>
        <ToolboxItems VSCategory = "Data">
        <ToolboxItems />
    </File>
    ```

4. Разместите элементы управления под разными именами категорий в Blend и Visual Studio.

    ```xml
    // Blend accepts a slightly different structure for the category name because it allows a path rather than a single category.
    <File Reference = "sample.winmd">
        <ToolboxItems VSCategory = "Graph" BlendCategory = "Controls/sample/Graph">
        <ToolboxItems />
    </File>
    ```

5. Перечисление конкретных элементов управления по-разному в Blend и Visual Studio.

    ```xml
    <File Reference = "sample.winmd">
        <ToolboxItems VSCategory = "Graph">
        <ToolboxItems/>
        <ToolboxItems BlendCategory = "Controls/sample/Graph">
        <ToolboxItems/>
    </File>
    ```

6. Перечислить определенные элементы управления и поместить их в общий путь Visual Studio или только в группу "все элементы управления".

    ```xml
    <File Reference = "sample.winmd">
        <ToolboxItems VSCategory = "Toolbox.Common">
        <ToolboxItems />
        <ToolboxItems VSCategory = "Toolbox.All">
        <ToolboxItems />
    </File>
    ```

7. Перечисление конкретных элементов управления и отображение только определенного набора в Чусеитемс без их включения в панель элементов.

    ```xml
    <File Reference = "sample.winmd">
        <ToolboxItems VSCategory = "Toolbox.ChooseItemsOnly">
        <ToolboxItems />
    </File>
    ```

## <a name="see-also"></a>См. также

- [Пошаговое руководство. Создание пакета SDK с помощью C++](../extensibility/walkthrough-creating-an-sdk-using-cpp.md)
- [Пошаговое руководство. Создание пакета SDK на C# или Visual Basic](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md)
- [Управление ссылками в проекте](../ide/managing-references-in-a-project.md)
