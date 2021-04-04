---
title: Пошаговое руководство. Создание пакета SDK с помощью C++ | Документация Майкрософт
description: Узнайте, как создать собственный пакет SDK для математической библиотеки C++, упаковать его как расширение Visual Studio, а затем использовать его для создания приложения с помощью этого пошагового руководства.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 36ea793b-3832-41a1-b906-69e680ad5e1d
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 743759896bf1de104825825d450be081ab2cc666
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/02/2021
ms.locfileid: "106217428"
---
# <a name="walkthrough-create-an-sdk-using-c"></a>Пошаговое руководство. Создание пакета SDK с помощью C++
В этом пошаговом руководстве показано, как создать собственный пакет SDK для математической библиотеки C++, упаковать пакет SDK как расширение Visual Studio (VSIX) и использовать его для создания приложения. Пошаговое руководство делится на следующие этапы.

- [Создание собственных и среда выполнения Windows библиотек](../extensibility/walkthrough-creating-an-sdk-using-cpp.md#createClassLibrary)

- [Создание проекта расширения Нативемасвсикс](../extensibility/walkthrough-creating-an-sdk-using-cpp.md#createVSIX)

- [Создание примера приложения, использующего библиотеку классов](../extensibility/walkthrough-creating-an-sdk-using-cpp.md#createSample)

## <a name="prerequisites"></a>Предварительные требования
 Для выполнения этого пошагового руководства необходимо установить пакет SDK для Visual Studio. Дополнительные сведения см. в разделе [пакет SDK для Visual Studio](../extensibility/visual-studio-sdk.md).

## <a name="to-create-the-native-and-windows-runtime-libraries"></a><a name="createClassLibrary"></a> Создание собственных и среда выполнения Windows библиотек

1. В строке меню выберите **Файл** > **Создать** > **Проект**.

2. В списке шаблонов разверните **Visual C++**  >  **Windows Universal**, а затем выберите шаблон **Библиотека DLL (универсальные приложения Windows)** . В поле **имя** укажите `NativeMath` , а затем нажмите кнопку **ОК** .

3. Обновите *нативемас. h* в соответствии с приведенным ниже кодом.

     :::code language="cpp" source="../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcpp/cpp/nativemath/nativemath.h" id="Snippet1":::

4. Обновите *нативемас. cpp* в соответствии с этим кодом:

     :::code language="cpp" source="../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcpp/cpp/nativemath/nativemath.cpp" id="Snippet2":::

5. В **Обозреватель решений** откройте контекстное меню **решения "нативемас"** и выберите команду **добавить**  >  **Новый проект**.

6. В списке шаблонов разверните узел **Visual C++**, а затем выберите шаблон **компонента Среда выполнения Windows** . В поле **имя** укажите `NativeMathWRT` , а затем нажмите кнопку **ОК** .

7. Обновите *Class1. h* , чтобы он соответствовал этому коду:

     :::code language="cpp" source="../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcpp/cpp/nativemathwrt/class1.h" id="Snippet3":::

8. Обновите *Class1. cpp* , чтобы он соответствовал этому коду:

     :::code language="cpp" source="../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcpp/cpp/nativemathwrt/class1.cpp" id="Snippet4":::

9. В строке меню последовательно выберите **Сборка** > **Собрать решение**.

## <a name="to-create-the-nativemathvsix-extension-project"></a><a name="createVSIX"></a> Создание проекта расширения Нативемасвсикс

1. В **Обозреватель решений** откройте контекстное меню **решения "нативемас"** и выберите команду **добавить**  >  **Новый проект**.

2. В списке шаблонов разверните узел расширяемость **Visual C#**  >  и выберите **проект VSIX**. В поле **имя** укажите **нативемасвсикс**, а затем нажмите кнопку **ОК** .

3. В **Обозреватель решений** откройте контекстное меню **source. extension. vsixmanifest** и выберите пункт **Просмотреть код**.

4. Используйте следующий XML-код, чтобы заменить существующий XML.

    :::code language="xml" source="../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcpp/cpp/nativemathvsix/source.extension.vsixmanifest" id="Snippet6":::


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

12. В строке меню выберите **Просмотреть**  >  **другие**  >  **окна свойств** Windows (клавиатура: нажмите клавишу **F4** ).

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

2. В списке шаблонов разверните узел **Visual C++**  >  **Windows Universal** , а затем выберите **пустое приложение**. В поле **имя** укажите **нативемассдксампле**, а затем нажмите кнопку **ОК** .

3. В **Обозреватель решений** откройте контекстное меню проекта **нативемассдксампле** и выберите команду **добавить**  >  **ссылку**.

4. В диалоговом окне **Добавление ссылки** в списке типов ссылок разверните узел **универсальные приложения Windows** и выберите **расширения**. Наконец, установите флажок " **собственный математический пакет SDK** ", а затем нажмите кнопку " **ОК** ".

5. Отображение свойств проекта для Нативемассдксампле.

    Свойства, определенные в *нативемассдк. props* , были применены при добавлении ссылки. Чтобы проверить, были ли свойства применены, проверьте свойство **каталоги VC + +** в **свойствах конфигурации** проекта.

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
