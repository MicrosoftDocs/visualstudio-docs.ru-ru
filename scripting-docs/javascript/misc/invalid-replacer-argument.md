---
description: Предпринята попытка вызвать JSON. stringify с недопустимым аргументом.
title: Недопустимый аргумент замены | Документация Майкрософт
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5035
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 4727186f-facd-4aa6-9447-bbefbae83f07
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 95a73d6fcbcf1350eece52e2cd58693646617a28
ms.sourcegitcommit: 691d2a47f92f991241fdb132a82c53a537198d50
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/16/2021
ms.locfileid: "103570899"
---
# <a name="invalid-replacer-argument"></a>Недопустимый аргумент замены
Предпринята попытка вызова `JSON.stringify` с недопустимым аргументом. `replacer`Аргумент должен быть функцией или массивом.  
  
### <a name="to-correct-this-error"></a>Исправление ошибки  
  
- Измените `replacer` аргумент на функцию или массив.  
  
## <a name="example"></a>Пример  
 Код в этом примере вызывает ошибку времени выполнения, поскольку `memberfilter` является объектом, а не функцией или массивом.  
  
```JavaScript  
var contact = new Object();  
contact.firstname = "Jesper";  
contact.surname = "Aaberg";  
contact.phone = ["555-0100", "555-0120"];  
  
var memberfilter = new Object();  
  
// This line will cause a runtime error.  
var jsontext = JSON.stringify(contact, memberfilter, "\t");  
```  
  
## <a name="see-also"></a>См. также  
 [Объект JSON](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/JSON)   
 [Функция JSON. Parse](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/JSON/parse)   
 [Ошибки времени выполнения JavaScript](/microsoft-edge/devtools-guide/console/error-and-status-codes#javascript-run-time-errors)
