---
title: Пакет отладки | Документация Майкрософт
description: Узнайте, как пакет отладки выполняется в оболочке Visual Studio и обрабатывает пользовательский интерфейс, используя интерфейсы отладки и взаимодействующие с диспетчером отладки сеанса.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- debugging [Debugging SDK], packages
ms.assetid: 99947fd4-fb87-4c69-b26c-65634e17d285
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 8be920ae352067a6e77593ca0a922474d68851d9
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/25/2021
ms.locfileid: "112905674"
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
