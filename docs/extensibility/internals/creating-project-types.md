---
title: Создание типов проектов | Документация Майкрософт
description: Узнайте, как расширить Visual Studio путем проектирования, создания и регистрации нового типа проекта, который поддерживает задачи программирования.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project types, new
- projects [Visual Studio SDK], new project types
ms.assetid: bdb2d22e-d622-450c-bb2d-98152a745fcf
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 5984afd2879f94a73ef02f77a85501c50f55bc93
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105056822"
---
# <a name="create-project-types"></a>Создание типов проектов
Можно расширить [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , создав новый тип проекта. Чтобы создать новый тип проекта, необходимо ознакомиться с некоторыми концепциями и выполнить ряд действий. В следующих разделах приводятся общие сведения о создании типов проектов.

## <a name="in-this-section"></a>Содержание раздела
- [Решения по проектированию типов проектов](../../extensibility/internals/project-type-design-decisions.md)

 Обсуждаются элементы, сохраняемость файлов проекта и обязательства по проектированию механику, которые необходимо выполнить перед созданием нового типа проекта.

- [Контрольный список: создание новых типов проектов](../../extensibility/internals/checklist-creating-new-project-types.md)

 Содержит общие сведения о шагах, которые необходимо выполнить для создания нового типа проекта, который поддерживает такие задачи программирования, как редактирование кода и компиляция, сборка, отладка и развертывание приложений в проекте.

- [Создание экземпляров проекта с помощью фабрик проекта](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)

 Содержит сведения о том, как предоставить и использовать фабрику проектов для создания экземпляров нового проекта.

- [Регистрация типа проекта](../../extensibility/internals/registering-a-project-type.md)

 Предоставляет образцы кода инструкций из реестра, которые предоставляют пути и данные по умолчанию, а также таблицу, содержащую записи из скрипта реестра для каждой инструкции.

- [Сохраняемость проекта](../../extensibility/internals/project-persistence.md)

 Обсуждается использование `IPersistFileFormat` для сохранения как файловых, так и нефайловых объектов проекта.

- [Использование MSBuild](../../extensibility/internals/using-msbuild.md)

 Описывает, как тип проекта может использовать [!INCLUDE[vstecmsbuild](../../extensibility/internals/includes/vstecmsbuild_md.md)] механизм сборки, чтобы разрешить пользователям выполнять сборку из [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] и из командной строки.

## <a name="related-sections"></a>Связанные разделы
- [Поддержка средств обзора символов](../../extensibility/internals/supporting-symbol-browsing-tools.md)

 Описание архитектуры средств просмотра кода, таких как **Обозреватель объектов** и окно **представление классов** . Описывает интерфейсы и методы, используемые для реализации обзора объектов в VSPackage.

- [Добавление шаблонов проектов и элементов проектов](../../extensibility/internals/adding-project-and-project-item-templates.md)

 Описывает важность, которую играют проекты при определении того, какой редактор используется при открытии элемента проекта и о том, как можно манипулировать ресурсами проекта.

- [Установка пакетов VSPackage с помощью установщик Windows](../../extensibility/internals/installing-vspackages-with-windows-installer.md)

 Здесь показано, как предоставить пакету VSPackage собственное уникальное удостоверение и как заключить в пакеты библиотеки DLL VSPackage и другие сведения в установщик Windowsном пакете (*. MSI* -файл) для развертывания на клиентах.

- [Иерархии в Visual Studio](../../extensibility/internals/hierarchies-in-visual-studio.md)

 Описывает [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , как представления и иерархии адресов.

- [VSPackages](../../extensibility/internals/vspackages.md)

 Содержит общие сведения о VSPackage, устанавливаемый COM-объект, который расширяет [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] среду и обсуждает реализацию собственного пакета VSPackage.

- [Типы проектов](../../extensibility/internals/project-types.md)

 Описывает, как использовать проекты для изменения кода, компиляции и построения кода, а также выполнения и отладки кода и предоставляет ссылки на подробные разделы, посвященные созданию типов проектов.
