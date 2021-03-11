---
title: Использование окон отладчика при отладке активной программы | Документация Майкрософт
description: При отладке программы, которая должна оставаться в активном режиме, используйте удаленную отладку, чтобы не помещать программу в фоновый режим.
ms.custom: SEO-VS-2020, seodec18
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.debug.background
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- foreground program debugging
- remote debugging, debugging foreground programs
- debugging [Visual Studio], while observing foreground programs
- focus, debugging while observing foreground programs
- debugging [Visual Studio], foreground programs
ms.assetid: 9e67a308-1c81-42ab-966b-7fc3c1d2bf7a
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 03a143ee2d04227171895bf2b14dff92545b9952
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102155098"
---
# <a name="how-can-i-use-debugger-windows-while-debugging-a-foreground-program"></a>Как использовать окна отладчика при отладке активной программы?
## <a name="problem-description"></a>Описание проблемы
 Выполняются попытки отладить проблему отображения на экране. Для этого приходится держать программу активной, а это означает, что отсутствует доступ к окнам отладчика. Что можно сделать?

## <a name="solution"></a>Решение
 Если есть второй компьютер, используйте удаленную отладку. С двумя компьютерами можно посмотреть отображение на экране на удаленном компьютере, работая в отладчике на основном хосте. Дополнительные сведения об удаленной отладке см. в разделе [Удаленная отладка](../debugger/remote-debugging.md).

## <a name="see-also"></a>См. также
- [Вопросы и ответы по отладке машинного кода](../debugger/debugging-native-code-faqs.md)
- [Отладка машинного кода](../debugger/debugging-native-code.md)
