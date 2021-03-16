---
description: Предпринята попытка использовать инструкцию по умолчанию более одного раза в операторе switch.
title: "\"default\" может использоваться в операторе \"Switch\" только один раз | Документация Майкрософт"
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT1027
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: a94100f4-6ee5-4759-b635-9d309e47111e
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 346643f1ecaae6ab59c0fa265ffe5ff55fa66dc9
ms.sourcegitcommit: 691d2a47f92f991241fdb132a82c53a537198d50
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/16/2021
ms.locfileid: "103571068"
---
# <a name="default-can-only-appear-once-in-a-switch-statement"></a>default может использоваться в операторе switch только один раз
Предпринята попытка использовать инструкцию **по умолчанию** более одного раза в операторе switch. Регистр по умолчанию всегда является последним оператором case в операторе switch (он является переделами).  
  
### <a name="to-correct-this-error"></a>Исправление ошибки  
  
- Удалите все лишние операторы Case **по умолчанию** из `switch` инструкции (используйте не более одного оператора case по умолчанию в операторе switch).  
  
## <a name="see-also"></a>См. также  
 [Оператор switch](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Statements/switch)   
 [Управление ходом выполнения программы](https://developer.mozilla.org/docs/Web/JavaScript/Guide/Control_flow_and_error_handling)   
 [Зарезервированные слова языка JavaScript](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Lexical_grammar)
