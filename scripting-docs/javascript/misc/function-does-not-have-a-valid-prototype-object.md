---
description: Вы попытались использовать instanceof, чтобы определить, является ли объект производным от определенного класса функции, но свойство прототипа объекта было переопределено как null или тип внешнего объекта (как недопустимые объекты JavaScript).
title: Функция не имеет допустимого объекта прототипа | Документация Майкрософт
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5023
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: b9e34652-190f-4b57-b253-df2e8c4d09c6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0356ac9ef7c63c77c0cc0dfca623ff24d3de24af
ms.sourcegitcommit: 691d2a47f92f991241fdb132a82c53a537198d50
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/16/2021
ms.locfileid: "103571419"
---
# <a name="function-does-not-have-a-valid-prototype-object"></a>Функция не имеет допустимого объекта прототипа
Вы попытались использовать **instanceof** , чтобы определить, является ли объект производным от определенного класса функции, но свойство объекта было переопределено `prototype` как либо либо `null` тип внешнего объекта (как недопустимые [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] объекты). Внешним объектом может быть объект из объектной модели узла (например, документ или объект окна Internet Explorer) или внешний COM-объект.  
  
### <a name="to-correct-this-error"></a>Исправление ошибки  
  
- Убедитесь, что `prototype` свойство функции ссылается на допустимый [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] объект.  
  
## <a name="see-also"></a>См. также  
 [Объект функции](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Function)   
 [Свойство prototype (Object)](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Object)
