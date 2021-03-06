---
title: Завершение операторов в языковой службе прежних версий | Документация Майкрософт
description: Узнайте, как работает завершение операторов и как его реализовать в устаревшей языковой службе в VSPackage.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- statement completion
- language services, statement completion
ms.assetid: 617439dc-3f0e-4e5f-b346-3e4e7fcf3c1b
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 63a784c850f4c88ecf17a978a2943577eb988a7b
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105080779"
---
# <a name="statement-completion-in-a-legacy-language-service"></a>Завершение операторов в языковой службе прежних версий
Завершение операторов — это процесс, с помощью которого служба языка помогает пользователям завершить ключевое слово языка или элемент, которые они начали вводить в основном редакторе. В этом разделе описывается, как работает завершение операторов и как его реализовать в языковой службе.

 Устаревшие языковые службы реализуются как часть VSPackage, но более новым способом реализации функций языковой службы является использование расширений MEF. Дополнительные сведения о новом способе реализации завершения операторов см. в разделе [Пошаговое руководство. Отображение завершения операторов](../../extensibility/walkthrough-displaying-statement-completion.md).

> [!NOTE]
> Рекомендуется как можно скорее начать использовать новый API редактора. Это улучшит производительность языковой службы и позволит использовать новые функции редактора.

## <a name="implementing-statement-completion"></a>Реализация завершения операторов
 В основном редакторе завершение операторов активирует специальный пользовательский интерфейс, который в интерактивном режиме упрощает и ускоряет написание кода. Завершение операторов позволяет при необходимости отображать соответствующие объекты или классы, что позволяет избежать необходимости запоминать определенные элементы или искать их в справочном разделе справки.

 Для реализации завершения операторов язык должен иметь триггер завершения операторов, который можно проанализировать. Например, [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] использует оператор с точкой (.), а [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] использует оператор стрелки (->). Языковая служба может использовать более одного триггера для завершения инструкции. Эти триггеры запрограммированы в фильтре команд.

## <a name="command-filters-and-triggers"></a>Фильтры и триггеры команд
 Команда фильтрует вхождения триггера или триггеров. Чтобы добавить фильтр команд в представление, реализуйте <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> интерфейс и присоедините его к представлению, вызвав <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> метод. Вы можете использовать один и тот же фильтр команд ( <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> ) для всех аспектов языковой службы, таких как завершение операторов, маркеры ошибок и советы по методам. Дополнительные сведения см. в разделе [перехват команд языковой службы прежних версий](../../extensibility/internals/intercepting-legacy-language-service-commands.md).

 При входе триггера в редактор, в частности, в текстовом буфере, языковая служба затем вызывает <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> метод. Это приводит к тому, что редактор выводит пользовательский интерфейс, чтобы пользователь мог выбирать из кандидатов на завершение операторов. Этот метод требует реализации <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> и <xref:Microsoft.VisualStudio.TextManager.Interop.UpdateCompletionFlags> флагов в качестве параметров. Список элементов завершения отображается в списке прокрутки. По мере того, как пользователь продолжит ввод, выбор в списке обновляется, чтобы отразить наиболее близкое совпадение с последними введенными символами. Основной редактор реализует пользовательский интерфейс для завершения операторов, но языковая служба должна реализовать интерфейс, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> чтобы определить набор элементов завершения для инструкции.

## <a name="see-also"></a>См. также
- [Перехват команд языковой службы прежних версий](../../extensibility/internals/intercepting-legacy-language-service-commands.md)
