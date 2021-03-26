---
title: Managed Extensibility Framework в редакторе | Документация Майкрософт
description: Сведения о Managed Extensibility Framework, позволяющем создавать собственные компоненты для расширения редактора в пакете SDK для Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - using MEF for extensions
ms.assetid: 3f59a285-6c33-4ae3-a4fb-ec1f5aa21bd1
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 881b0f4d112b7739ff33099b26a30ab073f55924
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105073174"
---
# <a name="managed-extensibility-framework-in-the-editor"></a>Managed Extensibility Framework в редакторе
Редактор строится с помощью компонентов Managed Extensibility Framework (MEF). Вы можете создавать собственные компоненты MEF для расширения редактора, а код может также использовать компоненты редактора.

## <a name="overview-of-the-managed-extensibility-framework"></a>Общие сведения о Managed Extensibility Framework
 MEF — это библиотека .NET, которая позволяет добавлять и изменять компоненты приложения или компонента, которые следуют за моделью программирования MEF. Редактор Visual Studio может предоставлять и использовать компоненты MEF.

 MEF содержится в сборке платформа .NET Framework версии 4 *System.ComponentModel.Composition.dll* .

 Дополнительные сведения о MEF см. в разделе [Managed Extensibility Framework (MEF)](/dotnet/framework/mef/index).

### <a name="component-parts-and-composition-containers"></a>Части компонентов и контейнеры композиции
 Часть компонента — это класс или член класса, который может выполнять одно (или оба) из следующих действий:

- Использование другого компонента

- Использовать другим компонентом

  Например, рассмотрим приложение для покупок, которое имеет компонент записи заказа, зависящий от данных о доступности продукта, предоставляемых компонентом складских запасов. В терминах MEF компонент инвентаризации может *экспортировать* данные о доступности продуктов, а часть заказа может *импортировать* данные. Часть записи заказа и часть инвентаризации не должны быть осведомлены о них. *контейнер композиции* (предоставляемый ведущим приложением) отвечает за поддержание набора экспортов и разрешение экспорта и импорта.

  Контейнер композиции, <xref:System.ComponentModel.Composition.Hosting.CompositionContainer> как правило, принадлежит узлу. Контейнер композиции хранит *Каталог* экспортированных частей компонентов.

### <a name="export-and-import-component-parts"></a>Экспорт и импорт частей компонентов
 Можно экспортировать любую функциональность, если она реализована как открытый класс или открытый член класса (свойство или метод). Не требуется создавать часть компонента из <xref:System.ComponentModel.Composition.Primitives.ComposablePart> . Вместо этого необходимо добавить <xref:System.ComponentModel.Composition.ExportAttribute> атрибут в класс или член класса, который требуется экспортировать. Этот атрибут указывает *контракт* , по которому другая часть компонента может импортировать ваши функции.

### <a name="the-export-contract"></a>Экспортный контракт
 <xref:System.ComponentModel.Composition.ExportAttribute>Определяет сущность (класс, интерфейс или структуру), которые экспортируются. Как правило, атрибут Export принимает параметр, указывающий тип экспорта.

```
[Export(typeof(ContentTypeDefinition))]
class TestContentTypeDefinition : ContentTypeDefinition {   }
```

 По умолчанию <xref:System.ComponentModel.Composition.ExportAttribute> атрибут определяет контракт, который является типом экспортируемого класса.

```
[Export]
[Name("Structure")]
[Order(After = "Selection", Before = "Text")]
class TestAdornmentLayerDefinition : AdornmentLayerDefinition {   }
```

 В этом примере атрибут по умолчанию `[Export]` эквивалентен `[Export(typeof(TestAdornmentLayerDefinition))]` .

 Можно также экспортировать свойство или метод, как показано в следующем примере.

```
[Export]
[Name("Scarlet")]
[Order(After = "Selection", Before = "Text")]
public AdornmentLayerDefinition scarletLayerDefinition;
```

### <a name="import-a-mef-export"></a>Импорт экспорта MEF
 Если требуется использовать экспорт MEF, необходимо получить сведения о контракте (обычно это тип), по которому он был экспортирован, и добавить <xref:System.ComponentModel.Composition.ImportAttribute> атрибут, имеющий это значение. По умолчанию атрибут import принимает один параметр, который является типом класса, который он изменяет. Следующие строки кода импортируют <xref:Microsoft.VisualStudio.Text.Classification.IClassificationTypeRegistryService> тип.

```
[Import]
internal IClassificationTypeRegistryService ClassificationRegistry;
```

## <a name="get-editor-functionality-from-a-mef-component-part"></a>Получение функциональных возможностей редактора из части компонента MEF
 Если существующий код является частью компонента MEF, можно использовать метаданные MEF для использования частей компонента редактора.

#### <a name="to-consume-editor-functionality-from-a-mef-component-part"></a>Использование функциональных возможностей редактора из части компонента MEF

1. Добавьте ссылки на *System.Composition.ComponentModel.dll*, которые находятся в глобальном кэше сборок (GAC), и в сборки редактора.

2. Добавьте соответствующие директивы using.

    ```
    using System.ComponentModel.Composition;
    using Microsoft.VisualStudio.Text;
    ```

3. Добавьте `[Import]` атрибут в интерфейс службы, как показано ниже.

    ```
    [Import]
    ITextBufferFactoryService textBufferService;
    ```

4. После получения службы можно использовать любой из ее компонентов.

5. После компиляции сборки вставьте ее в *.. \* Папка \Common7\IDE\Components установки Visual Studio.

## <a name="see-also"></a>См. также
- [Точки расширения языковой службы и редактора](../extensibility/language-service-and-editor-extension-points.md)
