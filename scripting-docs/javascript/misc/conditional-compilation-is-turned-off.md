---
description: Предпринята попытка использовать переменную условной компиляции без предварительного включения условной компиляции.
title: Условная компиляция отключена | Документация Майкрософт
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT1030
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 59a030b0-a6c6-47f2-b90e-c0ed204d5116
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ccda9769597d6a981a9277d2b1e1f54b73d6ae18
ms.sourcegitcommit: 691d2a47f92f991241fdb132a82c53a537198d50
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/16/2021
ms.locfileid: "103571432"
---
# <a name="conditional-compilation-is-turned-off"></a>Условная компиляция отключена
Предпринята попытка использовать переменную условной компиляции без предварительного включения условной компиляции. Включение условной компиляции означает, что [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] компилятор интерпретирует идентификаторы, начинающиеся с @, как переменные условной компиляции. Для этого необходимо начать условный код с помощью инструкции:  
  
```js
/*@cc_on @*/  
```  
  
### <a name="to-correct-this-error"></a>Исправление ошибки  
  
- Добавьте следующий оператор в начало условного кода:  
  
    ```JavaScript  
    /*@cc_on @*/  
    ```  
  
## <a name="see-also"></a>См. также  
 [Условная компиляция](/previous-versions/windows/internet-explorer/ie-developer/scripting-articles/121hztk3(v=vs.84))   
 [Переменные условной компиляции](/previous-versions/windows/internet-explorer/ie-developer/scripting-articles/s59bkzce(v=vs.84))   
 [@cc_on Баланс](https://developer.mozilla.org/docs/Archive/Web/JavaScript/Microsoft_Extensions/at-cc-on)   
 [@if Баланс](https://developer.mozilla.org/docs/Archive/Web/JavaScript/Microsoft_Extensions/at-if)   
 [@set Баланс](https://developer.mozilla.org/docs/Archive/Web/JavaScript/Microsoft_Extensions/at-set)
