---
description: Предпринята попытка присвоить значение результату функции.
title: Невозможно присвоить результат функции | Документация Майкрософт
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5003
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: ee8ffb3a-1451-4cb3-99bf-5e9cf8b77d79
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 125d2dc7d41b1b65027952e4e6cb94ff97083e6e
ms.sourcegitcommit: 691d2a47f92f991241fdb132a82c53a537198d50
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/16/2021
ms.locfileid: "103571926"
---
# <a name="cannot-assign-to-a-function-result"></a>Присвоение результату функции невозможно
Предпринята попытка присвоить значение результату функции. Результат функции можно присвоить переменной, но нельзя использовать в качестве переменной. Если необходимо назначить новое значение самой функции, не указывайте круглые скобки (оператор вызова функции). В следующем примере показана ситуация, в которой возникает эта ошибка.  
  
```js
myFunction() = 42;  // Attempting to assign the value 42 to the result of the function call.  
```  
  
### <a name="to-correct-this-error"></a>Исправление ошибки  
  
- Не используйте значение результата вызова функции, как и то, которое можно *присвоить*. Вы можете присвоить результат вызова функции *переменной* .  
  
    ```JavaScript  
    myVar = myFunction(42);  
    ```  
  
- Кроме того, в переменную можно назначить саму функцию (а не ее возвращаемое значение).  
  
    ```JavaScript  
    myFunction = new Function("return 42;");  
    ```  
  
## <a name="see-also"></a>См. также  
 [Объект функции](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Function)   
 [Написание кода JavaScript](https://developer.mozilla.org/docs/Learn/Getting_started_with_the_web/JavaScript_basics)   
 [Функции](https://developer.mozilla.org/docs/Learn/JavaScript/Building_blocks/Functions)
