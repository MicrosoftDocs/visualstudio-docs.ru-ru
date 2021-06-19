---
title: Изменение стандартной команды меню в DSL
description: Узнайте, как можно изменить поведение некоторых стандартных команд, определяемых автоматически в DSL.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- .vsct files, adding commands to a domain-specific language
- Domain-Specific Language, adding custom commands
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: ccbc82801c3570c74e96010d5f9fc0e0e7940937
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2021
ms.locfileid: "112387103"
---
# <a name="how-to-modify-a-standard-menu-command-in-a-domain-specific-language"></a>Практическое руководство. Изменение стандартной команды меню в доменном языке

Поведение некоторых стандартных команд, определенных в доменном языке автоматически, можно изменять. Например, можно изменить **вырезание** , чтобы исключить конфиденциальную информацию. Для этого необходимо переопределить методы в классе наборов команд. Эти классы определяются в файле CommandSet.cs проекта DslPackage project и являются производными от класса <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet>.

> [!NOTE]
> Если вы хотите создать собственные команды меню, см. раздел [как добавить команду в контекстное меню](../modeling/how-to-add-a-command-to-the-shortcut-menu.md).

## <a name="what-commands-can-you-modify"></a>Какие команды можно изменять?

### <a name="to-discover-what-commands-you-can-modify"></a>Поиск команд, доступных для изменения

1. В проекте `DslPackage` откройте `GeneratedCode\CommandSet.cs`. Этот файл C# можно найти в обозреватель решений в качестве дочернего элемента `CommandSet.tt` .

2. Найдите в этом файле классы, имена которых заканчиваются на " `CommandSet` ", например `Language1CommandSet` и `Language1ClipboardCommandSet` .

3. В каждом классе наборов команд введите "`override`" и пробел. IntelliSense отобразит список методов, которые можно переопределить. Каждая команда имеет пару методов, имена которых начинаются с "`ProcessOnStatus`" и "`ProcessOnMenu`".

4. Запомните, какой класс наборов команд содержит команду, подлежащую изменению.

5. Закройте файл без сохранения изменений.

    > [!NOTE]
    > Обычно генерируемые файлы не редактируются. При следующей генерации файлов все изменения будут утеряны.

## <a name="extend-the-appropriate-command-set-class"></a>Расширение соответствующего класса наборов команд

Создайте новый файл, содержащий частичное описание класса наборов команд.

### <a name="to-extend-the-command-set-class"></a>Расширение класса наборов команд

1. В Обозревателе решений в проекте DslPackage откройте папку GeneratedCode, найдите раздел CommandSet.tt и откройте созданный в нем файл CommandSet.cs. Запомните пространство имен и имя первого определенного здесь класса. Например:

     `namespace Company.Language1`

     `{ ...  internal partial class Language1CommandSet : ...`

2. В **DslPackage** создайте папку с именем **Пользовательский код**. В этой папке создайте новый файл класса с именем `CommandSet.cs` .

3. В новом файле напишите частичное объявление, используя то же пространство имен и имя, что и в созданном частичном классе. Пример.

    ```csharp
    using System;
    using System.Collections.Generic;
    using System.ComponentModel.Design;
    namespace Company.Language1 /* Make sure this is correct */
    { internal partial class Language1CommandSet { ...
    ```

    > [!NOTE]
    > Если для создания нового файла использовался шаблон файла класса, необходимо исправить как пространство имен, так и имя класса.

## <a name="override-the-command-methods"></a>Переопределение методов команд

У большинства команд есть два связанных метода: метод с именем, например `ProcessOnStatus` ... Определяет, должна ли команда быть видимой и включена. Она вызывается, когда пользователь щелкает схему правой кнопкой мыши, и должна выполняться быстро и не вносить изменений. `ProcessOnMenu`... вызывается, когда пользователь щелкает команду и выполняет функцию команды. Возможно, потребуется переопределение одного или двух этих методов.

### <a name="to-change-when-the-command-appears-on-a-menu"></a>Изменение условий отображения команды в меню

