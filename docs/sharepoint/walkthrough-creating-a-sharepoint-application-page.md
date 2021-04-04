---
title: Пошаговое руководство. Создание страницы приложения SharePoint | Документация Майкрософт
description: В этом пошаговом руководстве вы создадите страницу приложения (специальную форму страницы ASP.NET), а затем отлаживать ее с помощью локального сайта SharePoint.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application pages [SharePoint development in Visual Studio], developing
- application pages [SharePoint development in Visual Studio], creating
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 6640373dac6d08144f1ef7fd230afa172540afe6
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/02/2021
ms.locfileid: "106217766"
---
# <a name="walkthrough-create-a-sharepoint-application-page"></a>Пошаговое руководство: Создание страницы приложения SharePoint

Страница приложения является специализированной формой ASP.NET страницы. Страницы приложения содержат содержимое, объединенное с главной страницей SharePoint. Дополнительные сведения см. в разделе [Создание страниц приложений для SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md).

В этом пошаговом руководстве показано, как создать страницу приложения, а затем выполнить ее отладку с помощью локального сайта SharePoint. На этой странице показаны все элементы, созданные или измененные каждым пользователем на всех сайтах фермы серверов.

В этом пошаговом руководстве описаны следующие задачи:

- Создание проекта SharePoint.
- Добавление страницы приложения в проект SharePoint.
- Добавление элементов управления ASP.NET на страницу приложения.
- Добавление кода на основе элементов управления ASP.NET.
- Тестирование страницы приложения.

