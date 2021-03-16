---
description: Предпринята попытка вызвать JSON. stringify со значением, которое является недопустимым.
title: Циклическая ссылка в аргументе значения не поддерживается | Документация Майкрософт
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5034
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 5d06f0fa-86f5-49d1-8d50-af1759990f43
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 88e4ead99f8c59a1300d018bff9d3e81b0874b51
ms.sourcegitcommit: 691d2a47f92f991241fdb132a82c53a537198d50
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/16/2021
ms.locfileid: "103571146"
---
# <a name="circular-reference-in-value-argument-not-supported"></a>Циклическая ссылка в аргументе значения не поддерживается
Предпринята попытка вызова `JSON.stringify` со значением, которое является недопустимым. `value`Аргумент, массив или объект, содержит циклическую ссылку.  
  
### <a name="to-correct-this-error"></a>Исправление ошибки  
  
- Удалите циклическую ссылку из аргумента.  
  
## <a name="example"></a>Пример  
 Код в этом примере вызывает ошибку времени выполнения, так как `john` имеет ссылку на `mary` и `mary` имеет ссылку на `john` . чтобы удалить циклическую ссылку, удалите или отмените свойство `brother` `mary` объекта или `sister` свойства `john` объекта.  
  
```JavaScript  
var john = new Object();  
var mary = new Object();  
john.sister = mary;  
mary.brother = john;  
  
// This line causes a runtime error.  
var error = JSON.stringify(john);  
```  
  
## <a name="see-also"></a>См. также  
 [Объект JSON](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/JSON)   
 [Функция JSON. Parse](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/JSON/parse)   
 [Ошибки времени выполнения JavaScript](/microsoft-edge/devtools-guide/console/error-and-status-codes#javascript-run-time-errors)
