---
title: Создание проверок компонентов и пакетов для решений SharePoint
titleSuffix: ''
description: Создайте пользовательские правила проверки для проверки пакета решения, созданного Visual Studio, или для проверки всего компонента.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, extending deployment
- SharePoint development in Visual Studio, validation rules
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: ee6b27b92f1c79bfda95ba3d6dce7dbdce4a6fac
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/02/2021
ms.locfileid: "106216570"
---
# <a name="create-feature-and-package-validations-for-sharepoint-solutions"></a>Создание проверок компонентов и пакетов для решений SharePoint

  Можно создать пользовательские правила проверки, чтобы проверить пакет решения, созданный Visual Studio. Полную проверку для всей функции или пакета можно выполнить, выбрав пункт **проверить** в контекстном меню пакета или функции в **паккагинжексплорер**. Частичная проверка выполняется при добавлении в проект новых элементов или компонентов проекта SharePoint для определения того, что пакет или компонент будет находиться в допустимом состоянии.

### <a name="to-create-a-custom-package-validation-rule"></a>Создание настраиваемого правила проверки пакета

1. Создайте проект библиотеки классов.

2. Добавьте ссылки на следующие сборки:

    - Microsoft. VisualStudio. SharePoint

    - System.ComponentModel.Composition

3. Создайте класс, реализующий один из следующих интерфейсов:

    - Чтобы создать правило проверки пакета, реализуйте <xref:Microsoft.VisualStudio.SharePoint.Validation.IPackageValidationRule> интерфейс.

    - Чтобы создать правило проверки компонентов, реализуйте <xref:Microsoft.VisualStudio.SharePoint.Validation.IFeatureValidationRule> интерфейс.

4. Добавьте в <xref:System.ComponentModel.Composition.ExportAttribute> класс. Этот атрибут позволяет Visual Studio обнаруживать и загружать правило проверки. Передайте <xref:Microsoft.VisualStudio.SharePoint.Validation.IPackageValidationRule> тип или в <xref:Microsoft.VisualStudio.SharePoint.Validation.IFeatureValidationRule> конструктор атрибута.

## <a name="example"></a>Пример
 В следующем примере кода показано, как создать настраиваемое правило проверки компонентов.

 :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/featurevalidation/extension/customvalidationrule.vb" id="Snippet1":::
 :::code language="csharp" source="../sharepoint/codesnippet/CSharp/featurevalidation/extension/customfeaturevalidationrule.cs" id="Snippet1":::

## <a name="compile-the-code"></a>Компиляция кода
 Для этого примера требуются ссылки на следующие сборки:

- Microsoft. VisualStudio. SharePoint.

- System. ComponentModel. композиция.

## <a name="deploy-the-extension"></a>Развертывание расширения
 Чтобы развернуть расширение, создайте [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] пакет расширения (VSIX) для сборки и всех остальных файлов, которые требуется распространить с расширением. Дополнительные сведения см. [в статье Развертывание расширений для инструментов SharePoint в Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

## <a name="see-also"></a>См. также раздел
- [Расширение упаковки и развертывания SharePoint](../sharepoint/extending-sharepoint-packaging-and-deployment.md)
