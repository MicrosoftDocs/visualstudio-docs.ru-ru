---
title: Пошаговое руководство. вызов кода в надстройке VSTO из VBA
description: Узнайте, как предоставить объект в надстройке VSTO другим Microsoft Officeным решениям, включая Visual Basic для приложений (VBA) и надстройки VSTO для COM.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- VBA [Office development in Visual Studio], calling code in application-level add-ins
- application-level add-ins [Office development in Visual Studio], calling code from other solutions
- Video How tos, Office development in Visual Studio
- calling add-in code
- add-ins [Office development in Visual Studio], calling code from other solutions
- interoperability [Office development in Visual Studio]
- calling code from VBA
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 21e0928396327911ea794c6270340c6efd27a43e
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/21/2021
ms.locfileid: "107824605"
---
# <a name="walkthrough-call-code-in-a-vsto-add-in-from-vba"></a>Пошаговое руководство. вызов кода в надстройке VSTO из VBA
  В этом пошаговом руководстве показано, как предоставить объект в надстройке VSTO другим решениям Microsoft Office, включая Visual Basic для приложений (VBA) и надстроек VSTO COM.

 [!INCLUDE[appliesto_allapp](../vsto/includes/appliesto-allapp-md.md)]

 Хотя в этом пошаговом руководстве используется Excel, рассмотренная процедура применима к любому шаблону проекта надстройки VSTO, которые предоставляет Visual Studio.

 В этом пошаговом руководстве описаны следующие задачи:

- Определение класса, который может быть предоставлен другим решениям Office.

- Предоставление класса другим решениям Office.

- Вызов метода класса из кода VBA.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Предварительные требования
 Для выполнения этого пошагового руководства требуются следующие компоненты:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- Microsoft Excel

## <a name="create-the-vsto-add-in-project"></a>Создание проекта надстройки VSTO
 Первым шагом является создание проекта надстройки VSTO для Excel.

### <a name="to-create-a-new-project"></a>Создание нового проекта

1. Создайте проект надстройки VSTO для Excel с именем **ExcelImportData** с помощью шаблона проекта надстройки VSTO для Excel. Дополнительные сведения см. в разделе [How to: Create Office Projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] открывает файл кода **ThisAddIn. CS** или **ThisAddIn. vb** и добавляет проект **ExcelImportData** в **Обозреватель решений**.

## <a name="define-a-class-that-you-can-expose-to-other-office-solutions"></a>Определение класса, который можно предоставлять другим решениям Office
 В этом пошаговом руководстве описывается вызов метода `ImportData` класса с именем `AddInUtilities` в надстройке VSTO из кода VBA. Этот метод записывает строку в ячейку A1 активного листа.

 Для предоставления класса `AddInUtilities` другим решениям Office необходимо сделать класс общедоступным и видимым для COM. Необходимо также предоставить интерфейс [IDispatch](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch) в классе. Код в следующей процедуре демонстрирует один из способов выполнения этих требований. Для получения дополнительной информации см. [Calling Code in VSTO Add-ins from Other Office Solutions](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md).

### <a name="to-define-a-class-that-you-can-expose-to-other-office-solutions"></a>Определение класса, который можно предоставить другим решениям Office

1. В меню **Проект** выберите пункт **Добавить класс**.

2. В диалоговом окне **Добавить новый элемент** измените имя нового класса на **AddInUtilities** и нажмите кнопку **Добавить**.

     В редакторе кода откроется файл **AddInUtilities.cs** или **AddInUtilities.vb** .

3. Добавьте следующие директивы в начало файла.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_AddInInteropWalkthrough/AddInUtilities.cs" id="Snippet2":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_AddInInteropWalkthrough/AddInUtilities.vb" id="Snippet2":::

4. Замените класс `AddInUtilities` на следующий код.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_AddInInteropWalkthrough/AddInUtilities.cs" id="Snippet3":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_AddInInteropWalkthrough/AddInUtilities.vb" id="Snippet3":::

     Этот код делает класс `AddInUtilities` видимым для COM, а также добавляет метод `ImportData` в класс. Для предоставления интерфейса [IDispatch](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch) класс `AddInUtilities` также содержит атрибут <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> , который реализует интерфейс, видимый для COM.

## <a name="expose-the-class-to-other-office-solutions"></a>Предоставление класса другим решениям Office
 Для предоставления класса `AddInUtilities` другим решениям Office переопределите метод <xref:Microsoft.Office.Tools.AddInBase.RequestComAddInAutomationService%2A> в классе `ThisAddIn` . В переопределении верните экземпляр класса `AddInUtilities` .

