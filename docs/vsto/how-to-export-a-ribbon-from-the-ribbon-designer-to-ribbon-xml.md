---
title: Как экспортировать ленту из конструктора лент в XML-ленту
description: Сведения о настройке ленты. Вы можете экспортировать ленту из конструктора в XML-ленту и изменить XML-код напрямую.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- custom Ribbon, XML
- customizing the Ribbon, XML
- Ribbon [Office development in Visual Studio], XML
- Ribbon [Office development in Visual Studio], exporting
- XML [Office development in Visual Studio], Ribbon
- Ribbon Designer [Office development in Visual Studio]
- exporting Ribbon
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 1514410094deaf9c77e088c3b69e2d39d29175c2
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/21/2021
ms.locfileid: "107825593"
---
# <a name="how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml"></a>Как экспортировать ленту из конструктора лент в XML-ленту
  Элемент **Лента (визуальный конструктор)** не поддерживает все возможные типы настройки ленты. Чтобы настроить ленту с дополнительными способами, можно экспортировать ленту из конструктора в XML-ленту и изменить XML-код напрямую.

> [!NOTE]
> В XML-файле ленты отображаются не все значения свойств. Дополнительные сведения см. в статье [Общие сведения о ленте](../vsto/ribbon-overview.md).

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

### <a name="to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml"></a>Экспорт ленты из конструктора ленты в XML-ленту

1. Щелкните правой кнопкой мыши файл кода ленты в **Обозреватель решений** и выберите пункт **Конструктор представлений**.

2. Щелкните правой кнопкой мыши конструктор ленты и выберите пункт **экспортировать ленту в XML**.

     Visual Studio добавляет XML-файл ленты и файл кода XML ленты в проект.

3. В классе код ленты нахождение комментариев, начинающихся с `TODO:` .

4. Скопируйте блок кода в эти комментарии в класс **ThisAddIn**, **ThisWorkbook** или **ThisDocument** в зависимости от типа разрабатываемого решения.

     Этот код позволяет приложению Microsoft Office обнаруживать и загружать настраиваемую ленту. Дополнительные сведения см. в разделе [Ribbon XML](../vsto/ribbon-xml.md).

5. В классе **ThisAddIn**, **ThisWorkbook** или **ThisDocument** раскомментируйте блок кода.

     После раскомментирования кода он должен выглядеть следующим образом. В этом примере вызывается класс Ribbon `MyRibbon` .

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_Ribbon_Custom_Tab_XML_O12/ThisAddIn.cs" id="Snippet1":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_Ribbon_Custom_Tab_XML_O12/ThisAddIn.vb" id="Snippet1":::

6. Переключитесь в файл кода XML ленты и найдите `Ribbon Callbacks` регион.

     Здесь вы пишете методы обратного вызова для управления действиями пользователя, например нажатием кнопки.

7. Создайте метод обратного вызова для каждого обработчика событий, написанного в коде конструктора ленты.

8. Переместите весь код обработчика событий из обработчиков событий в методы обратного вызова и измените код для работы с моделью программирования расширения ленты (RibbonX).

     Сведения о написании методов обратного вызова и использовании модели программирования RibbonX см. в разделе [RIBBON XML](../vsto/ribbon-xml.md).

## <a name="see-also"></a>См. также статью
- [Общие сведения о ленте](../vsto/ribbon-overview.md)
- [Конструктор лент](../vsto/ribbon-designer.md)
- [Ribbon XML](../vsto/ribbon-xml.md)
- [Пошаговое руководство. Создание настраиваемой вкладки с помощью конструктора лент](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)
- [Пошаговое руководство. Создание настраиваемой вкладки с помощью XML-ленты](../vsto/walkthrough-creating-a-custom-tab-by-using-ribbon-xml.md)
