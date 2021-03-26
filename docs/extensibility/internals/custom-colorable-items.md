---
title: Настраиваемые цветные элементы | Документация Майкрософт
description: Узнайте, как создавать настраиваемые цветовые элементы как часть языковой службы путем переопределения элементов в диалоговом окне Шрифты и цвета, например ключевые слова и комментарии.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- colorable items
- language services, custom colorable items
ms.assetid: b4d0ddee-c04b-48dc-ba82-f6068570cef0
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: f08c5c9e533e3a21ec4b87e7d148c3022ee0fed1
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105056806"
---
# <a name="custom-colorable-items"></a>Настраиваемые цветные элементы
Можно переопределить список типов для выделения цветом, например ключевые слова и комментарии, путем реализации пользовательских цветовых элементов в рамках языковой службы.

## <a name="user-settings-of-colorable-items"></a>Пользовательские параметры цветовых элементов
 Диалоговое окно **шрифты и цвета** можно отобразить, выбрав пункт **Параметры** в меню **Сервис** , а затем выбрав пункт **шрифты и цвета** в разделе **Среда**. При выборе отображения, например **текстового редактора** или **командного окна**, в списке **Отображаемые элементы** отображаются все цветные элементы для этого дисплея. Можно просматривать и изменять шрифт, размер, цвет переднего плана и цвет фона для каждого цветового элемента. Выбранные параметры хранятся в кэше в реестре и доступны по имени элемента с цветовым названием.

## <a name="presentation-of-colorable-items"></a>Представление элементов с цветовым цветом
 Так как интегрированная среда разработки обрабатывает пользовательские переопределения цветовых элементов в диалоговом окне **шрифты и цвета** , необходимо указать каждый настраиваемый цветовой элемент с именем. Это имя отображается в списке **Отображаемые элементы** . Цветные элементы отображаются в алфавитном порядке. Для группирования настраиваемых цветовых элементов языковой службы можно начинать каждое имя с использованием своего имени языка, например **невлангуаже-Comment** и **невлангуаже-keyword**.

> [!CAUTION]
> Необходимо включить имя языка в имя цветового элемента, чтобы избежать конфликтов с существующими цветовыми именами элементов. При изменении имени одного из цветовых элементов во время разработки необходимо сбросить кэш, который был создан при первом обращении к цветовым элементам. Вы можете сбросить экспериментальный кэш с помощью средства **CreateExpInstance** , которое устанавливается вместе с пакетом SDK для Visual Studio, как правило, в каталоге:
>
> *C:\Program Files (x86) \Microsoft Visual Studio, версия: Вссдк\висуалстудиоинтегратион\тулс\бин*
>
> Чтобы сбросить кэш, введите **CreateExpInstance/Reset**. Дополнительные сведения о **CreateExpInstance** см. в разделе [служебная программа CreateExpInstance](../../extensibility/internals/createexpinstance-utility.md).

 Первый элемент в списке цветовых элементов никогда не упоминается. Первый элемент соответствует элементу с цветовым индексом, равным 0, и [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] всегда предоставляет цвета и атрибуты текста по умолчанию для этого элемента. Самый простой способ работы с этим неиспользуемым элементом — предоставить заполнитель цветовой элемент в списке в качестве первого элемента.

## <a name="implement-custom-colorable-items"></a>Реализация пользовательских цветовых элементов

1. Определите, что необходимо раскрасить на языке, например ключевое слово, оператор и идентификатор.

2. Создайте перечисление этих цветовых элементов.

3. Свяжите типы токенов, возвращаемые средством синтаксического анализа или сканера, со перечисляемыми значениями.

    Например, значения, представляющие типы токенов, могут быть одними и теми же значениями в перечислении пользовательских цветовых элементов.

4. В реализации <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> метода в <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> объекте заполните список атрибутов значениями из перечисления пользовательских цветовых элементов, соответствующих типам токенов, возвращаемым средством синтаксического анализа или сканера.

5. В том же классе, который реализует <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> интерфейс, реализуйте <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems> интерфейс и его два метода, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetItemCount%2A> и <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A> .

6. Реализовать интерфейс <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem>.

7. Если требуется поддержка 24-разрядных или высоких значений цвета, также реализуйте <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> интерфейс.

8. В объекте языковой службы создайте список, содержащий <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem> объекты, по одному для каждого цветового элемента, который может быть идентифицирован анализатором или средством проверки.

    Доступ к каждому элементу в списке можно получить, используя соответствующее значение из перечисления пользовательских цветовых элементов. Используйте значения перечисления в качестве индекса в списке. Первый элемент в списке никогда не обращается, так как он соответствует стилю текста по умолчанию, который [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] всегда обрабатывает сам себя. Вы можете компенсировать это, вставив замещающий цветовой элемент в начало списка.

9. В реализации <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetItemCount%2A> метода возвращайте число элементов в списке Настраиваемые цветные элементы.

10. В реализации <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A> метода верните запрошенный цветовой элемент из списка.

    Пример реализации <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> интерфейсов и см. в разделе <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> .

## <a name="see-also"></a>См. также
- [Модель языковой службы прежних версий](../../extensibility/internals/model-of-a-legacy-language-service.md)
- [Выделение синтаксиса в пользовательских редакторах](../../extensibility/syntax-coloring-in-custom-editors.md)
- [Выделение синтаксиса в языковой службе прежних версий](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)
- [Реализовать цветовую раскраску синтаксиса](../../extensibility/internals/implementing-syntax-coloring.md)
- [Как использовать встроенные цветные элементы](../../extensibility/internals/how-to-use-built-in-colorable-items.md)
