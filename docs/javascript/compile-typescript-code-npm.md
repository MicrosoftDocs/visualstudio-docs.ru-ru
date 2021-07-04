---
title: Компиляция и сборка кода TypeScript с использованием npm
description: Узнайте, как добавить поддержку Typescript в проекты Visual Studio с помощью пакета npm (Node Package Manager).
ms.date: 7/23/2020
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: jmartens
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: 96e5689c0108231be26ddf7d598227137f7bc1f7
ms.sourcegitcommit: ab5735d64a6ad7aecabf5d6df159888e3246bff5
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/04/2021
ms.locfileid: "111433783"
---
# <a name="compile-typescript-code-nodejs"></a>Компиляция кода TypeScript (Node.js)

Вы можете добавить в проекты поддержку TypeScript, используя пакет TypeScript SDK, который доступен по умолчанию в Visual Studio Installer или в виде пакета npm. Для проектов, которые разработаны в Visual Studio 2019, рекомендуется использовать пакеты npm TypeScript. Они обеспечивают лучшую переносимость между разными средами и платформами.

Для проектов ASP.NET Core рекомендуется использовать [пакет NuGet](../javascript/compile-typescript-code-nuget.md).

## <a name="add-typescript-support-using-npm"></a>Добавление поддержки TypeScript с использованием npm

[Пакет npm TypeScript](https://www.npmjs.com/package/typescript) позволяет включить поддержку TypeScript. Когда в проект устанавливается пакет npm или TypeScript 2.1 или более новой версии, в редактор загружается соответствующая версия языковой службы TypeScript.

1. [Следуя инструкциям](../ide/quickstart-nodejs.md?toc=%252fvisualstudio%252fjavascript%252ftoc.json), установите рабочую нагрузку разработки Node.js и среду выполнения Node.js.

   Для самой простой интеграции с Visual Studio создайте проект с помощью одного из шаблонов Node.js для TypeScript, например шаблона пустого веб-приложения Node.js. Либо используйте шаблон Node.js для JavaScript, предоставляемый в Visual Studio, и следуйте инструкциям в этом разделе или используйте проект [Открыть папку](../javascript/develop-javascript-code-without-solutions-projects.md).

1. Установите [пакет npm для TypeScript](https://www.npmjs.com/package/typescript), если он еще не включен в ваш проект.

   В Обозревателе решений (область справа) откройте *package.json* в корневом каталоге проекта. Перечисленные пакеты соответствуют пакетам в узле npm в Обозревателе решений. Дополнительные сведения см. в разделе [Управление пакетами npm](../javascript/npm-package-management.md).

   Установить пакет npm TypeScript для проекта Node.js можно с помощью командной строки или IDE. Чтобы установить пакет с помощью IDE, щелкните правой кнопкой мыши узел npm в Обозревателе решений, выберите **Установить новый пакет npm**, найдите **TypeScript** и установите пакет.

   Выберите параметр **npm** в окне **Вывод**, чтобы видеть ход установки пакета. Установленный пакет появится в узле **npm** в Обозревателе решений.

1. Если пакет не будет включен в проект, добавьте файл с расширением *.tsconfig* в корневой каталог проекта. Для этого щелкните правой кнопкой мыши узел проекта и выберите **Добавить > Новый элемент**. Выберите **Файл конфигурации TypeScript JSON**, а затем нажмите кнопку **Добавить**.

   Visual Studio добавит файл *tsconfig.json* в корневую папку проекта. Этот файл можно использовать для [настройки параметров](https://www.typescriptlang.org/docs/handbook/tsconfig-json.html) компилятора TypeScript.

1. Откройте файл *tsconfig.json* и обновите его, задав необходимые параметры компилятора.

   Ниже приведен пример простого файла *tsconfig.json*.

   ```json
   {
     "compilerOptions": {
       "noImplicitAny": false,
       "noEmitOnError": true,
       "removeComments": false,
       "sourceMap": true,
       "target": "es5",
       "outDir": "dist"
     },
     "include": [
       "scripts/**/*"
     ]
   }
   ```

   В этом примере:
   - *include* указывает компилятору, где искать файлы TypeScript (*.ts).
   - Параметр *outDir* указывает выходную папку для обычных файлов JavaScript, которые преобразуются компилятором TypeScript.
   - Параметр *sourceMap* указывает, нужно ли компилятору создать файлы *sourceMap*.

   В приведенной выше конфигурации представлен пример базовой конфигурации TypeScript. Сведения о других параметрах см. в разделе о файле [tsconfig.json](https://www.typescriptlang.org/docs/handbook/tsconfig-json.html).

## <a name="build-the-application"></a>Построение приложения

1. В проект добавьте файлы TypeScript ( *.ts*) или TypeScript JSX ( *.tsx*), а затем добавьте код TypeScript. В качестве простого примера TypeScript используйте следующий код:

   ```typescript
   let message: string = 'Hello World';
   console.log(message);
   ```

1. В *package.json* включите поддержку команд сборки и очистки Visual Studio, используя приведенные ниже скрипты.

   ```json
   "scripts": {
     "build": "tsc --build",
     "clean": "tsc --build --clean"
   },
   ```

   Если необходимо выполнить сборку с помощью стороннего средства, например webpack, можно добавить в файл *package.json* скрипт сборки для командной строки:

   ```json
   "scripts": {
      "build": "webpack-cli app.tsx --config webpack-config.js"
   }
   ```

   Пример использования webpack с React и файла конфигурации webpack см. в статье [Учебник. Создание приложения Node.js и React в Visual Studio](../javascript/tutorial-nodejs-with-react-and-jsx.md).

   Пример использования Vue.js с TypeScript см. в статье [Создание приложения Vue.js](/javascript/create-application-with-vuejs).

1. Если необходимо настроить такие параметры, как начальная страница, путь к среде выполнения Node.js, порт приложения или аргументы среды выполнения, щелкните правой кнопкой мыши узел проекта в Обозревателе решений и выберите **Свойства**.

   >[!NOTE]
   > При настройке сторонних средств в проектах Node.js не используются пути, заданные в разделе **Средства** > **Параметры** > **Проекты и решения** > **Управление веб-пакетами** > **Внешние веб-инструменты**. Эти параметры используются для проектов других типов.

1. Выберите **Сборка > Собрать решение**.

   Хотя сборка приложения выполняется автоматически при его запуске, рассмотрим, что происходит в процессе сборки.

   Если вы создали сопоставители с исходным кодом, откройте папку, указанную в параметре *outDir*, где вы найдете созданные файлы \*.js, а также созданные файлы \*js.map.

   Файлы сопоставителей с исходным кодом требуются для [отладки](../javascript/debug-nodejs.md).

### <a name="run-the-application"></a>Выполнение приложения

Инструкции по запуску приложения после его компиляции см. в разделе [Создание первого приложения Node.js](../ide/quickstart-nodejs.md?toc=%252fvisualstudio%252fjavascript%252ftoc.json#run-the-app).

## <a name="automate-build-tasks"></a>Автоматизация задач сборки

Для автоматизации задач сторонних средств, таких как npm и webpack, вы можете использовать обозреватель запускателя задач в Visual Studio.

- [Запускатель задач npm](https://marketplace.visualstudio.com/items?itemName=MadsKristensen.NPMTaskRunner) включает поддержку скриптов npm, определенных файле *package.json*. Поддерживает YARN.
- [Запускатель задач webpack](https://marketplace.visualstudio.com/items?itemName=MadsKristensen.WebPackTaskRunner) включает поддержку webpack.
