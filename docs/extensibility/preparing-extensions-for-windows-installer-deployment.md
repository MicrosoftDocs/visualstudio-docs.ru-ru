---
title: Подготовка расширений для развертывания установщик Windows | Документация Майкрософт
description: Узнайте, как подготовить проект, выходные данные которого по умолчанию — пакет VSIX для включения в проект установки.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- vsix msi
ms.assetid: 5ee2d1ba-478a-4cb7-898f-c3b4b2ee834e
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 6436d05d3b15be1c1fe8d7c7bb9c8592dee091dc
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105090282"
---
# <a name="prepare-extensions-for-windows-installer-deployment"></a>Подготовка расширений для развертывания установщик Windows
Нельзя использовать пакет установщик Windows (MSI) для развертывания пакета VSIX. Однако можно извлечь содержимое пакета VSIX для развертывания MSI. В этом документе показано, как подготовить проект, выходные данные которого по умолчанию — пакет VSIX для включения в проект установки.

## <a name="prepare-an-extension-project-for-windows-installer-deployment"></a>Подготовка проекта расширения для развертывания установщик Windows
 Перед добавлением в проект установки выполните эти действия в новых проектах расширений.

### <a name="to-prepare-an-extension-project-for-windows-installer-deployment"></a>Подготовка проекта расширения для развертывания установщик Windows

1. Создание пакета VSPackage, элемента MEF, оформления редактора или другого типа проекта расширяемости, включающего манифест VSIX.

2. Откройте манифест VSIX в редакторе кода.

3. Задайте `InstalledByMsi` для элемента манифеста VSIX значение `true` . Дополнительные сведения о манифесте VSIX см. в разделе [Справочник по схеме расширения vsix 2,0](../extensibility/vsix-extension-schema-2-0-reference.md).

     Это предотвращает попытку установщика VSIX установить компонент.

4. Щелкните правой кнопкой мыши проект в **Обозреватель решений** и выберите пункт **свойства**.

5. Перейдите на вкладку **VSIX** .

6. Установите флажок **Копировать содержимое VSIX в следующее расположение** и введите путь, по которому проект установки будет выбирать файлы.

## <a name="extract-files-from-an-existing-vsix-package"></a>Извлечение файлов из существующего пакета VSIX
 Выполните следующие действия, чтобы добавить содержимое существующего пакета VSIX в проект установки, если отсутствуют исходные файлы.

### <a name="to-extract-files-from-an-existing-vsix-package"></a>Извлечение файлов из существующего пакета VSIX

1. Переименуйте *. VSIX* файл, содержащий расширение *filename. vsix* для *filename.zip*.

2. Скопируйте содержимое *ZIP* -файла в каталог.

3. Удалите файл *[Content_types]. XML* из каталога.

4. Измените манифест VSIX, как показано в предыдущей процедуре.

5. Добавьте остальные файлы в проект установки.

## <a name="see-also"></a>См. также
- [Развертывание установщика Visual Studio](/previous-versions/2kt85ked(v=vs.120))
- [Пошаговое руководство. Создание настраиваемого действия](/previous-versions/visualstudio/visual-studio-2010/d9k65z2d(v=vs.100))