---
title: Пошаговое руководство. вызов кода из VBA в проекте Visual C#
description: Узнайте, как вызвать метод в настройке уровня документа для Microsoft Excel из кода Visual Basic для приложений (VBA) в книге.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Excel [Office development in Visual Studio], calling code from VBA
- Word [Office development in Visual Studio], calling code from VBA
- Visual C# [Office development in Visual Studio], calling code from VBA
- workbooks [Office development in Visual Studio], calling code from VBA
- VBA [Office development in Visual Studio], calling code in document-level customizations
- Office documents [Office development in Visual Studio, Visual Basic for Applications and
- calling code from VBA
- document-level customizations [Office development in Visual Studio], calling code
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 260872096f36f91a2618f636e297d3c48b3fe51b
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/21/2021
ms.locfileid: "107824475"
---
# <a name="walkthrough-call-code-from-vba-in-a-visual-c-project"></a>Пошаговое руководство. вызов кода из VBA в проекте Visual C#
  В этом пошаговом руководстве показано, как вызвать метод в настройке на уровне документа для Microsoft Office Excel из кода Visual Basic для приложений (VBA) в книге. Данная процедура состоит из трех основных этапов: добавление метода в класс ведущего элемента `Sheet1` , представление метода коду VBA в книге и вызов метода из кода VBA в книге.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 Хотя в этом пошаговом руководстве используется Excel, рассмотренная процедура также применима к проектам на уровне документа для Word.

 В этом пошаговом руководстве описаны следующие задачи:

- Создание книги, содержащей код VBA

- Предоставление доверия расположению книги с помощью центра управления безопасностью в Excel

- Добавление метода в класс ведущего элемента `Sheet1`

- Извлечение интерфейса для класса ведущего элемента `Sheet1`

- Представление метода коду VBA

- Вызов метода из кода VBA

> [!NOTE]
> Отображаемые на компьютере имена или расположения некоторых элементов пользовательского интерфейса Visual Studio могут отличаться от указанных в следующих инструкциях. Это зависит от имеющегося выпуска Visual Studio и используемых параметров. Дополнительные сведения см. в разделе [Персонализация интегрированной среды разработки Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Предварительные требования
 Для выполнения этого пошагового руководства требуются следующие компоненты:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- Microsoft Excel

## <a name="create-a-workbook-that-contains-vba-code"></a>Создание книги, содержащей код VBA
 Первым шагом является создание книги с поддержкой макросов, которая содержит простой макрос VBA. Прежде чем код в настройке можно будет предоставить VBA, книга уже должна содержать код VBA. В противном случае Visual Studio не сможет изменить проект VBA так, чтобы код VBA мог вызывать сборку настройки.

 Если у вас уже есть книга, содержащая код VBA, который необходимо использовать, данный шаг можно пропустить.

### <a name="to-create-a-workbook-that-contains-vba-code"></a>Создание книги, содержащей код VBA

1. Запустите Excel.

2. Сохраните активный документ в формате **Excel Macro-Enabled книги ( \* . xlsm)** с именем **WorkbookWithVBA**. Сохраните его в удобном месте, например на рабочем столе.

3. На ленте перейдите на вкладку **Разработчик** .

    > [!NOTE]
    > Если вкладка **Разработчик** не отображается, сделайте ее видимой. Дополнительные сведения см. в разделе [инструкции. Отображение вкладки разработчика на ленте](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).

4. В группе **Код** щелкните **Visual Basic**.

     Открывается редактор Visual Basic.

5. В окне **Проект** дважды щелкните **ThisWorkbook**.

     Открывается файл кода для объекта `ThisWorkbook` .

6. Добавьте следующий код VBA в файл кода. Этот код определяет простую функцию, которая не выполняет никаких действий. Данная функция предназначена исключительно для проверки наличия проекта VBA в книге. Это необходимо для выполнения последующих действий в данном пошаговом руководстве.

    ```vb
    Sub EmptySub()
    End Sub
    ```

7. Сохраните документ и выйдите из Excel.

## <a name="create-the-project"></a>Создание проекта
 Теперь можно создать проект на уровне документа для Excel, который использует созданную ранее книгу с поддержкой макросов.

### <a name="to-create-a-new-project"></a>Создание нового проекта

1. Запустите среду [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

2. В меню **Файл** выберите пункт **Создать**, а затем команду **Проект**.

3. В области шаблонов разверните узел **Visual C#**, а затем узел **Office/SharePoint**.

4. Выберите узел **Надстройки Office** .

5. В списке шаблонов проектов выберите проект **Книга Excel 2010** или **Книга Excel 2013** .

6. В поле **Имя** введите **CallingCodeFromVBA**.

7. Нажмите кнопку **ОК**.

     Откроется **Мастер проектов набора средств Visual Studio для Office** .

8. Выберите **Копировать существующий документ** и в поле **Полный путь к существующему документу** укажите расположение книги **WorkbookWithVBA** , которая была создана ранее. Если вы используете собственную книгу с поддержкой макросов, укажите расположение этой книги.

9. Нажмите кнопку **Готово**.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] открывает книгу **WorkbookWithVBA** в конструкторе и добавляет проект **проект callingcodefromvba** в **Обозреватель решений**.

## <a name="trust-the-location-of-the-workbook"></a>Доверять расположению книги
 Перед предоставлением кода в своем решении коду VBA в книге необходимо предоставить доверие VBA на выполнение в книге. Для этого существует несколько способов. В этом пошаговом руководстве данную задачу предстоит выполнить путем предоставления доверия расположению книги в **центре управления безопасностью** в Excel.

### <a name="to-trust-the-location-of-the-workbook"></a>Предоставление доверия расположению книги

1. Запустите Excel.

2. Перейдите на вкладку **Файл** .

3. Нажмите кнопку **Параметры Excel** .

4. В области категорий нажмите **Центр управления безопасностью**.

5. В области сведений нажмите **Параметры центра управления безопасностью**.

6. В области категорий нажмите **Надежные расположения**.

7. В области сведений нажмите **Добавить новое расположение**.

8. В диалоговом окне **Надежное расположение Microsoft Office** перейдите в папку, содержащую проект **CallingCodeFromVBA** .

9. Установите флажок **Также доверять всем вложенным папкам**.

10. В диалоговом окне **Надежное расположение Microsoft Office** нажмите кнопку **ОК**.

11. В диалоговом окне **Центр управления безопасностью** нажмите кнопку **ОК**.

12. В диалоговом окне **Параметры Excel** нажмите кнопку **ОК**.

13. Выйдите из **Excel**.

## <a name="add-a-method-to-the-sheet1-class"></a>Добавление метода в класс Sheet1
 Теперь, когда проект VBA настроен, добавьте открытый метод в класс ведущего элемента `Sheet1` , который можно вызвать из кода VBA.

### <a name="to-add-a-method-to-the-sheet1-class"></a>Порядок добавления метода в класс Sheet1

1. В **обозревателе решений** щелкните правой кнопкой мыши файл **Sheet1.cs** и выберите пункт **Просмотреть код**.

     Файл **Sheet1.cs** открывается в редакторе кода.

2. Добавьте в класс `Sheet1` приведенный далее код. Метод `CreateVstoNamedRange` создает новый объект <xref:Microsoft.Office.Tools.Excel.NamedRange> в указанном диапазоне. При этом также создается обработчик событий для события <xref:Microsoft.Office.Tools.Excel.NamedRange.Selected> в <xref:Microsoft.Office.Tools.Excel.NamedRange>. Далее в этом пошаговом руководстве будет вызван метод `CreateVstoNamedRange` из кода VBA в документе.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/CallingCodeFromVBA/Sheet1.cs" id="Snippet2":::

3. Добавьте следующий метод в класс `Sheet1`. Этот метод переопределяет метод <xref:Microsoft.Office.Tools.Excel.WorksheetBase.GetAutomationObject%2A> для возврата текущего экземпляра класса `Sheet1` .

     :::code language="csharp" source="../vsto/codesnippet/CSharp/CallingCodeFromVBA/Sheet1.cs" id="Snippet3":::

4. Примените следующие атрибуты перед первой строкой объявления класса `Sheet1` . Эти атрибуты делают класс видимым для модели COM, но без создания интерфейса класса.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/CallingCodeFromVBA/Sheet1.cs" id="Snippet1":::

## <a name="extract-an-interface-for-the-sheet1-class"></a>Извлечение интерфейса для класса Sheet1
 Перед предоставлением метода `CreateVstoNamedRange` коду VBA необходимо создать открытый интерфейс, который определяет данный метод, а также предоставить этот интерфейс модели COM.

### <a name="to-extract-an-interface-for-the-sheet1-class"></a>Извлечение интерфейса для класса Sheet1

1. В файле кода **Sheet1.cs** щелкните в любом месте внутри класса `Sheet1` .

2. В меню **Рефакторинг** выберите пункт **Извлечь интерфейс**.

3. В диалоговом окне **Извлечение интерфейса** в поле **Выбрать открытые методы для создания интерфейса** выберите значение для метода `CreateVstoNamedRange` .

4. Нажмите кнопку **ОК**.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] создает новый интерфейс с именем `ISheet1`и изменяет определение класса `Sheet1` , чтобы он реализовал интерфейс `ISheet1` . [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] также открывает файл **ISheet1. CS** в редакторе кода.

5. В файле **ISheet1.cs** замените объявление интерфейса `ISheet1` на следующий код. Этот код делает интерфейс `ISheet1` общедоступным и применяет атрибут <xref:System.Runtime.InteropServices.ComVisibleAttribute> , чтобы сделать интерфейс видимым для модели COM.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/CallingCodeFromVBA/ISheet1.cs" id="Snippet4":::

6. Выполните построение проекта.

## <a name="expose-the-method-to-vba-code"></a>Предоставление метода коду VBA
 Для предоставления метода `CreateVstoNamedRange` коду VBA в книге установите для свойства **ReferenceAssemblyFromVbaProject значения** для ведущего элемента `Sheet1` значение **True**.

### <a name="to-expose-the-method-to-vba-code"></a>Представление метода коду VBA

1. В **обозревателе решений** дважды щелкните файл **Sheet1.cs**.

     Файл **WorkbookWithVBA** открывается в конструкторе, и отображается Sheet1.

2. В окне **Свойства** выберите свойство **ReferenceAssemblyFromVbaProject** и установите значение **True**.

3. Появляется сообщение, в котором следует нажать кнопку **ОК** .

4. Выполните построение проекта.

## <a name="call-the-method-from-vba-code"></a>Вызов метода из кода VBA
 Теперь можно вызвать метод `CreateVstoNamedRange` из кода VBA в книге.

> [!NOTE]
> В этом пошаговом руководстве будет добавлен код VBA в книгу во время отладки проекта. Код VBA, добавляемый в этот документ, будет перезаписан в следующий раз при построении проекта, так как Visual Studio заменяет документ в выходной папке сборки копией документа из главной папки проекта. Если код VBA необходимо сохранить, его можно скопировать в документ в папке проекта. Дополнительные сведения см. в разделе [объединение VBA и настроек на уровне документа](../vsto/combining-vba-and-document-level-customizations.md).

### <a name="to-call-the-method-from-vba-code"></a>Вызов метода из кода VBA

1. Нажмите клавишу **F5** , чтобы запустить проект.

2. На вкладке **Разработчик** в группе **Код** щелкните элемент **Visual Basic**.

     Открывается редактор Visual Basic.

3. В меню **Вставить** выберите пункт **Модуль**.

4. Добавьте в новый модуль следующий код:

     Этот код вызывает метод `CreateTable` в сборке настройки. Макрос обращается к этому методу, используя глобальный метод `GetManagedClass` для доступа к классу ведущего элемента `Sheet1` , который был предоставлен коду VBA. Метод `GetManagedClass` был автоматически создан ранее при установке значения для свойства **ReferenceAssemblyFromVbaProject** в этом пошаговом руководстве.

    ```vb
    Sub CallVSTOMethod()
        Dim VSTOSheet1 As CallingCodeFromVBA.Sheet1
        Set VSTOSheet1 = GetManagedClass(Sheet1)
        Call VSTOSheet1.CreateVstoNamedRange(Sheet1.Range("A1"), "VstoNamedRange")
    End Sub
    ```

5. Нажмите клавишу **F5**.

6. В открытой книге щелкните ячейку **A1** на листе **Sheet1**. Убедитесь, что появляется окно сообщения.

7. Выйдите из Excel без сохранения изменений.

## <a name="next-steps"></a>Дальнейшие действия
 Дополнительные сведения о вызове кода в решениях Office из VBA см. в следующих разделах:

- Вызов кода в ведущем элементе в настройке Visual Basic из VBA. Этот процесс отличается от процесса Visual C#. Дополнительные сведения см. [в разделе Пошаговое руководство. вызов кода из VBA в Visual Basic проекте](../vsto/walkthrough-calling-code-from-vba-in-a-visual-basic-project.md).

- Вызов кода в надстройке VSTO из VBA. Дополнительные сведения см. [в разделе Пошаговое руководство. вызов кода в надстройке VSTO из VBA](../vsto/walkthrough-calling-code-in-a-vsto-add-in-from-vba.md).

## <a name="see-also"></a>См. также статью
- [Объединение настроек VBA и параметров на уровне документа](../vsto/combining-vba-and-document-level-customizations.md)
- [Программы настройки на уровне документа](../vsto/programming-document-level-customizations.md)
- [Руководство. предоставление кода коду VBA в Visual Basicном проекте](../vsto/how-to-expose-code-to-vba-in-a-visual-basic-project.md)
- [Руководство. предоставление кода VBA в проекте Visual C&#35;](../vsto/how-to-expose-code-to-vba-in-a-visual-csharp-project.md)
- [Пошаговое руководство. вызов кода из VBA в Visual Basicном проекте](../vsto/walkthrough-calling-code-from-vba-in-a-visual-basic-project.md)
