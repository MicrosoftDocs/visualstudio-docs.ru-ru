---
title: Краткие сведения в языковой службе прежних версий | Документация Майкрософт
description: Узнайте о поддержке операции IntelliSense для быстрой информации для отображения сведений об идентификаторе.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Quick Info, supporting in language services [managed package framework]
- IntelliSense, Quick Info
- language services [managed package framework], IntelliSense Quick Info
ms.assetid: 159ccb0b-f5d6-4912-b88b-e9612924ed5e
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 90cab5683c7a13aec25b15d75da0117beee34721
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105060891"
---
# <a name="quick-info-in-a-legacy-language-service"></a>Краткие сведения в языковой службе прежних версий
Краткие сведения IntelliSense отображает сведения об идентификаторе в источнике, когда пользователь либо помещает курсор в идентификатор, либо выбирает **краткие сведения** из меню **IntelliSense** или удерживает курсор мыши над идентификатором. В результате появится всплывающая подсказка со сведениями об идентификаторе. Эти сведения обычно состоят из типа идентификатора. Если активен модуль отладки, эти сведения могут включать текущее значение. Модуль отладки предоставляет значения выражений, тогда как языковая служба обрабатывает только идентификаторы.

 Устаревшие языковые службы реализуются как часть VSPackage, но более новым способом реализации функций языковой службы является использование расширений MEF. Дополнительные сведения см. в разделе [Пошаговое руководство. Отображение подсказок краткие сведения](../../extensibility/walkthrough-displaying-quickinfo-tooltips.md).

> [!NOTE]
> Рекомендуется как можно скорее начать использовать новый API редактора. Это улучшит производительность языковой службы и позволит использовать новые функции редактора.

 Классы языковой службы для управляемых пакетов Framework (MPF) обеспечивают полную поддержку отображения подсказок IntelliSense для быстрой информации. Все, что нужно сделать, — предоставить отображаемый текст и включить функцию кратких сведений.

 Отображаемый текст получается путем вызова <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> средства синтаксического анализа метода со значением причины синтаксического анализа <xref:Microsoft.VisualStudio.Package.ParseReason> . По этой причине средство синтаксического анализа получает сведения о типе (или то, что подходит для отображения в подсказке кратких сведений) для идентификатора в расположении, указанном в <xref:Microsoft.VisualStudio.Package.ParseRequest> объекте. <xref:Microsoft.VisualStudio.Package.ParseRequest>Объект передается в <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> метод.

 Синтаксический анализатор должен выполнить синтаксический анализ всех элементов, находящийся в <xref:Microsoft.VisualStudio.Package.ParseRequest> объекте, чтобы определить типы всех идентификаторов. Затем средство синтаксического анализа должно получить идентификатор в расположении запроса синтаксического анализа. Наконец, синтаксический анализатор должен передать в объект данные всплывающей подсказки, связанные с этим идентификатором, <xref:Microsoft.VisualStudio.Package.AuthoringScope> чтобы объект мог вернуть текст из <xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDataTipText%2A> метода.

## <a name="enabling-the-quick-info-feature"></a>Включение функции "краткие сведения"
 Чтобы включить функцию "быстрые сведения", необходимо задать `CodeSense` Параметры и `QuickInfo` с именем <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> . Эти атрибуты задают <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCodeSense%2A> <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableQuickInfo%2A> Свойства и.

## <a name="implementing-the-quick-info-feature"></a>Реализация функции "краткие сведения"
 <xref:Microsoft.VisualStudio.Package.ViewFilter>Класс обрабатывает операцию быстрой информации IntelliSense. Когда <xref:Microsoft.VisualStudio.Package.ViewFilter> класс получает <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> команду, класс вызывает <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> метод с причиной синтаксического анализа <xref:Microsoft.VisualStudio.Package.ParseReason> и расположением курсора на момент <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> отправки команды. <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>После этого средство синтаксического анализа методов должно выполнить синтаксический анализ источника вплоть до заданного расположения, а затем проанализировать идентификатор в заданном расположении, чтобы определить, что следует отображать в подсказке инструмента "краткие сведения".

 Большинство синтаксических анализаторов выполняют первоначальный синтаксический анализ всего исходного файла и сохраняют результаты в дереве синтаксического анализа. Полный анализ выполняется, когда <xref:Microsoft.VisualStudio.Package.ParseReason> передается <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> методу. Другие виды анализа могут затем использовать дерево синтаксического анализа для получения нужных сведений.

 Например, значение причины синтаксического анализа <xref:Microsoft.VisualStudio.Package.ParseReason> может найти идентификатор в исходном расположении и найти его в дереве синтаксического анализа для получения сведений о типе. Эти сведения о типе затем передаются в <xref:Microsoft.VisualStudio.Package.AuthoringScope> класс и возвращаются <xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDataTipText%2A> методом.
