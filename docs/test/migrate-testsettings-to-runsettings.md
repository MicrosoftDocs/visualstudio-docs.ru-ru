---
title: Переход с файла TESTSETTINGS на файл RUNSETTINGS
description: Узнайте, как перейти с testsettings на runsettings
ms.custom: SEO-VS-2020
ms.date: 03/18/2021
ms.topic: conceptual
f1_keywords:
- vs.UnitTest.Migrate
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: ab1cfe921777fa75d4f69251668934e8d78d9bec
ms.sourcegitcommit: 155d5f0fd54ac1d20df2f5b0245365924faa3565
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/31/2021
ms.locfileid: "106087200"
---
# <a name="upgrade-from--testsettings-to-runsettings"></a>Обновление с файла с расширением *.testsettings* до файла с расширением *.runsettings*

Вы можете изменить файл конфигурации теста с расширением *.testsettings* на файл с расширением *.runsettings* с помощью средства SettingsMigrator, которое устанавливается вместе с Visual Studio. В зависимости от расположения установки Visual Studio средство SettingsMigrator можно найти в следующем расположении: `C:\Program Files (x86)\Microsoft Visual Studio\2019\Enterprise\Common7\IDE\Extensions\TestPlatform\SettingsMigrator.exe`.

В правильном расположении каталога можно запустить это средство следующим образом:

```console
SettingsMigrator.exe <Full path to testsettings file to be migrated>
SettingsMigrator.exe <Full path to testsettings file to be migrated> <Full path to runsettings file to be created>
```

## <a name="examples"></a>Примеры
```console
SettingsMigrator.exe E:\MyTest\MyTestSettings.testsettings
SettingsMigrator.exe E:\MyTest\MyTestSettings.testsettings E:\MyTest\MyNewRunSettings.runsettings
```

Если вы хотите узнать больше о том, как параметры *.testsettings* преобразуются в *.runsettings*, см. дополнительные сведения о реализации в [репозитории платформы тестирования с открытым кодом](https://github.com/microsoft/vstest-docs/blob/master/RFCs/0023-TestSettings-Deprecation.md#migration) на сайте GitHub.

## <a name="see-also"></a>См. также раздел

- [Настройка тестовых запусков с помощью `.runsettings`](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md)
- [Обновление с MSTestv1 до MSTestv2](../test/mstest-update-to-mstestv2.md)
- [Модульное тестирование кода](../test/unit-test-your-code.md)
- [Отладка модульных тестов с помощью Обозревателя тестов](../test/debug-unit-tests-with-test-explorer.md)