Переопределите ProcessOnStatus... Method. Он должен задавать свойства Visible и Enabled своего параметра MenuCommand. Обычно команда проверяет this.CurrentSelection, чтобы определить, применяется ли команда к выбранным элементам, а также может проверить их свойства, чтобы определить возможность применения команды в их текущем состоянии.

Как правило, свойство Visible должно определяться выбранными элементами. Свойство Enabled, определяющее цвет отображения команды в меню (черный или серый), должно зависеть от текущего состояния выделения.

В следующем примере элемент меню "Удалить" отключается, когда пользователь выбирает больше одной фигуры.

> [!NOTE]
> Этот метод не влияет на доступность команды при нажатии клавиши. Например, отключение элемента меню "Удалить" не запрещает вызов команды с помощью клавиши Delete.

```csharp
/// <summary>
/// Called when user right-clicks on the diagram or clicks the Edit menu.
/// </summary>
/// <param name="command">Set Visible and Enabled properties.</param>
protected override void ProcessOnStatusDeleteCommand (MenuCommand command)
{
  // Default settings from the base method.
  base.ProcessOnStatusDeleteCommand(command);
  if (this.CurrentSelection.Count > 1)
  {
    // If user has selected more than one item, Delete is greyed out.
    command.Enabled = false;
  }
}
```

Рекомендуется вначале вызвать базовый метод, чтобы обработать все случаи и настройки, которые вас не беспокоят.

Метод ProcessOnStatus не должен создавать, удалять или обновлять элементы в Магазине.

### <a name="to-change-the-behavior-of-the-command"></a>Изменение поведения команды

Переопределите Процессонмену... Method. В следующем примере код запрещает пользователю удалять больше одного элемента за один раз даже с помощью клавиши Delete.

```csharp
/// <summary>
/// Called when user presses Delete key
/// or clicks the Delete command on a menu.
/// </summary>
protected override void ProcessOnMenuDeleteCommand()
{
  // Allow users to delete only one thing at a time.
  if (this.CurrentSelection.Count <= 1)
  {
    base.ProcessOnMenuDeleteCommand();
  }
}
```

Если код вносит в Магазин такие изменения, как создание, удаление или обновление элементов и ссылок, необходимо делать это внутри транзакции. Дополнительные сведения см. [в разделе Создание и обновление элементов модели](../modeling/how-to-modify-a-standard-menu-command-in-a-domain-specific-language.md).

### <a name="write-the-code-of-the-methods"></a>Напишите код методов

В этих методах часто используются следующие фрагменты:

- `this.CurrentSelection`. Фигура, которую пользователь щелкает правой кнопкой мыши, всегда включается в этот список фигур и соединителей. Если пользователь щелкает пустую область схемы, схема становится единственным членом списка.

- `this.IsDiagramSelected()` - `true` значение, если пользователь щелкнул пустую часть диаграммы.

- `this.IsCurrentDiagramEmpty()`

- `this.IsSingleSelection()` — пользователь не выберет несколько фигур.

- `this.SingleSelection` — Фигура или схема, которую пользователь щелкнул правой кнопкой мыши

- `shape.ModelElement as MyLanguageElement` — элемент модели, представленный фигурой.

Дополнительные сведения о переходе от элемента к элементу и о создании объектов и ссылок см. [в разделе Навигация и обновление модели в программном коде](../modeling/navigating-and-updating-a-model-in-program-code.md).

## <a name="see-also"></a>См. также

- <xref:System.ComponentModel.Design.MenuCommand>
- [Написание кода для настройки доменного языка](../modeling/writing-code-to-customise-a-domain-specific-language.md)
- [Практическое руководство. Добавление команды в контекстное меню](../modeling/how-to-add-a-command-to-the-shortcut-menu.md)
- [Как добавить элементы пользовательского интерфейса с помощью пакетов VSPackage](../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Файлы таблицы команд Visual Studio (VSCT-файлы)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
- [Справочник по схемам XML VSCT](../extensibility/vsct-xml-schema-reference.md)
- [Образец схем VMSDK. Расширенная настройка DSL](https://code.msdn.microsoft.com/Visualization-Modeling-SDK-763778e8)
