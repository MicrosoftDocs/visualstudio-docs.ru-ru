---
title: Команды, которые должны быть выполнены после установки | Документация Майкрософт
description: Сведения о командах, которые должны выполняться в процессе установки расширения, развернутого с помощью MSI-файла в Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- post-install commands
ms.assetid: c9601f2e-2c6e-4da9-9a6e-e707319b39e2
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: ef557c0c679fad0dff25a51a8529270e4bd7ced2
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105057147"
---
# <a name="commands-that-must-be-run-after-installation"></a>Команды, которые должны быть выполнены после установки
При развертывании расширения с помощью *MSI* -файла необходимо запустить команду **devenv/setup** в процессе установки, чтобы Visual Studio обнаружила свои расширения.

> [!NOTE]
> Сведения в этом разделе относятся к поиску *devenv.exe* с помощью Visual Studio 2008 и более ранних версий. Дополнительные сведения об обнаружении *devenv.exe* в более поздних версиях Visual Studio см. в разделе [Определение требований к системе](../../extensibility/internals/detecting-system-requirements.md).

## <a name="find-devenvexe"></a>Поиск devenv.exe
 Вы можете указать *devenv.exe* каждой версии из значений реестра, которые [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] установщики записывают, используя таблицу Реглокатор и таблицы аппсеарч для хранения значений реестра в качестве свойств. Дополнительные сведения см. в разделе [Определение требований к системе](../../extensibility/internals/detecting-system-requirements.md).

### <a name="reglocator-table-rows-to-locate-devenvexe-from-different-versions-of-visual-studio"></a>Реглокатор строки таблицы для нахождение devenv.exe из разных версий Visual Studio

|Подпись|Root|Клавиши|Название|Type|
|-----------------|----------|---------|----------|----------|
|RL_DevenvExe_2002|2|SOFTWARE\Microsoft\VisualStudio\7.0\Setup\VS|енвиронментпас|2|
|RL_DevenvExe_2003|2|SOFTWARE\Microsoft\VisualStudio\7.1\Setup\VS|енвиронментпас|2|
|RL_DevenvExe_2005|2|SOFTWARE\Microsoft\VisualStudio\8.0\Setup\VS|енвиронментпас|2|
|RL_DevenvExe_2008|2|SOFTWARE\Microsoft\VisualStudio\9.0\Setup\VS|енвиронментпас|2|

### <a name="appsearch-table-rows-for-corresponding-reglocator-table-rows"></a>Аппсеарч строки таблицы для соответствующих строк таблицы Реглокатор

|Свойство|Подпись|
|--------------|-----------------|
|DEVENV_EXE_2002|RL_DevenvExe_2002|
|DEVENV_EXE_2003|RL_DevenvExe_2003|
|DEVENV_EXE_2005|RL_DevenvExe_2005|
|DEVENV_EXE_2008|RL_DevenvExe_2008|

 Например, установщик Visual Studio записывает значение реестра **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0\Setup\VS\EnvironmentPath** как *C:\VS2008\Common7\IDE\devenv.exe*, полный путь к исполняемому файлу, который должен запустить установщик.

> [!NOTE]
> Так как столбец типа таблицы Реглокатор имеет значение 2, необязательно указывать дополнительные сведения о версии в таблице сигнатур.

## <a name="run-devenvexe"></a>Запустить devenv.exe
 После выполнения стандартного действия Аппсеарч в установщике каждое свойство в таблице Аппсеарч имеет значение, указывающее на файл *devenv.exe* для соответствующей версии Visual Studio. Если какие-либо из указанных значений реестра отсутствуют, так как эта версия Visual Studio не установлена, для указанного свойства устанавливается значение null.

 Установщик Windows поддерживает запуск исполняемого файла, на который указывает свойство через тип настраиваемого действия 50. Настраиваемое действие должно включать в себя параметры выполнения в скрипте `msidbCustomActionTypeInScript` (1024) и `msidbCustomActionTypeCommit` (512), чтобы убедиться, что пакет VSPackage успешно установлен перед интеграцией в [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . Дополнительные сведения см. в статьях [Таблица CustomAction](/windows/desktop/msi/customaction-table) и [настраиваемое действие в параметрах выполнения в скрипте](/windows/desktop/msi/custom-action-in-script-execution-options).

 Пользовательские действия типа 50 указывают свойство, содержащее исполняемый файл, в качестве значения исходного столбца и аргументов командной строки в целевом столбце.

### <a name="customaction-table-rows-to-run-devenvexe"></a>Строки таблицы CustomAction для выполнения devenv.exe

|Действие|Type|Источник|Назначение|
|------------|----------|------------|------------|
|CA_RunDevenv2002|1586|DEVENV_EXE_2002|/Setup|
|CA_RunDevenv2003|1586|DEVENV_EXE_2003|/Setup|
|CA_RunDevenv2005|1586|DEVENV_EXE_2005|/Setup|
|CA_RunDevenv2008|1586|DEVENV_EXE_2008|/Setup|

 Пользовательские действия должны быть созданы в таблице Инсталлексекутесекуенце, чтобы запланировать их выполнение во время установки. Используйте соответствующее свойство в каждой строке столбца Condition, чтобы предотвратить выполнение настраиваемого действия, если эта версия [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] не установлена в системе.

> [!NOTE]
> Свойства, возвращающие значение null, вычисляются `False` при использовании в условиях.

 Значение столбца последовательности для каждого настраиваемого действия зависит от других значений последовательности в пакете установщик Windows. Значения последовательности должны быть таким, чтобы *devenv.exe* настраиваемые действия запускаться как можно ближе, до выполнения стандартного действия функции InstallFinalize.

### <a name="installexecutesequence-table-to-schedule-the-devenvexe-custom-actions"></a>Инсталлексекутесекуенце таблица для планирования devenv.exe настраиваемых действий

|Действие|Условие|Последовательность|
|------------|---------------|--------------|
|CA_RunDevenv2002|DEVENV_EXE_2002|6602|
|CA_RunDevenv2003|DEVENV_EXE_2003|6603|
|CA_RunDevenv2005|DEVENV_EXE_2005|6605|
|CA_RunDevenv2008|DEVENV_EXE_2008|6608|

## <a name="see-also"></a>См. также
- [Установка пакетов VSPackage с помощью установщик Windows](../../extensibility/internals/installing-vspackages-with-windows-installer.md)