> [!NOTE]
> Отображаемые на компьютере имена или расположения некоторых элементов пользовательского интерфейса Visual Studio могут отличаться от указанных в следующих инструкциях. Это зависит от имеющегося выпуска Visual Studio и используемых параметров. Дополнительные сведения см. в разделе [Персонализация интегрированной среды разработки Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Предварительные требования

- Поддерживаемые выпуски Windows и SharePoint.

## <a name="create-a-sharepoint-project"></a>Создание проекта SharePoint

Сначала создайте **пустой проект SharePoint**. Позже в этот проект будет добавлен элемент **страницы приложения** .

1. Запустите среду [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

2. Откройте диалоговое окно **Новый проект** , разверните узел **Office/SharePoint** в соответствии с языком, который необходимо использовать, а затем выберите узел **решения SharePoint** .

3. В области **Установленные шаблоны Visual Studio** выберите шаблон **проекта SharePoint 2010-Empty** . Присвойте проекту имя **мишарепоинтпрожект**, а затем нажмите кнопку **ОК** .

     Откроется **Мастер настройки SharePoint** . Этот мастер позволяет выбрать сайт, который будет использоваться для отладки проекта, и уровень доверия решения.

4. Выберите параметр **Развернуть как решение фермы** , а затем нажмите кнопку **Готово** , чтобы принять локальный сайт SharePoint по умолчанию.

## <a name="create-an-application-page"></a>Страница «Создание приложения»

Чтобы создать страницу приложения, добавьте в проект элемент **страницы приложения** .

1. В **Обозреватель решений** выберите проект **мишарепоинтпрожект** .

2. В строке меню выберите **Проект** > **Добавить новый элемент**.

3. В диалоговом окне **Добавление нового элемента** выберите **страницу приложения (шаблон только для решения фермы** ).

4. Присвойте странице имя **сеарчитемс**, а затем нажмите кнопку **Добавить** .

     Конструктор Visual Web Developer отображает страницу приложения в представлении **исходного кода** , где можно видеть HTML-элементы страницы. Конструктор отображает разметку для нескольких <xref:System.Web.UI.WebControls.Content> элементов управления. Каждый элемент управления сопоставляется с <xref:System.Web.UI.WebControls.ContentPlaceHolder> элементом управления, который определен на главной странице приложения по умолчанию.

## <a name="design-the-layout-of-the-application-page"></a>Разработка макета страницы приложения

Элемент страницы приложения позволяет использовать конструктор для добавления элементов управления ASP.NET на страницу приложения. Этот конструктор является тем же конструктором, который используется в Visual Web Developer. Добавьте метку, список переключателей и таблицу в представление **источника** конструктора, а затем задайте свойства так же, как при проектировании любой стандартной страницы ASP.NET.

1. В строке меню выберите **вид**  >  **панель элементов**.

2. В стандартном узле **панели элементов** выполните одно из следующих действий.

    - Откройте контекстное меню для элемента **Метка** , выберите **Копировать**, откройте контекстное меню для строки под элементом управления содержимым **плацехолдермаин** в конструкторе и выберите **Вставить**.

    - Перетащите элемент **Label** из **области элементов** в текст элемента управления содержимым **плацехолдермаин** .

3. Повторите предыдущий шаг, чтобы добавить элемент **DropDownList** и элемент **таблицы** в элемент управления содержимым **плацехолдермаин** .

4. В конструкторе измените значение `Text` атрибута элемента управления метка, чтобы **отобразить все элементы**.

5. В конструкторе замените `<asp:DropDownList>` элемент следующим XML-кодом.

    ```xml
    <asp:DropDownList ID="DropDownList1" runat="server" AutoPostBack="true"
     OnSelectedIndexChanged="DropDownList1_SelectedIndexChanged">
        <asp:ListItem Text="Created by me" Value="Author"></asp:ListItem>
        <asp:ListItem Text="Modified by me" Value="Editor"></asp:ListItem>
    </asp:DropDownList>
    ```

## <a name="handle-the-events-of-controls-on-the-page"></a>Обработку событий элементов управления на странице

Обрабатывайте элементы управления на странице приложения точно так же, как любая страница ASP.NET. В этой процедуре будет обработано `SelectedIndexChanged` событие раскрывающегося списка.

1. В меню **вид** выберите **код**.

     Файл кода страницы приложения откроется в редакторе кода.

2. Добавьте следующий метод в класс `SearchItems`. Этот код обрабатывает <xref:System.Web.UI.WebControls.ListControl.SelectedIndexChanged> событие объекта, <xref:System.Web.UI.WebControls.DropDownList> вызывая метод, который будет создан далее в этом пошаговом руководстве.

     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.vb" id="Snippet5":::
     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.cs" id="Snippet5":::

3. Добавьте следующие инструкции в начало файла кода страницы приложения.

     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.vb" id="Snippet1":::
     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.cs" id="Snippet1":::

4. Добавьте следующий метод в класс `SearchItems`. Этот метод выполняет итерацию всех сайтов на ферме серверов и выполняет поиск элементов, созданных или измененных текущим пользователем.

     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.vb" id="Snippet2":::
     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.cs" id="Snippet2":::

5. Добавьте следующий метод в класс `SearchItems`. Этот метод отображает элементы, созданные или измененные текущим пользователем в таблице.

     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.vb" id="Snippet3":::
     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.cs" id="Snippet3":::

## <a name="test-the-application-page"></a>Тестирование страницы приложения

При запуске проекта открывается сайт SharePoint, и появляется страница приложения.

1. В **Обозреватель решений** откройте контекстное меню страницы приложения и выберите пункт **Назначить запускаемым элементом**.

2. Нажмите клавишу **F5**.

     Откроется сайт SharePoint.

3. На странице приложение выберите параметр **изменено мной** .

     Страница приложения обновляется и отображает все элементы, измененные на всех сайтах фермы серверов.

4. На странице приложение выберите пункт **создано мной** в списке.

     Страница приложения обновляется и отображает все элементы, созданные на всех сайтах фермы серверов.

## <a name="next-steps"></a>Дальнейшие действия

Дополнительные сведения о страницах приложений SharePoint см. в разделе [Создание страниц приложений для SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md).

Дополнительные сведения о проектировании содержимого страниц SharePoint с помощью визуального веб-конструктора см. в следующих статьях:

- [Создание веб-частей для SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md).

- [Создание многократно используемых элементов управления для веб-частей или страниц приложений](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md).

## <a name="see-also"></a>См. также раздел

[Как создать страницу приложения](../sharepoint/how-to-create-an-application-page.md) 
 [Тип страницы _layouts приложения](/previous-versions/office/aa979604(v=office.14))
