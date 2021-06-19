---
title: Поддерживаемые выпуски Visual Studio для визуализации и моделирования SDK
description: Сведения о выпусках Visual Studio, поддерживаемых инструментами DSL в средах разработки и развертывания.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language Tools, supported Visual Studio editions
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: b8435f37ebe68e954af135be0f513247191ea8a9
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2021
ms.locfileid: "112386401"
---
# <a name="supported-visual-studio-editions-for-visualization--modeling-sdk"></a>Выпуски Visual Studio, поддерживаемые пакетом SDK визуализации и моделирования

Ниже перечислены выпуски Visual Studio, которые поддерживаются [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] в средах разработки и развертывания. Дополнительные сведения об этих выпусках см. в [центре разработчиков](https://visualstudio.microsoft.com/)Microsoft Visual Studio.

## <a name="authoring-edition"></a>Разработка версии

Для определения доменного языка необходимо установить следующие компоненты.

|Продукт|Ссылка на скачивание|
|-|-|
|Visual Studio|[http://go.microsoft.com/fwlink/?LinkId=185579](https://visualstudio.microsoft.com/)|
|SDK для Visual Studio|[http://go.microsoft.com/fwlink/?LinkId=185580](/azure/devops/integrate/index?view=azure-devops&viewFallbackFrom=vsts&preserve-view=true)|
|Пакет SDK для визуализации и моделирования в Visual Studio|[http://go.microsoft.com/fwlink/?LinkID=186128](https://code.msdn.microsoft.com/Visualization-and-Modeling-313535db)|

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

## <a name="deployment-editions"></a>Развертывание выпусков

[!INCLUDE[dsl](../modeling/includes/dsl_md.md)] поддерживает следующие конфигурации для развертывания создаваемых доменных языков:

- Visual Studio Enterprise

- Visual Studio Professional

- Оболочка Visual Studio Shell (режим интеграции), распространяемый пакет.

- Оболочка Visual Studio Shell (изолированный режим), распространяемый пакет.

> [!NOTE]
> Чтобы обеспечить возможность запуска DSL в продукте оболочки, необходимо задать поле **Supported VS Edition** в манифесте расширения. Дополнительные сведения см. в разделе [Развертывание решения на предметно-ориентированном языке](msi-and-vsix-deployment-of-a-dsl.md).

## <a name="see-also"></a>См. также раздел

- [Глоссарий средств предметно-ориентированных языков](/previous-versions/bb126564(v=vs.100))