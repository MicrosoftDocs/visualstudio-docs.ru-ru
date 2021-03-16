---
description: Вы указали объект, который не был Visual Basic safeArray, если он ожидался.
title: Требуется VBArray | Документация Майкрософт
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5013
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: f2998d7d-13a4-4bbe-b872-3ff3316551e4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e344e24b3fbef7b7f119a36513c222e085328072
ms.sourcegitcommit: 691d2a47f92f991241fdb132a82c53a537198d50
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/16/2021
ms.locfileid: "103572082"
---
# <a name="vbarray-expected"></a>Требуется VBArray
Вы указали объект, который не был Visual Basic safeArray, если он ожидался.  
  
```js
new VBArray(safeArray);  
```  
  
 Объекты VBArray доступны только для чтения и не могут быть созданы напрямую. Аргумент safeArray является значением VBArray и должен получить значение VBArray перед передачей в `VBArray` конструктор. Это можно сделать только путем получения значения из существующего объекта ActiveX или другого объекта.  
  
### <a name="to-correct-this-error"></a>Исправление ошибки  
  
- Убедитесь, что в конструктор **VBArray** передаются только объекты **VBArray** .  
  
## <a name="see-also"></a>См. также  
 [Объект VBArray](https://developer.mozilla.org/docs/Archive/Web/JavaScript/Microsoft_Extensions/VBArray)   
 [Использование массивов](https://developer.mozilla.org/docs/Learn/JavaScript/First_steps/Arrays)
