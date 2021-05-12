---
title: Знакомство с Live Unit Testing
description: Сведения о преимуществах функции Live Unit Testing и ее использовании при модульном тестировании проектов.
ms.date: 09/11/2017
ms.topic: conceptual
helpviewer_keywords:
- Live Unit Testing
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: 2c4da809455a859479d0421bffaa1b257a18c4b5
ms.sourcegitcommit: d4887ef2ca97c55e2dad9f179eec2c9631d91c95
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/06/2021
ms.locfileid: "108798522"
---
# <a name="live-unit-testing-overview"></a>Обзор Live Unit Testing

Live Unit Testing выполняет модульные тесты автоматически в реальном времени по мере внесения изменений в код. Это позволяет более уверенно выполнять рефакторинг и изменять код. Live Unit Testing автоматически выполняет все соответствующие тесты в процессе редактирования кода для проверки того, не приведут ли изменения к регрессии.

Live Unit Testing сообщает о том, достаточно ли полно модульные тесты охватывают код. Эта функция наглядно демонстрирует охват кода в реальном времени. Вы можете сразу понять, какое число тестов охватывают каждую строку кода и какие строки не охвачены модульными тестами.

При наличии решения, включающего в себя один или несколько проектов модульных тестов, вы можете включить Live Unit Testing, выбрав в меню Visual Studio верхнего уровня пункты **Тест** > **Live Unit Testing** > **Запуск**.

> [!NOTE]
> Функция Live Unit Testing доступна только в выпуске Visual Studio Enterprise поддерживается только в .NET.

Дополнительные сведения о Live Unit Testing:

- Воспользуйтесь вводным руководством [Начало работы с Live Unit Testing](live-unit-testing-start.md).

- Подробную документацию см. здесь: [Использование Live Unit Testing с Visual Studio Enterprise Edition](live-unit-testing.md).

- Ознакомьтесь с [вопросами и ответами о Live Unit Testing](live-unit-testing-faq.yml), чтобы узнать о новых возможностях Live Unit Testing, а также получить советы и рекомендации по работе.

- Просмотрите видео на канале Channel 9 с обзором функции Live Unit Testing и ее возможностей.</p>

   > [!VIDEO https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T105/player]

## <a name="related-resources"></a>Связанные ресурсы

- [Средства тестирования кода](https://visualstudio.microsoft.com/vs/testing-tools/)
- [Модульное тестирование кода](unit-test-your-code.md)
