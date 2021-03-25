---
title: Пакет отладки | Документация Майкрософт
description: Узнайте, как пакет отладки выполняется в оболочке Visual Studio и обрабатывает пользовательский интерфейс, используя интерфейсы отладки и взаимодействующие с диспетчером отладки сеанса.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], packages
ms.assetid: 99947fd4-fb87-4c69-b26c-65634e17d285
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 90c4c82895f7a30d4df9126a280c6c9ffa7ffa76
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105067911"
---
# <a name="debug-package"></a>Пакет отладки
Пакет отладки выполняется в оболочке Visual Studio и обрабатывает весь пользовательский интерфейс. Он использует интерфейсы отладки Visual Studio и взаимодействует с диспетчером отладки сеансов (SDM).

 Прервать события, отправленные через модель SDM, переключит отладчик из режима выполнения в режим прерывания и измените фокус на программу, в которой произошло прерывание. Пакет отладки отслеживает кадр стека и поток из информации, переданной в нее событиями.

 Пакет отладки не имеет зависимостей среды языка или времени выполнения. Нет необходимости реализовывать или изменять пакет отладки.

 Пакет отладки реализуется *vsdebug.dll*.

## <a name="see-also"></a>См. также
- [Диспетчер отладки сеансов](../../extensibility/debugger/session-debug-manager.md)
- [Кадры стека](../../extensibility/debugger/stack-frames.md)
- [Потоки](../../extensibility/debugger/threads.md)
- [Компоненты отладчика](../../extensibility/debugger/debugger-components.md)
