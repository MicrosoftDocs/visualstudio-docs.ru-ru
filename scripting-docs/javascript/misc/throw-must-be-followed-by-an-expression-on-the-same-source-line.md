---
description: Вы использовали ключевое слово Throw, но не подписано выражением в той же строке исходного кода.
title: Оператору throw должно следовать выражение в той же строке исходного кода | Документация Майкрософт
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT1035
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: b03b7747-01a1-40c6-af80-a1dd70bc5781
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cfa2bace6f82ae972204cc0a405cc7e8682e98af
ms.sourcegitcommit: 691d2a47f92f991241fdb132a82c53a537198d50
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/16/2021
ms.locfileid: "103570717"
---
# <a name="throw-must-be-followed-by-an-expression-on-the-same-source-line"></a>throw требует после себя выражение на той же строке
Вы использовали `throw` ключевое слово, но не выполнили выражение в той же строке исходного кода. `throw`Оператор состоит из двух частей: `throw` ключевого слова, за которым следует вызываемое выражение. Например:  
  
```JavaScript  
if (denominator == 0) {  
 throw new DivideByZeroException();  
}  
```  
  
 Эти два компонента не могут быть разделены.  
  
### <a name="to-correct-this-error"></a>Исправление ошибки  
  
- Убедитесь, что `throw` ключевое слово и выражение, которые должны быть созданы, отображаются в одной строке.  
  
## <a name="see-also"></a>См. также  
 [Объект Error](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Error)   
 [Оператор Throw](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Statements/throw)   
 [Попробуйте... перехватить... Оператор finally](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Statements/try...catch)