### <a name="to-expose-the-addinutilities-class-to-other-office-solutions"></a>Предоставление класса AddInUtilities другим решениям Office

1. В **обозревателе решений** разверните **Excel**.

2. Щелкните правой кнопкой мыши **ThisAddIn.cs** или **ThisAddIn.vb**, а затем выберите пункт **Просмотреть код**.

3. Добавьте в класс `ThisAddIn` приведенный далее код.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_AddInInteropWalkthrough/ThisAddIn.cs" id="Snippet1":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_AddInInteropWalkthrough/ThisAddIn.vb" id="Snippet1":::

4. В меню **Сборка** выберите **Собрать решение**.

     Убедитесь, что сборка решения выполняется без ошибок.

## <a name="test-the-vsto-add-in"></a>Тестирование надстройки VSTO
 Класс `AddInUtilities` можно вызывать из решений Office различного типа. В этом пошаговом руководстве будет использоваться код VBA в книге Excel. Дополнительные сведения о других типах решений Office, которые также можно использовать, см. [в разделе вызов кода в надстройках VSTO из других решений Office](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md).

### <a name="to-test-your-vsto-add-in"></a>Для тестирования надстройки VSTO выполните следующие действия.

1. Нажмите клавишу **F5** , чтобы запустить проект.

2. В Excel сохраните активную книгу как книгу Excel с поддержкой макросов (*.xlsm). Сохраните ее в удобном месте, например на рабочем столе.

3. На ленте перейдите на вкладку **Разработчик** .

    > [!NOTE]
    > Если вкладка **Разработчик** не отображается, сделайте ее видимой. Дополнительные сведения см. в разделе [инструкции. Отображение вкладки разработчика на ленте](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).

4. В группе **Код** щелкните **Visual Basic**.

     Открывается редактор Visual Basic.

5. В окне **Проект** дважды щелкните **ThisWorkbook**.

     Открывается файл кода для объекта `ThisWorkbook` .

6. Добавьте следующий код VBA в файл кода. Этот код сначала получает объект Комаддин, представляющий надстройку **ExcelImportData** VSTO. Затем код использует свойство Object объекта Комаддин для вызова `ImportData` метода.

    ```vb
    Sub CallVSTOMethod()
        Dim addIn As COMAddIn
        Dim automationObject As Object
        Set addIn = Application.COMAddIns("ExcelImportData")
        Set automationObject = addIn.Object
        automationObject.ImportData
    End Sub
    ```

7. Нажмите клавишу **F5**.

8. Убедитесь, что новый лист **Imported Data** (Импортированные данные) добавлен в книгу. Также убедитесь, что ячейка A1 содержит строку **This is my data**(Это мои данные).

9. Выйдите из Excel.

## <a name="next-steps"></a>Дальнейшие действия
 Дополнительные сведения о программировании надстроек VSTO см. в следующих статьях:

- Для автоматизации ведущего приложения и выполнения других задач в проектах надстроек VSTO используйте класс `ThisAddIn` . Дополнительные сведения см. в разделе [программирование VSTO Add-ins](../vsto/programming-vsto-add-ins.md).

- Создание настраиваемой области задач в надстройке VSTO. Дополнительные сведения см. в статьях [пользовательские области задач](../vsto/custom-task-panes.md) и [инструкции: Добавление настраиваемой области задач в приложение](../vsto/how-to-add-a-custom-task-pane-to-an-application.md).

- Настройка ленты в надстройке VSTO. Дополнительные сведения см. в статьях [Общие сведения о ленте](../vsto/ribbon-overview.md) и [инструкции. Приступая к настройке ленты](../vsto/how-to-get-started-customizing-the-ribbon.md).

## <a name="see-also"></a>См. также статью
- [Программирование надстроек VSTO](../vsto/programming-vsto-add-ins.md)
- [Вызов кода в надстройках VSTO из других решений Office](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md)
- [Разработка решений Office](../vsto/developing-office-solutions.md)
- [Как создавать проекты Office в Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Architecture of VSTO Add-ins](../vsto/architecture-of-vsto-add-ins.md)
- [Настройка функций пользовательского интерфейса с помощью интерфейсов расширяемости](../vsto/customizing-ui-features-by-using-extensibility-interfaces.md)
