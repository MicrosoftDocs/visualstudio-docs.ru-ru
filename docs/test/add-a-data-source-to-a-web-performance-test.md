---
title: Добавление источника данных в веб-тест производительности
description: Сведения о том, как выполнить привязку данных для предоставления разных значений для одного и того же теста (например, для предоставления разных значений для параметров отправки форм).
ms.custom: SEO-VS-2020
ms.date: 10/03/2016
ms.topic: how-to
helpviewer_keywords:
- Web performance tests, walkthroughs
- Web performance tests, data binding (database)
ms.assetid: 2ada376d-f168-455d-9643-6acb535360c1
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.openlocfilehash: 71aa3dbf4657896093dae59451140f48f83f1622
ms.sourcegitcommit: 01a411cd7ae3488b7b979a947bca92fd296a98e9
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/09/2021
ms.locfileid: "111761008"
---
# <a name="add-a-data-source-to-a-web-performance-test"></a>Добавление источника данных в веб-тест производительности

Привязка данных позволяет предоставлять разные значения для одного и того же теста — например, предоставлять разные значения для параметров отправки форм.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

![Привязка данных в веб-тесту производительности](../test/media/web_test_databinding_conceptual.png)

Будет использован пример приложения ASP.NET. Оно содержит три *ASPX*-страницы — страницу по умолчанию, страницу "Красная" и страницу "Синяя". На странице по умолчанию расположены переключатель, позволяющий выбирать "Красная" или "Синяя", и кнопка "Отправить". Две другие *ASPX*-страницы очень просты. Одна имеет метку "Красная", а другая — метку "Синяя". При нажатии кнопки "Отправить" на странице по умолчанию открывается одна из других страниц. Вы можете скачать пример [ColorWebApp](https://code.msdn.microsoft.com/Sample-ColorWebApp-76ff7506) или просто создать собственное веб-приложение.

![Запуск веб-приложения, подлежащего тестированию](../test/media/web_test_databinding_runwebapp.png)

Решение должно также включать веб-тест производительности, просматривающий страницы веб-приложения.

![Решение с веб-тестом производительности](../test/media/web_test_databinding_solution.png)

## <a name="create-a-sql-database"></a>Создание базы данных SQL

::: moniker range="vs-2017"

1. Если у вас нет Visual Studio Enterprise, вы можете загрузить ее на странице [Загрузки Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download).

2. Создайте базу данных SQL.

     ![Добавление новой базы данных SQL](../test/media/web_test_databinding_sql_addnewdb.png)

3. Создайте проект базы данных.

     ![Создание нового проекта из базы данных](../test/media/web_test_databinding_sql_addnewdbproject.png)

4. Добавьте таблицу в проект базы данных.

     ![Добавление новой таблицы в проект базы данных](../test/media/web_test_databinding_sql_addnewdbtablename.png)

5. Добавьте поля в таблицу.

     ![Добавление полей в таблицу](../test/media/web_test_databinding_sql_addnewdbaddfields.png)

6. Опубликуйте проект базы данных.

     ![Публикация проекта базы данных из обозревателя решений](../test/media/web_test_databinding_sql_addnewdbpublish.png)

7. Добавьте данные в поля.

     ![Добавление данных в поля](../test/media/web_test_databinding_sql_addnewfieldsadddata.png)

::: moniker-end

::: moniker range=">=vs-2019"

1. Если у вас нет Visual Studio Enterprise, вы можете загрузить ее на странице [Загрузки Visual Studio](https://visualstudio.microsoft.com/downloads).

2. Создайте базу данных SQL.

     ![Добавление новой базы данных SQL](../test/media/web_test_databinding_sql_addnewdb.png)

3. Создайте проект базы данных.

     ![Создание нового проекта из базы данных](../test/media/web_test_databinding_sql_addnewdbproject.png)

4. Добавьте таблицу в проект базы данных.

     ![Добавление новой таблицы в проект базы данных](../test/media/web_test_databinding_sql_addnewdbtablename.png)

5. Добавьте поля в таблицу.

     ![Добавление полей в таблицу](../test/media/web_test_databinding_sql_addnewdbaddfields.png)

6. Опубликуйте проект базы данных.

     ![Публикация проекта базы данных из обозревателя решений](../test/media/web_test_databinding_sql_addnewdbpublish.png)

7. Добавьте данные в поля.

     ![Добавление данных в поля](../test/media/web_test_databinding_sql_addnewfieldsadddata.png)

::: moniker-end

## <a name="add-the-data-source"></a>Добавление источника данных

1. Добавьте источник данных.

     ![Добавление источника данных в веб-тест производительности](../test/media/web_test_databinding_sql_adddatasource.png)

2. Выберите тип источника данных и дайте ему имя.

     ![Присвоение имени источнику — базе данных](../test/media/web_test_databinding_sql_adddatasourcedialog.png)

3. Создайте подключение.

     ![Выбор нового подключения](../test/media/web_test_databinding_sql_adddatasourcedialogconnectionnew.png)

     Введите сведения о подключении.

     ![Ввод свойств подключения к базе данных SQL](../test/media/web_test_databinding_sql_adddatasourcedialogconnection.png)

4. Выберите таблицу, которую требуется использовать для теста.

     ![Добавление таблицы Color в качестве источника данных](../test/media/web_test_databinding_sql_adddatasourcedialogaddtable.png)

     Таблица привязана к тесту.

     ![Добавление узла "Источник данных" в веб-тест производительности](../test/media/web_test_databinding_requestnodeadded_mdb.png)

5. Сохраните тест.

## <a name="bind-the-data"></a>Привязка данных

1. Привяжите поле **ColorName**.

     ![Привязка поля ColorName к значению RadioButtonList1](../test/media/web_test_databinding_sql_binddatasource.png)

2. Откройте файл *Local.testsettings* в **обозревателе решений** и выберите параметр **Один запуск на строку источника данных**.

     ![Изменение файла параметров тестирования](../test/media/web_test_databinding_sql_testsettings.png)

3. Сохраните веб-тест производительности.

## <a name="run-the-test-with-the-data"></a>Выполнение теста с данными

1. Запустите тест.

     ![Запуск веб-теста производительности для проверки привязки](../test/media/web_test_databinding_sql_runtest.png)

     Два запуска отображаются для каждой строки данных. Запуск 1 отправляет запрос страницы *Red.aspx*, а запуск 2 отправляет запрос страницы *Blue.aspx*.

     ![Результаты выполнения теста](../test/media/web_test_databinding_sql_runresults.png)

     При привязке к источнику данных можно нарушить правило URL-адреса отклика по умолчанию. В этом случае ошибка в запуске 2 вызвана правилом, которое ожидает получить страницу *Red.aspx* из исходной записи теста, но привязка данных теперь направляет его на страницу *Blue.aspx*.

2. Исправьте ошибку проверки, удалив правила проверки **URL-адреса отклика**, и снова запустите тест.

     ![Удаление правила проверки URL-адреса отклика](../test/media/web_test_databinding_sql_deleteresponseurl.png)

     Теперь веб-тест производительности проходит успешно с использованием привязки данных.

     ![Тест проходит с использованием привязки данных](../test/media/web_test_databinding_sql_deleteresponseurlrunresults.png)

## <a name="q--a"></a>Вопросы и ответы

### <a name="q-what-databases-can-i-use-as-a-data-source"></a>Вопрос. Какие базы данных можно использовать в качестве источника данных?

**Ответ.** Можно использовать следующие компоненты:

- Microsoft SQL Azure.

- Любая версия Microsoft SQL Server 2005 или выше.

- Файл базы данных Microsoft SQL Server (включая SQL Express).

- Microsoft ODBC.

- Файл Microsoft Access, использующий для OLE DB поставщика .NET Framework.

- Oracle 7.3, 8i, 9i или 10g.

### <a name="q-how-do-i-use-a-comma-separated-value-csv-text-file-as-a-data-source"></a>Вопрос. Можно ли использовать текстовый CSV-файл в качестве источника данных?

**Ответ.** Ниже описан порядок действий.

1. Создайте папку, чтобы организовать артефакты базы данных проекта и добавить элемент.

     ![Добавление нового элемента в папку "Данные"](../test/media/web_test_databinding_foldernewitem.png)

2. Создание текстового файла.

     ![Присвоение новому текстовом файлу имени ColorData.csv](../test/media/web_test_databinding_foldernewitemtextfile.png)

3. Измените текстовый файл и добавьте в него следующий текст:

    ```text
    ColorId, ColorName
    0,Red
    1,Blue
    ```

4. Используйте инструкции в разделе [Добавление источника данных](#add-the-data-source), но в качестве источника данных выберите CSV-файл.

     ![Ввод имени и выбор CSV-файла](../test/media/web_test_databinding_adddatasourcedialog.png)

### <a name="q-what-if-my-existing-csv-file-does-not-contain-column-headers"></a>Вопрос. В моем CSV-файле нет заголовков столбцов. Как действовать в этом случае?

**Ответ.** Если нет возможности добавить заголовки столбцов, можно использовать файл описания схемы, чтобы рассматривать CSV-файл как базу данных.

1. Добавьте новый текстовый файл с именем *schema.ini*.

     ![Добавление файла schema.ini](../test/media/web_test_databinding_schemafile.png)

2. Измените файл *schema.ini*, добавив в него сведения, описывающие структуру данных. Например, файл схемы, описывающий CSV-файл, может выглядеть следующим образом.

    ```text
    [testdata.csv]
    ColNameHeader=False
    ```

3. Добавьте источник данных в тест.

     ![Добавление источника данных в веб-тест производительности](../test/media/web_test_databinding_sql_adddatasource.png)

4. Если используется файл *schema.ini*, выберите **базу данных** (не CSV-файл) в качестве источника данных и присвойте ей имя.

     ![Добавление базы данных в качестве источника данных](../test/media/web_test_databinding_adddatasourcecolortext.png)

5. Создайте подключение.

     ![Выбор нового подключения](../test/media/web_test_databinding_sql_adddatasourcedialogconnectionnew.png)

6. Выберите поставщика данных платформы .NET Framework для OLE DB.

     ![Выбор поставщика данных .NET Framework для OLE DB](../test/media/web_test_databinding_adddatasourcecolortext2.png)

7. Выберите **Дополнительно**.

     ![Выберите "Дополнительно"](../test/media/web_test_databinding_advanced.png)

8. Для свойства "Поставщик" выберите значение Microsoft.Jet.OLEDB.4.0, а затем установите для параметра **Расширенные свойства** значение Text;HDR=NO.

     ![Применение дополнительных свойств](../test/media/web_test_databinding_advancedproperties.png)

9. Введите имя папки, в которой находится файл схемы, и проверьте подключение.

     ![Ввод пути к папке данных](../test/media/web_test_databinding_adddatasourcecolortext5.png)

10. Выберите CSV-файл, который следует использовать.

     ![Выбор текстового файла](../test/media/web_test_databinding_adddatasourcecolortext6.png)

     После этого CSV-файл отображается как таблица.

     ![Источник данных добавлен в тест](../test/media/web_test_databinding_adddatasourcecolortext7.png)

### <a name="q-how-do-i-use-an-xml-file-as-a-data-source"></a>Вопрос. Как использовать XML-файл в качестве источника данных?

**Ответ.** Да.

1. Создайте папку, чтобы организовать артефакты базы данных проекта и добавить элемент.

     ![Добавление нового элемента в папку "Данные"](../test/media/web_test_databinding_foldernewitem.png)

2. Создайте XML-файл.

     ![Добавление файла ColorData.xml](../test/media/web_test_databinding_additemxmlfile.png)

3. Отредактируйте XML-файл и добавьте свои данные:

    ```xml
    <?xml version="1.0" encoding="utf-8" ?>
    <ColorData>
        <Color>
            <ColorId>0</ColorId>
            <ColorName>Red</ColorName>
        </Color>
        <Color>
            <ColorId>1</ColorId>
            <ColorName>Blue</ColorName>
        </Color>
    </ColorData>
    ```

4. Используйте инструкции в разделе [Добавление источника данных](#add-the-data-source), но в качестве источника данных выберите XML-файл.

     ![Ввод имени и выбор XML-файла](../test/media/web_test_databinding_adddatasourcedialogxml.png)

### <a name="q-can-i-add-data-binding-to-a-web-service-request-that-uses-soap"></a>Вопрос. Можно ли добавить привязку данных в запрос веб-службы, которая использует SOAP?

**Ответ.** Да, нужно изменить протокол SOAP XML вручную.

1. Выберите запрос веб-службы в дереве запросов и в окне "Свойства" выберите многоточие (…) в свойстве "Текст строки".

     ![Редактирование тела строки веб-службы](../test/media/web_test_databinding_webservicerequest.png)

2. Замените значения в тексте SOAP значениями привязанных данных с помощью следующего синтаксиса:

    ```xml
    {{DataSourceName.TableName.ColumnName}}
    ```

    Например, предположим, что имеется следующий код:

    ```xml
    <?xml version="1.0" encoding="utf-8"?>
    <soap:Envelope xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/">
        <soap:Body>
            <CheckStatus xmlns="http://tempuri.org/">
                <userName>string</userName> <password>string</password> <orderID>int</orderID>
            </CheckStatus>
        </soap:Body>
    </soap:Envelope>
    ```

    Можно изменить его на следующий код:

    ```xml
    <?xml version="1.0" encoding="utf-8"?>
    <soap:Envelope xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/">
        <soap:Body>
            <CheckStatus xmlns="http://tempuri.org/">
                <userName>{{DataSourceName.Users.Name}}</userName> <password>{{DataSourceName.Users.Password}}</password> <orderID>{{DataSourceName.Orders.OrderID}}</orderID>
            </CheckStatus>
        </soap:Body>
    </soap:Envelope>
    ```

3. Сохраните тест.
