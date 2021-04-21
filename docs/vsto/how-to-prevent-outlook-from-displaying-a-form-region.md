---
title: Как запретить Outlook отображать область формы
description: Узнайте, как предотвратить отображение области формы для определенного элемента в Microsoft Office Outlook.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- form regions [Office development in Visual Studio], canceling display
- canceling form region display
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 1dc9322dd2ad3c3a2111222d7491f9e1a82cd6c4
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/21/2021
ms.locfileid: "107825853"
---
# <a name="how-to-prevent-outlook-from-displaying-a-form-region"></a>Как запретить Outlook отображать область формы
  Могут возникнуть ситуации, когда не нужно, чтобы Microsoft Office Outlook отображали область формы для определенного элемента. Например, если элемент контактного лица не содержит рабочий адрес, можно запретить отображение области формы, в которой отображается расположение компании на карте.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="to-prevent-outlook-from-displaying-a-form-region"></a>Запрет отображения области формы в Outlook

1. Откройте файл кода для области формы, которую необходимо изменить.

2. Разверните область кода **фабрики области формы** .

3. Добавьте код в `FormRegionInitializing` обработчик событий, который устанавливает <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> <xref:Microsoft.Office.Tools.Outlook.FormRegionInitializingEventArgs> для свойства класса **значение true**.

   В этом примере, если элемент Contact не содержит адрес, <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> свойство имеет значение **true**, а область формы не отображается.

## <a name="example"></a>Пример
 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_Outlook_FR_Separate_O12/MapIt.cs" id="Snippet1":::
 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Separate_O12/MapIt.vb" id="Snippet1":::


## <a name="see-also"></a>См. также
- [Создание областей формы Outlook](../vsto/creating-outlook-form-regions.md)
- [Пошаговое руководство. Проектирование области формы Outlook](../vsto/walkthrough-designing-an-outlook-form-region.md)
- [Как добавить область формы в проект надстройки Outlook](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)
- [Пошаговое руководство. Проектирование области формы Outlook](../vsto/walkthrough-designing-an-outlook-form-region.md)
- [Пошаговое руководство. импорт области формы, разработанной в Outlook](../vsto/walkthrough-importing-a-form-region-that-is-designed-in-outlook.md)
