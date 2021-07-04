---
title: Переключение на другой поток при отладке
description: Сведения о различных способах переключения на другой поток при отладке многопоточного приложения в Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 04/27/2017
ms.topic: how-to
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- threads, switching [debugging]
ms.assetid: 5cd76c52-76fa-4fcc-b37e-e9f0ecac0e9e
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: a0a68047c5c9e772fc978c56f2cd70dc9454ca57
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2021
ms.locfileid: "112384698"
---
# <a name="how-to-switch-to-another-thread-while-debugging-in-visual-studio-c-visual-basic-c"></a>Практическое руководство. Переключение на другой поток при отладке в Visual Studio (C#, Visual Basic, C++)
При отладке многопоточных приложений существует несколько способов переключения с потока, над которым ведется работа, на другой поток.

> [!NOTE]
> Если вы хотите управлять порядком, в котором выполняются потоки, вам нужно [замораживать и размораживать потоки](../debugger/get-started-debugging-multithreaded-apps.md).

Когда вы исследуете потоки в редакторе кода и различных окнах многопоточной отладки, желтая стрелка указывает текущий поток. Зеленая стрелка с загнутым наконечником указывает, что поток, не являющийся текущим, имеет текущий контекст отладчика.

### <a name="to-switch-to-any-thread-that-appears"></a>Переключение на любой отображаемый поток

- В окне **Потоки** или **Контроль параллельных данных** дважды щелкните нужный поток.

### <a name="to-switch-to-a-thread-in-a-source-window"></a>Переключение на поток в окне исходного кода

- В поле слева щелкните правой кнопкой мыши значок метки потока ![Метка потока](../debugger/media/dbg-thread-marker.png "ThreadMarker"), выберите команду **Переключиться в**, а затем щелкните имя потока, в который хотите переключиться. В контекстном меню отображаются только потоки, работающие с этой конкретной точкой кода.

     Если никакие метки потока не отображаются, щелкните правой кнопкой мыши в окне **Потоки** и проверьте, установлен ли флажок **Показать потоки в исходном коде**.

### <a name="to-switch-to-a-thread-in-the-debug-location-toolbar"></a>Переключение на поток в панели инструментов "Место отладки"

1. В панели инструментов **Место отладки** щелкните список **Поток**.

2. В раскрывающемся списке выберите поток, на который необходимо переключиться.

## <a name="see-also"></a>См. также
- [Отладка многопоточных приложений](../debugger/debug-multithreaded-applications-in-visual-studio.md)
