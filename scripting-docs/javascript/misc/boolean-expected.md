---
description: Предпринята попытка вызвать метод Boolean. prototype. toString или Boolean. prototype. valueOf для объекта типа, отличного от Boolean.
title: Ожидалось логическое значение | Документация Майкрософт
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5010
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 35d71b7f-53fd-44c4-a7c7-b1550c65cfd4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1ceaddc9341d67ac60326fa7121c32655ab6a3f6
ms.sourcegitcommit: 691d2a47f92f991241fdb132a82c53a537198d50
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/16/2021
ms.locfileid: "103571445"
---
# <a name="boolean-expected"></a>Требуется логическое значение
Предпринята попытка вызвать метод **Boolean. prototype. ToString** или **Boolean. prototype. valueOf** для объекта типа, отличного от `Boolean` . Объект этого типа вызова должен иметь тип `Boolean` . Например:

```JavaScript
var o = new Object;
o.f = Boolean.prototype.toString;
o.f();
```

## <a name="to-correct-this-error"></a>Исправление ошибки

- Вызываются только методы **Boolean. prototype. ToString** или **Boolean. prototype. valueOf** для объектов типа **Boolean.**

## <a name="see-also"></a>См. также

- [Объект Boolean](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Boolean)
- [Типы данных](https://developer.mozilla.org/docs/Web/JavaScript/Data_structures)
- [Управление выполнением программы](https://developer.mozilla.org/docs/Web/JavaScript/Guide/Control_flow_and_error_handling)
- [Копирование, передача и сравнение данных](https://developer.mozilla.org/docs/Web/JavaScript/Guide/Functions)
