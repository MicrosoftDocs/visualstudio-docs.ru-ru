---
description: При вызове конструктора массива с аргументом, который не является целым числом (целые числа состоят из нуля и набора положительных целых чисел).
title: Длина массива должна быть конечным положительным целым числом | Документация Майкрософт
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5029
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 1a467040-4702-4178-848f-418a5974e907
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 49d3d2985706ad6cfca9b6ac441baa039ccf04af
ms.sourcegitcommit: 691d2a47f92f991241fdb132a82c53a537198d50
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/16/2021
ms.locfileid: "103572121"
---
# <a name="array-length-must-be-a-finite-positive-integer"></a>Длина массива должна быть выражена конечным положительным числом
При вызове конструктора **массива** с аргументом, который не является целым числом (целые числа состоят из нуля и набора положительных целых чисел).  
  
### <a name="to-correct-this-error"></a>Исправление ошибки  
  
- Используйте положительные целые числа только при создании нового `Array` объекта. Если нужно создать массив с одним элементом, который не является целым числом, сделайте это в два этапа. Сначала создайте массив с одним элементом, а затем поместите значение в первый элемент (массив [0]). Ниже приведен пример, в котором создается эта ошибка.  
  
    ```JavaScript  
    var piArray = new Array(3.14159);  
    ```  
  
     В следующем примере показан правильный способ указания массива с одним числовым элементом.  
  
    ```JavaScript  
    var piArray = new Array(1);  
    piArray [0] = 3.14159;  
    ```  
  
     Отсутствует верхний предел размера массива, кроме максимального целого значения (приблизительно 4 000 000 000).  
  
## <a name="see-also"></a>См. также  
 [Использование массивов](https://developer.mozilla.org/docs/Learn/JavaScript/First_steps/Arrays)
