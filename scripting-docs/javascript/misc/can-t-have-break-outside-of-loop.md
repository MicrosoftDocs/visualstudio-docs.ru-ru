---
description: Предпринята попытка использовать ключевое слово Break вне цикла.
title: "\"Break\" не может находиться вне цикла | Документация Майкрософт"
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT1019
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 11d02172-2a78-4705-a730-d21111db5f42
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d761a1cff89f650e5fc465b6a6aef2713aafb765
ms.sourcegitcommit: 691d2a47f92f991241fdb132a82c53a537198d50
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/16/2021
ms.locfileid: "103570652"
---
# <a name="cant-have-break-outside-of-loop"></a>break не может располагаться вне цикла
Предпринята попытка использовать ключевое слово **break** вне цикла. Ключевое слово **break** используется для завершения цикла или `switch` оператора. Он должен быть внедрен в тело цикла или `switch` оператора. Однако **Метка** может следовать за ключевым словом break.  
  
```js
break labelname;  
```  
  
 При использовании вложенных циклов или инструкций требуется только форма с метками с **меткой,** `switch` и необходимо разорвать цикл, который не является самым внутренним.  
  
### <a name="to-correct-this-error"></a>Исправление ошибки  
  
- Убедитесь, что ключевое слово **break** отображается внутри внешнего цикла или оператора switch.  
  
## <a name="see-also"></a>См. также  
 [Оператор break](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Statements/break)   
 [Управление ходом выполнения программы](https://developer.mozilla.org/docs/Web/JavaScript/Guide/Control_flow_and_error_handling)   
 [Устранение неполадок в скриптах](https://developer.mozilla.org/docs/Learn/JavaScript/First_steps/What_went_wrong)
