---
title: Доступ к данным в документах на сервере
description: Узнайте, как программировать данные в настройке на уровне документа без использования объектной модели Microsoft Office Word или Microsoft Office Excel.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data [Office development in Visual Studio], accessing on server
- data access [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 0df6aef3c83d66b84f569e85e953fde8a3f0e16c
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/21/2021
ms.locfileid: "107826776"
---
# <a name="access-data-in-documents-on-the-server"></a>Доступ к данным в документах на сервере
  Вы можете программировать данные в настройке на уровне документа без использования объектной модели Microsoft Office Word или Microsoft Office Excel. Это означает, что вы можете получить доступ к данным, содержащимся в документе на сервере, на котором не установлен Word или Excel. Например, код на сервере (например, на [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] странице) может настраивать данные в документе и отсылать настроенный документ конечному пользователю. Когда конечный пользователь открывает документ, код привязки данных в сборке решения привязывает пользовательские данные к документу. Это возможно, поскольку данные в документе отделены от пользовательского интерфейса. Дополнительные сведения см. [в разделе кэшированные данные в настройках уровня документа](../vsto/cached-data-in-document-level-customizations.md).

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

## <a name="cache-data-for-use-on-a-server"></a>Кэширование данных для использования на сервере
 Чтобы кэшировать объект данных в документе, пометьте его <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> атрибутом во время разработки или используйте `StartCaching` метод ведущего элемента во время выполнения. При кэшировании объекта данных в документе [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] сериализует объект в XML-строку, которая хранится в документе. Объекты должны удовлетворять определенным требованиям для кэширования. Дополнительные сведения см. в разделе [кэширование данных](../vsto/caching-data.md).

 Код на стороне сервера может управлять любыми объектами данных в кэше данных. Элементы управления, привязанные к кэшированным экземплярам данных, синхронизируются с пользовательским интерфейсом, поэтому любые изменения на стороне сервера, внесенные в данные, отображаются автоматически при открытии документа на клиенте.

## <a name="access-data-in-the-cache"></a>Доступ к данным в кэше
 Доступ к данным в кэше можно получить из приложений, находящихся за пределами Office, например из консольного приложения, Windows Forms приложения или веб-страницы. Приложение, обращающееся к кэшированным данным, должно иметь полное доверие. Веб-приложение с частичным доверием не может вставлять, извлекать или изменять данные, кэшированные в документе Office.

 Кэш данных доступен через иерархию коллекций, предоставляемых <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.CachedData%2A> свойством <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> класса:

- <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.CachedData%2A>Свойство возвращает объект <xref:Microsoft.VisualStudio.Tools.Applications.CachedData> , который содержит все кэшированные данные в настройке на уровне документа.

- Каждый <xref:Microsoft.VisualStudio.Tools.Applications.CachedData> содержит один или несколько объектов <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataHostItem>. <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataHostItem>Содержит все объекты кэшированных данных, определенные в одном классе.

- Каждый <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataHostItem> содержит один или несколько объектов <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem>. <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem>Представляет один объект кэшированных данных.

  В следующем примере кода показано, как получить доступ к кэшированной строке в `Sheet1` классе проекта книги Excel. Этот пример является частью более крупного примера, предоставляемого для <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.Save%2A> метода.

  :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_ServerDocument/Form1.cs" id="Snippet12":::
  :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_ServerDocument/Form1.vb" id="Snippet12":::

## <a name="modify-data-in-the-cache"></a>Изменение данных в кэше
 Для изменения объекта кэшированных данных обычно выполняются следующие действия.

1. Десериализация XML-представления кэшированного объекта в новый экземпляр объекта. Доступ к XML можно получить с помощью <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem.Xml%2A> свойства <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem> объекта, представляющего кэшированный объект данных.

2. Внесите изменения в эту копию.

3. Выполните сериализацию измененного объекта обратно в кэш данных с помощью одного из следующих параметров:

    - Если вы хотите автоматически сериализовать изменения, используйте <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem.SerializeDataInstance%2A> метод. Этот метод использует формат **DiffGram** для сериализации <xref:System.Data.DataSet> , <xref:System.Data.DataTable> и типизированных объектов DataSet в кэше данных. Формат **DiffGram** гарантирует, что изменения в кэше данных в автономном документе отправляются на сервер правильно.

    - Если вы хотите выполнить собственную сериализацию изменений в кэшированные данные, можно непосредственно выполнить запись в <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem.Xml%2A> свойство. Укажите формат **DiffGram** , если используется <xref:System.Data.Common.DataAdapter> для обновления базы данных с изменениями, внесенными в данные в <xref:System.Data.DataSet> , <xref:System.Data.DataTable> или типизированном наборе данных. В противном случае <xref:System.Data.Common.DataAdapter> будет обновлена база данных путем добавления новых строк вместо изменения существующих строк.

### <a name="modify-data-without-deserializing-the-current-value"></a>Изменение данных без десериализации текущего значения
 В некоторых случаях может потребоваться изменить значение кэшированного объекта без предварительной десериализации текущего значения. Например, это можно сделать, если изменить значение объекта, имеющего простой тип, например строку или целое число, или инициализировать кэширование <xref:System.Data.DataSet> в документе на сервере. В таких случаях можно использовать <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem.SerializeDataInstance%2A> метод без предварительной десериализации текущего значения кэшированного объекта.

 В следующем примере кода показано, как изменить значение кэшированной строки в `Sheet1` классе проекта книги Excel. Этот пример является частью более крупного примера, предоставляемого для <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.Save%2A> метода.

 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_ServerDocument/Form1.cs" id="Snippet11":::
 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_ServerDocument/Form1.vb" id="Snippet11":::

### <a name="modify-null-values-in-the-data-cache"></a>Изменение значений NULL в кэше данных
 В кэше данных не хранятся объекты, имеющие значение **null** при сохранении и закрытии документа. Это ограничение имеет несколько последствий при изменении кэшированных данных.

- Если для любого объекта в кэше данных задано значение **null**, все объекты в кэше данных будут автоматически установлены в значение **null** при открытии документа, а весь кэш данных будет очищаться при сохранении и закрытии документа. То есть все кэшированные объекты будут удалены из кэша данных, а <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.CachedData%2A> коллекция будет пустой.

- Если вы создаете решение с **пустыми** объектами в кэше данных и хотите инициализировать эти объекты с помощью <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> класса до первого открытия документа, необходимо убедиться, что инициализируются все объекты в кэше данных. При инициализации только некоторых объектов все объекты будут установлены в **значение NULL** при открытии документа, а весь кэш данных будет очищаться при сохранении и закрытии документа.

## <a name="access-typed-datasets-in-the-cache"></a>Доступ к типизированным наборам данных в кэше
 Если требуется получить доступ к данным в типизированном наборе данных как из решения Office, так и из приложения, находящегося за пределами Office, например Windows Forms приложения или [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] проекта, необходимо определить типизированный набор данных в отдельной сборке, на которую есть ссылки в обоих проектах. Если добавить типизированный набор данных в каждый проект с помощью мастера **настройки источника данных** или **Конструктор наборов данных**, платформа .NET Framework будет обрабатывать типизированные наборы данных в двух проектах как разные типы. Дополнительные сведения о создании типизированных наборов данных см. [в разделе Создание и Настройка наборов данных в Visual Studio](../data-tools/create-and-configure-datasets-in-visual-studio.md).

## <a name="see-also"></a>См. также статью

- [Доступ к данным в документах на сервере](../vsto/accessing-data-in-documents-on-the-server.md)
- [Кэшированные данные в настройках уровня документа](../vsto/cached-data-in-document-level-customizations.md)