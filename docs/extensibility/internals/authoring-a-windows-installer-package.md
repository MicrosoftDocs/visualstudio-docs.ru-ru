---
title: Создание пакета установщик Windows | Документация Майкрософт
description: Узнайте, как создать пакет установщик Windows для Visual Studio, состоящий из таблиц базы данных, содержащих данные файлов и реестра.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- .msi files, VSPackages
- msi files, VSPackages
ms.assetid: 0ce7c21d-0d3f-47fe-a0bb-eed506e32609
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: afc21237b72d76b73e619740cab0b196e29e928d
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105078959"
---
# <a name="author-a-windows-installer-package"></a>Создание пакета установщик Windows
Данные установщик Windows модели. Вместо написания процедурного скрипта для копирования файлов и записи записей реестра, например, создаются строки и столбцы в таблицах базы данных, содержащих данные файлов и реестра.

## <a name="database-entries"></a>Записи базы данных
Чтобы установить VSPackage, пакет установщик Windows должен содержать записи базы данных для выполнения следующих задач:

- Выполните поиск в системе, чтобы найти версии пакета [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] VSPackage (с помощью установщик Windows таблиц, включающих аппсеарч, комплокатор, реглокатор, дрлокатор и Signature).

- Отмените установку, если не установлена поддерживаемая версия [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] или если не выполнено другое требование к системе VSPackage (с использованием таблицы лаунчкондитион).

- Установите пакет VSPackage и зависимые файлы (с помощью таблиц каталога, компонента и файлов).

- Добавьте соответствующие сведения для пакета VSPackage в реестр (с помощью таблицы реестра).

- Интегрируйте VSPackage в [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , вызвав **devenv.exe/Setup** (с помощью таблицы CustomAction).

Дополнительные сведения см. в разделе [установщик Windows](/windows/desktop/Msi/windows-installer-portal).

## <a name="setup-tools"></a>Средства установки
Различные средства настройки сторонних разработчиков предоставляют среду разработки для установщик Windows пакетов. Доступны следующие бесплатные средства:

- InstallShield Limited Edition

   Вы можете получить ограниченную версию InstallShield с помощью диалогового окна **Новый проект** Visual Studio. Разверните узел **другие типы проектов** , а затем выберите **Установка и развертывание**. Выберите шаблон InstallShield.

- Набор инструментов установщик Windows XML

   Набор средств установщик Windows XML (WiX) создает установщик Windows пакеты из исходных файлов XML. Набор инструментов WiX — это проект Microsoft с открытым исходным кодом. Исходный код и исполняемые файлы можно загрузить из [набора инструментов WiX](https://sourceforge.net/projects/wix/).

   Сведения о коммерческих продуктах, которые интегрируются с с [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] помощью [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] , см. в разделе [Visual Studio Marketplace](https://marketplace.visualstudio.com/).

## <a name="see-also"></a>См. также
- [Установка пакетов VSPackage с помощью установщик Windows](../../extensibility/internals/installing-vspackages-with-windows-installer.md)
