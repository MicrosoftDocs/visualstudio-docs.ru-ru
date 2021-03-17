---
description: Либо вы попытались вызвать один из методов прототипа функции для объекта, который не является объектом функции, либо вы использовали объект в контексте вызова функции.
title: Требуется функция | Документация Майкрософт
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5002
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: f62ade94-9f6f-4832-9b9b-49a06a385bbe
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 99e354118844d7e57f708cf3f2d5653ee1c0fc65
ms.sourcegitcommit: 3a855d3513407ea78336386dc3be0b75142614b0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/17/2021
ms.locfileid: "103622612"
---
# <a name="function-expected"></a>Требуется функция
Либо вы попытались вызвать один из методов **прототипа функции** для объекта, который не является `Function` объектом, либо вы использовали объект в контексте вызова функции. Например, следующий код выдает эту ошибку, так как **Пример** не является функцией.  
  
```JavaScript  
var example = new Object();  // Create a new object called "example".  
var x = example();           // Try and call example as if it were a function.  
```  
  
### <a name="to-correct-this-error"></a>Исправление ошибки  
  
- Вызываются только методы **прототипа функции** для `Function` объектов.  
  
- Убедитесь, что оператор вызова функции используется `()` только для вызова функций.  
  
## <a name="see-also"></a>См. также раздел  
 [Объект функции](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Function)   
 [Свойство prototype (Object)](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Object)
