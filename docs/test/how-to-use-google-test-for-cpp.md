---
title: Использование Google Test для C++
description: Используйте Google Test для создания модульных тестов на C++ в Visual Studio.
ms.date: 05/06/2017
ms.topic: how-to
ms.author: corob
manager: markl
ms.workload:
- cplusplus
author: corob-msft
ms.openlocfilehash: a338b6f62aee6ec342ef6a16abec71cb6a833bc0
ms.sourcegitcommit: 4b2b6068846425f6964c1fd867370863fc4993ce
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/12/2021
ms.locfileid: "112042968"
---
# <a name="how-to-use-google-test-for-c-in-visual-studio"></a>Использование Google Test для C++ в Visual Studio

В Visual Studio 2017 и более поздних версиях решение Google Test интегрировано в среду Visual Studio как компонент рабочей нагрузки **Разработка классических приложений на C++**. Чтобы проверить, установлен ли этот компонент на компьютере, откройте Visual Studio Installer и найдите Google Test в списке компонентов рабочей нагрузки.

![Установка Google Test](media/cpp-google-component.png)

::: moniker range=">=vs-2019"

## <a name="add-a-google-test-project-in-visual-studio-2019"></a>Добавление проекта Google Test в Visual Studio 2019

1. В **обозревателе решений** щелкните узел решения правой кнопкой мыши и выберите пункты **Добавить** > **Новый проект**.
2. Задайте **Язык** как **C++** и введите **тест** в поле поиска. Выберите в списке результатов **Проект Google Test**.
3. Укажите имя тестового проекта и нажмите кнопку **ОК**.

![Новый проект Google Test](media/vs-2019/cpp-gtest-new-project-vs2019.png)

::: moniker-end

::: moniker range="vs-2017"

## <a name="add-a-google-test-project-in-visual-studio-2017"></a>Создание проекта Google Test в Visual Studio 2017

1. В **обозревателе решений** щелкните узел решения правой кнопкой мыши и выберите пункты **Добавить** > **Новый проект**.
2. В левой области выберите **Visual C++** > **Тест**, а в центральной области — **Проект Google Test**.
3. Укажите имя тестового проекта и нажмите кнопку **ОК**.

![Новый проект Google Test](media/cpp-gtest-new-project.png)

::: moniker-end

## <a name="configure-the-test-project"></a>Настройка тестового проекта

В открывшемся диалоговом окне **Конфигурация тестового проекта** можно выбрать проект, который необходимо тестировать. При выборе проекта Visual Studio добавляет ссылку на него. Если проект не выбран, необходимо вручную добавить ссылки на проекты, которые следует тестировать. При выборе статического или динамического связывания с двоичными файлами Google Test следует учитывать те же факторы, что и в случае с любой другой программой C++. Дополнительные сведения см. в статье [DLL в Visual C++](/cpp/build/dlls-in-visual-cpp).

![Настройка проекта Google Test](media/cpp-gtest-config.png)

## <a name="set-additional-options"></a>Настройка дополнительных параметров

Чтобы настроить дополнительные параметры, в главном меню выберите **Сервис** > **Параметры** > **Адаптер тестов для Google Test**. Дополнительные сведения об этих параметрах см. в документации по Google Test.

![Параметры проекта Google Test](media/cpp-gtest-settings.png)

## <a name="add-include-directives"></a>Добавление директив include

В *CPP*-файле теста добавьте необходимые директивы `#include`, чтобы типы и функции программы были доступны коду теста. Как правило, программа находится в иерархии папок на один уровень выше. Если ввести `#include "../"`, появится окно IntelliSense, в котором можно выбрать полный путь к файлу заголовка.

![Добавление директив #include](media/cpp-gtest-includes.png)

## <a name="write-and-run-tests"></a>Написание и запуск тестов

Все готово к написанию и выполнению тестов Google Test. Сведения о макросах тестов см. в [учебнике по началу работы с Google Test](https://github.com/google/googletest/blob/master/docs/primer.md). Сведения об обнаружении, выполнении и группировании тестов с помощью **обозревателя тестов** см. в статье [Выполнение модульных тестов с помощью обозревателя тестов](run-unit-tests-with-test-explorer.md).

## <a name="see-also"></a>См. также раздел

[Написание модульных тестов для C/C++](writing-unit-tests-for-c-cpp.md)
