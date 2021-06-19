---
title: Проверка системы в ходе разработки
description: Узнайте, как Visual Studio помогает обеспечить соответствие программного обеспечения требованиям пользователей и архитектуре системы.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- dependency diagrams
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: ae85c7f98aab3e852a810976cc1cecbd83b65307
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2021
ms.locfileid: "112388377"
---
# <a name="validate-your-system-during-development"></a>Проверка системы в ходе разработки

Visual Studio поможет обеспечить соответствие программного обеспечения требованиям пользователей и архитектуры системы.

Чтобы узнать, какие версии Visual Studio поддерживают каждую функцию, см. раздел [Version support for architecture and modeling tools](../modeling/analyze-and-model-your-architecture.md#VersionSupport).

## <a name="key-tasks"></a>Ключевые задачи

Для проверки программного обеспечения выполните следующие действия.

|**Задачи**|**Связанные разделы**|
|-|-|
|**Убедитесь, что программное обеспечение соответствует требованиям пользователей**:<br /><br />Используйте требования и модели архитектуры для организации тестов системы и ее компонентов. Такой подход позволяет обеспечить проверку требований, важных для пользователей и других заинтересованных лиц, и помогает быстро обновлять тесты при изменении требований.|- [Разработка тестов из модели](../modeling/develop-tests-from-a-model.md)|
|**Убедитесь, что программное обеспечение соответствует предполагаемой структуре системы:**<br /><br />Схемы зависимостей описывают предполагаемые зависимости между компонентами приложения. В процессе разработки можно следить за тем, чтобы фактические зависимости в коде соответствовали предполагаемой структуре.|- [Создание схем зависимостей на основе кода](../modeling/create-layer-diagrams-from-your-code.md)<br />- [Проверка кода по схемам зависимостей](../modeling/validate-code-with-layer-diagrams.md)|

## <a name="external-resources"></a>Внешние ресурсы

|**Категория**|**Ссылки**|
|-|-|
|**Видео**|![Ссылка на видео ](../data-tools/media/playvideo.gif) [Channel 9: Дуг семь: понимание кода и проектирование систем с помощью Visual Studio 2010](https://channel9.msdn.com/shows/VS2010Launch/Doug-Seven-Code-Understanding-and-Systems-Design-with-Visual-Studio-2010)<br /><br /> ![Ссылка на видео ](../data-tools/media/playvideo.gif) - [канал 9: создание архитектуры приложения](https://channel9.msdn.com/blogs/clinted/uml-with-vs-2010-part-5-architecting-an-application))|
|**Форумы**|- [Средства моделирования и визуализации Visual Studio](https://social.msdn.microsoft.com/Forums/en-US/home?forum=vsarch)<br />- [Расширяемость Visual Studio](https://social.msdn.microsoft.com/Forums/vstudio/home?forum=vsx)|

## <a name="see-also"></a>См. также

- [Моделирование требований пользователей](../modeling/model-user-requirements.md)
- [Анализ и моделирование архитектуры](../modeling/analyze-and-model-your-architecture.md)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]
