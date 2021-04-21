---
title: Доступ к области формы во время выполнения
description: Узнайте, как получить доступ к области формы в различных типах проектов и версиях Microsoft Office во время выполнения.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Inspectors [Office development in Visual Studio]
- Explorers [Office development in Visual Studio]
- form regions [Office development in Visual Studio], accessing at run time
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: dbd60f5773392af2066e4693751dd6fff99128b9
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/21/2021
ms.locfileid: "107827972"
---
# <a name="access-a-form-region-at-run-time"></a>Доступ к области формы во время выполнения

|Применяется к|
|----------------|
|Сведения, приведенные в данном разделе, относятся только к следующим типам проектов и версиям Microsoft Office. Дополнительные сведения см. в разделе [доступность функций по типам приложений Office и проектов](../vsto/features-available-by-office-application-and-project-type.md).<br /><br /> **Тип проекта**<br /><br /> -Проекты надстроек VSTO<br /><br /> **Версия Microsoft Office**<br /><br /> -   [!INCLUDE[Outlook_14_short](../vsto/includes/outlook-14-short-md.md)]|

 Используйте класс `Globals` для доступа к областям форм из любого места в проекте Outlook. Дополнительные сведения о `Globals` классе см. в разделе [глобальный доступ к объектам в проектах Office](../vsto/global-access-to-objects-in-office-projects.md).

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="access-form-regions-that-appear-in-a-specific-outlook-inspector-window"></a>Доступ к областям форм, отображаемым в конкретном окне инспектора Outlook
 Для доступа ко всем областям форм, которые отображаются в определенном инспекторе Outlook, вызовите свойство `FormRegions` класса `Globals` и передайте в объект <xref:Microsoft.Office.Interop.Outlook.Inspector> , представляющий инспектор.

 В следующем примере извлекается коллекция областей форм в инспекторе, в котором в текущий момент находится фокус. Затем производится доступ к области формы в коллекции с именем `formRegion1` и задается текст, отображаемый в текстовом поле для `Hello World`.

 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Access_O12/ThisAddIn.vb" id="Snippet2":::
 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_Outlook_FR_Access_O12/ThisAddIn.cs" id="Snippet2":::

## <a name="access-form-regions-that-appear-in-a-specific-outlook-explorer-window"></a>Доступ к областям форм, отображаемым в определенном окне проводника Outlook
 Для доступа ко всем областям форм, которые отображаются в определенном проводнике Outlook, вызовите свойство `FormRegions` класса `Globals` и передайте в объект <xref:Microsoft.Office.Interop.Outlook.Explorer> , представляющий проводник.

 В следующем примере извлекается коллекция областей форм в проводнике, в котором в текущий момент находится фокус. Затем производится доступ к области формы в коллекции с именем `formRegion1` и задается текст, отображаемый в текстовом поле для `Hello World`.

 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Access_O12/ThisAddIn.vb" id="Snippet3":::
 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_Outlook_FR_Access_O12/ThisAddIn.cs" id="Snippet3":::

## <a name="access-all-form-regions"></a>Доступ ко всем областям формы
 Для доступа ко всем областям форм, отображаемым во всех проводниках и инспекторах, вызовите свойство `FormRegions` класса `Globals` .

 В следующем примере извлекается коллекция областей форм во всех проводниках и всех инспекторах. Затем производится доступ к области формы с именем `formRegion1` и задается текст, отображаемый в текстовом поле для `Hello World`.

 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Access_O12/ThisAddIn.vb" id="Snippet1":::
 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_Outlook_FR_Access_O12/ThisAddIn.cs" id="Snippet1":::

## <a name="access-controls-on-a-form-region"></a>Элементы управления доступом в области формы
 Для доступа к элементам управления в области формы с помощью класса `Globals` необходимо сделать эти элементы управления доступными для кода вне файла кода области формы.

### <a name="form-regions-designed-in-the-form-region-designer"></a>Области формы, разработанные в конструкторе областей формы
 Для C# измените модификатор каждого элемента управления, к которому необходимо получить доступ. Для этого выделите каждый элемент управления в конструкторе областей форм и измените свойство **Модификатор** на **Внутренний** или **Общедоступный** в окне **Свойства** . Например, если изменить свойство **Модификатор** объекта `textBox1` на **Внутренний**, можно получить доступ к `textBox1` , введя `Globals.FormRegions.FormRegion1.textBox1`.

 В Visual Basic изменение модификатора не требуется.

### <a name="imported-form-regions"></a>Импортированные области формы
 При импорте созданной в Outlook области формы модификатор доступа каждого элемента управления в области формы меняется на закрытый. Поскольку вы не можете использовать конструктор областей форм для изменения импортированной области формы, нет способа изменить модификатор элемента управления в окне **Свойства** .

 Для включения доступа к элементу управления извне файла кода области формы создайте свойство в файле кода области формы для получения этого элемента управления.

 Дополнительные сведения о создании свойств в C# см. в разделе [как объявить и использовать свойства чтения и записи &#40;C&#35; руководство по программированию&#41;](/dotnet/csharp/programming-guide/classes-and-structs/how-to-declare-and-use-read-write-properties).

 Дополнительные сведения о создании свойств в Visual Basic см. в разделе [инструкции. Создание свойства (Visual Basic)](/dotnet/visual-basic/programming-guide/language-features/procedures/how-to-create-a-property).

## <a name="see-also"></a>См. также статью
- [Рекомендации по созданию областей формы Outlook](../vsto/guidelines-for-creating-outlook-form-regions.md)
- [Пошаговое руководство. Проектирование области формы Outlook](../vsto/walkthrough-designing-an-outlook-form-region.md)
- [Как добавить область формы в проект надстройки Outlook](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)
- [Пользовательские действия в областях формы Outlook](../vsto/custom-actions-in-outlook-form-regions.md)
- [Связывание области формы с классом сообщений Outlook](../vsto/associating-a-form-region-with-an-outlook-message-class.md)
- [Пошаговое руководство. импорт области формы, разработанной в Outlook](../vsto/walkthrough-importing-a-form-region-that-is-designed-in-outlook.md)
- [Как запретить Outlook отображать область формы](../vsto/how-to-prevent-outlook-from-displaying-a-form-region.md)
- [Создание областей формы Outlook](../vsto/creating-outlook-form-regions.md)
- [Доступ к ленте во время выполнения](../vsto/accessing-the-ribbon-at-run-time.md)
