---
title: Несколько доменных языков в одном решении
description: Узнайте, как можно упаковать несколько доменных языков (DSL) как часть одного решения, чтобы они были установлены вместе.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 11baf6439062e28c7361e2fabb4dea4a3430f237
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2021
ms.locfileid: "112390923"
---
# <a name="multiple-dsls-in-one-solution"></a>Несколько доменных языков в одном решении

Несколько доменных языков можно упаковать как часть единого решения, чтобы устанавливать их вместе.

Для интеграции нескольких доменных языков можно использовать различные технологии. Дополнительные сведения см. в статьях [Интеграция моделей с помощью Visual Studio ModelBus](../modeling/integrating-models-by-using-visual-studio-modelbus.md) и [инструкции: Добавление обработчика перетаскивания](../modeling/how-to-add-a-drag-and-drop-handler.md) и [Настройка поведения копирования](../modeling/customizing-copy-behavior.md).

## <a name="build-more-than-one-dsl-in-the-same-solution"></a>Создание более одного DSL в одном решении

1. Создание нового проекта **VSIX** .

2. Создайте два или более проекта DSL в каталоге решения VSIX.

   - Для каждого доменного языка откройте новый экземпляр в Visual Studio. Создайте новый доменный язык и укажите ту же папку решения, что и для решения VSIX.

   - Убедитесь, что каждый доменный язык создается с разным расширением имени файла.

   - Измените имена проектов **DSL** и **DslPackage** , чтобы они были разными. Примеры: `Dsl1`, `DslPackage1`, `Dsl2`, `DslPackage2`.

   - В каждом **DslPackage \* \ Source.extension.TT** измените эту строку на правильное имя проекта DSL:

      `string dslProjectName = "Dsl2";`

   - В решении VSIX добавьте проекты DSL * и DslPackage \* . Можно добавить каждую пару в отдельную папку решения.

2. Объедините манифесты VSIX доменных языков:

   1. Откройте _йоурвсикспрожект_**\саурце.екстенсион.манифест**.

   2. Для каждого DSL выберите **Добавить содержимое** и добавьте:

       - `Dsl*` проект как **компонент MEF**

       - `DslPackage*` проект как **компонент MEF**

       - `DslPackage*` проект как **пакет VS**

3. Создайте решение.

   Получившийся проект VSIX установит оба доменных языка. Их можно проверить с помощью клавиши F5 или развернуть _йоурвсикспрожект_**\bin\Debug \\ \* . VSIX**.

## <a name="see-also"></a>См. также

- [Интеграция моделей с помощью Visual Studio Modelbus](../modeling/integrating-models-by-using-visual-studio-modelbus.md)
- [Практическое руководство. Добавление обработчика перетаскивания](../modeling/how-to-add-a-drag-and-drop-handler.md)
- [Настройка функции копирования](../modeling/customizing-copy-behavior.md)