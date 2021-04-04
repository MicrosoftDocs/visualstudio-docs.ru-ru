---
title: Пошаговое руководство. Создание расширения проекта SharePoint | Документация Майкрософт
description: Создайте расширение проекта SharePoint, которое можно использовать для реагирования на события уровня проекта, например при добавлении, удалении или переименовании проекта.
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
ms.openlocfilehash: 1de6cdc2f5c1f1480a738f99aa05b8833eb4b2ed
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/02/2021
ms.locfileid: "106217799"
---
# <a name="walkthrough-create-a-sharepoint-project-extension"></a>Пошаговое руководство. Создание расширения проекта SharePoint
  В этом пошаговом руководстве показано, как создать расширение для проектов SharePoint. Расширение проекта можно использовать для реагирования на события уровня проекта, например при добавлении, удалении или переименовании проекта. Можно также добавить пользовательские свойства или ответить при изменении значения свойства. В отличие от расширений элементов проекта, расширения проектов не могут быть связаны с определенным типом проекта SharePoint. При создании расширения проекта это расширение загружается при открытии любого типа проекта SharePoint в [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

 В этом пошаговом руководстве вы создадите пользовательское логическое свойство, добавляемое в любой проект SharePoint, созданный в [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . Если задано **значение true**, новое свойство добавляет или сопоставляет папку ресурсов Images с проектом. Если задано **значение false**, папка Images удаляется, если она существует. Дополнительные сведения см. [в разделе инструкции. Добавление и удаление сопоставленных папок](../sharepoint/how-to-add-and-remove-mapped-folders.md).

 В этом пошаговом руководстве описаны следующие задачи.

- Создание [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] расширения для проектов SharePoint, которое выполняет следующие действия:

  - Добавляет настраиваемое свойство проекта в окно свойств. Свойство применяется к любому проекту SharePoint.

  - Использует объектную модель проекта SharePoint для добавления в проект сопоставленной папки.

  - Использует [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] объектную модель автоматизации (DTE) для удаления сопоставленной папки из проекта.

- Создание [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] пакета расширения (VSIX) для развертывания сборки расширения свойства проекта.

- Отладка и тестирование свойства проекта.

## <a name="prerequisites"></a>Предварительные требования
 Для выполнения этого пошагового руководства на компьютере разработчика потребуются следующие компоненты:

- Поддерживаемые выпуски [!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)] , SharePoint и [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

- [!INCLUDE[vssdk_current_long](../sharepoint/includes/vssdk-current-long-md.md)]. В этом пошаговом руководстве используется шаблон **проекта VSIX** в, [!INCLUDE[TLA2#tla_sdk](../sharepoint/includes/tla2sharptla-sdk-md.md)] чтобы создать пакет VSIX для развертывания расширения свойства проекта. Дополнительные сведения см. [в разделе Расширение инструментов SharePoint в Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md).

## <a name="create-the-projects"></a>Создание проектов
 Для выполнения этого пошагового руководства необходимо создать два проекта:

- Проект VSIX для создания пакета VSIX для развертывания расширения проекта.

- Проект библиотеки классов, реализующий расширение проекта.

  Начните пошаговое руководство, создав проекты.

#### <a name="to-create-the-vsix-project"></a>Создание проекта VSIX

1. Запустите среду [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

2. В строке меню выберите **Файл** > **Создать** > **Проект**.

3. В диалоговом окне **Новый проект** разверните узлы **Visual C#** или **Visual Basic** , а затем выберите узел **расширяемость** .

    > [!NOTE]
    > Этот узел доступен только при установке пакета SDK для Visual Studio. Дополнительные сведения см. в разделе Предварительные требования ранее в этом разделе.

4. В верхней части диалогового окна выберите **платформа .NET Framework 4,5** в списке версий платформа .NET Framework, а затем выберите шаблон **проекта VSIX** .

5. В поле **имя** введите **прожектекстенсионпаккаже**, а затем нажмите кнопку **ОК** .

     Проект **прожектекстенсионпаккаже** появится в **Обозреватель решений**.

#### <a name="to-create-the-extension-project"></a>Создание проекта расширения

1. В **Обозреватель решений** откройте контекстное меню узла решения, выберите **Добавить**, а затем выберите **Новый проект**.

2. В диалоговом окне **Новый проект** разверните узлы **Visual C#** или **Visual Basic** , а затем выберите **Windows**.

3. В верхней части диалогового окна выберите **платформа .NET Framework 4,5** в списке версий платформа .NET Framework, а затем выберите шаблон проекта **Библиотека классов** .

4. В поле **имя** введите **ProjectExtension**, а затем нажмите кнопку **ОК** .

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Добавляет проект **ProjectExtension** в решение и открывает файл кода Class1 по умолчанию.

5. Удалите файл кода Class1 из проекта.

## <a name="configure-the-project"></a>Настройка проекта
 Перед написанием кода для создания расширения проекта добавьте файлы кода и ссылки на сборки в проект расширения.

#### <a name="to-configure-the-project"></a>Настройка проекта

1. Добавьте файл кода с именем **CustomProperty** в проект ProjectExtension.

2. Откройте контекстное меню проекта **ProjectExtension** и выберите команду **Добавить ссылку**.

3. В диалоговом окне **Диспетчер ссылок — CustomProperty** выберите узел **Framework** , а затем установите флажок рядом с сборками System. ComponentModel. композиция и System. Windows. Forms.

4. Выберите узел **расширения** , установите флажок рядом с сборками Microsoft. VisualStudio. SharePoint и EnvDTE, а затем нажмите кнопку **ОК** .

5. В **Обозреватель решений** в папке **References** для проекта **ProjectExtension** выберите **EnvDTE**.

6. В окне **Свойства** измените значение свойства **Внедрить типы взаимодействия** на **false**.

## <a name="define-the-new-sharepoint-project-property"></a>Определение нового свойства проекта SharePoint
 Создайте класс, определяющий расширение проекта и поведение нового свойства проекта. Чтобы определить новое расширение проекта, класс реализует <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> интерфейс. Реализуйте этот интерфейс всякий раз, когда необходимо определить расширение для проекта SharePoint. Кроме того, добавьте в <xref:System.ComponentModel.Composition.ExportAttribute> класс. Этот атрибут позволяет [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] обнаруживать и загружать <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> реализацию. Передайте <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> тип в конструктор атрибута.

#### <a name="to-define-the-new-sharepoint-project-property"></a>Определение нового свойства проекта SharePoint

1. Вставьте следующий код в файл кода CustomProperty.

     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/projectextension/customproperty.vb" id="Snippet1":::
     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/projectextension/customproperty.cs" id="Snippet1":::

## <a name="build-the-solution"></a>Выполните сборку решения.
 Затем постройте решение, чтобы убедиться, что оно компилируется без ошибок.

#### <a name="to-build-the-solution"></a>Построение решения

1. В строке меню последовательно выберите **Сборка** > **Собрать решение**.

## <a name="create-a-vsix-package-to-deploy-the-project-property-extension"></a>Создание пакета VSIX для развертывания расширения свойства проекта
 Чтобы развернуть расширение проекта, используйте проект VSIX в решении для создания пакета VSIX. Сначала настройте пакет VSIX, изменив файл Source. extension. vsixmanifest, который включен в проект VSIX. Затем создайте пакет VSIX, создав решение.

#### <a name="to-configure-and-create-the-vsix-package"></a>Настройка и создание пакета VSIX

1. В **Обозреватель решений** откройте контекстное меню для файла Source. extension. vsixmanifest, а затем нажмите кнопку **Открыть** .

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] открывает файл в конструкторе манифестов. Сведения, отображаемые на вкладке **метаданные** , также отображаются в списке **расширения и обновления**. Для всех пакетов VSIX требуется файл Extension. vsixmanifest. Дополнительные сведения об этом файле см. в разделе [Справочник по схеме расширения VSIX 1,0](/previous-versions/dd393700(v=vs.110)).

2. В поле **Название продукта** введите **настраиваемое свойство проекта**.

3. В поле **Author (автор** ) введите **contoso**.

4. В поле **Описание** введите **настраиваемое свойство проекта SharePoint, которое переключает сопоставление папки ресурсов Images с проектом**.

5. Перейдите на вкладку **активы** и нажмите кнопку **создать** .

     Откроется диалоговое окно **Добавление нового ресурса** .

6. В списке **тип** выберите **Microsoft. VisualStudio. MefComponent**.

    > [!NOTE]
    > Это значение соответствует `MEFComponent` элементу в файле Extension. vsixmanifest. Этот элемент задает имя сборки расширения в пакете VSIX. Дополнительные сведения см. в разделе [элемент MEFComponent (Схема VSX)](/previous-versions/visualstudio/visual-studio-2010/dd393736\(v\=vs.100\)).

7. В списке **источник** выберите параметр **проект в текущем решении** .

8. В списке **проект** выберите **ProjectExtension**.

     Это значение определяет имя сборки, создаваемой в проекте.

9. Нажмите кнопку **ОК** , чтобы закрыть диалоговое окно **Добавление нового актива** .

10. В строке меню выберите **файл**  >  **сохранить все** после завершения и закройте конструктор манифестов.

11. В строке меню выберите **Сборка**  >  **сборка решения**, а затем убедитесь, что проект компилируется без ошибок.

12. В **Обозреватель решений** откройте контекстное меню проекта **прожектекстенсионпаккаже** и нажмите кнопку **Открыть папку в проводнике** .

13. В **проводнике** откройте папку выходных данных сборки для проекта прожектекстенсионпаккаже, а затем убедитесь, что в папке содержится файл с именем прожектекстенсионпаккаже. VSIX.

     По умолчанию выходной папкой сборки является.. \bin\Debug в папке, содержащей файл проекта.

## <a name="test-the-project-property"></a>Тестирование свойства проекта
 Теперь все готово для тестирования пользовательского свойства проекта. Проще всего выполнить отладку и тестирование нового расширения свойства проекта в экспериментальном экземпляре [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . Этот экземпляр [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] создается при запуске VSIX-или другого проекта расширения. После отладки проекта можно установить расширение в системе, а затем продолжить отладку и тестирование в обычном экземпляре [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

#### <a name="to-debug-and-test-the-extension-in-an-experimental-instance-of-visual-studio"></a>Отладка и тестирование расширения в экспериментальном экземпляре Visual Studio

1. Перезапустите [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] с учетными данными администратора, а затем откройте решение прожектекстенсионпаккаже.

2. Запустите отладочную сборку проекта, нажав клавишу **F5** , или в строке меню выберите **Отладка**  >  **начать отладку**.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] устанавливает расширение в%UserProfile%\AppData\Local\Microsoft\VisualStudio\11.0Exp\Extensions\Contoso\Custom Project Property\1.0 и запускает экспериментальный экземпляр [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

3. В экспериментальном экземпляре [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Создайте проект SharePoint для решения фермы и используйте значения по умолчанию для других значений в мастере.

    1. В строке меню выберите **Файл** > **Создать** > **Проект**.

    2. В верхней части диалогового окна **Новый проект** выберите **платформа .NET Framework 3,5** в списке версий платформа .NET Framework.

         Для расширений инструментов SharePoint требуются функции в этой версии [!INCLUDE[dnprdnshort](../sharepoint/includes/dnprdnshort-md.md)] .

    3. В узле **шаблоны** разверните узел **Visual C#** или **Visual Basic** , выберите узел **SharePoint** , а затем выберите узел **2010** .

    4. Выберите шаблон **проекта SharePoint 2010** , а затем введите **модулетест** в качестве имени проекта.

4. В **Обозреватель решений** выберите узел проекта **модулетест** .

     В окне " **свойства** " появится новая **Папка с изображением** настраиваемой схемы свойств со значением по умолчанию **false**.

5. Измените значение этого свойства на **true**.

     В проект SharePoint будет добавлена папка ресурсов изображений.

6. Измените значение этого свойства обратно на **false**.

     Если нажать кнопку **Да** в диалоговом окне **Удаление папки изображений?** , то папка ресурсов Images будет удалена из проекта SharePoint.

7. Закройте экспериментальный образец [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

## <a name="see-also"></a>См. также раздел
- [Расширение проектов SharePoint](../sharepoint/extending-sharepoint-projects.md)
- [Как добавить свойство в проекты SharePoint](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md)
- [Преобразование между типами системы проектов SharePoint и другими типами проектов Visual Studio](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md)
- [Сохранение данных в расширениях системы проектов SharePoint](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md)
- [Связывание пользовательских данных с помощью расширений инструментов SharePoint](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)