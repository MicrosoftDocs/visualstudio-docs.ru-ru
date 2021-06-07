---
title: Инструменты Visual Studio сценариев установки среды выполнения Office
description: Узнайте, как можно установить среду выполнения Visual Studio 2010 Tools for Office. В этой статье описываются три сценария установки.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Visual Studio Tools for Office runtime, installation scenarios
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 671d8e929ebef1085f0bf2aedad2a3280c36514c
ms.sourcegitcommit: f430d014f912aa7874e1db65026dc72688b973e4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/04/2021
ms.locfileid: "111448341"
---
# <a name="visual-studio-tools-for-office-runtime-installation-scenarios"></a>Инструменты Visual Studio сценариев установки среды выполнения Office

  Установить Visual Studio 2010 Tools для Office Runtime можно тремя способами:

- Во время установки Visual Studio.

- Во время установки Microsoft Office.

- При установке распространяемого пакета средств Visual Studio 2010 для среды выполнения Office.

  Установленные компоненты среды выполнения зависят от конфигурации компьютера и сценария установки.

## <a name="runtime-components-that-are-installed-in-each-installation-scenario"></a>Компоненты среды выполнения, установленные в каждом сценарии установки

 Среда выполнения Visual Studio 2010 Tools for Office имеет три компонента: Загрузчик решений Office, расширения Office для платформа .NET Framework 3,5 и расширения Office для [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] или более поздней версии. Загрузчик решений Office всегда устанавливается при установке среды выполнения. Установка расширений Office для платформы .NET Framework зависит от конфигурации компьютера и сценария установки. Если одно из расширений Office невозможно установить при установке среды выполнения, среда автоматически установит отсутствующие расширения Office позже при соблюдении определенных требований. Эта функция среды выполнения называется *Install по запросу*.

 В следующей таблице указывается, какие компоненты среды выполнения устанавливаются по умолчанию в каждом сценарии установки среды выполнения. Дополнительные сведения о каждом сценарии представлены далее.

|Сценарий установки среды выполнения|Загрузчик решений Office|Расширения Office для платформы .NET Framework 3.5|Расширения Office для [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]|Расширения Office для [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]|
|-----------------------------------|----------------------------|--------------------------------------------------| - |---------------------------------------------------------------------------|
|С [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)] и более поздними версиями|Да|Да, если платформа .NET Framework 3.5 уже установлена.|Да|Да|
|С добавлением [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)]|Да|Да, если платформа .NET Framework 3.5 уже установлена.|Нет|Нет|
|С Office 2010 с пакетом обновления 1 (SP1) или более поздней версии|Да|Да, если платформа .NET Framework 3.5 уже установлена.|Да, если платформа [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] уже установлена.|Нет|
|С Office 2013 и более поздних версий|Да|Да, если платформа .NET Framework 3.5 уже установлена.|Да, если платформа [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] уже установлена.|Да, если платформа [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] уже установлена.|
|С распространяемой средой выполнения|Да|Да, если платформа .NET Framework 3.5 уже установлена.|Да, если платформа [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] уже установлена.|Да, если платформа [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] уже установлена.|

### <a name="install-the-runtime-with-visual-studio-or-the-microsoft-office-developer-tools-for-visual-studio"></a>Установка среды выполнения с помощью Visual Studio или Инструменты разработчика Microsoft Office для Visual Studio

 При установке Office Developer Tools в Visual Studio расширения Office для [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] и [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] всегда устанавливаются на компьютере разработчика. Расширения Office для платформы .NET Framework 3.5 устанавливаются только в том случае, если .NET Framework 3.5 уже имеется на компьютере разработчика. Если вы устанавливаете платформу .NET Framework 3.5 после установки [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)], среда выполнения автоматически установит расширения Office для .NET Framework 3.5 при первом создании проекта Office, ориентированном на .NET Framework 3.5.

> [!WARNING]
> Создать проект Office, ориентированный на платформу .NET Framework 3.5, с помощью [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)] или более поздней версии, нельзя.

 Дополнительные сведения об установке средств разработчика Office см. в разделе [как настроить компьютер для разработки решений Office](../vsto/how-to-configure-a-computer-to-develop-office-solutions.md).

### <a name="install-the-runtime-with-office"></a>Установка среды выполнения с помощью Office

 При установке Office расширения Office для платформы .NET Framework 3.5 устанавливаются в случае, если .NET Framework 3.5 уже имеется на компьютере. При установке платформы .NET Framework 3.5 после Office среда выполнения автоматически установит расширения Office для .NET Framework 3.5, когда приложение Office попытается в первый раз загрузить решение, ориентированное на .NET Framework 3.5.

 Расширения Office для [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] или более поздней версии также устанавливаются вместе с Office, если на компьютере уже имеются соответствующие версии платформа .NET Framework.

 Чтобы убедиться, что пользователи имеют необходимые расширения для использования приложения, включите последнюю версию распространяемого пакета средств Visual Studio 2010 Tools для Office в качестве необходимого компонента для вашего решения. Дополнительные сведения о предварительных требованиях см. в разделе [Предварительные требования для решения Office для развертывания](/previous-versions/bb608617(v=vs.110)).

### <a name="install-the-runtime-by-using-the-runtime-redistributable"></a>Установка среды выполнения с помощью распространяемого пакета среды выполнения

 Среду выполнения можно установить, запустив распространяемый пакет средств Visual Studio 2010 для среды выполнения Office вручную или включив распространяемый пакет как обязательный компонент при развертывании решения Office.

 При установке среды выполнения с помощью распространяемого пакета средств Visual Studio 2010 для среды выполнения Office расширения Office для платформа .NET Framework 3,5 и расширения Office для [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] или более поздней версии устанавливаются, если на компьютере уже имеются соответствующие версии платформа .NET Framework. Если при установке среды выполнения одна из этих версий платформы .NET Framework на компьютере отсутствует, расширения Office для отсутствующей версии платформы .NET Framework не будут установлены. Если вы установите отсутствующую версию платформы .NET Framework позже, среда выполнения автоматически установит соответствующие расширения Office, когда решение, для которого требуются эти расширения, будет в следующий раз установлено (если среда выполнения была установлена с решением, развернутым с помощью ClickOnce) или загружено (если среда выполнения была установлена с решением, развернутым с помощью установщика Windows).

 Дополнительные сведения о включении необходимых компонентов в решение ClickOnce см. в разделе [инструкции. Установка необходимых компонентов на компьютерах конечных пользователей для запуска решений Office](/previous-versions/bb608608(v=vs.110)). Дополнительные сведения об установке среды выполнения из распространяемого пакета вручную см. [в разделе как установить распространяемый пакет среды выполнения Office инструменты Visual Studio](../vsto/how-to-install-the-visual-studio-tools-for-office-runtime-redistributable.md).

## <a name="see-also"></a>См. также раздел

- [Общие сведения о Инструменты Visual Studio для среды выполнения Office](../vsto/visual-studio-tools-for-office-runtime-overview.md)
- [Сборки в Инструменты Visual Studio среды выполнения Office](../vsto/assemblies-in-the-visual-studio-tools-for-office-runtime.md)
