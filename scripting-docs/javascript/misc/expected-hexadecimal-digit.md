---
description: Вы создали неверную escape-последовательность Юникода.
title: Ожидалась шестнадцатеричная цифра | Документация Майкрософт
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT1023
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 67a86df7-49f9-43cb-99c6-99b1a427827a
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 107ce2dd4f9a65a0a04b8e2ec773367ffae4ce81
ms.sourcegitcommit: 691d2a47f92f991241fdb132a82c53a537198d50
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/16/2021
ms.locfileid: "103570431"
---
# <a name="expected-hexadecimal-digit"></a>Ожидалась шестнадцатеричная цифра
Вы создали неверную escape-последовательность Юникода. Escape-последовательности Юникода начинаются с \u, за которым следуют ровно четыре шестнадцатеричных цифры (больше и не меньше). Шестнадцатеричные цифры в Юникоде могут содержать только цифры 0-9, прописные буквы A – F, а строчные буквы a – f. В следующем примере показана правильно сформированная escape-последовательность в Юникоде.  
  
```JavaScript  
z = "\u1A5F";  
```  
  
### <a name="to-correct-this-error"></a>Исправление ошибки  
  
- Убедитесь, что шестнадцатеричные цифры в Юникоде начинаются с \u, содержат только цифры 0-9, прописные буквы A – F, строчные буквы a-f; и группируются в четыре цифры.  
  
    > [!NOTE]
    > Если вы хотите использовать литеральный текст \u в строке, используйте две обратные косые черты ( \\ \u) — один для экранирования первой обратной косой черты.  
  
## <a name="see-also"></a>См. также  
 [Типы данных](https://developer.mozilla.org/docs/Web/JavaScript/Data_structures)
