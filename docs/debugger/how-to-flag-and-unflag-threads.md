---
title: Установка и снятие отметки для потоков | Документация Майкрософт
description: Сведения о том, как устанавливать и снимать отметки для потоков в Visual Studio. Вы можете установить или снять отметку для одного, нескольких или всех потоков. Также вы можете помечать только собственный код или код, связанный с модулем.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- treads, switching [debugging]
ms.assetid: 952d579d-6911-413e-b3e5-54e7e797e70c
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: d5f31bb73b4a22a11235e471dfa1fa99545e422e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99877607"
---
# <a name="how-to-flag-and-unflag-threads-c-visual-basic-c"></a>Практическое руководство. Установка и снятие отметки для потока (C#, Visual Basic, C++)

Поток, которому требуется уделить особое внимание, можно пометить, поставив рядом с ним значок в окне **Потоки**, **Параллельные стеки** (представление потока), **Контроль параллельных данных** или **Потоки GPU**. С помощью этого значка можно будет отличать помеченные потоки от остальных.

Отмеченные потоки также имеют специальную обработку в списке **Поток** на панели инструментов **Место отладки** и в других многопоточных окнах. В списке **Поток** или в других окнах можно отобразить все или только отмеченные потоки.

### <a name="to-flag-or-unflag-a-thread"></a>Пометка и снятие пометки потока

- В окне **Потоки** или **Контроль параллельных данных** перейдите к нужному потоку и щелкните значок флага, чтобы выделить или снять этот флаг.
- В окне **Параллельные стеки** щелкните правой кнопкой мыши на поток или группу потоков и выберите пункт **Установка отметки / \<thread>** или **Снятие отметки / \<thread>** .

### <a name="to-unflag-all-threads"></a>Сброс флагов у всех потоков

- В окне **Потоки** щелкните правой кнопкой мыши любой поток и выберите **Снять пометку со всех потоков**.
- В окне **Контроль параллельных данных** выберите все помеченные потоки, щелкните правой кнопкой мыши и выберите **Снять пометку**.

### <a name="to-display-only-flagged-threads"></a>Отображение только помеченных потоков

- Выберите **Показать только помеченные потоки** в одном из окон многопоточной отладки.

### <a name="to-flag-just-my-code"></a>Пометка только собственного кода ("Только мой код")

1. В панели инструментов, находящейся в верхней части окна **Потоки**, щелкните значок флага.

2. В раскрывающемся списке выберите **Пометить только мой код**.

### <a name="to-flag-threads-that-are-associated-with-selected-modules"></a>Пометка потоков, связанных с выбранными модулями

1. В панели инструментов окна **Потоки** щелкните значок флага.

2. В раскрывающемся списке выберите **Пометить настраиваемые выбранные модули**.

3. В диалоговом окне **Выбор модулей** выберите нужные модули.

4. В поле **Поиск** введите строку для поиска конкретных модулей (необязательно).

5. Нажмите кнопку **ОК**.

## <a name="see-also"></a>См. также
- [Отладка многопоточных приложений](../debugger/debug-multithreaded-applications-in-visual-studio.md)
- [Начало отладки многопоточных приложений](../debugger/get-started-debugging-multithreaded-apps.md)
- [Пошаговое руководство: Отладка многопоточных приложений с помощью окна "Потоки"](../debugger/how-to-use-the-threads-window.md)