---
title: Python в Visual Studio. Руководство. Шаг 0 — установка
titleSuffix: ''
description: Шаг 0 (предварительные требования для установки) базового пошагового руководства по работе с Python в Visual Studio.
ms.date: 01/28/2019
ms.topic: tutorial
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.custom: vs-acquisition
ms.workload:
- python
- data-science
ms.openlocfilehash: ee6454a3414b8b586dc596ea25ff76066009df50
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2021
ms.locfileid: "112390689"
---
# <a name="install-python-support-in-visual-studio"></a>Установка поддержки Python в Visual Studio

> [!Note]
> Сейчас Python поддерживается только в Visual Studio для Windows. В Mac и Linux его поддержка реализуется посредством [Visual Studio Code](https://code.visualstudio.com/docs/python/python-tutorial).

1. Скачайте и запустите последнюю версию Visual Studio Installer для Windows (поддержка Python имеется в выпуске 15.2 и более поздних). Если вы уже установили Visual Studio, запустите установщик Visual Studio и перейдите к шагу 2.

    > [!div class="nextstepaction"]
    > [Установка Visual Studio Community](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=Community&rel=15&rid=34347&utm_source=docs&utm_medium=clickbutton&utm_campaign=python_gettingstarted)

    >[!Tip]
    > Выпуск Community предназначен для индивидуальных разработчиков, использования при аудиторном обучении и в научных исследованиях, а также разработки решений с открытым кодом. Если программу планируется использовать в других целях, установите [Visual Studio Professional](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=Professional&rel=15&rid=34347&utm_source=docs&utm_medium=clickbutton&utm_campaign=python_gettingstarted) или [Visual Studio Enterprise](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=Enterprise&rel=15&rid=34347&utm_source=docs&utm_medium=clickbutton&utm_campaign=python_gettingstarted).

1. В установщике предлагается список рабочих нагрузок, то есть групп связанных параметров для определенных целей разработки. Для Python выберите рабочую нагрузку **Разработка на Python** и нажмите **Установить**.

    ![Рабочая нагрузка разработки Python в установщике Visual Studio](media/installation-python-workload.png)

1. Чтобы быстро протестировать поддержку Python, запустите Visual Studio, нажмите клавиши **ALT**+**I**, чтобы открыть **интерактивное окно Python**, и введите `2+2`. Если вы не увидите результат **4**, проверьте выполненные действия.

    ![Тестирование Python в интерактивном окне](media/installation-interactive-test.png)

## <a name="next-step"></a>Следующий шаг

> [!div class="nextstepaction"]
> [Шаг 1. Создание проекта Python](tutorial-working-with-python-in-visual-studio-step-01-create-project.md)

## <a name="see-also"></a>См. также раздел

- [Определение существующего интерпретатора Python вручную](managing-python-environments-in-visual-studio.md#manually-identify-an-existing-environment)
- [Установка поддержки Python в Visual Studio 2015 и более ранних версиях](installing-python-support-in-visual-studio.md)
- [Расположения установки](installing-python-support-in-visual-studio.md#install-locations)
