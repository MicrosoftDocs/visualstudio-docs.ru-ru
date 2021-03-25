---
title: Реализация поставщика порта | Документация Майкрософт
description: Сведения о реализации поставщика порта, который необходим при отладке на компьютере, отличном от DCOM, или при необходимости поддержки нового устройства.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], implementing port suppliers
- port suppliers, implementing
ms.assetid: 6b8579df-58df-4c7f-8112-6015993e8765
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 98cc83ac9640241f0f97dc6e4adaacf8f90599b7
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105059916"
---
# <a name="implement-a-port-supplier"></a>Реализация поставщика порта
Поставщик порта предоставляет порты по запросу к диспетчеру отладки сеансов (SDM). Поставщик порта должен быть реализован при отладке на компьютере, отличном от DCOM, или при необходимости поддержки нового устройства. Например, чтобы обеспечить отладку на мобильном телефоне, можно настроить поставщика порта, который предоставляет порты, которые подключаются к сотовому телефону (возможно, с помощью ИНФРАКРАСного соединения или подключения к ячейке) и перечисляют процессы и программы, запущенные на телефоне.

 Для отладки программ на компьютерах под управлением Windows (включая удаленную отладку) Visual Studio предоставляет поставщики портов для процессов машинного кода и среды CLR, поэтому в таких случаях нет необходимости настраивать собственный поставщик порта.

## <a name="in-this-section"></a>Содержание раздела
 [Реализация и регистрация поставщика портов](../../extensibility/debugger/implementing-and-registering-a-port-supplier.md) Описывает взаимодействие SDM с поставщиком порта и его портами.

 [Требуемые интерфейсы поставщика портов](../../extensibility/debugger/required-port-supplier-interfaces.md) Документирует интерфейсы, которые необходимо реализовать для получения поставщика порта.

## <a name="related-sections"></a>Связанные разделы
 [Основные понятия отладчика](../../extensibility/debugger/debugger-concepts.md). Описываются основные понятия архитектуры отладки.

## <a name="see-also"></a>См. также
 [Расширяемость отладчика Visual Studio](../../extensibility/debugger/visual-studio-debugger-extensibility.md)
