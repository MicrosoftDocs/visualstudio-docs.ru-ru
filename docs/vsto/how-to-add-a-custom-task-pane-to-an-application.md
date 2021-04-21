---
title: Как добавить настраиваемую область задач в приложение
description: Узнайте, как можно добавить настраиваемую область задач в приложения с помощью надстройки Инструменты Visual Studio для Office (VSTO).
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- task panes [Office development in Visual Studio], adding to application
- custom task panes [Office development in Visual Studio], adding to application
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: d85edb9773783abe6282918c432fc1a4eff83944
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/21/2021
ms.locfileid: "107826724"
---
# <a name="how-to-add-a-custom-task-pane-to-an-application"></a>Как добавить настраиваемую область задач в приложение
  Вы можете добавить настраиваемую область задач в приложения, перечисленные выше, с помощью надстройки VSTO. Дополнительные сведения см. в разделе [настраиваемые области задач](../vsto/custom-task-panes.md).

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

> [!NOTE]
> Отображаемые на компьютере имена или расположения некоторых элементов пользовательского интерфейса Visual Studio могут отличаться от указанных в следующих инструкциях. Это зависит от имеющегося выпуска Visual Studio и используемых параметров. Дополнительные сведения см. в разделе [Персонализация интегрированной среды разработки Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="add-a-custom-task-pane-to-an-application"></a>Добавление настраиваемой области задач в приложение

### <a name="to-add-a-custom-task-pane-to-an-application"></a>Добавление настраиваемой панели задач в приложение

1. Откройте или создайте проект надстройки VSTO для одного из приложений, указанных выше. Дополнительные сведения см. в разделе [как создавать проекты Office в Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

2. В меню **Проект** выберите команду **Добавить пользовательский элемент управления**.

3. В диалоговом окне **Добавление нового элемента** измените имя нового пользовательского элемента управления на **MyUserControl** и нажмите кнопку **добавить**.

     Пользовательский элемент управления откроется в конструкторе.

4. Добавьте один или несколько элементов управления Windows Forms из **панели элементов** в пользовательский элемент управления.

5. Откройте файл кода **ThisAddIn. CS** или **ThisAddIn. vb** .

6. Добавьте в класс `ThisAddIn` приведенный далее код. Этот код объявляет экземпляры `MyUserControl` и <xref:Microsoft.Office.Tools.CustomTaskPane> как члены класса `ThisAddIn` .

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_TaskPaneBasic/ThisAddIn.vb" id="Snippet1":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_TaskPaneBasic/ThisAddIn.cs" id="Snippet1":::

7. Добавьте следующий код в обработчик событий `ThisAddIn_Startup`. Этот код создает новый объект <xref:Microsoft.Office.Tools.CustomTaskPane> , добавляя  объект `MyUserControl` в коллекцию `CustomTaskPanes` . Код также отображает область задач.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_TaskPaneBasic/ThisAddIn.vb" id="Snippet2":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_TaskPaneBasic/ThisAddIn.cs" id="Snippet2":::

    > [!NOTE]
    > Этот код связывает настраиваемую область задач с активным окном приложения. Для некоторых приложений может потребоваться изменить этот код, чтобы убедиться, что область задач отображается с другими документами или элементами в приложении. Дополнительные сведения см. в разделе [настраиваемые области задач](../vsto/custom-task-panes.md).

## <a name="see-also"></a>См. также статью
- [Настройка пользовательского интерфейса Office](../vsto/office-ui-customization.md)
- [Настраиваемые области задач](../vsto/custom-task-panes.md)
- [Пошаговое руководство. Автоматизация приложения с помощью настраиваемой области задач](../vsto/walkthrough-automating-an-application-from-a-custom-task-pane.md)
