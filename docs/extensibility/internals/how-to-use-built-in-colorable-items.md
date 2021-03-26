---
title: Как использовать Built-In цветные элементы | Документация Майкрософт
description: Узнайте, как использовать встроенные цветные элементы в интегрированной среде разработки (IDE) Visual Studio для языковой службы.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- colorable items
- language services, built-in colorable items
ms.assetid: 5e5f3436-6bad-4fd2-8823-6a30353ba648
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 253c108fe83eaf44f945f546bd64dd6529de1dd6
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105086083"
---
# <a name="how-to-use-built-in-colorable-items"></a>Как использовать встроенные цветные элементы
Перед использованием встроенных цветовых элементов необходимо сначала сообщить в интегрированную среду разработки (IDE), которая не предоставляет собственные настраиваемые цветовые элементы, которые в данном случае будут <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems> объектами. Это делается путем настройки записи реестра для языковой службы.

## <a name="to-use-built-in-colorable-items"></a>Использование встроенных цветовых элементов

1. В разделе **HKEY_LOCAL_MACHINE\VisualStudio\\<X. Y> \лангуажес\лангуаже Services \\<имя \> языка**, где — это \<X.Y> версия [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , а \<Language Name> — имя вашего языка, создайте значение записи реестра DWORD с именем **рекуестстоккколорс**.

2. Задайте для записи реестра **рекуестстоккколорс** значение *1*.

    После создания записи в реестре метод, используемый в этом <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> перечислении, может использовать члены <xref:Microsoft.VisualStudio.TextManager.Interop.DEFAULTITEMS> перечисления для заполнения массива атрибутов цвета, используемых редактором.

   > [!NOTE]
   > Не устанавливайте эту запись реестра, если вы предоставляете настраиваемые цветные элементы. Дополнительные сведения см. в разделе [Настраиваемые цветные элементы](../../extensibility/internals/custom-colorable-items.md).

## <a name="see-also"></a>См. также
- [Выделение синтаксиса в пользовательских редакторах](../../extensibility/syntax-coloring-in-custom-editors.md)
- [Выделение синтаксиса в языковой службе прежних версий](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)
- [Реализация цветового выделения синтаксиса](../../extensibility/internals/implementing-syntax-coloring.md)
- [Настраиваемые цветные элементы](../../extensibility/internals/custom-colorable-items.md)
- [Регистрация языковой службы прежних версий](../../extensibility/internals/registering-a-legacy-language-service2.md)
