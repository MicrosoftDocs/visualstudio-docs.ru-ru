---
title: Чтение моделей и схем в других выпусках Visual Studio
description: Сведения о чтении моделей и схем в Visual Studio, а также о поведении только для чтения при использовании версии Visual Studio, которая не поддерживает создание модели.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- models, versions of Visual Studio
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 95fbf6451a3f07581ff2bdb098428f41904d4276
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2021
ms.locfileid: "112389908"
---
# <a name="read-models-and-diagrams-in-other-visual-studio-editions"></a>Чтение моделей и схем в других выпусках Visual Studio

При открытии модели в версии Visual Studio, которая не поддерживает создание моделей, она открывается в режиме "только для чтения". В этом режиме можно изменить структуру схемы, но невозможно изменить модель.

Сведения о том, какие версии Visual Studio поддерживают создание моделей, см. в разделе [Поддержка версий для инструментов архитектуры и моделирования](../modeling/analyze-and-model-your-architecture.md#VersionSupport).

## <a name="obtaining-access-to-a-model-and-diagrams"></a>Получение доступа к модели и схемам

Для чтения схемы зависимостей необходимо сначала использовать Visual Studio, чтобы открыть проект моделирования, а затем открыть в нем диаграмму.

По этой причине, если необходимо прочитать схему зависимостей, необходимо также иметь доступ к проекту моделирования, в котором она была создана. Это можно сделать, обратившись к проекту из системы управления версиями или получив копию файлов проекта.

> [!NOTE]
> Это не относится к картам кода и схемам классов .NET, созданным из кода. Эти схемы можно просматривать независимо от проекта моделирования.

Для чтения схемы зависимостей требуется минимальный набор необходимых файлов.

- Два файла схемы для диаграммы, которые необходимо прочитать, например **мидиаграм. classdiagram и мидиаграм. classdiagram. Layout**.

    > [!NOTE]
    > Для схем зависимостей необходимо также иметь файл с именем _мидиаграм_**. LAYERDIAGRAM. подавляютй**.

- Файл проекта моделирования (**MyModel. modelproj**)

- Файл корневой модели (**моделдефинитион\мимодел.УМЛ**)

- Файлы пакета для любого пакета, на который ссылается схема (**моделдефинитион\мипаккаже.УМЛ**)

## <a name="changes-that-you-can-make-in-read-only-mode"></a>Изменения, которые можно внести в режиме только для чтения

Если открыть модель и ее схемы в версии Visual Studio, которая не поддерживает создание модели, то модель нельзя будет изменять. То есть нельзя изменять элементы и отношения, которые отображаются на схемах или в обозревателе моделей. Однако можно внести некоторые изменения в структуру схем:

- изменить расположение фигур и соединителей на схеме;

- развернуть или свернуть фигуры.

Эти изменения можно сохранить. Если вы хотите сделать изменения видимыми для других пользователей, необходимо по крайней мере отправить обновленные файлы **макета** .

## <a name="see-also"></a>См. также

- [Схемы зависимостей: справочные материалы](../modeling/layer-diagrams-reference.md)
- [Создание моделей для приложения](../modeling/create-models-for-your-app.md)
