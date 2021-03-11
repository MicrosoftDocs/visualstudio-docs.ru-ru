---
title: Как определить, повреждают ли указатели адрес памяти? | Документация Майкрософт
description: Чтобы определить, не повреждает ли указатель память, можно выполнить поиск повреждения кучи, а также задать точку останова по данным и узнать, как изменяется значение.
ms.custom: SEO-VS-2020, seodec18
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- addresses, pointers corrupting memory address
- memory, corruption
- pointers, corrupting memory addresses
- memory address corruption by pointers
- debugging [C++], memory corruption
- corrupted memory address
ms.assetid: a147c939-4fb1-415c-8410-cf303781e9e8
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: d95e38c6393d6576f2867aad5d1224940f33cebc
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102155204"
---
# <a name="how-can-i-find-out-if-my-pointers-corrupt-a-memory-address"></a>Как определить, повреждают ли указатели адрес памяти?
## <a name="problem-description"></a>Описание проблемы
 Возможно, один из указателей повреждает память по адресу 0x00408000. Как определить, что происходит в этой точке?

## <a name="solution"></a>Решение

#### <a name="check-for-heap-corruption"></a>Проверка целостности кучи

- В большинстве случаев повреждение памяти происходит из-за повреждения кучи. Используйте программу глобальных флагов (gflags.exe) или pageheap.exe. См. [/windows-hardware/drivers/debugger/gflags-and-pageheap](/windows-hardware/drivers/debugger/gflags-and-pageheap).

#### <a name="to-find-where-the-memory-address-is-modified"></a>Поиск места изменения адреса памяти

1. Задайте точку останова данных по адресу 0x00408000. Подробнее см. раздел [Установка точки останова, действующей при изменении данных (только для машинного кода C++)](../debugger/using-breakpoints.md#BKMK_set_a_data_breakpoint_native_cplusplus).

2. При попадании в точку останова используйте окно **Память** для просмотра содержимого памяти начиная с адреса 0x00408000. Дополнительные сведения см. в разделе [Окно "Память"](../debugger/memory-windows.md).

## <a name="see-also"></a>См. также
- [Вопросы и ответы по отладке машинного кода](../debugger/debugging-native-code-faqs.md)
- [Отладка машинного кода](../debugger/debugging-native-code.md)
