---
description: При создании шаблона поиска регулярных выражений вы создали элемент шаблона с недопустимым коэффициентом повтора.
title: Непредвиденный квантор (JavaScript) | Документация Майкрософт
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5018
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: ba6d34f9-2d6f-486c-a929-6cd9818be322
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9351f9306cea9e3f6346b007d6fe05c1d7bbf319
ms.sourcegitcommit: 691d2a47f92f991241fdb132a82c53a537198d50
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/16/2021
ms.locfileid: "103571965"
---
# <a name="unexpected-quantifier-javascript"></a>Непредвиденный квантификатор (JavaScript)
При создании шаблона поиска регулярных выражений вы создали элемент шаблона с недопустимым коэффициентом повтора. Например, шаблон  
  
```js
/^+/  
```  
  
 является недопустимым, поскольку элемент ^ (начало ввода) не может иметь фактор повторения. В следующей таблице перечислены элементы, которые не могут иметь коэффициентов повторения.  
  
|Элемент|Описание|  
|-------------|-----------------|  
|^|Начало входных данных|  
|$|Конец входных данных|  
|\b|Граница слова|  
|\B|Граница, не относящаяся к слову|  
|*|Ноль или более повторений|  
|+|Одно или несколько повторений|  
|?|Ноль или одно повторение|  
|\n|n повторений|  
|{n,}|n или более повторений|  
|{n, m}|От n до m повторений, включительно|  
  
### <a name="to-correct-this-error"></a>Исправление ошибки  
  
- Убедитесь, что элемент шаблона поиска содержит только допустимые коэффициенты повторения.  
  
## <a name="see-also"></a>См. также  
 [Объект регулярного выражения](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/RegExp)   
 [Синтаксис регулярных выражений (JavaScript)](/previous-versions/1400241x(v=vs.100))
