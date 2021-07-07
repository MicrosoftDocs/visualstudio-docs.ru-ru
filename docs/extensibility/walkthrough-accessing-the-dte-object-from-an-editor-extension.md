---
title: Доступ к объекту DTE из расширения редактора
description: Это пошаговое руководство содержит пример кода, демонстрирующий доступ к объекту DTE из расширения редактора.
ms.custom: SEO-VS-2020
ms.date: 04/24/2019
ms.topic: tutorial
helpviewer_keywords:
- editors [Visual Studio SDK], new - getting the DTE object
ms.assetid: c1f40bab-c6ec-45b0-8333-ea5ceb02a39d
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 094a37960fa5b32d018eebe3becee4fde43cc392
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/25/2021
ms.locfileid: "112905128"
---
# <a name="walkthrough-access-the-dte-object-from-an-editor-extension"></a>Пошаговое руководство. Доступ к объекту DTE из расширения редактора

Работая с VSPackages, вы можете получить объект DTE, вызвав метод <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> с типом такого объекта. В расширениях Managed Extensibility Framework (MEF) можно импортировать <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider>, а затем вызвать метод <xref:Microsoft.VisualStudio.Shell.ServiceProvider.GetService%2A> с типом <xref:EnvDTE.DTE>.

## <a name="prerequisites"></a>Предварительные требования

Для выполнения этого пошагового руководства необходимо установить пакет SDK для Visual Studio. См. дополнительные сведения о пакете [SDK для Visual Studio](../extensibility/visual-studio-sdk.md).

## <a name="get-the-dte-object"></a>Получает объект DTE.

1. Создайте в VSIX проект на C# и назовите его **DTETest**. Добавьте шаблон элемента **Editor Classifier** (Классификатор редактора) и назовите его **DTETest**.

   Дополнительные сведения: [Создание расширения с помощью шаблона элемента редактора](../extensibility/creating-an-extension-with-an-editor-item-template.md).

::: moniker range=">=vs-2019"

2. Добавьте в проект ссылки на следующие сборки:

    - Microsoft.VisualStudio.Shell.Framework
    - Microsoft.VisualStudio.Shell.Immutable.10.0

3. Добавьте в файл *DTETestProvider.cs* следующие директивы `using`:

    ```csharp
    using EnvDTE;
    using Microsoft.VisualStudio.Shell;
    ```

4. Импортируйте в класс `DTETestProvider` элемент <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider>.

    ```csharp
    [Import]
    internal SVsServiceProvider ServiceProvider = null;
    ```

5. Добавьте в метод `GetClassifier()` следующий код перед инструкцией `return`:

    ```csharp
   ThreadHelper.ThrowIfNotOnUIThread();
   DTE dte = (DTE)ServiceProvider.GetService(typeof(DTE));
   ```

::: moniker-end

::: moniker range="vs-2017"

2. Добавьте в проект ссылки на следующие сборки:

   - EnvDTE
   - Microsoft.VisualStudio.Shell.Framework

3. Добавьте в файл *DTETestProvider.cs* следующие директивы `using`:

    ```csharp
    using EnvDTE;
    using Microsoft.VisualStudio.Shell;
    ```

4. Импортируйте в класс `DTETestProvider` элемент <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider>.

    ```csharp
    [Import]
    internal SVsServiceProvider ServiceProvider = null;
    ```

5. Добавьте в метод `GetClassifier()` следующий код перед инструкцией `return`:

    ```csharp
   DTE dte = (DTE)ServiceProvider.GetService(typeof(DTE));
   ```

::: moniker-end

## <a name="see-also"></a>См. также

- [Языковая служба и точки расширения редактора](../extensibility/language-service-and-editor-extension-points.md)
- [Запуск Visual Studio с помощью DTE](launch-visual-studio-dte.md)
