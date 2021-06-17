---
title: Отладка приложения SharePoint с помощью IntelliTrace
description: Используйте IntelliTrace для упрощения отладки и исправления приложений SharePoint. Создание и добавление кода для приемника компонента. Протестируйте проект. Собирайте данные IntelliTrace.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- IntelliTrace [SharePoint development in Visual Studio]
- standalone data collector
- SharePoint development in Visual Studio, IntelliTrace
- data collector
- IntelliTrace
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: cf7fa6c7255e05c465d6c209db5e9581a49aee64
ms.sourcegitcommit: 1f27f33852112702ee35fbc0c02fba37899e4cf5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2021
ms.locfileid: "112112840"
---
# <a name="walkthrough-debug-a-sharepoint-application-by-using-intellitrace"></a>Пошаговое руководство. Отладка приложения SharePoint с помощью IntelliTrace

С помощью IntelliTrace гораздо легче отлаживать решения SharePoint. Традиционные отладчики показывают только снимок решения в текущий момент. Тем не менее IntelliTrace можно использовать для просмотра прошедших событий решения и контекста, в котором эти события произошли, а также для перехода к коду.

 В этом пошаговом руководстве показано, как выполнить отладку проекта SharePoint в Visual Studio с помощью Microsoft Monitoring Agent для получения данных IntelliTrace из развернутых приложений. Для анализа этих данных необходимо использовать Visual Studio Enterprise. Этот проект включает в себя приемник компонента, который при активации компонента добавляет задачу в список задач и объявление в список извещений. При деактивации этой функции задача помечается как завершенная, а второе объявление добавляется в список извещений. Однако процедура содержит логическую ошибку, которая не дает корректного выполнения проекта. С помощью IntelliTrace вы сможете найти и исправить ошибку.

 **Применимо к:** Сведения в этом разделе относятся к решениям SharePoint, созданным в Visual Studio.

 В этом пошаговом руководстве описаны следующие задачи:

