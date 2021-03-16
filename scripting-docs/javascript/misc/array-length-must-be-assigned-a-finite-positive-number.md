---
description: При задании свойства Length существующего объекта массива вы указали длину массива, которая не является положительным числом или нулем.
title: Длине массива должно быть присвоено конечное положительное число | Документация Майкрософт
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5030
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: c51c66a4-a543-4e95-b18d-2cfbcb3d1fdd
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3938f240580564112915ab0ba3036b63dc96cd8f
ms.sourcegitcommit: 691d2a47f92f991241fdb132a82c53a537198d50
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/16/2021
ms.locfileid: "103572147"
---
# <a name="array-length-must-be-assigned-a-finite-positive-number"></a>Длина массива должна быть указана в виде конечного положительного числа
При задании свойства **length** существующего объекта **массива** вы указали длину массива, которая не является положительным числом или нулем. Эта ошибка возникает при присвоении значения свойству **length** `Array` объекта, который является отрицательным или не является числом ( `NaN` ). Обратите внимание, что [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] автоматически преобразует дробные числа в целые целые числа.  
  
### <a name="to-correct-this-error"></a>Исправление ошибки  
  
- Присвойте положительное целое число свойству Length. Отсутствует верхний предел размера массива, кроме максимального целого значения (приблизительно 4 000 000 000). В следующем примере показан правильный способ задания свойства **length** объекта **массива** .  
  
    ```JavaScript  
    var my_array = new Array();  
    my_array.length = 99;  
    ```  
  
## <a name="see-also"></a>См. также  
 [Использование массивов](https://developer.mozilla.org/docs/Learn/JavaScript/First_steps/Arrays)
