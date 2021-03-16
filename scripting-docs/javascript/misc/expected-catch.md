---
description: Вы использовали блок try обработки исключений, но не написали соответствующий оператор catch.
title: Требуется "Catch" | Документация Майкрософт
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT1033
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: f1cd947f-eba2-411e-8e84-8ca86f608643
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b5cf6087ff5a299c575ac4f2cd5eb8a3e206b7e0
ms.sourcegitcommit: 691d2a47f92f991241fdb132a82c53a537198d50
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/16/2021
ms.locfileid: "103571042"
---
# <a name="expected-catch"></a>Ожидалось ключевое слово "catch"
Вы использовали блок **try** обработки исключений, но не написали соответствующий оператор **catch** . Механизм обработки исключений требует, чтобы код, который может завершиться ошибкой, вместе с кодом, который не должен выполняться при возникновении исключения, был заключен внутрь блока **try** . Исключения создаются в блоке **try** с помощью инструкции **throw** и перехватываются вне блока **try** с помощью одного или нескольких инструкций **catch** .  
  
### <a name="to-correct-this-error"></a>Исправление ошибки  
  
- Добавьте связанный блок **catch** .  
  
- Попробуйте использовать блок **finally** вместо блока **catch** .  
  
## <a name="see-also"></a>См. также  
 [Попробуйте... перехватить... Оператор finally](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Statements/try...catch)   
 [Объект Error](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Error)
