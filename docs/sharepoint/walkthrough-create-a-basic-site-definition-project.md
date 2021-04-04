---
title: Пошаговое руководство. Создание базового проекта определения сайта | Документация Майкрософт
description: В этом пошаговом руководстве по SharePoint вы узнаете, как создать базовое определение сайта, содержащее визуальную веб-часть с некоторыми элементами управления.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, site definitions
- site definitions [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: a505ff059b347c6adbef15a8fe8bcfe7b274eaa4
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/02/2021
ms.locfileid: "106218026"
---
# <a name="walkthrough-create-a-basic-site-definition-project"></a>Пошаговое руководство. Создание базового проекта определения сайта
  В этом пошаговом руководстве показано, как создать базовое определение сайта, содержащее визуальную веб-часть с некоторыми элементами управления. Для простоты в создаваемой визуальной веб-части есть только несколько элементов управления. Тем не менее можно создать более сложные определения сайтов SharePoint, которые содержат дополнительные функциональные возможности.

 В этом пошаговом руководстве описаны следующие задачи.

- Создание определения сайта с помощью [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] шаблона проекта.

- Создание сайта SharePoint с помощью определения сайта в SharePoint.

- Добавление визуальной веб-части в решение.

- Настройка страницы Default. aspx сайта путем добавления в нее новой визуальной веб-части.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Предварительные требования
 Для выполнения этого пошагового руководства требуются следующие компоненты:

- Поддерживаемые редакции Microsoft Windows и SharePoint. Дополнительные сведения см. в разделе Требования для разработки решений SharePoint.

- приведенному.

## <a name="create-a-site-definition-solution"></a>Создание решения для определения сайта
 Сначала создайте проект определения сайта в [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

#### <a name="to-create-a-site-definition-project"></a>Создание проекта определения сайта

1. В строке меню выберите **Файл** > **Создать** > **Проект**. Если в интегрированной среде разработки настроено использование параметров Visual Basic разработки, в строке меню выберите **файл**  >  **создать проект**.

    Откроется диалоговое окно **Новый проект** .

2. Разверните узел **Visual C#** или узел **Visual Basic** , разверните узел **SharePoint** , а затем выберите узел **2010** .

3. В списке **шаблоны** выберите шаблон **проекта SharePoint 2010** .

4. В поле **имя** введите **тестситедеф**, а затем нажмите кнопку **ОК** .

    Откроется **Мастер настройки SharePoint** .

5. На странице **Укажите сайт и уровень безопасности для отладки** введите URL-адрес сайта SharePoint, на котором нужно выполнить отладку определения сайта, или используйте расположение по умолчанию (http://<em>System Name</em>/).

6. В разделе **что такое уровень доверия для этого решения SharePoint?** выберите параметр **Развернуть как решение фермы** .

    Все проекты определений сайтов должны быть развернуты как решения фермы. Дополнительные сведения о изолированных решениях и решениях фермы см. в статье [рекомендации по изолированным решениям](../sharepoint/sandboxed-solution-considerations.md).

7. Нажмите кнопку **Готово**.

    Проект отобразится в **Обозреватель решений**.

8. В **Обозреватель решений** выберите узел проекта, а затем в строке меню выберите **проект**  >  **Добавить новый элемент**.

9. В **Visual C#** или **Visual Basic** разверните узел **SharePoint** , а затем выберите узел **2010** .

10. В области **шаблоны** выберите шаблон **Определение сайта** , оставьте **имя** **SiteDefinition1**, а затем нажмите кнопку **Добавить** .

## <a name="create-a-visual-web-part"></a>Создание визуальной веб-части
 Теперь необходимо создать визуальную веб-часть, отображаемую на главной странице определения сайта.

#### <a name="to-create-a-visual-web-part"></a>Создание визуальной веб-части

1. В **Обозреватель решений** нажмите кнопку " **отобразить все файлы** ".

2. Выберите узел проекта **SiteDefinition1** , а затем в строке меню выберите **проект**  >  **Добавить новый элемент**.

     Откроется диалоговое окно **Добавление нового элемента**.

3. Разверните узел **Visual C#** или узел **Visual Basic** , разверните узел **SharePoint** , а затем выберите узел **2010** .

4. В списке шаблонов выберите шаблон **Визуальная веб-часть** , сохраните имя по умолчанию VisualWebPart1, а затем нажмите кнопку **Добавить** .

     Откроется файл *VisualWebPart1. ascx* .

5. В нижней части *VisualWebPart1. ascx* добавьте следующую разметку, чтобы добавить в форму три элемента управления: текстовое поле, кнопку и метку:

    ```aspx-csharp
    <table>
      <tr>
        <td>
          <asp:TextBox runat="server" ID="tbName"></asp:TextBox>
        </td>
        <td>
          <asp:Button runat="server" ID="btnSubmit" Text = "Change Label Text" OnClick="btnSubmit_Click"></asp:Button>
        </td>
        <td>
          <asp:Label runat="server" ID="lblName"></asp:Label>
        </td>
      </tr>
    </table>
    ```

6. В разделе *VisualWebPart1. ascx* откройте файл *VisualWebPart1. ascx. CS* (для [!INCLUDE[csprcs](../sharepoint/includes/csprcs-md.md)] ) или *VisualWebPart1. ascx. vb* (для [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] ), а затем добавьте следующий код:

     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/testsitedefvb/sitedefinition/visualwebpart1/visualwebpart1usercontrol.ascx.vb" id="Snippet1":::
     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/testsitedef/sitedefinition/visualwebpart1/visualwebpart1usercontrol.ascx.cs" id="Snippet1":::

     Этот код добавляет функции для нажатия кнопки веб-части.

## <a name="add-the-visual-web-part-to-the-default-aspx-page"></a>Добавление визуальной веб-части на страницу ASPX по умолчанию
 Затем добавьте визуальную веб-часть на страницу Default определения сайта ASPX.

#### <a name="to-add-a-visual-web-part-to-the-default-aspx-page"></a>Добавление визуальной веб-части на страницу ASPX по умолчанию

1. Откройте страницу default.aspx и добавьте следующую строку после тега `WebPartPages`:

    ```aspx-csharp
    <%@ Register Tagprefix="MyWebPartControls" Namespace="TestSiteDef.VisualWebPart1" Assembly="$SharePoint.Project.AssemblyFullName$" %>
    ```

     Эта строка связывает имя Мивебпартконтролс с веб-частью и его кодом. Параметр *Namespace* соответствует пространству имен, используемому в файле кода *VisualWebPart1. ascx* .

2. Найдите элемент `</asp:Content>` и замените весь последующий раздел `ContentPlaceHolderId="PlaceHolderMain"` и его содержимое следующим кодом.

    ```aspx-csharp
    <asp:Content ID="Content1" ContentPlaceHolderId="PlaceHolderMain" runat="server">
        <MyWebPartControls:VisualWebPart1 runat="server" />
    </asp:Content>
    ```

     Этот код создает ссылку на визуальную веб-часть, созданную ранее.

3. В **Обозреватель решений** откройте контекстное меню для узла **SiteDefinition1** , а затем выберите пункт **Назначить запускаемым элементом**.

## <a name="deploy-and-run-the-site-definition-solution"></a>Развертывание и запуск решения "определение сайта"
 Далее, разверните проект в SharePoint, а затем запустите проект.

#### <a name="to-deploy-and-run-the-site-definition"></a>Развертывание и запуск определения сайта

- В строке меню выберите **Build**  >  **deploy тестситедеф**.

- Нажмите клавишу **F5**.

     Visual Studio скомпилирует код, добавит его компоненты, поместит все его файлы в WSP-файл пакета и развернет этот WSP-файл на сервере SharePoint. Затем SharePoint устанавливает файлы, а затем активирует эти компоненты.

## <a name="create-a-site-based-on-the-site-definition"></a>Создание сайта на основе определения сайта
 Затем создайте сайт с помощью нового определения сайта.

#### <a name="to-create-a-site-by-using-the-site-definition"></a>Создание сайта с помощью определения сайта

1. На сайте SharePoint откроется страница новый сайт SharePoint.

2. В разделе **заголовок и описание** введите **Мой новый сайт** в поле Заголовок и описание сайта.

3. В разделе **адрес веб-сайта** введите **Миневсите** в поле **URL-имя** .

4. В разделе **шаблон** перейдите на вкладку **настройки SharePoint** .

5. В списке **выберите шаблон** выберите **SiteDefinition1**.

6. Оставьте для остальных параметров значения по умолчанию, а затем нажмите кнопку **создать** .

     Откроется новый сайт.

## <a name="test-the-new-site"></a>Тестирование нового сайта
 Теперь необходимо протестировать работу созданного сайта.

#### <a name="to-test-the-new-site"></a>Тестирование нового сайта

- На странице Default ASPX введите какой-либо текст, а затем нажмите кнопку **изменить текст метки** рядом с текстовым полем.

     Текст отобразится на метке справа от кнопки.

## <a name="see-also"></a>См. также раздел
- [Практическое руководство. Создание приемника событий](../sharepoint/how-to-create-an-event-receiver.md)
- [Разработка решений SharePoint](../sharepoint/developing-sharepoint-solutions.md)
