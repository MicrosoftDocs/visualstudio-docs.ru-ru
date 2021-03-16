---
description: Предпринята попытка вызвать метод или свойство для объекта типа, отличного от Object, или был передан аргумент типа, отличного от Object, если требуется объект.
title: Ожидался объект | Документация Майкрософт
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5007
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 5d88c93d-e5b5-4b11-9bb5-bf1a5e41ccc3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a62a68b8dd5289794086dad6858238db6cc4f449
ms.sourcegitcommit: 691d2a47f92f991241fdb132a82c53a537198d50
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/16/2021
ms.locfileid: "103572069"
---
# <a name="object-expected"></a>Ожидался объект
Предпринята попытка вызвать метод или свойство для объекта, тип которого отличается от типа `Object`, или передать аргумент, тип которого отличается от типа `Object`. Объект вызова этого типа должен иметь тип `Object`.  
  
### <a name="to-correct-this-error"></a>Исправление ошибки  
  
- Вызывайте этот метод или свойство только для объектов типа `Object`.  
  
- Если ошибка связана с аргументом без объектов, передайте объект типа `Object`.  
  
- Проверьте, не вызывается ли вместо объекта типа `Object` неопределенная или пустая ссылка.  
  
     Такая ошибка возникает, например, в связи с аргументом myVar, указанном в следующем коде:  
  
    ```JavaScript  
    var str = myVar.toString();  
    ```  
  
     Вместо него можно использовать следующий код:  
  
    ```JavaScript  
    if (myVar) {  
        var str = myVar.toString();  
    }  
    ```  
  
## <a name="see-also"></a>См. также  
 [Объект Object](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Object)   
 [Объекты и массивы](https://developer.mozilla.org/docs/Learn/JavaScript/Objects)
