---
title: Требования к контроллерам и агентам тестирования (нагрузочное тестирование)
description: Узнайте о требованиях к контроллерам и агентам тестирования для нагрузочного тестирования. Visual Studio поддерживает несколько типов тестов.
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- agents, requirements
- controllers, requirements
ms.assetid: 372d97ce-12e4-46a9-9863-da508adba68f
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.openlocfilehash: a123a147d038a41f799c2fdf9d4fb26eaa4f3490
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99894495"
---
# <a name="test-controller-and-test-agent-requirements-for-load-testing"></a>Требования к контроллерам и агентам тестирования для нагрузочного тестирования

Некоторые типы тестов, включая модульные тесты, веб-тесты производительности, нагрузочные тесты и ручные тесты, интегрированы в Visual Studio. Visual Studio позволяет пользователям управления жизненным циклом приложений Visual Studio запускать тесты на удаленных компьютерах с использованием контроллера тестирования и одного или нескольких агентов тестирования. См. раздел [Установка и настройка агентов тестирования](../test/lab-management/install-configure-test-agents.md).

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="hardware-and-software-requirements"></a>Требования к аппаратному и программному обеспечению

Компьютер с тестовым контроллером и компьютеры с агентами должны соответствовать требованиям к оборудованию и программному обеспечению. Кроме того, если планируется развертывать контроллер тестирования и агенты тестирования для нескольких языков, нужно обеспечить поддержку этих языков.

### <a name="hardware-requirements"></a>Требования к оборудованию

В следующей таблице приведены рекомендуемые параметры оборудования для развертывания контроллера тестирования и агентов тестирования.

|**Конфигурация**|**Компонент**|**ЦП**|**Жесткий диск**|**Память**|
|-|-------------------|-|------------|-|
|< 500 виртуальных пользователей|Тестовый агент|2,6 ГГц|10 ГБ|2 ГБ|
|< 1000 виртуальных пользователей|Тестовый агент|Двухъядерный процессор, 2,6 ГГц|10 ГБ|2 ГБ|
|N x 1000 виртуальных пользователей|Тестовый агент|N агентов, каждый с двухъядерным процессором частотой 2,6 ГГц|10 ГБ|2 ГБ|
|\< 30 компьютеров в тестовой среде. Включая участвующие в тестировании агенты и серверы.|Test Controller|2,6 ГГц|||
|N x 30 компьютеров в тестовой среде. Включая участвующие в тестировании агенты и серверы.|Test Controller|N процессоров частотой 2,6 ГГц|||

> [!NOTE]
> Число виртуальных пользователей может значительно различаться в разных тестах. Основная причина различий — разница во *времени обработки* (задержки пользователей). Дополнительные сведения см. в статье [Изменение значений времени обработки для имитации задержек действий человека на веб-сайте](../test/edit-think-times-in-load-test-scenarios.md). В нагрузочном тесте веб-тесты обычно работают более эффективно и создают больше нагрузки, чем модульные тесты. Значения в приведенной выше таблицы действительны для запуска веб-тестов со временем ожидания 3–5 с для типичных веб-приложений.

Данные рекомендации носят общий характер и должны учитываться при планировании оборудования. Производительность тестирования существенно различается в зависимости от объема тестовых данных и числа агентов тестирования. Для агентов тестирования нагрузка ограничивается скоростью ЦП и объемом доступной памяти. Контроллерам тестирования нужно больше ресурсов в зависимости от объема тестовых данных и числа агентов тестирования.

Сервер, на котором работает Visual Studio, должен иметь надежное сетевое соединение с минимальной пропускной способностью 1 Мбит/с и максимальной задержкой 350 мс. Между агентами тестирования и контроллером тестирования не должно быть брандмауэра. Если производительность тестов оказывается слишком низкой, следует обновить оборудование.

### <a name="additional-hardware-considerations"></a>Дополнительное оборудование

Агенты тестирования создают большой объем данных для контроллеров (в зависимости от длительности и размера тестов). В общем случае следует запланировать использование тестовыми данными дополнительных 10 ГБ места на жестком диске за каждые 24 часа.

Помимо перечисленного оборудования следует рассмотреть возможность установки дополнительного оборудования для важных серверов, такого как резервных источников бесперебойного питания и вентиляторов.

### <a name="language-requirements"></a>Требования к языку

Чтобы избежать затруднений и путаницы, на контроллере тестирования и агентах тестирования должен использоваться язык, соответствующий языку операционной системы компьютера и Team Foundation Server. Если агент и контроллер тестирования установлены на разные компьютеры, на них должен использоваться одинаковый язык. Однако можно установить другую языковую версию Visual Studio или поменять ее на английскую версию операционной системы, если язык совпадает с языком развертывания Team Foundation Server.

## <a name="monitor-agent-resources"></a>Отслеживание ресурсов агента

Можно осуществлять мониторинг компьютеров агентов, чтобы определить их потребности в ресурсах, наблюдая за процессами *QTAgent\*.exe*, которые выполняются и масштабируются во время тестов. Самое распространенное узкое место процессов *QTAgent\*.exe* — это загрузка ЦП. Если загрузка ЦП постоянно превышает 95 % процентов, это указывает на чрезмерную загрузку агента. Еще одно распространенное узкое место — использование памяти. Для ресурсоемких тестов отслеживание этих ресурсов может помочь определить, следует ли увеличить ресурсы компьютера или распределять тесты по-другому.

## <a name="see-also"></a>См. также раздел

- [Установка и настройка агентов тестирования](../test/lab-management/install-configure-test-agents.md)
