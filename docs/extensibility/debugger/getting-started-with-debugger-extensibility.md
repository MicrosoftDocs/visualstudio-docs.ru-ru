---
title: начало работы с расширяемостью отладчика | Документация Майкрософт
description: Приступая к созданию и настройке компонентов отладчика, используемых для отладки программ в среде Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- getting started, Debugging SDK
- debugging [Debugging SDK], getting started
- Debugging SDK, getting started
ms.assetid: d6ce6f43-1409-4bf7-93cd-f3464ca23504
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 20591adffbfdfd21d1ff1a77eaade39c165b9c51
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105059981"
---
# <a name="get-started-with-debugger-extensibility"></a>Приступая к работе с расширяемостью отладчика
[!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]Предоставляет сведения, необходимые для создания и настройки компонентов отладчика, используемых для отладки программ в [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] среде.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] в отладке добавлены улучшения, полученные в результате расширенного тестирования удобства использования, выполненного на предыдущих [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] отладчиках. Можно использовать [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] отладку для пошагового выполнения многоязыкового приложения. также можно реализовать Оперативное редактирование переменных во время отладки приложений и решений на разных языках.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] отладка выполняется вне процесса с отлаживаемой программой и, таким образом, менее агрессивна в пространстве процесса приложения. Следовательно, проще писать компоненты, взаимодействующие с отладчиком, не влияя на программу отладки.

 Для лучшего использования необходимо [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] ознакомиться со следующими элементами:

- [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Интегрированная среда разработки (IDE)

- Язык программирования C++

- ATL COM

## <a name="in-this-section"></a>Содержание раздела
 [Стратегия расширения отладчика](../../extensibility/debugger/roadmap-for-extending-the-debugger.md) Описывает процесс реализации отладки в продукте в зависимости от компилятора и его выходных данных.

 [Компоненты отладчика](../../extensibility/debugger/debugger-components.md) Содержит общие сведения о [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] компонентах отладки, включая модуль отладки (de), средство оценки выражений (EE) и обработчик символов (SH).

 [Основные понятия отладчика](../../extensibility/debugger/debugger-concepts.md). Описываются основные понятия архитектуры отладки.

 [Контексты отладчика](../../extensibility/debugger/debugger-contexts.md) Объясняет, как подсистема отладки (DE) работает одновременно в рамках кода, документации и контекстов оценки выражений. Для каждого из трех контекстов описывается относящееся к нему расположение, позиция или вычисление.

 [Задачи отладки](../../extensibility/debugger/debugging-tasks.md) Содержит ссылки на различные задачи отладки, такие как запуск программы и вычисление выражений.
