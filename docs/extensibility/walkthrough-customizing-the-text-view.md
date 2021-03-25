---
title: Пошаговое руководство. Настройка представления текста | Документация Майкрософт
description: Узнайте, как настроить представление текста, изменив любое из нескольких свойств в сопоставлении формата редактора с помощью этого пошагового руководства.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- editors [Visual Studio SDK], new - customizing the view
ms.assetid: 32d32ac8-22ff-4de7-af69-bd46ec4ad9bf
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 17aa8644fc4823df5b68378e9045fa190980306d
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105080311"
---
# <a name="walkthrough-customize-the-text-view"></a>Пошаговое руководство. Настройка представления текста
Можно настроить представление текста, изменив любое из следующих свойств в его сопоставлении в формате редактора:

- Поле индикаторов

- Курсор вставки

- Перезаписать курсор

- Выделенный текст

- Неактивный выделенный текст (т. е. выбранный текст, который потерял фокус)

- Видимый пробел

## <a name="prerequisites"></a>Предварительные требования
 Начиная с Visual Studio 2015, пакет SDK для Visual Studio не устанавливается из центра загрузки. Он входит в состав программы установки Visual Studio как дополнительный компонент. Пакет SDK для VS можно установить и позже. Дополнительные сведения см. [в статье Установка пакета SDK для Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-mef-project"></a>Создание проекта MEF

1. Создание проекта VSIX C#. (В диалоговом окне **Новый проект** выберите **Visual C#/Extensibility**, а затем **проект VSIX**.) Присвойте решению имя `ViewPropertyTest` .

2. Добавьте шаблон элемента классификатора редактора в проект. Дополнительные сведения см. в разделе [Создание расширения с помощью шаблона элемента редактора](../extensibility/creating-an-extension-with-an-editor-item-template.md).

3. Удалите файлы существующих классов.

## <a name="define-the-content-type"></a>Определение типа содержимого

1. Добавьте файл класса с именем `ViewPropertyModifier`.

2. Затем добавьте следующие `using` директивы:

    [!code-csharp[VSSDKViewPropertyTest#1](../extensibility/codesnippet/CSharp/walkthrough-customizing-the-text-view_1.cs)]
    [!code-vb[VSSDKViewPropertyTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-customizing-the-text-view_1.vb)]

3. Объявите класс с именем `TestViewCreationListener` , наследуемый от <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener> . Экспортируйте этот класс со следующими атрибутами:

   - <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> для указания типа содержимого, к которому применяется этот прослушиватель.

   - <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute> для указания роли этого прослушивателя.

     [!code-csharp[VSSDKViewPropertyTest#2](../extensibility/codesnippet/CSharp/walkthrough-customizing-the-text-view_2.cs)]
     [!code-vb[VSSDKViewPropertyTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-customizing-the-text-view_2.vb)]

4. В этом классе импортируйте <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMapService> .

    [!code-csharp[VSSDKViewPropertyTest#3](../extensibility/codesnippet/CSharp/walkthrough-customizing-the-text-view_3.cs)]
    [!code-vb[VSSDKViewPropertyTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-customizing-the-text-view_3.vb)]

## <a name="change-the-view-properties"></a>Изменение свойств представления

1. Настройте <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener.TextViewCreated%2A> метод таким образом, чтобы свойства представления изменялись при открытии представления. Чтобы внести изменения, сначала найдите объект <xref:System.Windows.ResourceDictionary> , соответствующий аспекту представления, которое необходимо найти. Затем измените соответствующее свойство в словаре ресурсов и задайте свойства. Выполните пакетную обработку вызовов <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap.SetProperties%2A> метода, вызвав <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap.BeginBatchUpdate%2A> метод до задания свойств, а затем <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap.EndBatchUpdate%2A> после установки свойств.

     [!code-csharp[VSSDKViewPropertyTest#4](../extensibility/codesnippet/CSharp/walkthrough-customizing-the-text-view_4.cs)]
     [!code-vb[VSSDKViewPropertyTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-customizing-the-text-view_4.vb)]

## <a name="build-and-test-the-code"></a>Сборка и тестирование кода

1. Создайте решение.

     При запуске этого проекта в отладчике запускается второй экземпляр Visual Studio.

2. Создайте текстовый файл и введите любой текст.

    - Курсор вставки должен быть пурпурным, а курсор перезаписи должен быть бирюзовым.

    - Поле индикатора (слева от текстового представления) должно быть светло-зеленым.

3. Выберите набранный текст. Цвет выделенного текста должен быть светло-розовый.

4. Пока текст выбран, щелкните в любом месте за пределами текстового окна. Цвет выделенного текста должен быть темно-розовым.

5. Включите видимый пробел. (В меню **Правка** наведите указатель на пункт **Дополнительно** и выберите пункт **Показать пустое пространство**). Введите в текст некоторые вкладки. Должны отобразиться красные стрелки, представляющие вкладки.

## <a name="see-also"></a>См. также
- [Точки расширения языковой службы и редактора](../extensibility/language-service-and-editor-extension-points.md)
