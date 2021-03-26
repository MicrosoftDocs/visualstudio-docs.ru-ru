---
title: Общие сведения о модели автоматизации | Документация Майкрософт
description: Сведения о модели автоматизации Visual Studio, состоящей из набора объектов, с которыми можно создать надстройку или расширение Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK], about automation
- extensibility
ms.assetid: 12b6d6db-0d22-4aaa-aa7d-1365f759b7b0
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: d763fea140ddac1b4dba955421c563700373dc22
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105086239"
---
# <a name="automation-model-overview"></a>Общие сведения о модели автоматизации
Модель автоматизации состоит из набора объектов, с которыми можно создать надстройку или расширение Visual Studio. Надстройка — это приложение, которое может управлять средой Visual Studio и автоматизировать общие задачи. Расширение Visual Studio может создавать пользовательские компоненты Visual Studio или добавлять к функциональным возможностям стандартных компонентов, таких как текстовый редактор.

## <a name="objects-in-the-automation-model"></a>Объекты в модели автоматизации
 Модель автоматизации состоит из связанных групп объектов, которые управляют основными аспектами общей среды. На следующей диаграмме показан обширный набор объектов Visual Studio, образующих модель автоматизации.

 ![Диаграмма объектов автоматизации Visual Studio](../../extensibility/internals/media/vsvisualstudioautomationobjectchart.gif "всвисуалстудиоаутоматионобжектчарт")

 Дополнительные сведения см. [в разделе Расширение среды Visual Studio](/previous-versions/esk3eey8(v=vs.140)).

 Среда предоставляет модель для различных функциональных областей. Например, существует модель кода для различных элементов, которые могут быть найдены в коде. Существует модель документа для различных элементов документа. Одна область, область проекта, является особым интересом к поставщикам VSPackage. Вам, вероятно, потребуется, чтобы новые типы проектов участвовали в модели автоматизации практически так же, как [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] и в [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] модели автоматизации. Этот процесс описан в статьи [предоставление автоматизации для пакетов VSPackage](../../extensibility/internals/providing-automation-for-vspackages.md).

 Места, где можно расдумать расширение модели автоматизации среды:

- Project

- Документ

- Код

- Сборка

Дополнительные сведения об автоматизации см. в разделе [Автоматизация и расширяемость для Visual Studio](/previous-versions/visualstudio/visual-studio-2015/extensibility/extensibility-in-visual-studio?preserve-view=true&view=vs-2015). Этот документ и содержащиеся в нем документы содержат ссылки на, которые помогут принять решение о том, как следует предоставлять автоматизацию для VSPackage.

## <a name="see-also"></a>См. также
- [Пошаговое руководство. Создание надстройки](/previous-versions/80493a3w(v=vs.140))