- [Создание приемника компонента](#create-a-feature-receiver)

- [Добавление кода в приемник компонента](#add-code-to-the-feature-receiver)

- [Тестирование проекта](#test-the-project)

- [Получение данных IntelliTrace с помощью Microsoft Monitoring Agent](#collect-intellitrace-data-by-using-microsoft-monitoring-agent)

- [Отладка и исправление решения SharePoint](#debug-and-fix-the-sharepoint-solution)

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Предварительные требования

Для выполнения этого пошагового руководства требуются следующие компоненты:

- Поддерживаемые выпуски Windows и SharePoint.

- Visual Studio Enterprise.

## <a name="create-a-feature-receiver"></a>Создание приемника компонента

Сначала создайте пустой проект SharePoint с приемником компонента.

1. Создайте проект решения SharePoint, предназначенный для установленной версии SharePoint, и назовите его **интеллитрацетест**.

     Откроется **Мастер настройки SharePoint** , в котором можно указать сайт SharePoint для проекта и уровень доверия решения.

2. Выберите параметр **Развернуть как решение фермы** , а затем нажмите кнопку **Готово** .

     IntelliTrace работает только с решениями фермы.

3. В **Обозреватель решений** откройте контекстное меню узла **компоненты** и выберите пункт **Добавить компонент**.

     Откроется *компонент Feature1. Feature* .

4. Откройте контекстное меню для Feature1. feature, а затем выберите **Добавить приемник событий** , чтобы добавить в компонент модуль кода.

## <a name="add-code-to-the-feature-receiver"></a>Добавление кода в приемник компонента

Затем добавьте код в два метода в приемнике компонента: `FeatureActivated` и `FeatureDeactivating` . Эти методы запускаются каждый раз, когда компонент активируется или деактивируется в SharePoint соответственно.

1. В верхней части класса `Feature1EventReceiver` добавьте следующий код для объявления переменных, которые задают сайт и дочерний сайт SharePoint.

    ```vb
    ' SharePoint site and subsite.
    Private siteUrl As String = "http://localhost"
    Private webUrl As String = "/"
    ```

    ```csharp
    // SharePoint site and subsite.
    private string siteUrl = "http://localhost";
    private string webUrl = "/";
    ```

2. Замените метод `FeatureActivated` следующим кодом:

    ```vb
    Public Overrides Sub FeatureActivated(ByVal properties As SPFeatureReceiverProperties)
        Try
            Using site As New SPSite(siteUrl)
                Using web As SPWeb = site.OpenWeb(webUrl)
                    ' Reference the lists.
                    Dim announcementsList As SPList = web.Lists("Announcements")
                    Dim taskList As SPList = web.Lists("Tasks")

                    ' Add an announcement to the Announcements list.
                    Dim listItem As SPListItem = announcementsList.Items.Add()
                    listItem("Title") = "Activated Feature: " & Convert.ToString(properties.Definition.DisplayName)
                    listItem("Body") = Convert.ToString(properties.Definition.DisplayName) & " was activated on: " & DateTime.Now.ToString()
                    listItem.Update()

                    ' Add a task to the Task list.
                    Dim newTask As SPListItem = taskList.Items.Add()
                    newTask("Title") = "Deactivate feature: " & Convert.ToString(properties.Definition.DisplayName)
                    newTask.Update()
                End Using
            End Using

        Catch e As Exception
            Console.WriteLine("Error: " & e.ToString())
        End Try

    End Sub
    ```

    ```csharp
    public override void FeatureActivated(SPFeatureReceiverProperties properties)
    {
        try
        {
            using (SPSite site = new SPSite(siteUrl))
            {
                using (SPWeb web = site.OpenWeb(webUrl))
                {
                    // Reference the lists.
                    SPList announcementsList = web.Lists["Announcements"];
                    SPList taskList = web.Lists["Tasks"];

                    // Add an announcement to the Announcements list.
                    SPListItem listItem = announcementsList.Items.Add();
                    listItem["Title"] = "Activated Feature: " + properties.Definition.DisplayName;
                    listItem["Body"] = properties.Definition.DisplayName + " was activated on: " + DateTime.Now.ToString();
                    listItem.Update();

                    // Add a task to the Task list.
                    SPListItem newTask = taskList.Items.Add();
                    newTask["Title"] = "Deactivate feature: " + properties.Definition.DisplayName;
                    newTask.Update();
                }
            }
        }

        catch (Exception e)
        {
            Console.WriteLine("Error: " + e.ToString());
        }

    }
    ```

3. Замените метод `FeatureDeactivating` следующим кодом:

    ```vb
    Public Overrides Sub FeatureDeactivating(ByVal properties As SPFeatureReceiverProperties)
        ' The following line induces an error to demonstrate debugging.
        ' Remove this line later for proper operation.
        Throw New System.InvalidOperationException("Serious error occurred!")
        Try
            Using site As New SPSite(siteUrl)
                Using web As SPWeb = site.OpenWeb(webUrl)
                    ' Reference the lists.
                    Dim taskList As SPList = web.Lists("Tasks")
                    Dim announcementsList As SPList = web.Lists("Announcements")

                    ' Add an announcement that the feature was deactivated.
                    Dim listItem As SPListItem = announcementsList.Items.Add()
                    listItem("Title") = "Deactivated Feature: " & Convert.ToString(properties.Definition.DisplayName)
                    listItem("Body") = Convert.ToString(properties.Definition.DisplayName) & " was deactivated on: " & DateTime.Now.ToString()
                    listItem.Update()

                    ' Find the task that the feature receiver added to the Task list when the
                    ' feature was activated.
                    Dim qry As New SPQuery()
                    qry.Query = "<Where><Contains><FieldRef Name='Title' /><Value Type='Text'>Deactivate</Value></Contains></Where>"
                    Dim taskItems As SPListItemCollection = taskList.GetItems(qry)

                    For Each taskItem As SPListItem In taskItems
                        ' Mark the task as complete.
                        taskItem("PercentComplete") = 1
                        taskItem("Status") = "Completed"
                        taskItem.Update()
                    Next
                End Using

            End Using

        Catch e As Exception
            Console.WriteLine("Error: " & e.ToString())
        End Try

    End Sub
    ```

    ```csharp
    public override void FeatureDeactivating(SPFeatureReceiverProperties properties)
    {
        // The following line induces an error to demonstrate debugging.
        // Remove this line later for proper operation.
        throw new System.InvalidOperationException("A serious error occurred!");
        try
        {
            using (SPSite site = new SPSite(siteUrl))
            {
                using (SPWeb web = site.OpenWeb(webUrl))
                {
                    // Reference the lists.
                    SPList taskList = web.Lists["Tasks"];
                    SPList announcementsList = web.Lists["Announcements"];

                    // Add an announcement that the feature was deactivated.
                    SPListItem listItem = announcementsList.Items.Add();
                    listItem["Title"] = "Deactivated Feature: " + properties.Definition.DisplayName;
                    listItem["Body"] = properties.Definition.DisplayName + " was deactivated on: " + DateTime.Now.ToString();
                    listItem.Update();

                    // Find the task that the feature receiver added to the Task list when the
                    // feature was activated.
                    SPQuery qry = new SPQuery();
                    qry.Query = "<Where><Contains><FieldRef Name='Title' /><Value Type='Text'>Deactivate</Value></Contains></Where>";
                    SPListItemCollection taskItems = taskList.GetItems(qry);

                    foreach (SPListItem taskItem in taskItems)
                    {
                        // Mark the task as complete.
                        taskItem["PercentComplete"] = 1;
                        taskItem["Status"] = "Completed";
                        taskItem.Update();
                    }
                }
            }

        }

        catch (Exception e)
        {
            Console.WriteLine("Error: " + e.ToString());
        }
    }
    ```

## <a name="test-the-project"></a>Тестирование проекта

Теперь, когда код добавлен в приемник компонента и сборщик данных выполняется, разверните и запустите решение SharePoint для тестирования правильности работы.

> [!IMPORTANT]
> В этом примере возникает ошибка в обработчике событий FeatureDeactivating. Далее в этом пошаговом руководстве ошибка обнаруживается с помощью .iTrace-файла, созданного сборщиком данных.

1. Разверните решение в SharePoint, а затем откройте сайт SharePoint в браузере.

     Возможность автоматически активируется, что приводит к добавлению приемником возможности объявления и задачи.

2. Отображение содержимого списков извещений и задач.

     В списке извещений должно быть новое извещение с именем **активированная функция: IntelliTraceTest_Feature1**, а список задач должен иметь новую задачу с именем **деактивация компонента: IntelliTraceTest_Feature1**. Если один из этих элементов отсутствует, проверьте, активирован ли компонент. Если он не активирован, активируйте его.

3. Отключите компонент, выполнив следующие действия.

   1. В меню **действия сайта** в SharePoint выберите **Параметры сайта**.

   2. В разделе **действия сайта** выберите ссылку **Управление компонентами сайта** .

   3. Рядом с **Интеллитрацетест Feature1** нажмите кнопку **деактивировать** .

   4. На странице предупреждения щелкните ссылку **Деактивировать этот компонент** .

      Обработчик событий FeatureDeactivating() вызывает ошибку.

## <a name="collect-intellitrace-data-by-using-microsoft-monitoring-agent"></a>Получение данных IntelliTrace с помощью Microsoft Monitoring Agent

При установке Microsoft Monitoring Agent в системе, где работает SharePoint, можно отлаживать решения SharePoint, используя более конкретные данные, чем общие сведения, возвращаемые IntelliTrace. Агент работает вне Visual Studio с помощью командлетов PowerShell для захвата отладочной информации в процессе выполнения решения SharePoint.

> [!NOTE]
> Сведения о конфигурации в этом разделе относятся к этому примеру. Дополнительные сведения о других параметрах конфигурации см. [в разделе Использование автономного сборщика IntelliTrace](../debugger/using-the-intellitrace-stand-alone-collector.md).

1. На компьютере, на котором работает SharePoint, [настройте Microsoft Monitoring Agent и запустите мониторинг решения](../debugger/using-the-intellitrace-stand-alone-collector.md).

2. Отключение компонента.

   1. В меню **действия сайта** в SharePoint выберите **Параметры сайта**.

   2. В разделе **действия сайта** выберите ссылку **Управление компонентами сайта** .

   3. Рядом с **Интеллитрацетест Feature1** нажмите кнопку **деактивировать** .

   4. На странице предупреждения щелкните ссылку **Деактивировать этот компонент** .

      Возникает ошибка (в данном случае из-за возникшей в обработчике событий FeatureDeactivating() ошибки).

3. В окне PowerShell выполните команду "WebApplicationMonitoring", чтобы создать iTrace [-](/previous-versions/system-center/powershell/system-center-2012-r2/dn472753(v=sc.20)) файл, прерывать мониторинг и перезапустить решение SharePoint.

     **WebApplicationMonitoring***" \<SharePointSite> \\<шарепоинтаппнаме \>* "  

## <a name="debug-and-fix-the-sharepoint-solution"></a>Отладка и исправление решения SharePoint

Теперь можно просмотреть файл журнала IntelliTrace в Visual Studio для поиска и исправления ошибки в решении SharePoint.

1. В папке \IntelliTraceLogs откройте .iTrace-файл в Visual Studio.

     Откроется страница **сводки IntelliTrace** . Так как ошибка не была обработана, идентификатор корреляции SharePoint (GUID) отображается в области необработанные исключения в разделе **анализ** . Нажмите кнопку **Стек вызовов** , если хотите просмотреть стек вызовов, в котором произошла ошибка.

2. Нажмите кнопку **Отладка исключения** .

     При появлении соответствующего запроса загрузите символьные файлы. В окне **IntelliTrace** исключение выделено как "вызванное: серьезная ошибка".

     В окне IntelliTrace выберите исключение для отображения кода, в котором произошла ошибка.

3. Устраните ошибку, открыв решение SharePoint, а затем либо закомментируйте или удалив инструкцию **throw** , в начале процедуры FeatureDeactivating ().

4. Повторите сборку решения в Visual Studio, а затем заново разверните его в SharePoint.

5. Отключите компонент, выполнив следующие действия.

    1. В меню **действия сайта** в SharePoint выберите **Параметры сайта**.

    2. В разделе **действия сайта** выберите ссылку **Управление компонентами сайта** .

    3. Рядом с **Интеллитрацетест Feature1** нажмите кнопку **деактивировать** .

    4. На странице предупреждения щелкните ссылку **Деактивировать этот компонент** .

6. Откройте список задач и убедитесь, что значение **состояния** задачи деактивации — "завершено", а значение **% завершения** — 100%.

     Теперь код будет выполнен правильно.

## <a name="see-also"></a>См. также раздел

- [Проверка и отладка кода SharePoint](../sharepoint/verifying-and-debugging-sharepoint-code.md)
- [IntelliTrace](../debugger/intellitrace.md)
- [Пошаговое руководство. Проверка кода SharePoint с помощью модульных тестов](/previous-versions/visualstudio/visual-studio-2010/gg599006\(v\=vs.100\))
