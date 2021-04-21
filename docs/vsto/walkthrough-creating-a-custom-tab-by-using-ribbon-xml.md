---
title: Пошаговое руководство. Создание настраиваемой вкладки с помощью XML-ленты
description: Узнайте, как добавлять кнопки на вкладку Add-Ins и автоматизировать Microsoft Word с помощью ленты (XML).
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Ribbon [Office development in Visual Studio], tabs
- customizing the Ribbon, tabscustom Ribbon, tabs
- Ribbon [Office development in Visual Studio], XML
- XML [Office development in Visual Studio], Ribbon
- Ribbon [Office development in Visual Studio], customizing
- Custom tab [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: a5d7992462ac3ece9782b0168feedd87577c2d0e
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/21/2021
ms.locfileid: "107826334"
---
# <a name="walkthrough-create-a-custom-tab-by-using-ribbon-xml"></a>Пошаговое руководство. Создание настраиваемой вкладки с помощью XML-ленты
  В этом пошаговом руководстве показано, как создать настраиваемую вкладку ленты с помощью элемента **Лента (XML)** .

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

 В этом пошаговом руководстве описаны следующие задачи:

- Добавление кнопок на вкладку **надстройки** . Вкладка **надстройки** — это вкладка по умолчанию, определенная в XML-файле ленты.

- Автоматизация Microsoft Office Word с помощью кнопок на вкладке **надстройки** .

> [!NOTE]
> Отображаемые на компьютере имена или расположения некоторых элементов пользовательского интерфейса Visual Studio могут отличаться от указанных в следующих инструкциях. Это зависит от имеющегося выпуска Visual Studio и используемых параметров. Дополнительные сведения см. в разделе [Персонализация интегрированной среды разработки Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Предварительные требования
 Для выполнения этого пошагового руководства требуются следующие компоненты:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- Microsoft Word.

## <a name="create-the-project"></a>Создание проекта
 Первым шагом является создание проекта надстройки Word VSTO. Позже **на вкладке Надстройки** этого документа будут внесены изменения.

### <a name="to-create-a-new-project"></a>Создание нового проекта

1. Создайте проект **надстройки Word** с именем **мириббонаддин**.

     Дополнительные сведения см. в разделе [как создавать проекты Office в Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] открывает файл кода **ThisAddIn. CS** или **ThisAddIn. vb** и добавляет проект **мириббонаддин** в **Обозреватель решений**.

## <a name="create-the-vsto-add-ins-tab"></a>Создание вкладки надстроек VSTO
 Чтобы создать вкладку **надстройки** , добавьте в проект элемент **Лента (XML)** . Далее в этом пошаговом руководстве мы добавим некоторые кнопки на эту вкладку.

### <a name="to-create-the-add-ins-tab"></a>Создание вкладки «надстройки»

1. В меню **Проект** выберите **Добавить новый элемент**.

2. В диалоговом окне **Добавление нового элемента** выберите **Лента (XML)**.

3. Измените имя новой ленты на **MyRibbon** и нажмите кнопку **Добавить**.

     В конструкторе откроется файл **MyRibbon. CS** или **MyRibbon. vb** . В проект также добавляется XML-файл с именем **MyRibbon.xml** .

4. В **Обозреватель решений** щелкните правой кнопкой мыши **ThisAddIn. CS** или **ThisAddIn. vb** и выберите пункт **Просмотреть код**.

5. Добавьте следующий код в класс **ThisAddin** . Этот код переопределяет метод `CreateRibbonExtensibilityObject` и возвращает XML-класс ленты в приложение Office.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_Ribbon_Custom_Tab_XML_O12/ThisAddIn.cs" id="Snippet1":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_Ribbon_Custom_Tab_XML_O12/ThisAddIn.vb" id="Snippet1":::

6. В **Обозреватель решений** щелкните правой кнопкой мыши проект **мириббонаддин** и выберите пункт **Сборка**. Убедитесь, что сборка проекта выполняется без ошибок.

## <a name="add-buttons-to-the-add-ins-tab"></a>Добавление кнопок на вкладку «надстройки»
 Данная надстройка VSTO предназначена для того, чтобы пользователи могли добавлять стандартный текст и конкретную таблицу в активный документ. Чтобы предоставить пользовательский интерфейс, добавьте две кнопки на вкладку **надстройки** , ИЗМЕНИВ XML-файл ленты. Далее в этом пошаговом руководстве мы определим методы обратного вызова для кнопок. Дополнительные сведения о XML-файле ленты см. в разделе [RIBBON XML](../vsto/ribbon-xml.md).

### <a name="to-add-buttons-to-the-add-ins-tab"></a>Добавление кнопок на вкладку «надстройки»

1. В **Обозреватель решений** щелкните правой кнопкой мыши **MyRibbon.xml** и выберите пункт **Открыть**.

2. Замените содержимое элемента **вкладки** следующим XML-кодом. Этот XML-файл изменяет метку группы элементов управления по умолчанию на **содержимое** и добавляет две новые кнопки с метками **Вставить текст** и **Вставить таблицу**.

    ```xml
    <tab idMso="TabAddIns">
        <group id="ContentGroup" label="Content">
            <button id="textButton" label="Insert Text"
                 screentip="Text" onAction="OnTextButton"
                 supertip="Inserts text at the cursor location."/>
            <button id="tableButton" label="Insert Table"
                 screentip="Table" onAction="OnTableButton"
                 supertip="Inserts a table at the cursor location."/>
        </group>
    </tab>
    ```

## <a name="automate-the-document-by-using-the-buttons"></a>Автоматизация документа с помощью кнопок
 Необходимо добавить `onAction` методы обратного вызова для кнопок **Вставить текст** и **Вставить таблицу** для выполнения действий, когда пользователь щелкнет их. Дополнительные сведения о методах обратного вызова для элементов управления ленты см. в разделе [RIBBON XML](../vsto/ribbon-xml.md).

### <a name="to-add-callback-methods-for-the-buttons"></a>Добавление методов обратного вызова для кнопок

1. В **Обозреватель решений** щелкните правой кнопкой мыши **MyRibbon. CS** или **MyRibbon. vb** и выберите команду **Открыть**.

2. Добавьте следующий код в начало файла **MyRibbon. CS** или **MyRibbon. vb** . Этот код создает псевдоним для пространства имен <xref:Microsoft.Office.Interop.Word>.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_RibbonButtons/MyRibbon.cs" id="Snippet1":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_RibbonButtons/MyRibbon.vb" id="Snippet1":::

3. Добавьте следующий метод в класс `MyRibbon`. Это метод обратного вызова для кнопки **Вставить текст** , который добавляет строку в активный документ в текущем положении курсора.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_Ribbon_Custom_Tab_XML_O12/MyRibbon.cs" id="Snippet2":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_Ribbon_Custom_Tab_XML_O12/MyRibbon.vb" id="Snippet2":::

4. Добавьте следующий метод в класс `MyRibbon`. Это метод обратного вызова для кнопки **Вставить таблицу** , который добавляет таблицу в активный документ в текущем положении курсора.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_Ribbon_Custom_Tab_XML_O12/MyRibbon.cs" id="Snippet3":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_Ribbon_Custom_Tab_XML_O12/MyRibbon.vb" id="Snippet3":::

## <a name="testing-the-vsto-add-in"></a>Тестирование надстройки VSTO
 При запуске проекта открывается Word, а на ленте появляется вкладка с именем **надстройки** . Нажмите кнопки **Вставить текст** и **Вставить таблицу** на вкладке **надстройки** , чтобы проверить код.

### <a name="to-test-your-vsto-add-in"></a>Для тестирования надстройки VSTO выполните следующие действия.

1. Нажмите клавишу **F5** , чтобы запустить проект.

2. Убедитесь, что вкладка **надстройки** отображается на ленте.

3. Перейдите на вкладку **Надстройки** .

4. Убедитесь, что группа **содержимого** отображается на ленте.

5. Нажмите кнопку **Вставить текст** в группе **содержимое** .

     Строка добавляется в документ в текущем положении курсора.

6. Нажмите кнопку **Вставить таблицу** в группе **содержимое** .

     Таблица добавляется в документ в текущем положении курсора.

## <a name="next-steps"></a>Дальнейшие действия
 Дополнительные сведения о настройке пользовательского интерфейса Office см. в следующих разделах:

- Настройка ленты для другого приложения Office. Дополнительные сведения о приложениях, поддерживающих настройку ленты, см. в разделе [Общие сведения о ленте](../vsto/ribbon-overview.md).

- Настройка ленты приложения Office с помощью конструктора лент. Для получения дополнительной информации см. [Ribbon Designer](../vsto/ribbon-designer.md).

- Создание настраиваемой панели действий. Дополнительные сведения см. в разделе [Общие сведения о панели действий](../vsto/actions-pane-overview.md).

- Настройка пользовательского интерфейса для Microsoft Office Outlook с помощью областей формы Outlook. Дополнительные сведения см. в разделе [Пошаговое руководство. Проектирование области формы Outlook](../vsto/walkthrough-designing-an-outlook-form-region.md).

## <a name="see-also"></a>См. также статью
- [Общие сведения о ленте](../vsto/ribbon-overview.md)
- [Ribbon XML](../vsto/ribbon-xml.md)
- [Пошаговое руководство. Создание настраиваемой вкладки с помощью конструктора лент](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)
