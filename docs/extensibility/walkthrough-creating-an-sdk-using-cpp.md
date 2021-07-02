---
title: Пошаговое руководство. Создание пакета SDK с помощью C++ | Документация Майкрософт
description: узнайте, как создать собственный пакет sdk для математической библиотеки C++, упаковать его как расширение Visual Studio, а затем использовать его для создания приложения с помощью этого пошагового руководства.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 36ea793b-3832-41a1-b906-69e680ad5e1d
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 6a52322e575dc201a6bf1648af93d813828e0b17
ms.sourcegitcommit: 8b75524dc544e34d09ef428c3ebbc9b09f14982d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2021
ms.locfileid: "113223011"
---
# <a name="walkthrough-create-an-sdk-using-c"></a>Пошаговое руководство. Создание пакета SDK с помощью C++
в этом пошаговом руководстве показано, как создать собственный пакет sdk для математической библиотеки C++, упаковать пакет sdk как расширение Visual Studio (VSIX), а затем использовать его для создания приложения. Пошаговое руководство делится на следующие этапы.

- [создание собственных и среда выполнения Windows библиотек](../extensibility/walkthrough-creating-an-sdk-using-cpp.md#createClassLibrary)

- [Создание проекта расширения Нативемасвсикс](../extensibility/walkthrough-creating-an-sdk-using-cpp.md#createVSIX)

- [Создание примера приложения, использующего библиотеку классов](../extensibility/walkthrough-creating-an-sdk-using-cpp.md#createSample)

## <a name="prerequisites"></a>Предварительные требования
 Для выполнения этого пошагового руководства необходимо установить пакет SDK для Visual Studio. дополнительные сведения см. в разделе [Visual Studio SDK](../extensibility/visual-studio-sdk.md).

## <a name="to-create-the-native-and-windows-runtime-libraries"></a><a name="createClassLibrary"></a>создание собственных и среда выполнения Windows библиотек

1. В строке меню выберите **Файл** > **Создать** > **Проект**.

2. в списке шаблонов разверните узел **Visual C++**  >  **Windows универсальный**, а затем выберите шаблон **DLL (Windows универсальные приложения)** . В поле **имя** укажите `NativeMath` , а затем нажмите кнопку **ОК** .

3. Обновите *нативемас. h* в соответствии с приведенным ниже кодом.

     :::code language="cpp" source="../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcpp/cpp/nativemath/nativemath.h" id="Snippet1":::

4. Обновите *нативемас. cpp* в соответствии с этим кодом:

     :::code language="cpp" source="../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcpp/cpp/nativemath/nativemath.cpp" id="Snippet2":::

5. в **обозреватель решений** откройте контекстное меню **решения "нативемас"** и выберите **добавить**  >  **новый Project**.

6. в списке шаблонов разверните узел **Visual C++**, а затем выберите шаблон **компонента среда выполнения Windows** . В поле **имя** укажите `NativeMathWRT` , а затем нажмите кнопку **ОК** .

7. Обновите *Class1. h* , чтобы он соответствовал этому коду:

     :::code language="cpp" source="../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcpp/cpp/nativemathwrt/class1.h" id="Snippet3":::

8. Обновите *Class1. cpp* , чтобы он соответствовал этому коду:

     :::code language="cpp" source="../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcpp/cpp/nativemathwrt/class1.cpp" id="Snippet4":::

9. В строке меню последовательно выберите **Сборка** > **Собрать решение**.

## <a name="to-create-the-nativemathvsix-extension-project"></a><a name="createVSIX"></a> Создание проекта расширения Нативемасвсикс

1. в **обозреватель решений** откройте контекстное меню **решения "нативемас"** и выберите **добавить**  >  **новый Project**.

2. в списке шаблонов разверните узел расширяемость **Visual C#**  >  и выберите **VSIX Project**. В поле **имя** укажите **нативемасвсикс**, а затем нажмите кнопку **ОК** .

3. В **Обозреватель решений** откройте контекстное меню **source. extension. vsixmanifest** и выберите пункт **Просмотреть код**.

4. Используйте следующий XML-код, чтобы заменить существующий XML.

    ```xml
    <PackageManifest Version="2.0.0" xmlns="http://schemas.microsoft.com/developer/vsx-schema/2011" xmlns:d="http://schemas.microsoft.com/developer/vsx-schema-design/2011">
      <Metadata>
        <Identity Id="NativeMathVSIX..c6b3cae1-e7e2-4e71-90f6-21017ea0dff7" Version="1.0" Language="en-US" Publisher="MyName" />
        <DisplayName>Native Math SDK</DisplayName>
        <Description>Native Math Library w/ Windows Runtime Additions</Description>
      </Metadata>
      <Installation Scope="Global" AllUsers="true">
        <InstallationTarget Id="Microsoft.ExtensionSDK" TargetPlatformIdentifier="Windows" TargetPlatformVersion="v8.0" SdkName="NativeMathSDK" SdkVersion="1.0" />
      </Installation>
      <Dependencies>
      </Dependencies>
      <Assets>
        <Asset Type="Microsoft.ExtensionSDK" d:Source="File" Path="SDKManifest.xml" />
      </Assets>
    </PackageManifest>
    ```

5. В **Обозреватель решений** откройте контекстное меню проекта **нативемасвсикс** и выберите команду **добавить**  >  **новый элемент**.

6. В списке **элементов Visual C#** разверните узел **данные**, а затем выберите пункт **XML-файл**. В поле **имя** укажите `SDKManifest.xml` , а затем нажмите кнопку **ОК** .

7. Используйте этот XML-код для замены содержимого файла:

    :::code language="xml" source="../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcpp/cpp/nativemathvsix/sdkmanifest.xml" id="Snippet5":::

8. В **Обозреватель решений** в проекте **нативемасвсикс** создайте следующую структуру папок:

    ```xml
    \DesignTime
          \CommonConfiguration
                \Neutral
                      \Include
          \Debug
                \x86
    \Redist
          \Debug
                \x86
    \References
          \CommonConfiguration
                \Neutral
    ```

9. В **Обозреватель решений** откройте контекстное меню **решения "нативемас"**, а затем выберите пункт **Открыть папку в проводнике**.

10. В **проводнике** скопируйте *$SolutionRoot $ \нативемас\нативемас.х*, а затем в **Обозреватель решений** в проекте **нативемасвсикс** вставьте его в папку *$SolutionRoot $ \нативемасвсикс\десигнтиме\коммонконфигуратион\неутрал\инклуде \\* .

     Скопируйте *$SolutionRoot $ \дебуг\нативемас\нативемас.либ* и вставьте его в папку *$SolutionRoot $ \NativeMathVSIX\DesignTime\Debug\x86 \\* .

     Скопируйте *$SolutionRoot $\Debug\NativeMath\NativeMath.dll* и вставьте его в папку *$SolutionRoot $ \NativeMathVSIX\Redist\Debug\x86 \\* .

     Скопируйте *$SolutionRoot $\Debug\NativeMathWRT\NativeMathWRT.dll* и вставьте его в папку *$SolutionRoot $ \NativeMathVSIX\Redist\Debug\x86* .
     Скопируйте *$SolutionRoot $ \дебуг\нативемасврт\нативемасврт.винмд* и вставьте его в папку *$SolutionRoot $ \нативемасвсикс\референцес\коммонконфигуратион\неутрал* .

     Скопируйте *$SolutionRoot $ \дебуг\нативемасврт\нативемасврт.при* и вставьте его в папку *$SolutionRoot $ \нативемасвсикс\референцес\коммонконфигуратион\неутрал* .

11. В папке *$SolutionRoot $ \NativeMathVSIX\DesignTime\Debug\x86 \\* создайте текстовый файл с именем *нативемассдк. props*, а затем вставьте в него следующее содержимое:
   
    ```xml
    <Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
      <PropertyGroup>
        <NativeMathSDKPath>$(FrameworkSDKRoot)\..\..\UAP\v0.8.0.0\ExtensionSDKs\NativeMathSDK\1.0\</NativeMathSDKPath>
        <IncludePath>$(NativeMathSDKPath)DesignTime\CommonConfiguration\Neutral\Include;$(IncludePath)</IncludePath>
        <LibraryPath>$(NativeMathSDKPath)DesignTime\Debug\x86;$(LibraryPath)</LibraryPath>
      </PropertyGroup>
      <ItemDefinitionGroup Condition="'$(Configuration)|$(Platform)'=='Debug|Win32'">
         <Link>
           <AdditionalDependencies>NativeMath.lib;%(AdditionalDependencies)</AdditionalDependencies>
         </Link>
      </ItemDefinitionGroup>
    </Project>
    ```

12. в строке меню выберите **просмотреть**  >  **другие Windows**  >  **свойства окно** (клавиатура: нажмите клавишу **F4** ).

13. В **Обозреватель решений** выберите файл **нативемасврт. winmd** . В окне **Свойства** измените свойство **действие сборки** на **содержимое**, а затем измените значение свойства **включить в VSIX** на **true**.

     Повторите эту процедуру для файла **нативемас. h** .

     Повторите эту процедуру для файла **нативемасврт. PRI** .

     Повторите эту процедуру для файла **нативемас. lib** .

     Повторите эту процедуру для файла **нативемассдк. props** .

14. В **Обозреватель решений** выберите файл **нативемас. h** . В окне **Свойства** измените значение свойства **включить в VSIX** на **true**.

     Повторите эту процедуру для файла **NativeMath.dll** .

     Повторите эту процедуру для файла **NativeMathWRT.dll** .

     Повторите эту процедуру для файла **SDKManifest.xml** .

15. В строке меню последовательно выберите **Сборка** > **Собрать решение**.

16. В **Обозреватель решений** откройте контекстное меню проекта **нативемасвсикс** , а затем выберите пункт **Открыть папку в проводнике**.

17. В **проводнике** перейдите в папку *$SolutionRoot $ \нативемасвсикс\бин\дебуг* , а затем запустите *нативемасвсикс. VSIX* , чтобы начать установку.

18. Нажмите кнопку **установить** , дождитесь завершения установки, а затем откройте Visual Studio.

## <a name="to-create-a-sample-app-that-uses-the-class-library"></a><a name="createSample"></a> Создание примера приложения, использующего библиотеку классов

1. В строке меню выберите **Файл** > **Создать** > **Проект**.

2. в списке шаблонов разверните узел **Visual C++**  >  **Windows универсальный** , а затем выберите **пустое приложение**. В поле **имя** укажите **нативемассдксампле**, а затем нажмите кнопку **ОК** .

3. В **Обозреватель решений** откройте контекстное меню проекта **нативемассдксампле** и выберите команду **добавить**  >  **ссылку**.

4. в диалоговом окне **добавление ссылки** в списке типов ссылок разверните узел **универсальные Windows**, а затем выберите **расширения**. Наконец, установите флажок " **собственный математический пакет SDK** ", а затем нажмите кнопку " **ОК** ".

5. Отображение свойств проекта для Нативемассдксампле.

    Свойства, определенные в *нативемассдк. props* , были применены при добавлении ссылки. чтобы проверить, были ли свойства применены, проверьте свойство **VC++ Directories** **свойств конфигурации** проекта.

6. В **Обозреватель решений** откройте **MainPage. XAML**, а затем используйте следующий XAML для замены его содержимого:

    :::code language="xml" source="../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcppdemoapp/cpp/mainpage.xaml" id="Snippet1":::

7. Обновите *MainPage. XAML. h* , чтобы сопоставить этот код:

    :::code language="cpp" source="../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcppdemoapp/cpp/mainpage.xaml.h" id="Snippet2":::

8. Обновите *MainPage. XAML. cpp* , чтобы сопоставить этот код:

    :::code language="cpp" source="../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcppdemoapp/cpp/mainpage.xaml.cpp" id="Snippet3":::

9. Нажмите клавишу **F5** , чтобы запустить приложение.

10. В приложении введите любые два числа, выберите операцию, а затем нажмите **=** кнопку.

     Появится правильный результат.

    В этом пошаговом руководстве показано, как создать и использовать пакет SDK расширения для вызова [!INCLUDE[wrt](../extensibility/includes/wrt_md.md)] библиотеки и не [!INCLUDE[wrt](../extensibility/includes/wrt_md.md)] библиотеки.

## <a name="next-steps"></a>Дальнейшие действия

## <a name="see-also"></a>См. также раздел
- [Пошаговое руководство. Создание пакета SDK на C# или Visual Basic](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md)
- [Создание пакета средств разработки программного обеспечения](../extensibility/creating-a-software-development-kit.md)
