---
title: Концепции отладчика | Документация Майкрософт
description: Сведения об архитектурных концепциях, используемых при проектировании пакета отладки Visual Studio для упрощения создания этого пакета.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK]
ms.assetid: 2d371d38-f1a0-4a9a-8ea3-100e8c0149b7
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 94249a6ff7c50fb054a3fc460708a8e36181bff8
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105094891"
---
# <a name="debugger-concepts"></a>Основные понятия отладчика
Для создания пакета отладки Visual Studio необходимо ознакомиться с концепциями архитектуры, используемыми при проектировании пакета.

## <a name="in-this-section"></a>Содержание раздела
 [Сеанс отладки](../../extensibility/debugger/debug-session.md) Объясняет роль сеанса в архитектуре отладки.

 [Серверы](../../extensibility/debugger/servers-visual-studio-sdk.md) Определяет, что представляет собой сервер в контексте архитектуры отладки, как абстрактные, так и физические термины.

 [Поставщики портов](../../extensibility/debugger/port-suppliers.md) Определяет, что представляет собой поставщик порта в контексте архитектуры отладки.

 [Порты](../../extensibility/debugger/ports.md) Определяет, что представляет собой порт в контексте архитектуры отладки.

 [Процессы](../../extensibility/debugger/processes.md) Определяет, что такое процесс в контексте архитектуры отладки.

 [Узлы программы](../../extensibility/debugger/program-nodes.md) Определяет узел программы с точки зрения архитектуры отладки, включая то, как он может идентифицировать себя и процесс, в котором он выполняется.

 [Программы](../../extensibility/debugger/programs.md) Определяет программу с точки зрения архитектуры отладки.

 [Потоки](../../extensibility/debugger/threads.md) Определяет характеристики потоков с точки зрения архитектуры отладки.

 [Кадры стека](../../extensibility/debugger/stack-frames.md) Определяет кадр стека с точки зрения архитектуры отладки. Кадр стека — это абстракция стека, предоставляющего контекст выполнения потока.

 [Модули](../../extensibility/debugger/modules.md) Определяет модуль с точки зрения архитектуры отладки в качестве физического контейнера кода, например исполняемого файла или библиотеки DLL.

 [Точки останова](../../extensibility/debugger/breakpoints-visual-studio-sdk.md) Определяет три типа точек останова: ожидание, привязка и ошибка — с точки зрения архитектуры отладки.

## <a name="related-sections"></a>Связанные разделы
 [Контексты отладчика](../../extensibility/debugger/debugger-contexts.md) Объясняет, как подсистема отладки (DE) работает одновременно в рамках кода, документации и контекстов оценки выражений. Для каждого из трех контекстов описывается относящееся к нему расположение, позиция или вычисление.

 [Компоненты отладчика](../../extensibility/debugger/debugger-components.md) Содержит общие сведения о компонентах отладки Visual Studio, включая модуль отладки (DE), средство оценки выражений (EE) и обработчик символов (SH).

 [Задачи отладки](../../extensibility/debugger/debugging-tasks.md) Содержит ссылки на различные задачи отладки, такие как запуск программы и вычисление выражений.
