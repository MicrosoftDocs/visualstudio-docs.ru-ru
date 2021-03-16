---
description: Вы попытались создать класс символов для сопоставления регулярного выражения, но не включили правую квадратную скобку.
title: Ожидался символ "]" в регулярном выражении (JavaScript) | Документация Майкрософт
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5019
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 1ca2079a-44dd-479f-a1e3-e04a14d0739e
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6b5e7a25f6fbef3bf87d084b149ee9f356981600
ms.sourcegitcommit: 691d2a47f92f991241fdb132a82c53a537198d50
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/16/2021
ms.locfileid: "103570951"
---
# <a name="expected--in-regular-expression-javascript"></a>В регулярном выражении ожидался символ "]" (JavaScript)
Вы попытались создать класс символов для сопоставления регулярного выражения, но не включили правую квадратную скобку. Отдельные комбинации литеральных символов можно собрать в классы символов, поместив их в квадратные скобки. Класс символов соответствует любому символу, который он содержит. Например,/[abc]/соответствует любому из букв "a", "b" или "c".  
  
### <a name="to-correct-this-error"></a>Исправление ошибки  
  
- Добавьте правую квадратную скобку в регулярное выражение.  
  
    > [!NOTE]
    > Если нужно сопоставить одну квадратную скобку, построчно отменяйте ее с помощью обратной косой черты \\ [-, поэтому она не интерпретируется как Специальный символ [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] .  
  
## <a name="see-also"></a>См. также  
 [Объект регулярного выражения](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/RegExp)   
 [Синтаксис регулярных выражений (JavaScript)](/previous-versions/1400241x(v=vs.100))
