---
title: не удается подключиться к компьютеру &lt;имя&gt;. Не удается найти компьютер в сети. | Документы Майкрософт
description: 'Такое поведение возникает при соблюдении одного из следующих условий: (1) Подключение к удаленному компьютеру было прервано. (2) Учетная запись пользователя на удаленном компьютере отключена. (3) Истек срок действия пароля на удаленном компьютере.'
ms.date: 11/04/2016
ms.topic: error-reference
f1_keywords:
- vs.debug.remote.dcom_disabled
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- DCOM, unable to connect error
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 5e0d83f043e020ad3c65ac0f986ec174fac95585
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102146435"
---
# <a name="error-unable-to-connect-to-the-machine-ltnamegt-the-machine-cannot-be-found-on-the-network"></a>Ошибка: не удается подключиться к компьютеру &lt;имя&gt;. Не удается найти компьютер в сети.
Такая ошибка возникает, если выполняется одно из следующих условий:

- Подключение к удаленному компьютеру разорвано.

- Учетная запись пользователя на удаленном компьютере отключена.

- Истек срок действия пароля на удаленном компьютере.

### <a name="to-resolve-this-behavior"></a>Устранение ошибки

- Убедитесь, что удаленный и локальный компьютеры находятся в одной сети. Для этого попытайтесь обратиться к удаленному компьютеру с помощью Проводника Microsoft Windows.

     — и —

- Убедитесь в том, что учетная запись пользователя, используемая для подключения к удаленному компьютеру, активна.

     — и —

- Убедитесь в том, что пароль для подключения к удаленному компьютеру правильный, и срок его действия не истек.

## <a name="see-also"></a>См. также
- [Remote Debugging](../debugger/remote-debugging.md)
- [Параметры отладчика и подготовка](../debugger/debugger-settings-and-preparation.md)
