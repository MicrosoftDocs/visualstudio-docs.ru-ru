---
title: Расширение схем зависимостей
description: Узнайте, как написать код для создания и обновления схем зависимостей, а также как проверить структуру программного кода на соответствие диаграммам зависимостей в Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- dependency diagrams, creating extensions
- layer models
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: c2ed8700cfb18aacf41464bfdfacaedac557bb00
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2021
ms.locfileid: "112388910"
---
# <a name="extend-dependency-diagrams"></a>Расширение схем зависимостей

Можно написать код для создания и обновления схем зависимостей, а также для проверки структуры кода программы на соответствие диаграммам зависимостей в Visual Studio. Вы можете добавить команды, которые отображаются в контекстном меню схем, настроить жесты перетаскивания, а также получить доступ к модели слоев из текстовых шаблонов. Вы можете упаковать эти расширения в расширение Visual Studio Integration Extension (VSIX) и предоставить их другим пользователям Visual Studio.

## <a name="requirements"></a>Требования

На компьютере, где планируется разрабатывать расширения слоев, должны быть установлены следующие компоненты:

- Visual Studio

- [SDK для Visual Studio](../extensibility/visual-studio-sdk.md)

- Пакет SDK моделирования для Visual Studio

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

На компьютере, на котором нужно запустить расширения слоев, должен быть установлен подходящий выпуск Visual Studio. Чтобы узнать, какие выпуски поддерживаются на схемах зависимостей в Visual Studio, см. раздел [Поддержка архитектуры и средств моделирования в выпуске](../modeling/analyze-and-model-your-architecture.md#VersionSupport).

## <a name="see-also"></a>См. также

- [Схемы зависимостей: справочные материалы](../modeling/layer-diagrams-reference.md)
- [Схемы зависимостей: рекомендации](../modeling/layer-diagrams-guidelines.md)
- [Создание схем зависимостей на основе кода](../modeling/create-layer-diagrams-from-your-code.md)
- [Проверка кода по схемам зависимостей](../modeling/validate-code-with-layer-diagrams.md)
