---
title: Доступ к объекту DTE из расширения редактора
description: Узнайте, как получить доступ к объекту DTE из расширения редактора, используя пример кода в этом пошаговом руководстве.
ms.custom: SEO-VS-2020
ms.date: 04/24/2019
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - getting the DTE object
ms.assetid: c1f40bab-c6ec-45b0-8333-ea5ceb02a39d
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 7035842f608428f149dd2c0965b4792afa25db67
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105062074"
---
# <a name="walkthrough-access-the-dte-object-from-an-editor-extension"></a>Пошаговое руководство. доступ к объекту DTE из расширения редактора

В VSPackage можно получить объект DTE, вызвав <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> метод с типом объекта DTE. В расширениях Managed Extensibility Framework (MEF) можно импортировать, <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider> а затем вызвать <xref:Microsoft.VisualStudio.Shell.ServiceProvider.GetService%2A> метод с типом <xref:EnvDTE.DTE> .

## <a name="prerequisites"></a>Предварительные требования

Для выполнения этого пошагового руководства необходимо установить пакет SDK для Visual Studio. Дополнительные сведения см. в разделе [пакет SDK для Visual Studio](../extensibility/visual-studio-sdk.md).

## <a name="get-the-dte-object"></a>Получает объект DTE.

1. Создайте проект VSIX C# и назовите его **дтетест**. Добавьте шаблон элемента **классификатора редактора** и назовите его **дтетест**.

   Дополнительные сведения см. в разделе [Создание расширения с помощью шаблона элемента редактора](../extensibility/creating-an-extension-with-an-editor-item-template.md).

::: moniker range=">=vs-2019"

2. Добавьте в проект следующие ссылки на сборки:

    - Microsoft. VisualStudio. Shell. Framework
    - Microsoft. VisualStudio. Shell. неизменяемый. 10.0

3. В файле *дтетестпровидер. CS* добавьте следующие `using` директивы:

    ```csharp
    using EnvDTE;
    using Microsoft.VisualStudio.Shell;
    ```

4. В `DTETestProvider` классе импортируйте <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider> .

    ```csharp
    [Import]
    internal SVsServiceProvider ServiceProvider = null;
    ```

5. В `GetClassifier()` метод добавьте следующий код перед `return` оператором:

    ```csharp
   ThreadHelper.ThrowIfNotOnUIThread();
   DTE dte = (DTE)ServiceProvider.GetService(typeof(DTE));
   ```

::: moniker-end

::: moniker range="vs-2017"

2. Добавьте в проект следующие ссылки на сборки:

   - EnvDTE
   - Microsoft. VisualStudio. Shell. Framework

3. В файле *дтетестпровидер. CS* добавьте следующие `using` директивы:

    ```csharp
    using EnvDTE;
    using Microsoft.VisualStudio.Shell;
    ```

4. В `DTETestProvider` классе импортируйте <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider> .

    ```csharp
    [Import]
    internal SVsServiceProvider ServiceProvider = null;
    ```

5. В `GetClassifier()` метод добавьте следующий код перед `return` оператором:

    ```csharp
   DTE dte = (DTE)ServiceProvider.GetService(typeof(DTE));
   ```

::: moniker-end

## <a name="see-also"></a>См. также

- [Точки расширения языковой службы и редактора](../extensibility/language-service-and-editor-extension-points.md)
- [Запуск Visual Studio с помощью DTE](launch-visual-studio-dte.md)
