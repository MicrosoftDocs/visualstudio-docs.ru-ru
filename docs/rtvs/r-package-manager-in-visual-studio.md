---
title: Диспетчер пакетов для R
description: Практическое руководство по установке пакетов R и управление ими с помощью диспетчера пакетов R в Visual Studio.
ms.date: 01/24/2018
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: jmartens
ms.workload:
- data-science
ms.openlocfilehash: f6c543286951e50fb1f51e7496e166968b5d98e9
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99939426"
---
# <a name="package-manager"></a>Диспетчер пакетов

Диспетчер пакетов в инструментах R для Visual Studio (RTVS) — это пользовательский интерфейс для управления пакетами R. Чтобы открыть его, выберите **Инструменты R** > **Окна** > **Пакеты** или нажмите клавиши **CTRL**+**7**.

В диспетчере пакетов имеется три вкладки. На каждой отображаются списки соответствующих пакетов (слева) и определенные сведения о выбранном пакете (справа), включая версию пакета, описание, сведения о лицензии, расположении установки пакета, а также ссылки на другие важные сведения. С помощью поля поиска в правом верхнем углу можно сортировать список.

> [!Tip]
> Текст в поле поиска сохраняется при переключении между вкладками.

- **Доступные** — список пакетов для установки. Если пакет уже установлен, кнопка **Установить** справа изменяется на **Удалить**.

    ![Вкладка доступных пакетов в диспетчере пакетов в инструментах R для Visual Studio](media/package-manager-available.png)

- **Установленные** — список всех установленных и загруженных пакетов. Зеленая точка рядом с пакетом указывает на то, что пакет загружен в сеанс R. Чтобы удалить пакет, воспользуйтесь красным значком X слева или кнопкой **Удалить** справа. Если доступна более новая версия установленного пакета, расположенная справа синяя стрелка вверх позволяет обновить его.

    ![Вкладка установленных пакетов в диспетчере пакетов в инструментах R для Visual Studio](media/package-manager-installed.png)

- На вкладке **Загруженные** отображаются только те пакеты, которые загружены в сеанс R, поэтому для всех таких пакетов отображаются зеленые точки. Здесь можно также удалить и обновить пакеты.

    ![Вкладка загруженных пакетов в диспетчере пакетов в инструментах R для Visual Studio](media/package-manager-loaded.png)

## <a name="package-locations"></a>Расположения пакетов

Пакеты устанавливаются в следующие расположения.

- Основные пакеты, которые входят в состав RTVS, устанавливаются в *C:\Program Files\Microsoft\R Client\R_SERVER\library*
- Дополнительные пакеты устанавливаются в *%userprofile%\Documents\R\win-library\3.3*
