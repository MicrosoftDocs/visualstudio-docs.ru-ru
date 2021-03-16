---
description: Предпринята попытка создать переменную, которая будет использоваться с инструкциями условной компиляции с помощью @set инструкции, но не поместит знак @ перед именем переменной.
title: Ожидался символ "@" | Документация Майкрософт
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT1032
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 82ff8b74-1710-4358-9a26-dc92ab29c53b
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e7aa02ed1e436c92014d44e57f2c71ff7db5f99b
ms.sourcegitcommit: 691d2a47f92f991241fdb132a82c53a537198d50
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/16/2021
ms.locfileid: "103570626"
---
# <a name="expected-"></a>Ожидался "\@"
Предпринята попытка создать переменную, которая будет использоваться с инструкциями условной компиляции с помощью `@set` инструкции, но не поместит знак " **@** " перед именем переменной.  
  
### <a name="to-correct-this-error"></a>Исправление ошибки  
  
- Добавьте знак at " **@** " непосредственно перед именем переменной. Пример:  
  
    ```JavaScript  
    @set @myvar = 1  
    ```  
  
## <a name="see-also"></a>См. также  
 [@set Баланс](https://developer.mozilla.org/docs/Archive/Web/JavaScript/Microsoft_Extensions/at-set)   
 [Условная компиляция](/previous-versions/windows/internet-explorer/ie-developer/scripting-articles/121hztk3(v=vs.84))   
 [Переменные условной компиляции](/previous-versions/windows/internet-explorer/ie-developer/scripting-articles/s59bkzce(v=vs.84))
