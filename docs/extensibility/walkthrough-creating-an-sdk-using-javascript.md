---
title: Пошаговое руководство. Создание пакета SDK с помощью JavaScript | Документация Майкрософт
description: Узнайте, как использовать JavaScript для создания простого математического пакета SDK в качестве расширения Visual Studio с помощью этого пошагового руководства.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: a8c89d5d-5b78-4435-817f-c5f25ca6d715
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 3b9a3d9e84731fe0c2526b69f60cdda1b1487583
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105080389"
---
# <a name="walkthrough-create-an-sdk-using-javascript"></a>Пошаговое руководство. Создание пакета SDK с помощью JavaScript
В этом пошаговом руководстве описывается использование JavaScript для создания простого математического пакета SDK в качестве расширения Visual Studio (VSIX).  Пошаговое руководство делится на следующие части:

- [Создание проекта пакета SDK для расширения Симплемасвсикс](../extensibility/walkthrough-creating-an-sdk-using-javascript.md#createSimpleMathVSIX)

- [Создание примера приложения, использующего пакет SDK](../extensibility/walkthrough-creating-an-sdk-using-javascript.md#createSampleApp)

  Для JavaScript тип проекта библиотеки классов отсутствует. В этом пошаговом руководстве файл примера *arithmetic.js* создается непосредственно в проекте VSIX. На практике рекомендуется сначала создать и протестировать файлы JavaScript и CSS как приложение для Магазина Windows, например с помощью шаблона **пустое приложение** , прежде чем добавлять их в проект VSIX.

## <a name="prerequisites"></a>Предварительные требования
 Для выполнения этого пошагового руководства необходимо установить пакет SDK для Visual Studio. Дополнительные сведения см. в разделе [пакет SDK для Visual Studio](../extensibility/visual-studio-sdk.md).

## <a name="to-create-the-simplemathvsix-extension-sdk-project"></a><a name="createSimpleMathVSIX"></a> Создание проекта пакета SDK для расширения Симплемасвсикс

1. В строке меню выберите **Файл** > **Создать** > **Проект**.

2. В списке категорий шаблонов в разделе **Visual C#** выберите **расширяемость**, а затем выберите шаблон **проекта VSIX** .

3. В текстовом поле **имя** укажите `SimpleMathVSIX` и нажмите кнопку **ОК** .

4. Если откроется **Мастер пакетов Visual Studio** , нажмите кнопку **Далее** на странице **Приветствие** , а затем на **странице 1 из 7** нажмите кнопку **Готово** .

     Несмотря на то, что **конструктор манифеста** открывается, это пошаговое руководство будет упрощено путем непосредственного изменения файла манифеста.

5. В **Обозреватель решений** откройте контекстное меню для файла **source. extension. vsixmanifest** и выберите пункт **Просмотреть код**. Используйте этот код для замены существующего содержимого в файле.

    ```xml
    <?xml version="1.0" encoding="utf-8"?>
    <PackageManifest Version="2.0.0" xmlns="http://schemas.microsoft.com/developer/vsx-schema/2011" xmlns:d="http://schemas.microsoft.com/developer/vsx-schema-design/2011">
      <Metadata>
        <Identity Id="SimpleMathVSIX" Version="1.0" Language="en-US" Publisher="myname" />
        <DisplayName>Simple Math</DisplayName>
        <Description>Does basic arithmetic calculations.</Description>
      </Metadata>
      <Installation Scope="Global" AllUsers="true">
        <InstallationTarget Id="Microsoft.ExtensionSDK" TargetPlatformIdentifier="Windows" TargetPlatformVersion="v8.0" SdkName="SimpleMath" SdkVersion="1.0" />
      </Installation>
      <Dependencies>
        <Dependency Id="Microsoft.Framework.NDP" DisplayName="Microsoft .NET Framework" d:Source="Manual" Version="4.5" />
      </Dependencies>
      <Assets>
        <Asset Type="Microsoft.ExtensionSDK" d:Source="File" Path="SDKManifest.xml" />
      </Assets>
    </PackageManifest>
    ```

6. В **Обозреватель решений** откройте контекстное меню проекта **симплемасвсикс** и выберите команду **добавить**  >  **новый элемент**.

7. В категории **данные** выберите **XML-файл**, укажите имя файла `SDKManifest.xml` и нажмите кнопку **Добавить** .

8. В **Обозреватель решений** откройте контекстное меню для **SDKManifest.xml** файла и нажмите кнопку **Открыть** , чтобы отобразить файл в **редакторе XML**.

9. Добавьте следующий код в файл **SDKManifest.xml** .

    ```xml
    <?xml version="1.0" encoding="utf-8" ?>
    <FileList
      DisplayName="Simple Math"
      MinVSVersion="14.0"
      AppliesTo="JavaScript+WindowsAppContainer"
      SupportsMultipleVersions="Error"
      MoreInfo="https://msdn.microsoft.com/">

      <!-- JS -->
      <File Content="js\arithmetic.js" />
    </FileList>

    ```

10. В **Обозреватель решений** в контекстном меню файла **SDKManifest.xml** выберите пункт **Свойства**.

11. В окне **Свойства** задайте для свойства **включить в VSIX** значение **true**.

12. В **Обозреватель решений** в контекстном меню проекта **симплемасвсикс** выберите **добавить**  >  **новую папку**, а затем назовите папку `Redist` .

13. Добавьте вложенные папки в файле Redist, чтобы создать эту структуру папок:

     *\редист\коммонконфигуратион\неутрал\симплемас\жс\\*

14. В контекстном меню папки **\js \\** выберите **добавить**  >  **новый элемент**.

15. В разделе **элементы Visual C#** выберите категорию **веб** , а затем выберите элемент **файл JavaScript** . Присвойте файлу имя `arithmetic.js` , а затем нажмите кнопку **Добавить** .

16. Вставьте следующий код в *arithmetic.js*:

    ```csharp
    (function (global) {
        "use strict";
        global.Arithmetic = {
            add: function (firstNumber, secondNumber) {
                return firstNumber + secondNumber;
            },

            subtract: function (firstNumber, secondNumber) {
                return firstNumber - secondNumber;
            },

            multiply: function (firstNumber, secondNumber) {
                return firstNumber * secondNumber;
            },

            divide: function (firstNumber, secondNumber) {
                return firstNumber / secondNumber;
            }
        };
    })(this);

    ```

17. В **Обозреватель решений** в контекстном меню файла **arithmetic.js** выберите пункт **Свойства**. Внесите следующие изменения в свойства:

    - Присвойте свойству **включить в VSIX** значение **true**.

    - Для свойства **Копировать в выходной каталог** установите значение **всегда копировать**.

18. В **Обозреватель решений** в контекстном меню проекта **симплемасвсикс** выберите **Сборка**.

19. После успешного завершения сборки в контекстном меню проекта выберите **Открыть папку в проводнике**. Перейдите в **\bin\Debug \\** и запустите, `SimpleMathVSIX.vsix` чтобы установить его.

20. Нажмите кнопку **установить** и позвольте завершить установку.

21. Перезапустите Visual Studio.

## <a name="to-create-a-sample-app-that-uses-the-sdk"></a><a name="createSampleApp"></a> Создание примера приложения, использующего пакет SDK

1. В строке меню выберите **Файл** > **Создать** > **Проект**.

2. В списке категорий шаблонов в разделе **JavaScript** выберите **Магазин Windows** и выберите шаблон **пустое приложение** .

3. В поле **имя** укажите `ArithmeticUI` . Нажмите кнопку **ОК** .

4. В **Обозреватель решений** откройте контекстное меню проекта **арисметикуи** и выберите команду **добавить**  >  **ссылку**.

5. В разделе **Windows** выберите **расширения** и обратите внимание, что отображается **простая математическая формула** .

6. Установите флажок **простые математические** знаки, а затем нажмите кнопку **ОК** .

7. В **Обозреватель решений** в разделе **ссылки** Обратите внимание на то, что отображается простая ссылка на **математический символ** . Разверните его и обратите внимание на папку **\js \\** , которая содержит **arithmetic.js**. Вы можете открыть **arithmetic.js** , чтобы убедиться, что исходный код был установлен.

8. Используйте следующий код, чтобы заменить содержимое *default.htm*.

   ```html
   <!DOCTYPE html>
   <html>
   <head>
       <meta charset="utf-8" />
       <title>ArithmeticUI</title>

       <!-- WinJS references -->
       <link href="//Microsoft.WinJS.1.0/css/ui-dark.css" rel="stylesheet" />
       <script src="//Microsoft.WinJS.1.0/js/base.js"></script>
       <script src="//Microsoft.WinJS.1.0/js/ui.js"></script>

       <!-- ArithmeticUI references -->
       <link href="/css/default.css" rel="stylesheet" />
       <script src="/js/default.js"></script>
       <script src="/SimpleMath/js/arithmetic.js"></script>
   </head>
   <body>
       <form>
       <div id="calculator" class="ms-grid">
           <input name="firstNumber" id="firstNumber" type="number" step="any">
           <div id="operators">
               <button class="operator" type="button">+</button>
               <button class="operator" type="button">-</button>
               <button class="operator" type="button">*</button>
               <button class="operator" type="button">/</button>
           </div>
           <input id="secondNumber" type="number">
           <button class="calculate" type="button">=</button>
           <input id="result" type="number" name="result" disabled="" readonly="">
       </div>
       </form>
   </body>
   </html>
   ```

9. Используйте следующий код, чтобы заменить содержимое *\js\default.js*.

    ```csharp
    (function () {
        "use strict";

        var app = WinJS.Application;
        var operation = null;

        function calculateResult() {
            var firstNumber = parseFloat(document.querySelector("#firstNumber").value),
                secondNumber = parseFloat(document.querySelector("#secondNumber").value),
                result = 0;

            if (isNaN(firstNumber) || isNaN(secondNumber)) {
                result = 0;
            }
            else {
                switch (operation) {
                    case "+":
                        result = Arithmetic.add(firstNumber, secondNumber);
                        break;
                    case "-":
                        result = Arithmetic.subtract(firstNumber, secondNumber);
                        break;
                    case "*":
                        result = Arithmetic.multiply(firstNumber, secondNumber);
                        break;
                    case "/":
                        result = Arithmetic.divide(firstNumber, secondNumber);
                        break;
                    default:
                }
            }
            document.querySelector("#result").value = result.toString();
        }

        app.onactivated = function (args) {
            document.querySelector("#calculator").addEventListener("click", function (event) {
                if (event.target.tagName.toLowerCase() === "button") {
                    switch (event.target.className) {
                        case "operator":
                            operation = event.target.innerText;
                            break;
                        case "calculate":
                            calculateResult();
                            break;
                        default:
                            break;
                    }
                }
            });
        };

        app.start();
    })();
    ```

10. Замените содержимое *\ксс\дефаулт.КСС* следующим кодом:

    ```xml
    form {
        display: -ms-grid;
        -ms-grid-rows: 1fr auto 1fr;
        -ms-grid-columns: 1fr auto 1fr;
        height: 100%;
        width: 100%;
    }

    button, input[type=number] {
        margin-right: 5px;
        -ms-grid-row-align: center;
    }

    #calculator {
        -ms-grid-column: 2;
        -ms-grid-row: 2;
        display: -ms-grid;
        -ms-grid-rows: 1fr;
        -ms-grid-columns: auto min-content auto auto auto;
    }

    .ms-grid input {
        width: 5em;
    }

    #firstNumber {
        -ms-grid-column: 1;
        -ms-grid-row-align: center;
    }

    #operators {
        -ms-grid-column: 2;
        -ms-grid-row-align: center;
    }

        #operators button.operator {
            margin-bottom: 5px;
            height: 40px;
        }

    #secondNumber {
        -ms-grid-column: 3;
    }

    button.calculate {
        -ms-grid-column: 4;
        -ms-grid-row-align: center;
        height: 40px;
    }

    #result {
        -ms-grid-column: 5;
    }

    ```

11. Нажмите клавишу **F5** , чтобы создать и запустить приложение.

12. В пользовательском интерфейсе приложения введите любые два числа, выберите операцию, а затем нажмите **=** кнопку. Появится правильный результат.

## <a name="see-also"></a>См. также
- [Создание пакета средств разработки](../extensibility/creating-a-software-development-kit.md)
