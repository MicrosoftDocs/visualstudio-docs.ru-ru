---
title: Практические руководства. Поддержка структурирования в языковой службе прежних версий | Документация Майкрософт
description: Узнайте, как обеспечить поддержку структурирования, расширения или свертывания различных областей текста в языковой службе прежних версий.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], collapse to definitions command
- language services, supporting Collapse to Definitions command
- hidden text, Collapse to Definitions command
ms.assetid: bb6e74c3-93e4-4ef7-afc7-1c9b342f083b
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 0c275a6a466cc58187293f6ebd84a39fdf8064e6
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105078689"
---
# <a name="how-to-support-outlining-in-a-legacy-language-service"></a>Практические руководства. Поддержка структурирования в языковой службе прежних версий
Структурирование используется для разворачивания или сворачивания различных областей текста. Способ структурирования можно определить по-разному на разных языках. Дополнительные сведения см. в разделе [Структура](../../ide/outlining.md).

 Устаревшие языковые службы реализуются как часть VSPackage, но более новым способом реализации функций языковой службы является использование расширений MEF. Дополнительные сведения о новом способе реализации структуры см. в разделе [Пошаговое руководство. структурирование](../../extensibility/walkthrough-outlining.md).

> [!NOTE]
> Рекомендуется как можно скорее начать использовать новый API редактора. Это улучшит производительность языковой службы и позволит использовать новые функции редактора.

 Ниже показано, как обеспечить поддержку этой команды для языковой службы.

## <a name="to-support-outlining"></a>Поддержка структурирования

1. Реализуйте <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningCapableLanguage> для своего объекта языковой службы.

2. Вызовите <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A> для текущего объекта сеанса структуризации, чтобы добавить новые области структуры.

## <a name="robust-programming"></a>Отказоустойчивость
 Когда пользователь выбирает пункт **Свернуть в определения** в меню **Структура** , интегрированная среда разработки обращается к <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningCapableLanguage.CollapseToDefinitions%2A> языковой службе.

 При вызове этого метода интегрированная среда разработки передает <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> указатель (указатель на текстовый буфер) и <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession> (указатель на текущий сеанс структуры).

 Метод можно вызвать <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A> для нескольких областей структуры, указав эти регионы в `rgOutlnReg` параметре. `rgOutlnReg`Параметр является <xref:Microsoft.VisualStudio.TextManager.Interop.NewOutlineRegion> структурой. Этот процесс позволяет задавать различные характеристики скрытой области, например, разворачивается или сворачивается определенный регион.

> [!NOTE]
> Будьте внимательны, скрывая символы новой строки. Скрытый текст должен находиться от начала первой строки до последнего символа последней строки в разделе, в результате чего отображается итоговый символ новой строки.

## <a name="see-also"></a>См. также
- [Как обеспечить поддержку скрытого текста в языковой службе прежних версий](../../extensibility/internals/how-to-provide-hidden-text-support-in-a-legacy-language-service.md)
- [Руководство. Предоставление расширенной поддержки структурирования в языковой службе прежних версий](../../extensibility/internals/how-to-provide-expanded-outlining-support-in-a-legacy-language-service.md)
