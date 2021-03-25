---
title: Установка пакета SDK для Visual Studio | Документация Майкрософт
description: Узнайте о вариантах установки комплекта SDK программного обеспечения Visual Studio, в том числе во время установки Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 07/12/2018
ms.topic: overview
ms.assetid: c730edb6-5099-4c16-85a8-08def09f1455
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 331a219210c990aed2f9601cd1f9b1f0bc5710ed
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105079167"
---
# <a name="install-the-visual-studio-sdk"></a>Установка пакета SDK для Visual Studio

Пакет SDK для Visual Studio (пакет средств разработки программного обеспечения) — дополнительный компонент программы установки Visual Studio. Пакет SDK для VS можно установить и позже.

## <a name="install-the-visual-studio-sdk-as-part-of-a-visual-studio-installation"></a>Установка пакета SDK для Visual Studio при установке Visual Studio

Чтобы включить пакет SDK для VS в установку Visual Studio, установите рабочую нагрузку **Разработка расширения Visual Studio** в разделе **Другие наборы инструментов**. Эта рабочая нагрузка установит пакет SDK для Visual Studio и необходимые компоненты. Дальнейшую настройку установки можно выполнить, выбрав или отменив выбор компонентов в представлении **Сводка** .

## <a name="install-the-visual-studio-sdk-after-installing-visual-studio"></a>Установка пакета SDK для Visual Studio после установки Visual Studio

Чтобы установить пакет SDK для Visual Studio после завершения установки Visual Studio, снова запустите установщик Visual Studio и выберите рабочую нагрузку **Разработка расширения Visual Studio**.

## <a name="install-the-visual-studio-sdk-from-a-solution"></a>Установка пакета SDK для Visual Studio из решения

Если вы открываете решение с проектом расширяемости без предварительной установки пакета SDK для VS, в диалоговом окне **Установка отсутствующей функции** вам будет предложено установить рабочую нагрузку **Разработка расширения Visual Studio**:

![Установка разработки расширения](../extensibility/media/install-extension-development.png "Установка разработки расширения")

## <a name="install-the-visual-studio-sdk-from-the-command-line"></a>Установка пакета SDK для Visual Studio из командной строки

Как и в случае с любой другой рабочей нагрузкой или компонентом Visual Studio, вы также можете установить рабочую нагрузку **Разработка расширения Visual Studio** (идентификатор: Microsoft.VisualStudio.Workload.VisualStudioExtension) из командной строки. Дополнительные сведения о соответствующих параметрах командной строки и общие инструкции по определению идентификаторов рабочей нагрузки или компонентов см. в разделе [Использование параметров командной строки для установки Visual Studio](../install/use-command-line-parameters-to-install-visual-studio.md).

Обратите внимание на то, что вам необходимо использовать установщик Visual Studio, соответствующий установленной версии Visual Studio. Например, если на компьютере установлен Visual Studio Enterprise, необходимо запустить установщик Visual Studio Enterprise (*vs_enterprise. exe*).
