---
title: Как добавить свойство в расширение элемента проекта SharePoint | Документация Майкрософт
titleSuffix: ''
description: Используйте расширение элемента проекта SharePoint, чтобы добавить свойство в любой элемент проекта SharePoint, уже установленный в Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- project items [SharePoint development in Visual Studio], extending
- SharePoint project items, extending
- SharePoint development in Visual Studio, extending project items
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 2634035435679bd5ab2627f803ff9d2c1dc5a863
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/02/2021
ms.locfileid: "106215452"
---
# <a name="how-to-add-a-property-to-a-sharepoint-project-item-extension"></a>Как добавить свойство в расширение элемента проекта SharePoint
  Расширение элемента проекта можно использовать для добавления свойства в любой элемент проекта SharePoint, уже установленный в Visual Studio. Свойство отображается в окне **Свойства** при выборе элемента проекта в **Обозреватель решений**.

 В следующих шагах предполагается, что вы уже создали расширение элемента проекта. Дополнительные сведения см. [в разделе инструкции. Создание расширения элемента проекта SharePoint](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md).

### <a name="to-add-a-property-to-a-project-item-extension"></a>Добавление свойства в расширение элемента проекта

1. Определите класс с открытым свойством, представляющим свойство, добавляемое в тип элемента проекта. Если необходимо добавить несколько свойств в тип элемента проекта, можно определить все свойства в одном и том же классе или в разных классах.

2. В <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension.Initialize%2A> методе <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension> реализации обработайте <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemPropertiesRequested> событие параметра *прожектитемтипе* .

3. В обработчике событий для <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemPropertiesRequested> события добавьте экземпляр класса Properties в <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemPropertiesRequestedEventArgs.PropertySources%2A> коллекцию параметра аргументов события.

## <a name="example"></a>Пример
 В следующем примере кода показано, как добавить свойство с именем **example** в элемент проекта приемника событий.

:::code language="csharp" source="../sharepoint/codesnippet/CSharp/projectitemmenuandproperty/extension/projectitemextensionproperty.cs" id="Snippet8":::
:::code language="vb" source="../sharepoint/codesnippet/VisualBasic/projectitemmenuandproperty/extension/projectitemextensionproperty.vb" id="Snippet8":::

### <a name="understand-the-code"></a>Изучение кода
 Чтобы гарантировать, что один и тот же экземпляр `CustomProperties` класса используется каждый раз при <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemPropertiesRequested> возникновении события, в примере кода в свойство элемента проекта добавляется объект Properties <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> при первом возникновении этого события. Код извлекает этот объект при повторном возникновении этого события. Дополнительные сведения об использовании <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> свойства для связывания данных с элементами проекта см. в разделе [Связывание пользовательских данных с помощью расширений инструментов SharePoint](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md).

 Чтобы сохранить изменения в значении свойства, метод доступа **Set** `ExampleProperty` сохраняет новое значение в <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> свойство <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem> объекта, с которым связано свойство. Дополнительные сведения об использовании <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> свойства для сохранения данных с элементами проекта см. в разделе [Сохранение данных в расширениях системы проектов SharePoint](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md).

### <a name="specify-the-behavior-of-custom-properties"></a>Определение поведения пользовательских свойств
 Можно определить, как пользовательское свойство отображается и ведет себя в окне " **Свойства** ", применяя атрибуты из <xref:System.ComponentModel> пространства имен к определению свойства. Во многих сценариях полезны следующие атрибуты:

- <xref:System.ComponentModel.DisplayNameAttribute>: Задает имя свойства, которое отображается в окне **Свойства** .

- <xref:System.ComponentModel.DescriptionAttribute>: Указывает строку описания, которая отображается в нижней части окна **свойств** при выборе свойства.

- <xref:System.ComponentModel.DefaultValueAttribute>: Задает значение свойства по умолчанию.

- <xref:System.ComponentModel.TypeConverterAttribute>: Определяет пользовательское преобразование между строкой, отображаемой в окне " **Свойства** ", и значением свойства, не являющегося строкой.

- <xref:System.ComponentModel.EditorAttribute>: Определяет настраиваемый редактор, используемый для изменения свойства.

## <a name="compile-the-code"></a>Компиляция кода
 Для этих примеров требуется проект библиотеки классов со ссылками на следующие сборки:

- Microsoft. VisualStudio. SharePoint

- System.ComponentModel.Composition

## <a name="deploy-the-extension"></a>Развертывание расширения
 Чтобы развернуть расширение, создайте [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] пакет расширения (VSIX) для сборки и всех остальных файлов, которые требуется распространить с расширением. Дополнительные сведения см. [в статье Развертывание расширений для инструментов SharePoint в Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

## <a name="see-also"></a>См. также раздел
- [Как создать расширение элемента проекта SharePoint](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)
- [Как добавить пункт контекстного меню в расширение элемента проекта SharePoint](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-sharepoint-project-item-extension.md)
- [Расширение элементов проектов SharePoint](../sharepoint/extending-sharepoint-project-items.md)
- [Пошаговое руководство. расширение типа элемента проекта SharePoint](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md)
