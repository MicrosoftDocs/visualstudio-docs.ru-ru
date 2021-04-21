---
title: Доступ к ленте во время выполнения
description: Вы можете написать код, чтобы отобразить, скрыть или изменить ленту и позволить пользователям запускать код из элементов управления в настраиваемой области задач, панели действий или области формы Outlook.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Globals class, Ribbon
- Ribbon [Office development in Visual Studio], accessing
- RibbonManager class
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: e20c9a54d2fa352c51d5ae5383f5c5b7861e0fdf
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/21/2021
ms.locfileid: "107825229"
---
# <a name="access-the-ribbon-at-run-time"></a>Доступ к ленте во время выполнения
  Вы можете написать код, чтобы отобразить, скрыть или изменить ленту и позволить пользователям запускать код из элементов управления в настраиваемой области задач, панели действий или области формы Outlook.

 Доступ к ленте осуществляется с помощью класса `Globals`. Для проектов Outlook можно получить доступ к лентам, которые отображаются в конкретном окне инспектора или проводника Outlook.

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

## <a name="access-the-ribbon-by-using-the-globals-class"></a>Доступ к ленте с помощью класса Globals
 Вы можете использовать класс `Globals` для доступа к ленте в проекте уровня документа или проекте надстройки VSTO из любого места в проекте.

 Дополнительные сведения о `Globals` классе см. в разделе [глобальный доступ к объектам в проектах Office](../vsto/global-access-to-objects-in-office-projects.md).

 Следующий пример использует класс `Globals` для доступа к пользовательской ленте с именем `Ribbon1` и задает текст `Hello World`, отображаемый в поле со списком на ленте.

 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Access_O12/ThisAddIn.vb" id="Snippet4":::
 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_Outlook_FR_Access_O12/ThisAddIn.cs" id="Snippet4":::

## <a name="access-a-collection-of-ribbons-that-appear-in-a-specific-outlook-inspector-window"></a>Доступ к коллекции лент, отображаемых в определенном окне инспектора Outlook
 Вы можете получить доступ к коллекции лент, отображаемых в *Инспекторах* Outlook. Инспектор — это окно, которое открывается в Outlook при выполнении пользователем определенных задач, таких как создание электронного сообщения. Для доступа к ленте окна инспектора вызовите свойство `Ribbons` класса `Globals` и передайте объект <xref:Microsoft.Office.Interop.Outlook.Inspector>, представляющий инспектор.

 Следующий пример получает коллекцию лент в инспекторе, в котором фокус находится в данный момент. Пример кода затем получает доступ к ленте `Ribbon1` и задает текст `Hello World`, отображаемый в поле со списком на ленте.

 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Access_O12/ThisAddIn.vb" id="Snippet5":::
 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_Outlook_FR_Access_O12/ThisAddIn.cs" id="Snippet5":::

## <a name="access-a-collection-of-ribbons-that-appear-for-a-specific-outlook-explorer"></a>Доступ к коллекции лент, отображаемой для конкретного обозревателя Outlook
 Можно получить доступ к коллекции лент, отображаемых в *обозревателе* Outlook. Проводник — это пользовательский интерфейс основного приложения экземпляра Outlook. Для доступа к ленте окна проводника вызовите свойство `Ribbons` класса `Globals` и передайте объект <xref:Microsoft.Office.Interop.Outlook.Explorer>, представляющий проводник.

 Следующий пример получает коллекцию лент проводника, в котором фокус находится в данный момент. Пример кода затем получает доступ к ленте `Ribbon1` и задает текст `Hello World`, отображаемый в поле со списком на ленте.

 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Access_O12/ThisAddIn.vb" id="Snippet6":::
 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_Outlook_FR_Access_O12/ThisAddIn.cs" id="Snippet6":::

## <a name="see-also"></a>См. также статью
- [Общие сведения о ленте](../vsto/ribbon-overview.md)
- [Конструктор лент](../vsto/ribbon-designer.md)
- [Ribbon XML](../vsto/ribbon-xml.md)
- [Общие сведения об объектной модели ленты](../vsto/ribbon-object-model-overview.md)
- [Пошаговое руководство. Создание настраиваемой вкладки с помощью конструктора лент](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)
- [Пошаговое руководство. Обновление элементов управления на ленте во время выполнения](../vsto/walkthrough-updating-the-controls-on-a-ribbon-at-run-time.md)
- [Настройка ленты для Outlook](../vsto/customizing-a-ribbon-for-outlook.md)
- [Доступ к области формы во время выполнения](../vsto/accessing-a-form-region-at-run-time.md)
