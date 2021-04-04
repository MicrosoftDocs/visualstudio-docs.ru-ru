---
title: Как добавить свойство в проекты SharePoint | Документация Майкрософт
description: Используйте расширение проекта, чтобы добавить свойство в проект SharePoint. Свойство отображается в окно свойств при выборе проекта в обозреватель решений.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- projects [SharePoint development in Visual Studio], extending
- SharePoint development in Visual Studio, extending projects
- SharePoint projects, extending
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 7be241dd4a043b8104c628e73f98e8881dc8b88b
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/02/2021
ms.locfileid: "106215426"
---
# <a name="how-to-add-a-property-to-sharepoint-projects"></a>Как добавить свойство в проекты SharePoint
  Расширение проекта можно использовать для добавления свойства в любой проект SharePoint. Свойство отображается в окне **Свойства** при выборе проекта в **Обозреватель решений**.

 В следующих шагах предполагается, что вы уже создали расширение проекта. Дополнительные сведения см. [в разделе инструкции. Создание расширения проекта SharePoint](../sharepoint/how-to-create-a-sharepoint-project-extension.md).

### <a name="to-add-a-property-to-a-sharepoint-project"></a>Добавление свойства в проект SharePoint

1. Определите класс с открытым свойством, которое представляет свойство, добавляемое в проекты SharePoint. Если необходимо добавить несколько свойств, можно определить все свойства в одном и том же классе или в разных классах.

2. В <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension.Initialize%2A> методе <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> реализации обработайте <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectPropertiesRequested> событие параметра *прожектсервице* .

3. В обработчике событий для <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectPropertiesRequested> события добавьте экземпляр класса Properties в <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectPropertiesRequestedEventArgs.PropertySources%2A> коллекцию параметра аргументов события.

## <a name="example"></a>Пример
 В следующем примере кода показано, как добавить два свойства в проекты SharePoint. Одно свойство сохраняет свои данные в файле пользовательских параметров проекта (файл *. csproj. User* или *. vbproj. User* ). Другое свойство сохраняет свои данные в файле проекта (файл *. csproj* или *. vbproj* ).

 :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/customspproperty/customproperty.vb" id="Snippet1":::
 :::code language="csharp" source="../sharepoint/codesnippet/CSharp/customspproperty/customproperty.cs" id="Snippet1":::

### <a name="understand-the-code"></a>Изучение кода
 Чтобы гарантировать, что один и тот же экземпляр `CustomProjectProperties` класса используется каждый раз при <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectPropertiesRequested> возникновении события, в примере кода в свойство проекта добавляется объект Properties <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> при первом возникновении этого события. Код извлекает этот объект при повторном возникновении этого события. Дополнительные сведения об использовании <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> свойства для связывания данных с проектами см. в разделе [Связывание пользовательских данных с помощью расширений инструментов SharePoint](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md).

 Чтобы сохранить изменения в значениях свойств, методы доступа **Set** для свойств используют следующие API:

- `CustomUserFileProperty` использует <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject.ProjectUserFileData%2A> свойство, чтобы сохранить свое значение в файле параметров пользователя проекта.

- `CustomProjectFileProperty` использует <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetPropertyValue%2A> метод, чтобы сохранить свое значение в файле проекта.

  Дополнительные сведения о сохранении данных в этих файлах см. в разделе [Сохранение данных в расширениях системы проектов SharePoint](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md).

### <a name="specify-the-behavior-of-custom-properties"></a>Определение поведения пользовательских свойств
 Можно определить, как пользовательское свойство отображается и ведет себя в окне " **Свойства** ", применяя атрибуты из <xref:System.ComponentModel> пространства имен к определению свойства. Во многих сценариях полезны следующие атрибуты:

- <xref:System.ComponentModel.DisplayNameAttribute>: Задает имя свойства, которое отображается в окне **Свойства** .

- <xref:System.ComponentModel.DescriptionAttribute>: Указывает строку описания, которая отображается в нижней части окна **свойств** при выборе свойства.

- <xref:System.ComponentModel.DefaultValueAttribute>: Задает значение свойства по умолчанию.

- <xref:System.ComponentModel.TypeConverterAttribute>: Определяет пользовательское преобразование между строкой, отображаемой в окне " **Свойства** ", и значением свойства, не являющегося строкой.

- <xref:System.ComponentModel.EditorAttribute>: Определяет настраиваемый редактор, используемый для изменения свойства.

## <a name="compile-the-code"></a>Компиляция кода
 Для этого примера требуются ссылки на следующие сборки:

- Microsoft. VisualStudio. SharePoint

- Microsoft. VisualStudio. Shell

- Microsoft. VisualStudio. Shell. Interop

- Microsoft. VisualStudio. Shell. Interop. 8.0

- System.ComponentModel.Composition

## <a name="deploy-the-extension"></a>Развертывание расширения
 Чтобы развернуть расширение, создайте [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] пакет расширения (VSIX) для сборки и всех остальных файлов, которые требуется распространить с расширением. Дополнительные сведения см. [в статье Развертывание расширений для инструментов SharePoint в Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

## <a name="see-also"></a>См. также раздел
- [Расширение проектов SharePoint](../sharepoint/extending-sharepoint-projects.md)
- [Как создать расширение проекта SharePoint](../sharepoint/how-to-create-a-sharepoint-project-extension.md)
- [Как добавить пункт контекстного меню в проекты SharePoint](../sharepoint/how-to-add-a-shortcut-menu-item-to-sharepoint-projects.md)
- [Расширение системы проектов SharePoint](../sharepoint/extending-the-sharepoint-project-system.md)
