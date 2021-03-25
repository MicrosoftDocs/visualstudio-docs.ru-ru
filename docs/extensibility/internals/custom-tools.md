---
title: Настраиваемые инструменты | Документация Майкрософт
description: Узнайте, как создавать пользовательские инструменты в Visual Studio, которые связывают средство с элементом в проекте и запускают это средство при каждом сохранении файла.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, custom tools
- tools [Visual Studio], custom
- custom tools
ms.assetid: d669f154-9b23-48b6-b9f6-7419c8dd61a6
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: d714822605178382ec2ef3574db617f7986cf888
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105091049"
---
# <a name="custom-tools"></a>Специальные инструменты
*Пользовательские средства* позволяют связать средство с элементом в проекте и запускать его при каждом сохранении файла. Некоторые пользовательские средства, иногда называемые *генераторами с одним файлом*, часто используются для реализации переводчиков, создающих код на основе данных и наоборот. Например, генераторы с одним файлом создают [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] и [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] *исключают* исходный код из файлов. Settings и *. resx* . Созданный исходный код предоставляет строго типизированный доступ к данным в файлах *. Settings* и *. resx* . [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] Типы проектов и поддерживают пользовательские средства; [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] типы проектов — нет. Собственные типы проектов также могут поддерживать пользовательские средства.

 Пользовательские средства — это зарегистрированные компоненты, реализующие `IVsSingleFileGenerator` интерфейс.

 Пользовательские инструменты связаны с `ProjectItem` объектом интерфейса и подобны конструкторам и редакторам. Пользовательский инструмент принимает файл, представленный в `ProjectItem` качестве входных данных, и записывает новый файл, имя которого предоставляется `DefaultExtension` методом.

## <a name="in-this-section"></a>Содержание раздела
- [Реализация генераторов с одним файлом](../../extensibility/internals/implementing-single-file-generators.md)

 Описывает использование <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator> интерфейса для реализации пользовательского инструмента.

- [Регистрация генераторов одиночных файлов](../../extensibility/internals/registering-single-file-generators.md)

 Содержит описания всех записей реестра для пользовательского инструмента.

- [Предоставление типов для визуальных конструкторов](../../extensibility/internals/exposing-types-to-visual-designers.md)

 Объясняет, как системы проектов обеспечивают поддержку визуальных конструкторов для доступа к создаваемым классам и типам через временные переносимые исполняемые файлы (PE).

- [Сохранение свойства элемента проекта](../../extensibility/persisting-the-property-of-a-project-item.md)

 Показывает, как сохранить свойство элемента проекта, например автора исходного файла, в файле проекта.

## <a name="reference"></a>Справочник
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator> Предоставляет подробные сведения о компоненте <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator> , который преобразует один входной файл в отдельный выходной файл, который может быть скомпилирован или добавлен в проект.

 <xref:EnvDTE.ProjectItem> Описывает `ProjectItem` интерфейс, который представляет элемент в проекте.

 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.DefaultExtension%2A> Предоставляет подробные сведения о `DefaultExtension` методе, который извлекает расширение имени файла, присвоенное имени выходного файла.

## <a name="related-sections"></a>Связанные разделы
- [Расширение проектов](../../extensibility/extending-projects.md)

 Описывается использование проектов и решений [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] для организации файлов кода и файлов ресурсов, а также реализация системы управления версиями.
