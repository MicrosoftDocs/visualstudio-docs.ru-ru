---
title: Расширение устаревшей языковой службы | Документация Майкрософт
description: Сведения о структуре, реализации и расширении устаревших языковых служб в Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services
- Visual Studio, language services
ms.assetid: 2700cd4d-5f68-43fc-b62f-dc80c3f3aa85
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: f22d6997d932884e5aeb8d794b7884b40a8d5dab
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105074500"
---
# <a name="legacy-language-service-extensibility"></a>Расширяемость языковой службы прежних версий
Языковая служба предоставляет зависящую от языка поддержку редактирования исходного кода в интегрированной среде разработки.

 Устаревшие языковые службы реализуются как часть VSPackage, но более новым способом реализации функций языковой службы является использование расширений MEF. Дополнительные сведения о новом способе реализации языковой службы см. в статье [расширения редактора и языковой службы](../../extensibility/editor-and-language-service-extensions.md).

 В этом разделе обсуждается структура и реализация устаревшей языковой службы.

## <a name="in-this-section"></a>в этом разделе
- [Миграция языковой службы прежних версий](../../extensibility/internals/migrating-a-legacy-language-service.md)

 В этой статье объясняется, как обновить языковую службу с Visual Studio 2008 до последней версии.

- [Основные компоненты языковой службы прежних версий](../../extensibility/internals/legacy-language-service-essentials.md)

 Содержит важные сведения о разработке языковых служб для интеграции языка программирования в Visual Studio.

- [Разработка языковой службы прежних версий](../../extensibility/internals/developing-a-legacy-language-service.md)

 Содержит ссылки на разделы, которые могут помочь при создании языковой службы.

- [Цветовая маркировка синтаксиса в языковой службе прежних версий](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)

 Содержит сведения о поддержке выделения синтаксиса в языковой службе.

- [Реализация языковой службы прежних версий](../../extensibility/internals/implementing-a-legacy-language-service1.md)

 Содержит сведения об использовании платформы управляемых пакетов (MPF) для реализации полнофункциональной языковой службы в управляемом коде.

- [Вспомогательные средства просмотра символов](../../extensibility/internals/supporting-symbol-browsing-tools.md)

 Описывает библиотеки и средства, позволяющие просматривать древовидные представления символов в интегрированной среде разработки.

## <a name="related-sections"></a>Связанные разделы
- [Расширения редактора и языковой службы](../../extensibility/editor-and-language-service-extensions.md)

 Содержит общие сведения о редакторах Visual Studio.

- [Поддержка языковой службы для отладки](../../extensibility/internals/language-service-support-for-debugging.md)

 Содержит сведения о и ссылку на пакет SDK для отладки Visual Studio, который содержит сведения, необходимые для создания и настройки компонентов отладчика, используемых для отладки программ.
