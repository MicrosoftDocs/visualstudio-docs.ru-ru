---
description: Предпринята попытка кодирования строки в виде URI, но она содержала недопустимые символы.
title: URI для кодирования содержит недопустимый символ | Документация Майкрософт
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5024
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: a3f0fdbb-8d4b-41ae-a396-43dfc9483760
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 73ed9a814c5d608df1a9686c2b61166d664115f7
ms.sourcegitcommit: 691d2a47f92f991241fdb132a82c53a537198d50
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/16/2021
ms.locfileid: "103570665"
---
# <a name="the-uri-to-be-encoded-contains-an-invalid-character"></a>Кодируемый URI содержит недопустимый символ
Предпринята попытка кодирования строки в виде универсального кода ресурса (URI), но она содержала недопустимые символы. Хотя большинство символов допустимо в строках для преобразования в URI, некоторые последовательности символов Юникода являются недопустимыми.  
  
### <a name="to-correct-this-error"></a>Исправление ошибки  
  
- Убедитесь, что строка, которая должна быть закодирована, содержит только допустимые последовательности Юникода. Полный URI состоит из последовательности компонентов и разделителей. Имена в угловых скобках представляют компоненты, а ":", "/", ";" и "?" являются зарезервированными символами, используемыми в качестве разделителей. Общая форма:  
  
    ```JavaScript  
    <Scheme>:<first>/<second>;<third>?<fourth>  
    ```  
  
## <a name="see-also"></a>См. также  
 [Функция encodeURI](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/encodeuri)   
 [Функция encodeURIComponent](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/encodeuricomponent)
