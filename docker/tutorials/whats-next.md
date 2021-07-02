---
title: Учебник по Docker. Дальнейшие действия
description: Описывает варианты добавления оркестрации в приложения DOCKER с использованием проектов Cloud Native Computing Foundation.
ms.date: 08/04/2020
author: nebuk89
ms.author: ghogen
manager: jmartens
ms.topic: conceptual
ms.workload:
- azure
ms.openlocfilehash: e777d80f44c9a11e4d2a893c968d33e348ca442a
ms.sourcegitcommit: 8b75524dc544e34d09ef428c3ebbc9b09f14982d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2021
ms.locfileid: "113222699"
---
# <a name="whats-next"></a>Дальнейшие действия

Несмотря на то, что вы закончили работу с учебником, вам еще есть что узнать о контейнерах!
Мы не будем углубляться в это, но предложим вам несколько других областей, заслуживающих внимания.

## <a name="container-orchestration"></a>Оркестрация контейнеров

Выполнять контейнеры в рабочей среде непросто. Вряд ли вам захочется просто входить в компьютер и запускать `docker run` или `docker-compose up`. Причины. А что будет, если контейнеры откажут? Как масштабировать их между несколькими компьютерами? Эту проблему решает оркестрация контейнеров. Такие средства, как Kubernetes, Swarm, Nomad и AKS, позволяют решить эту проблему несколько разными способами.

Общая идея в том, что у вас есть "руководство", которое получает **ожидаемое состояние**. Это может быть состояние "я хочу запустить два экземпляра веб-приложения и открыть порт 80". Затем руководство просматривает все компьютеры в кластере и делегируют задачу "рабочим" узлам. Руководство может отслеживать изменения (например, выход из контейнера), а затем стараться сделать так, чтобы **фактическое состояние** отражало ожидаемое.

## <a name="cloud-native-computing-foundation-projects"></a>Проекты Cloud Native Computing Foundation

CNCF — это коммерчески нейтральная платформа для различных проектов с открытым кодом, включая Kubernetes, Prometheus, Envoy, Linkerd, NAT и многие другие! См. [градиентные и инкубированные проекты здесь](https://www.cncf.io/projects/), а весь [ландшафт CNCF здесь](https://landscape.cncf.io/). Существует множество проектов, помогающих решать задачи, связанные с мониторингом, ведением журнала, безопасностью, реестрами образов, обменом сообщениями и т. д.

Если вы не знакомы с системой контейнеров и разработкой ориентированных на облако приложений, добро пожаловать! Присоединяйтесь к сообществу, задавайте вопросы и продолжайте учиться! Мы рады, что вы с нами!

## <a name="working-with-docker-in-vs-code"></a>Работа с Docker в VS Code

Дополнительные сведения об использовании расширения VS Code Docker:

- [Общие сведения о расширении Docker для VS Code](https://code.visualstudio.com/docs/containers/overview)
- [Начало работы с Node.js](https://code.visualstudio.com/docs/containers/quickstart-node)
- [Начало работы с Python](https://code.visualstudio.com/docs/containers/quickstart-python)
- [Начало работы с .NET Core](https://code.visualstudio.com/docs/containers/quickstart-aspnet-core)
- [Отладка контейнерных приложений](https://code.visualstudio.com/docs/containers/debug-common)
