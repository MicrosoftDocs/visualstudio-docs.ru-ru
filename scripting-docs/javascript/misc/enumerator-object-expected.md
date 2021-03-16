---
description: Предпринята попытка вызова метода Enumerator. prototype. atEnd, перечислителя. prototype. Item, перечислителя. prototype. moveFirst или Enumerator. prototype. moveNext для объекта типа, отличного от перечислителя.
title: Ожидался объект перечислителя | Документация Майкрософт
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5015
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: dc6e32c1-a6e6-4e12-ac99-e3f65f91c8d7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9fc48ca3e0f17d97af3d538033c2319538afc079
ms.sourcegitcommit: 691d2a47f92f991241fdb132a82c53a537198d50
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/16/2021
ms.locfileid: "103571055"
---
# <a name="enumerator-object-expected"></a>Требуется объект Enumerator
Предпринята попытка вызова метода **Enumerator. prototype. atEnd, перечислителя. prototype. Item, перечислителя. prototype. MoveFirst** или **Enumerator. prototype. MoveNext** для объекта типа, отличного от `Enumerator` . Объект этого типа вызова должен иметь тип `Enumerator` . Ниже приведен пример кода, который нарушает это правило:  
  
```JavaScript  
var o = new Object;  
o.f = Enumerator.prototype.atEnd;  
o.f();  
```  
  
### <a name="to-correct-this-error"></a>Исправление ошибки  
  
- Вызываются только методы **Enumerator. prototype. atEnd**, **перечислитель. prototype. Item**, **Enumerator. prototype. MoveFirst** или **Enumerator. prototype. MoveNext** для объектов типа `Enumerator` . Чтобы определить, является ли объект `Enumerator` объектом, используйте:  
  
    ```js
    if(x instanceof Enumerator)  
    ```  
  
## <a name="see-also"></a>См. также  
 [Объект Enumerator](https://developer.mozilla.org/docs/Archive/Web/JavaScript/Microsoft_Extensions/Enumerator)
