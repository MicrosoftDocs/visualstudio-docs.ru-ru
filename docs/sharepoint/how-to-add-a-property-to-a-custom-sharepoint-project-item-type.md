---
title: Добавление свойства в пользовательский тип элемента проекта SharePoint
description: Добавление свойства в пользовательский тип элемента проекта SharePoint. Свойство отображается в окно свойств при выборе элемента проекта в обозреватель решений.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint project items, defining your own types
- project items [SharePoint development in Visual Studio], defining your own types
- SharePoint development in Visual Studio, defining new project item types
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 17d9ac144b97c090292395dd5ae5e85319dd1308
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/02/2021
ms.locfileid: "106215517"
---
# <a name="how-to-add-a-property-to-a-custom-sharepoint-project-item-type"></a>Как добавить свойство в пользовательский тип элемента проекта SharePoint
  При определении пользовательского типа элемента проекта SharePoint можно добавить свойство в элемент проекта. Свойство отображается в окне **Свойства** при выборе элемента проекта в **Обозреватель решений**.

 В следующих шагах предполагается, что вы уже определили собственный тип элемента проекта SharePoint. Дополнительные сведения см. [в разделе инструкции. определение типа элемента проекта SharePoint](../sharepoint/how-to-define-a-sharepoint-project-item-type.md).

### <a name="to-add-a-property-to-a-definition-of-a-project-item-type"></a>Добавление свойства в определение типа элемента проекта

1. Определите класс с открытым свойством, которое представляет свойство, добавляемое в пользовательский тип элемента проекта. Если необходимо добавить несколько свойств в пользовательский тип элемента проекта, можно определить все свойства в одном и том же классе или в разных классах.

2. В <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A> методе <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> реализации обработайте <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemPropertiesRequested> событие параметра *прожектитемтипедефинитион* .

3. В обработчике событий для <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemPropertiesRequested> события добавьте экземпляр класса пользовательских свойств в <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemPropertiesRequestedEventArgs.PropertySources%2A> коллекцию параметра аргументов события.

## <a name="example"></a>Пример
 В следующем примере кода показано, как добавить свойство с именем **example** в пользовательский тип элемента проекта.

 :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/projectitemmenuandproperty/extension/projectitemtypeproperty.vb" id="Snippet11":::
 :::code language="csharp" source="../sharepoint/codesnippet/CSharp/projectitemmenuandproperty/extension/projectitemtypeproperty.cs" id="Snippet11":::

### <a name="understand-the-code"></a>Изучение кода
 Чтобы гарантировать, что один и тот же экземпляр `CustomProperties` класса используется каждый раз при <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemPropertiesRequested> возникновении события, пример кода сохраняет объект свойств в <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> свойство элемента проекта при первом возникновении этого события. Код извлекает этот объект при повторном возникновении этого события. Дополнительные сведения об использовании <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> свойства для сохранения данных с элементами проекта см. в разделе [Связывание пользовательских данных с помощью расширений инструментов SharePoint](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md).

 Чтобы сохранить изменения в значении свойства, метод доступа **Set** `ExampleProperty` сохраняет новое значение в <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> свойство <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem> объекта, с которым связано свойство. Дополнительные сведения об использовании <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> свойства для сохранения данных с элементами проекта см. в разделе [Сохранение данных в расширениях системы проектов SharePoint](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md).

### <a name="specify-the-behavior-of-custom-properties"></a>Определение поведения пользовательских свойств
 Можно определить, как пользовательское свойство отображается и ведет себя в окне " **Свойства** ", применяя атрибуты из <xref:System.ComponentModel> пространства имен к определению свойства. Во многих сценариях полезны следующие атрибуты:

- <xref:System.ComponentModel.DisplayNameAttribute>: Задает имя свойства, которое отображается в окне **Свойства** .

- <xref:System.ComponentModel.DescriptionAttribute>: Указывает строку описания, которая отображается в нижней части окна **свойств** при выборе свойства.

- <xref:System.ComponentModel.DefaultValueAttribute>: Задает значение свойства по умолчанию.

- <xref:System.ComponentModel.TypeConverterAttribute>: Определяет пользовательское преобразование между строкой, отображаемой в окне " **Свойства** ", и значением свойства, не являющегося строкой.

- <xref:System.ComponentModel.EditorAttribute>: Определяет настраиваемый редактор, используемый для изменения свойства.

## <a name="compile-the-code"></a>Компиляция кода
 Для этих примеров кода требуется проект библиотеки классов со ссылками на следующие сборки:

- Microsoft. VisualStudio. SharePoint

- System.ComponentModel.Composition

## <a name="deploy-the-project-item"></a>Развертывание элемента проекта
 Чтобы позволить другим разработчикам использовать элемент проекта, создайте шаблон проекта или шаблон элемента проекта. Дополнительные сведения см. в разделе [Создание шаблонов элементов и шаблонов проектов для элементов проектов SharePoint](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).

 Чтобы развернуть элемент проекта, создайте [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] пакет расширения (VSIX) для сборки, шаблона и других файлов, которые необходимо распространить с элементом проекта. Дополнительные сведения см. [в статье Развертывание расширений для инструментов SharePoint в Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

## <a name="see-also"></a>См. также раздел
- [Как определить тип элемента проекта SharePoint](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)
- [Как добавить пункт контекстного меню в пользовательский тип элемента проекта SharePoint](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-custom-sharepoint-project-item-type.md)
- [Определение пользовательских типов элементов проектов SharePoint](../sharepoint/defining-custom-sharepoint-project-item-types.md)
