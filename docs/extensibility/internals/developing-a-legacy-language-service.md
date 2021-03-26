---
title: Разработка языковой службы прежних версий | Документация Майкрософт
description: Сведения о реализации устаревшей языковой службы в составе VSPackage или с помощью расширений Managed Extensibility Framework (MEF).
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.vsip.LangServWiz.langtoks
- vs.vsip.LangServWiz.welcome
- vs.vsip.LangServWiz.langSpec
- vs.vsip.LangServWiz.langInfo
- vs.vsip.LangServWiz.langServOpts
helpviewer_keywords:
- language services, developing
ms.assetid: 6151ba88-c1c3-41de-a1cc-668f494d48d1
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 59c06c96d2a0263c9e76ed4359e0fac93ab2ab25
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105056731"
---
# <a name="develop-a-legacy-language-service"></a>Разработка языковой службы прежних версий
В этом разделе содержатся ссылки на разделы, которые помогут создать устаревшую языковую службу.

 Устаревшие языковые службы реализуются как часть VSPackage, но более новым способом реализации функций языковой службы является использование расширений MEF. Дополнительные сведения о новом способе реализации языковой службы см. в статье [расширения редактора и языковой службы](../../extensibility/editor-and-language-service-extensions.md).

> [!NOTE]
> Рекомендуется как можно скорее начать использовать новый API редактора. Это улучшит производительность языковой службы и позволит использовать новые функции редактора.

## <a name="in-this-section"></a>Содержание раздела
- [Модель языковой службы прежних версий](../../extensibility/internals/model-of-a-legacy-language-service.md)

 Предоставляет модель службы минимального языка для [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] базового редактора. Эту модель можно использовать в качестве руководств по созданию собственной языковой службы.

- [Интерфейсы языковой службы прежних версий](../../extensibility/internals/legacy-language-service-interfaces.md)

 Описывает объекты, необходимые для реализации языковой службы, и предоставляет список дополнительных объектов, которые можно использовать для выделения синтаксических конструкций, данных методов и других функций.

- [Перехват команд языковой службы прежних версий](../../extensibility/internals/intercepting-legacy-language-service-commands.md)

 Описание вставки фильтра команд в языковую службу для перехвата команд, которые в противном случае будут обработаны в текстовом представлении.

- [Регистрация языковой службы прежних версий](../../extensibility/internals/registering-a-legacy-language-service2.md)

 Содержит сведения о регистрации языковой службы с помощью [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

- [Поддержка языковой службы для отладки](../../extensibility/internals/language-service-support-for-debugging.md)

 Описывает, как языковая служба может предоставлять функции для поддержки отладчика.

- [Контрольный список: создание языковой службы прежних версий](../../extensibility/internals/checklist-creating-a-legacy-language-service.md)

 Содержит пошаговые инструкции по созданию и интеграции языковой службы для базового редактора.

## <a name="related-sections"></a>Связанные разделы
- [Выделение синтаксиса в языковой службе прежних версий](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)

 Описывает, как реализовать выделение синтаксиса в языковой службе.

- [Завершение операторов в языковой службе прежних версий](../../extensibility/internals/statement-completion-in-a-legacy-language-service.md)

 Обсуждается завершение операторов, процесс, с помощью которого служба языка помогает пользователям завершить ключевое слово языка или элемент, который они начали вводить.

- [Сведения о параметрах в устаревшей языковой службе](../../extensibility/internals/parameter-info-in-a-legacy-language-service1.md)

 Описывает способы предоставления советов по методам для перегруженных функций и методов.

- [Как обеспечить поддержку скрытого текста в языковой службе прежних версий](../../extensibility/internals/how-to-provide-hidden-text-support-in-a-legacy-language-service.md)

 Объясняет назначение скрытой области текста и предоставляет инструкции о том, как реализовать скрытую область текста.

- [Руководство. Предоставление расширенной поддержки структурирования в языковой службе прежних версий](../../extensibility/internals/how-to-provide-expanded-outlining-support-in-a-legacy-language-service.md)

 Описание двух вариантов, расширяющих поддержку структурирования для вашего языка, после того как команда *Свернуть в определения* не поддерживается.
