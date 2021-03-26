---
title: Реализация устаревшего языка Service1 | Документация Майкрософт
description: Узнайте, как реализовать устаревшую языковую службу, поддерживающую функции расширенной языковой службы, с помощью платформы управляемых пакетов (MPF). Часть 1 из 2.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services, managed
ms.assetid: df638f24-166d-4b80-be82-c9c39ca7a556
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 99e3f11a9ea60595b2372921702282c2bb4d8dcd
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105085914"
---
# <a name="implementing-a-legacy-language-service-1"></a>Реализация устаревшей языковой службы 1
Классы в среде управляемого пакета (MPF) можно использовать для реализации устаревшей языковой службы, поддерживающей широкий спектр функций, таких как выделение синтаксиса, сопоставление фигурных скобок и завершение IntelliSense.

 Устаревшие языковые службы реализуются как часть VSPackage, но более новым способом реализации функций языковой службы является использование расширений MEF. Дополнительные сведения о новом способе реализации языковой службы см. в статье [расширения редактора и языковой службы](../../extensibility/editor-and-language-service-extensions.md).

> [!NOTE]
> Рекомендуется как можно скорее начать использовать новый API редактора. Это улучшит производительность языковой службы и позволит использовать новые функции редактора.

## <a name="in-this-section"></a>в этом разделе
- [Обзор языковой службы прежних версий](../../extensibility/internals/legacy-language-service-overview.md)

 Общие сведения о функциях языковой службы, поддерживаемых в MPF.

- [Реализация языковой службы прежних версий](../../extensibility/internals/implementing-a-legacy-language-service2.md)

 Описывает, что необходимо для реализации языковой службы с помощью MPF.

- [Регистрация языковой службы прежних версий](../../extensibility/internals/registering-a-legacy-language-service1.md)

 Описание действий, необходимых для регистрации службы языка на основе MPF с помощью [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

- [Средство синтаксического анализа и сканер языковой службы прежних версий](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)

 Описывает два средства синтаксического анализа, необходимые для реализации всех функций языковой службы с помощью MPF.

- [Пошаговое руководство. Создание языковой службы прежних версий](../../extensibility/internals/walkthrough-creating-a-legacy-language-service.md)

 Предоставляет основные шаги, необходимые для реализации языковой службы MPF в VSPackage.

- [Пошаговое руководство. Получение списка установленных фрагментов кода (реализация прежних версий)](../../extensibility/internals/walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation.md)

 Демонстрирует методы получения списка установленных фрагментов кода.

- [Функции языковой службы прежних версий](../../extensibility/internals/legacy-language-service-features1.md)

 Содержит ссылки на разделы с подробными сведениями о том, что необходимо сделать для реализации всех функций языковой службы с помощью MPF.
