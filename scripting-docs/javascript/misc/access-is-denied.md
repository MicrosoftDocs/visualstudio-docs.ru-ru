---
description: Скрипт попытался получить доступ к данным из источника, который не является узлом текущей страницы.
title: Отказано в доступе | Документация Майкрософт
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 8a512060-d744-47af-a83e-4ba42ea2c5b2
author: mikejo5000
ms.author: mikejo
ms.openlocfilehash: 6be3bce0643a5892973235871191766cac140962
ms.sourcegitcommit: 691d2a47f92f991241fdb132a82c53a537198d50
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/16/2021
ms.locfileid: "103571939"
---
# <a name="access-is-denied"></a>Доступ запрещен
Скрипт попытался получить доступ к данным из источника, который не является узлом текущей страницы. Политика одного источника, которой следует Internet Explorer и другие браузеры, позволяет скриптам получать доступ к данным только из тех источников, которые находятся в той же схеме, на том же узле и в том же порте, что и URL-адрес текущей страницы.  
  
 Например, если текущая страница имеет значение `https://employees.mycompany.com` , доступ к данным из следующих URL-адресов невозможен:  
  
- `http://data.contoso.com`, так как он использует HTTP, а не HTTPS.  
  
- `https://somedatasource.com`, так как это другой домен.  
  
- `https://employees.mycompany.com:8888`, так как он использует другой порт.  
  
### <a name="to-correct-this-error"></a>Исправление ошибки  
  
- Проверьте, поддерживает ли API, который вы пытаетесь вызвать, JSONP или CORS (два способа запроса данных, позволяющих создавать скрипты для безопасного обращения к другим доменам).  
  
- Если вызывается API REST, переадресуйте этот вызов на код со стороны вашего сервера, а затем добавьте в скрипты на стороне клиента новую конечную точку REST.  
  
     Дополнительные сведения см. в документации по политике одного источника, JSONP и CORS.
