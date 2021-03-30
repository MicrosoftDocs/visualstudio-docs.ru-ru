---
title: Модульное тестирование JavaScript и TypeScript
description: Visual Studio поддерживает код JavaScript и TypeScript для модульного тестирования с помощью инструментов Node.js для Visual Studio
ms.date: 03/18/2021
ms.topic: how-to
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: jmartens
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: dc44e39223fd252ae8c4130a1b358aa6af981119
ms.sourcegitcommit: 3fc099cdc484344c781f597581f299729c6bfb10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/19/2021
ms.locfileid: "104671512"
---
# <a name="unit-testing-javascript-and-typescript-in-visual-studio"></a>Модульное тестирование JavaScript и TypeScript в Visual Studio

Вы можете писать и выполнять модульные тесты в Visual Studio с помощью самых популярных платформ JavaScript без необходимости переключаться на командную строку. Поддерживаются проекты Node.js и ASP.NET Core.

Поддерживаемые платформы:
* Mocha ([mochajs.org](https://mochajs.org/))
* Jasmine ([Jasmine.github.io](https://jasmine.github.io/))
* Tape ([github.com/substack/tape](https://github.com/substack/tape))
* Jest ([jestjs.io](https://jestjs.io/))
* Export Runner (это специальная платформа для инструментов Node.js для Visual Studio)

Сведения о модульных тестах для ASP.NET Core, JavaScript или TypeScript см. в разделе [Написание модульных тестов для ASP.NET Core ](#write-unit-tests-for-aspnet-core).

Если ваша любимая платформа не поддерживается, сведения о расширении поддержки см. в разделе [Расширение поддержки платформ для модульного тестирования](#addingFramework).

## <a name="write-unit-tests-in-a-nodejs-project"></a>Написание модульных тестов в проекте Node.js

Прежде чем добавлять модульные тесты в проект, убедитесь, что выбранная платформа локально установлена в проекте. Это легко сделать в [окне установки пакета npm](npm-package-management.md#npmInstallWindow).

Чтобы добавлять в проект модульные тесты, рекомендуется создать в проекте папку *tests* и настроить ее как тестовый корень в свойствах проекта. Также необходимо выбрать желаемую платформу тестирования.

![Выбор тестового корня и платформы тестирования](../javascript/media/unit-test-project-properties.png)

Вы можете добавлять в проект простые пустые тесты в диалоговом окне **Добавить новый элемент**. В одном проекте поддерживаются JavaScript и TypeScript.

![Добавление нового модульного теста](../javascript/media/unit-test-add-new-item.png)

Для модульного теста Mocha используйте следующий код:

```javascript
var assert = require('assert');

describe('Test Suite 1', function() {
    it('Test 1', function() {
        assert.ok(true, "This shouldn't fail");
    })

    it('Test 2', function() {
        assert.ok(1 === 1, "This shouldn't fail");
        assert.ok(false, "This should fail");
    })
})
```

Если вы не задали параметры модульного теста в свойствах проекта, необходимо убедиться, что для свойства **Платформа тестирования** в окне **Свойства** будет установлена верная платформа тестирования для файлов модульных тестов. Это выполняется автоматически шаблонами файлов модульного теста.

![Тестовая платформа](../javascript/media/UnitTestsFrameworkMocha.png)

> [!Note]
> Параметры модульного теста имеют приоритет над параметрами отдельных файлов.

После открытия обозревателя тестов (выберите **Тест** > **Windows** > **Обозреватель тестов**) Visual Studio обнаруживает и отображает тесты. Если тесты не отображаются изначально, перестройте проект, чтобы обновить список.

![Обозреватель тестов](../javascript/media/UnitTestsDiscoveryMocha.png)

> [!NOTE]
> В файле *tsconfig.json* TypeScript не используйте параметр `outdir` или `outfile`, так как обозреватель тестов не сможет найти модульные тесты.

## <a name="run-tests-nodejs"></a>Выполнение тестов (Node.js)

Вы можете выполнять тесты в Visual Studio или из командной строки.

### <a name="run-tests-in-visual-studio"></a>Выполнение тестов в Visual Studio

::: moniker range=">=vs-2019"
Чтобы выполнить тест, нажмите на ссылку **Выполнить все** в обозревателе тестов. Или выберите один или несколько тестов или групп, щелкните правой кнопкой мыши и в контекстном меню выберите команду **Выполнить**. Тесты выполняются в фоновом режиме, и обозреватель тестов автоматически обновится, отображая результаты. Кроме того, вы можете отладить выбранные тесты, щелкнув их правой кнопкой мыши и выбрав **Отладить**.
::: moniker-end
::: moniker range="vs-2017"
Чтобы выполнить тест, нажмите на ссылку **Выполнить все** в обозревателе тестов. Или выберите один или несколько тестов или групп, щелкните правой кнопкой мыши и в контекстном меню выберите команду **Выполнить выбранные тесты**. Тесты выполняются в фоновом режиме, и обозреватель тестов автоматически обновится, отображая результаты. Кроме того, вы можете отладить выбранные тесты, нажав **Отладить выбранные тесты**.
::: moniker-end

Для TypeScript модульные тесты выполняются в созданном коде JavaScript.

> [!NOTE]
> В большинстве сценариев TypeScript можно выполнить отладку модульного теста, установив точку останова в коде TypeScript, щелкнув правой кнопкой мыши тест в обозревателе тестов и выбрав **Отладка**. В более сложных сценариях, например там, где используются сопоставители с исходным кодом, тестовые файлы могут не достичь точек останова в коде TypeScript. В качестве обходного решения рекомендуется использовать ключевое слово `debugger`.

> [!NOTE]
> В настоящее время мы не поддерживаем тесты профилирования или объем протестированного кода.

### <a name="run-tests-from-the-command-line"></a>Запуск тестов из командной строки

Вы можете выполнять тесты из [командной строки разработчика](../ide/reference/command-prompt-powershell.md) в Visual Studio, используя следующую команду:

```
vstest.console.exe <path to project file>\NodejsConsoleApp23.njsproj /TestAdapterPath:<VisualStudioFolder>\Common7\IDE\Extensions\Microsoft\NodeJsTools\TestAdapter
```

Выходные данные этой команды выглядят примерно следующим образом:

```
Microsoft (R) Test Execution Command Line Tool Version 15.5.0
Copyright (c) Microsoft Corporation.  All rights reserved.

Starting test execution, please wait...
Processing: NodejsConsoleApp23\NodejsConsoleApp23\UnitTest1.js
  Creating TestCase:NodejsConsoleApp23\NodejsConsoleApp23\UnitTest1.js::Test Suite 1 Test 1::mocha
  Creating TestCase:NodejsConsoleApp23\NodejsConsoleApp23\UnitTest1.js::Test Suite 1 Test 2::mocha
Processing finished for framework of Mocha
Passed   Test Suite 1 Test 1
Standard Output Messages:
 Using default Mocha settings
 1..2
 ok 1 Test Suite 1 Test 1

Failed   Test Suite 1 Test 2
Standard Output Messages:
 not ok 1 Test Suite 1 Test 2
   AssertionError [ERR_ASSERTION]: This should fail
       at Context.<anonymous> (NodejsConsoleApp23\NodejsConsoleApp23\UnitTest1.js:10:16)

Total tests: 2. Passed: 1. Failed: 1. Skipped: 0.
Test Run Failed.
Test execution time: 1.5731 Seconds
```

> [!NOTE]
> Если отобразится сообщение об ошибке, указывающее, что невозможно найти *vstest.console.exe*, убедитесь, что открыли командную строку разработчика, а не обычную командную строку.

## <a name="write-unit-tests-for-aspnet-core"></a>Написание модульных тестов для ASP.NET Core

1. Создайте проект ASP.NET Core и добавьте поддержку TypeScript.

   Пример проекта см. в разделе [Создание приложения ASP.NET Core с помощью TypeScript](../javascript/tutorial-aspnet-with-typescript.md). Для поддержки модульного тестирования рекомендуется начать со стандартного шаблона проекта ASP.NET Core.

   Для добавления поддержки TypeScript используйте пакет NuGet вместо пакета npm TypeScript.

1. Установка пакета NuGet [Microsoft.JavaScript.UnitTest](https://www.nuget.org/packages/Microsoft.JavaScript.UnitTest/)

1. В обозревателе решений щелкните узел проекта правой кнопкой мыши и выберите **Выгрузить проект**.

   Файл *.csproj* должен быть открыт в Visual Studio.

1. Добавьте следующие элементы в файл *.csproj* в элементе `PropertyGroup`.

   В этом примере в качестве платформы тестирования используется Mocha. Вместо нее можно указать Jest, Tape или Jasmine.

   ```xml
   <PropertyGroup>
      ...
      <JavaScriptTestRoot>tests\</JavaScriptTestRoot>
      <JavaScriptTestFramework>Mocha</JavaScriptTestFramework>
      <GenerateProgramFile>false</GenerateProgramFile>
   </PropertyGroup>
   ```

   Элемент `JavaScriptTestRoot` указывает, что модульные тесты будут находиться в папке *tests* корневого каталога проекта.

1. В обозревателе решений щелкните узел проекта правой кнопкой мыши и выберите **Выгрузить проект**.

1. Добавьте поддержку npm, как описано в статье "Управление пакетами npm" в разделе [Проекты ASP.NET Core](../javascript/npm-package-management.md#aspnet-core-projects).

   Для этого необходимо установить среду выполнения Node.js для поддержки npm и добавить *package.js* в корневую папку проекта.

1. В файле *package.json* добавьте необходимый пакет npm в разделе зависимостей.

   Например для mocha можно использовать следующий код JSON:

   ```json
   "dependencies": {
     "mocha": "8.3.0",
   ```

   Для некоторых платформ модульного тестирования, таких как Jest, требуются дополнительные пакеты npm. Для Jest используйте следующий код JSON:

   ```json
   "dependencies": {
     "jest": "26.6.3",
     "jest-editor-support": "28.1.0"
   ```

   >[!NOTE]
   > В некоторых сценариях узел npm может не отображаться в обозревателе решений из-за известной проблемы, описанной [здесь](https://github.com/aspnet/Tooling/issues/479). Если необходимо просмотреть узел npm, можно выгрузить проект (щелкнув проект правой кнопкой мыши и выбрав команду **Выгрузить проект**), а затем перезагрузить проект, чтобы снова отобразить узел npm.

1. Добавьте код в тест.

   Если вы используете пример, описанный в разделе [Создание приложения ASP.NET Core с помощью TypeScript](tutorial-aspnet-with-typescript.md), добавьте следующий код в конец файла *library.ts*, находящегося в папке *scripts*.

   ```typescript
   function getData(value) {
      if (value > 1) {
         return true;
      }
   }
    
   module.exports = getData;
   ```

   Для TypeScript модульные тесты выполняются в созданном коде JavaScript.

1. Добавьте модульные тесты в папку *tests* в корневом каталоге проекта.

   Например, вы можете использовать следующий код, выбрав вкладку документации, соответствующую вашей платформе тестирования, в данном случае, Mocha или Jest. Этот код проверяет функцию с именем `getData`.

   # <a name="mocha"></a>[Мокко](#tab/mocha)

   ```typescript
   const getData = require('../wwwroot/js/library.js');
   var assert = require('assert');
    
   describe('Test Suite 1', function () {
      it('getData', function () {
         assert.ok(true, getData(2));
      })
   })
   ```

   # <a name="jest"></a>[Jest](#tab/jest)

   ```typescript
   const getData = require('../wwwroot/js/library.js');
    
   test('should return true', () => {
      expect(getData(2)).toBe(true);
   });
   ```

1. Откройте обозреватель тестов (выберите **Тест** > **Windows** > **Обозреватель тестов**), и тесты будут обнаружены и показаны в Visual Studio. Если тесты не отображаются изначально, перестройте проект, чтобы обновить список.

   ![Обнаружение тестов с помощью обозревателя тестов](../javascript/media/unit-tests-aspnet-core-discovery.png)

   > [!NOTE]
   > В файле *tsconfig.json* TypeScript не используйте параметр `outfile`, так как обозреватель тестов не сможет найти модульные тесты. Можно использовать параметр `outdir`, но убедитесь, что в корневом каталоге проекта есть файлы конфигурации, такие как `package.json` и `tsconfig.json`.

## <a name="run-tests-aspnet-core"></a>Выполнение тестов (ASP.NET Core)

::: moniker range=">=vs-2019"
Чтобы выполнить тест, нажмите на ссылку **Выполнить все** в обозревателе тестов. Или выберите один или несколько тестов или групп, щелкните правой кнопкой мыши и в контекстном меню выберите команду **Выполнить**. Тесты выполняются в фоновом режиме, и обозреватель тестов автоматически обновится, отображая результаты. Кроме того, вы можете отладить выбранные тесты, щелкнув их правой кнопкой мыши и выбрав **Отладить**.
::: moniker-end
::: moniker range="vs-2017"
Чтобы выполнить тест, нажмите на ссылку **Выполнить все** в обозревателе тестов. Или выберите один или несколько тестов или групп, щелкните правой кнопкой мыши и в контекстном меню выберите команду **Выполнить выбранные тесты**. Тесты выполняются в фоновом режиме, и обозреватель тестов автоматически обновится, отображая результаты. Кроме того, вы можете отладить выбранные тесты, нажав **Отладить выбранные тесты**.
::: moniker-end

Для TypeScript модульные тесты выполняются в созданном коде JavaScript.

![Результаты обозревателя тестов](../javascript/media/unit-tests-aspnet-core-run.png)

> [!NOTE]
> В большинстве сценариев TypeScript можно выполнить отладку модульного теста, установив точку останова в коде TypeScript, щелкнув правой кнопкой мыши тест в обозревателе тестов и выбрав **Отладка**. В более сложных сценариях, например там, где используются сопоставители с исходным кодом, тестовые файлы могут не достичь точек останова в коде TypeScript. В качестве обходного решения рекомендуется использовать ключевое слово `debugger`.

> [!NOTE]
> В настоящее время мы не поддерживаем тесты профилирования или объем протестированного кода.

## <a name="add-support-for-a-unit-test-framework"></a><a name="addingFramework"></a>Расширение поддержки платформ модульного тестирования

Вы можете добавить поддержку дополнительных платформ тестирования, реализовав логику обнаружения и выполнения с помощью JavaScript. Для этого добавьте папку с именем платформы тестирования в раздел:

`<VisualStudioFolder>\Common7\IDE\Extensions\Microsoft\NodeJsTools\TestAdapter\TestFrameworks`

Эта папка должна содержать файл JavaScript с тем же именем, который экспортирует следующие две функции:

* `find_tests`
* `run_tests`

Хороший пример реализаций `find_tests` и `run_tests` см. в реализации платформы модульного тестирования Mocha в:

`<VisualStudioFolder>\Common7\IDE\Extensions\Microsoft\NodeJsTools\TestAdapter\TestFrameworks\mocha\mocha.js`

Обнаружение доступных тестовых платформ выполняется при запуске Visual Studio. Если платформа добавляется во время выполнения Visual Studio, перезапустите Visual Studio для обнаружения платформы. Но вам не нужно перезапускать платформу, если вы вносите изменения в реализацию.

## <a name="unit-tests-in-net-framework"></a>Модульные тесты в .NET Framework

Вы можете писать модульные тесты не только в проектах Node.js и ASP.NET Core. Когда вы добавляете свойства TestFramework и TestRoot в проект C# или Visual Basic, эти тесты будут перечислены и вы сможете выполнять их в окне обозревателя тестов.

Чтобы включить эту функцию, щелкните правой кнопкой мыши узел проекта в обозревателе решений, выберите **Выгрузить проект**, а затем **Изменить проект**. Затем в файле проекта добавьте следующие два элемента в группу свойств.

> [!IMPORTANT]
> Убедитесь, что для группы свойств, в которую вы добавляете элементы, не указано условие.
> Это может привести к непредвиденному поведению.

```xml
<PropertyGroup>
    <JavaScriptTestRoot>tests\</JavaScriptTestRoot>
    <JavaScriptTestFramework>Tape</JavaScriptTestFramework>
</PropertyGroup>
```

Затем добавьте тесты в указанную папку тестового корня, и они будут доступны для выполнения в окне обозревателя тестов. Если они не отображаются, возможно, потребуется перестроить проект.

## <a name="unit-test-net-core-and-net-standard"></a>Модульное тестирование в .NET Core и .NET Standard

В дополнение к указанным выше свойствам вам необходимо также установить пакет NuGet [Microsoft.JavaScript.UnitTest](https://www.nuget.org/packages/Microsoft.JavaScript.UnitTest/) и установить следующее свойство:

```xml
<PropertyGroup>
    <GenerateProgramFile>false</GenerateProgramFile>
</PropertyGroup>
```

Некоторым платформам тестирования могут потребоваться дополнительные пакеты npm для обнаружения тестов. Например, для jest требуется пакет npm jest-editor-support. При необходимости ознакомьтесь с документацией по конкретной платформе.
