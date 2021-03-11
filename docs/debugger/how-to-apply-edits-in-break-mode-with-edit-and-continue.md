---
title: Применение изменений в режиме приостановки выполнения с помощью функции "Изменить и продолжить" | Документация Майкрософт
description: Сведения о том, как с помощью функции "Изменить и продолжить" изменить код в Visual Basic в режиме приостановки выполнения. Существует несколько способов перехода в режим приостановки выполнения.
ms.custom: SEO-VS-2020, seodec18
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.debug.variables.failededit
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Edit and Continue [Visual Basic], applying edits in break mode
- break mode, applying code changes
- Edit and Continue, applying edits in break mode
- editing, break mode
- coding, editing in break mode
- code, editing in break mode
ms.assetid: 1eef7498-6a1f-4fba-8146-510adc6375c9
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: a9074d992c06c1b7d49f59481bee35345c5199f8
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102155046"
---
# <a name="how-to-apply-edits-in-break-mode-with-edit-and-continue-visual-basic"></a>Практическое руководство. Применение изменений в режиме приостановки выполнения с помощью функции "Изменить и продолжить" (Visual Basic)
Можно использовать "Изменить и продолжить" для изменения кода в режиме приостановки и продолжения затем работы без остановки и перезапуска приложения.

Ограничения использования функции "Изменить и продолжить" во время отладки см. в разделе [Поддерживаемые изменения кода (C# и Visual Basic)](../debugger/supported-code-changes-csharp.md).

### <a name="to-edit-code-in-break-mode"></a>Изменение кода в режиме приостановки

1. Войдите в режим приостановки, выполнив одно из следующих действий:

    - установите точку останова в коде, а затем выберите команду **Начать отладку** в меню **Отладка** и ждите, когда приложение попадет на точке останова;

         -или-

    - начните отладку, а затем выберите команду **Прервать все** в меню **Отладка**;

         -или-

    - при возникновении исключения выберите **Разрешить изменение** в **помощнике по исключениям**.

2. Внесите в код все необходимые и поддерживаемые изменения.

     Дополнительные сведения см. в разделе [Поддерживаемые изменения кода (C# и Visual Basic)](../debugger/supported-code-changes-csharp.md).

    > [!NOTE]
    > При попытке недопустимого режимом "Изменить и продолжить" изменения кода, изменения будут подчеркнуты фиолетовой волнистой линией и соответствующая пометка появится в списке задач. Если не отменить недопустимые изменения кода, возможности продолжить выполнение кода не будет.

3. В меню **Отладка** выберите пункт **Продолжить**, чтобы возобновить выполнение.

     Код теперь выполняется с учетом примененных к проекту изменений.

## <a name="see-also"></a>См. также
- [Поддерживаемые изменения кода (C# и Visual Basic)](../debugger/supported-code-changes-csharp.md)
- [Изменить и продолжить (Visual Basic)](../debugger/edit-and-continue-visual-basic.md)
