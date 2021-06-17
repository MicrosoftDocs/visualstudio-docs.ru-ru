---
title: Инструкции. Создание веб-части SharePoint с помощью конструктора | Документация Майкрософт
titleSuffix: ''
description: Создайте веб-часть, добавив элемент визуальной веб-части в проект SharePoint, который открывает конструктор Visual Web Developer в Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Web Parts [SharePoint development in Visual Studio], designer
- Web Parts [SharePoint development in Visual Studio], adding
- Web Parts [SharePoint development in Visual Studio], creating
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: cbbb290af0029329910a23a71f68024ee0e5e5f4
ms.sourcegitcommit: 1f27f33852112702ee35fbc0c02fba37899e4cf5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2021
ms.locfileid: "112112383"
---
# <a name="how-to-create-a-sharepoint-web-part-by-using-a-designer"></a>Инструкции. Создание веб-части SharePoint с помощью конструктора

  Веб-часть можно создать путем добавления **визуального элемента веб-части** в любой проект SharePoint. Откроется конструктор Visual Web Developer в Visual Studio, в котором можно добавить элементы управления и код в веб-часть. Визуальные веб-части работают так же, как и веб-части. Единственное отличие заключается в проектировании визуальных веб-частей в конструкторе Visual Web Developer.

## <a name="to-create-a-project-for-visual-web-parts"></a>Создание проекта для визуальных веб-частей

1. В строке меню выберите **Файл** >**Создать** > **Проект**.
::: moniker range="=vs-2017"

2. В диалоговом окне **Новый проект** в разделе **Visual C#** или **Visual Basic** разверните узел **Office/SharePoint** , а затем выберите категорию **решения SharePoint** .

3. В списке шаблонов проектов выберите **SharePoint 2013 — Визуальная веб-часть**, а затем нажмите кнопку **ОК** .

     Откроется **Мастер настройки SharePoint** .
::: moniker-end
::: moniker range=">=vs-2019"
2. В диалоговом окне **Создание нового проекта** выберите *визуальную веб-часть SharePoint** для конкретной установленной версии SharePoint. Например, если установлен SharePoint 2019, выберите шаблон **веб-части sharepoint 2019-Visual** .
    [!INCLUDE[new-project-dialog-search](../sharepoint/includes/new-project-dialog-search-md.md)]

3. Измените имя проекта, если хотите, а затем нажмите кнопку **создать** .

::: moniker-end
4. На странице **Укажите сайт и уровень безопасности для отладки** укажите URL-адрес сайта SharePoint, который находится на локальном компьютере, а затем нажмите кнопку **Готово** .

     В **Обозреватель решений** отображается веб-часть. После разработки веб-части в конструкторе Visual Web Developer вы протестируете его на указанном сайте.

### <a name="to-add-a-visual-web-part-to-an-existing-sharepoint-project"></a>Добавление визуальной веб-части в существующий проект SharePoint

1. В строке меню выберите **Проект** > **Добавить новый элемент**.

2. В диалоговом окне **Добавление нового элемента** выберите узел **Office/SharePoint** .

3. В списке шаблонов проектов выберите **Визуальная веб-часть**, присвойте ей имя, а затем нажмите кнопку **Добавить** .

     В **Обозреватель решений** откроется веб-часть. После разработки веб-части в конструкторе Visual Web Developer вы протестируете его на указанном сайте.

## <a name="see-also"></a>См. также раздел

- [Создание веб-частей для SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md)
- [Практическое руководство. Создание веб-части SharePoint](../sharepoint/how-to-create-a-sharepoint-web-part.md)
- [Пошаговое руководство: создание веб-части для SharePoint](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint.md)
- [Пошаговое руководство: создание веб-части для SharePoint с помощью конструктора](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint-by-using-a-designer.md)
