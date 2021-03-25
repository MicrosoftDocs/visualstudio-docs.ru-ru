---
title: Связывание типа содержимого с расширением имени файла
description: Узнайте, как связать собственный тип содержимого с расширением имени файла с помощью редактора Managed Extensibility Framework расширений в этом пошаговом руководстве.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- editors [Visual Studio SDK], new - link content type to file name extension
ms.assetid: 21ee64ce-9afe-4b08-94a0-8389cc4dc67c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 990f10fe82b9230c12ba13d736750f2f644c3ee5
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105078452"
---
# <a name="walkthrough-link-a-content-type-to-a-file-name-extension"></a>Пошаговое руководство. Связывание типа содержимого с расширением имени файла
Можно определить собственный тип содержимого и связать с ним расширение имени файла с помощью расширений Managed Extensibility Framework (MEF). В некоторых случаях расширение имени файла уже определено языковой службой. Однако, чтобы использовать его с MEF, необходимо по-прежнему связать его с типом содержимого.

## <a name="prerequisites"></a>Предварительные требования
 Начиная с Visual Studio 2015, пакет SDK для Visual Studio не устанавливается из центра загрузки. Он входит в состав программы установки Visual Studio как дополнительный компонент. Пакет SDK для VS можно установить и позже. Дополнительные сведения см. [в статье Установка пакета SDK для Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-mef-project"></a>Создание проекта MEF

1. Создание проекта VSIX C#. (В диалоговом окне **Новый проект** выберите **Visual C#/Extensibility**, а затем **проект VSIX**.) Присвойте решению имя `ContentTypeTest` .

2. В файле **source. extension. vsixmanifest** перейдите на вкладку **активы** и задайте для поля **Тип** значение **Microsoft. VisualStudio. MefComponent**, поле **источник** для **проекта в текущем решении**, а в поле **проект** — имя проекта.

## <a name="define-the-content-type"></a>Определение типа содержимого

1. Добавьте файл класса с именем `FileAndContentTypes`.

2. Добавьте ссылки на следующие сборки:

    1. System.ComponentModel.Composition

    2. Microsoft. VisualStudio. Text. Logic

    3. Microsoft. VisualStudio. Кореутилити

3. Добавьте следующие `using` директивы.

    ```csharp
    using System.ComponentModel.Composition;
    using Microsoft.VisualStudio.Text.Classification;
    using Microsoft.VisualStudio.Utilities;

    ```

4. Объявите статический класс, содержащий определения.

    ```csharp
    internal static class FileAndContentTypeDefinitions
    {. . .}
    ```

5. В этом классе экспортируйте <xref:Microsoft.VisualStudio.Utilities.ContentTypeDefinition> с именем "HID" и объявите его базовое определение как "Text".

    ```csharp
    internal static class FileAndContentTypeDefinitions
    {
        [Export]
        [Name("hid")]
        [BaseDefinition("text")]
        internal static ContentTypeDefinition hidingContentTypeDefinition;
    }
    ```

## <a name="link-a-file-name-extension-to-a-content-type"></a>Связывание расширения имени файла с типом содержимого

- Чтобы преобразовать этот тип содержимого в расширение имени файла, экспортируйте объект с <xref:Microsoft.VisualStudio.Utilities.FileExtensionToContentTypeDefinition> расширением *HID* и типом содержимого "HID".

    ```csharp
    internal static class FileAndContentTypeDefinitions
    {
         [Export]
         [Name("hid")]
         [BaseDefinition("text")]
        internal static ContentTypeDefinition hidingContentTypeDefinition;

         [Export]
         [FileExtension(".hid")]
         [ContentType("hid")]
        internal static FileExtensionToContentTypeDefinition hiddenFileExtensionDefinition;
    }
    ```

## <a name="add-the-content-type-to-an-editor-export"></a>Добавление типа содержимого в экспортируемый редактор

1. Создайте расширение редактора. Например, можно использовать расширение глифа поля, описанное в [разделе Пошаговое руководство. Создание глифа поля](../extensibility/walkthrough-creating-a-margin-glyph.md).

2. Добавьте класс, определенный в этой процедуре.

3. При экспорте класса расширения добавьте <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> к нему тип "HID".

    ```csharp
    [Export]
    [ContentType("hid")]
    ```

## <a name="see-also"></a>См. также
- [Точки расширения языковой службы и редактора](../extensibility/language-service-and-editor-extension-points.md)
