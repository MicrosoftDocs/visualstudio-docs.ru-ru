---
title: Как добавить команду в контекстное меню
description: Узнайте, как добавлять команды меню на доменный язык (DSL), чтобы пользователи могли выполнять задачи, характерные для вашего DSL.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- Domain-Specific Language Tools, walkthroughs
- walkthroughs [Domain-Specific Language Tools]
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 4b578c949b3b5121eb90b2c034766ea15ae6d096
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2021
ms.locfileid: "112386570"
---
# <a name="how-to-add-a-command-to-the-shortcut-menu"></a>Как добавить команду в контекстное меню

Чтобы пользователи могли выполнять задачи, характерные для вашего доменного языка (DSL), можно добавить в него команды меню. Команды отображаются в контекстном меню, когда пользователь нажимает схему правой кнопкой мыши. Команду можно настроить таким образом, чтобы она появлялась в меню только при определенных обстоятельствах. Например, можно сделать команду видимой, только когда пользователь выбирает определенные типы элементов или элементы в определенных состояниях.

В сводке действия выполняются в проекте DslPackage следующим образом:

1. [Объявите команду в командах Commands. vsct](#VSCT)

2. [Обновите номер версии пакета в Package.TT](#version). (Это действие выполняется при любом изменении файла Commands.vsct.)

3. [Напишите методы в классе командного метода](#CommandSet) , чтобы сделать команду видимой, и определить, что должна делать команда.

> [!NOTE]
> Также можно изменить поведение некоторых существующих команд, например "Вырезать", "Вставить", "Выбрать все" и "Печать", переопределив соответствующие методы в CommandSet.cs. Дополнительные сведения см. [в разделе инструкции. Изменение стандартной команды меню](../modeling/how-to-modify-a-standard-menu-command-in-a-domain-specific-language.md).

## <a name="define-a-command-using-mef"></a>Определение команды с помощью MEF

MEF (Managed Extension Framework) предлагает альтернативный метод определения команд в меню схемы. Его основная задача — включение доменного языка для расширения вами или другими сторонами. Пользователи могут выбрать установить только DSL или DSL и расширения. Кроме того, MEF уменьшает объем работы по определению команд контекстного меню после выполнения начальной работы по включению MEF в DSL.

Используйте метод, описанный в этом разделе, если:

1. вы хотите определить команды меню или других меню, кроме контекстного (вызываемого щелчком правой кнопки мыши);

2. вы хотите настроить определенные группы команд в меню;

3. вы не хотите разрешать другим пользователям добавлять в DSL их собственные команды;

4. вы хотите определить только одну команду.

   В остальных случаях используйте для определения команд метод MEF. Дополнительные сведения см. в статье [расширение возможностей DSL с помощью MEF](../modeling/extend-your-dsl-by-using-mef.md).

## <a name="declare-the-command-in-commandsvsct"></a><a name="VSCT"></a> Объявите команду в командах Commands. vsct
 Команды меню объявляются в файле DslPackage\Commands.vsct. Эти определения указывают на метки элементов меню и место их отображения в меню.

 Файл, который вы изменяете, Commands. vsct, импортирует определения из нескольких h файлов, которые находятся в каталоге *установки пакета SDK для Visual Studio*\висуалстудиоинтегратион\коммон\инк. Он также включает Женератедвскт. vsct, который создается из определения DSL.

 Дополнительные сведения о vsct-файлах см. в разделе [Командная таблица Visual Studio (. Vsct) файлы](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).

### <a name="to-add-the-command"></a>Добавление команды

1. В **Обозреватель решений** в проекте **DslPackage** откройте команды. vsct.

2. В элементе `Commands` определите одну или несколько кнопок и группу. *Кнопка* — это элемент меню. *Группа* — это раздел в меню. Чтобы определить эти элементы, добавьте следующий код:

    ```xml
    <!-- Define a group - a section in the menu -->
    <Groups>
      <Group guid="guidCustomMenuCmdSet" id="grpidMyMenuGroup" priority="0x0100">
        <!-- These symbols are defined in GeneratedVSCT.vsct -->
        <Parent guid="guidCmdSet" id="menuidContext" />
      </Group>
    </Groups>
    <!-- Define a button - a menu item - inside the Group -->
    <Buttons>
      <Button guid="guidCustomMenuCmdSet" id="cmdidMyContextMenuCommand"
        priority="0x0100" type="Button">
        <Parent guid="guidCustomMenuCmdSet" id="grpidMyMenuGroup"/>
        <!-- If you do not want to place the command in your own Group,
             use Parent guid="guidCmdSet" id="grpidContextMain".
             These symbols are defined in GeneratedVSCT.vsct -->
        <CommandFlag>DynamicVisibility</CommandFlag>
        <Strings>
          <ButtonText>My Context Menu Command</ButtonText>
        </Strings>
      </Button>
    </Buttons>
    ```

    > [!NOTE]
    > Каждая кнопка или группа идентифицируются по GUID и целочисленному идентификатору. Один и тот же GUID можно использовать при создании различных групп и кнопок, но при этом у них должны быть разные идентификаторы. Имена GUID и ИДЕНТИФИКАТОРы преобразуются в фактические идентификаторы GUID и числовые идентификаторы в `<Symbols>` узле.

3. Чтобы она загружалась только в контексте вашего доменного языка, добавьте для нее ограничение видимости. Дополнительные сведения см. в разделе [элемент висибилитиконстраинтс](../extensibility/visibilityconstraints-element.md).

     Для этого добавьте в элемент `CommandTable` после элемента `Commands` следующий код:

    ```xml
    <VisibilityConstraints>
      <!-- Ensures the command is only loaded for this DSL -->
      <VisibilityItem guid="guidCustomMenuCmdSet" id="cmdidMyContextMenuCommand"
        context="guidEditor"/>
    </VisibilityConstraints>
    ```

4. Определите имена, которые использовались для идентификаторов GUID и идентификаторов. Для этого добавьте `Symbols` в элемент `CommandTable` после элемента `Commands` следующий код:

    ```xml
    <Symbols>
      <!-- Substitute a unique GUID for the placeholder: -->
      <GuidSymbol name="guidCustomMenuCmdSet"
        value="{00000000-0000-0000-0000-000000000000}" >
        <IDSymbol name="grpidMyMenuGroup" value="0x01001"/>
        <IDSymbol name="cmdidMyContextMenuCommand" value="0x00001"/>
      </GuidSymbol>
    </Symbols>
    ```

5. Замените `{000...000}` на GUID, идентифицирующий группы и элементы меню. Чтобы получить новый идентификатор GUID, используйте средство **создания GUID** в меню **Сервис** .

    > [!NOTE]
    > Если вы хотите добавить сразу несколько групп или элементов меню, можно использовать один и тот же GUID. При этом необходимо использовать новые значения для `IDSymbols`.

6. В скопированном из данной процедуры коде замените собственными строками каждое вхождение следующих строк:

    - `grpidMyMenuGroup`

    - `cmdidMyContextMenuCommand`

    - `guidCustomMenuCmdSet`

    - `My Context Menu Command`

## <a name="update-the-package-version-in-packagett"></a><a name="version"></a> Обновление версии пакета в Package.tt
 При добавлении или изменении команды обновляйте параметр `version`<xref:Microsoft.VisualStudio.Shell.ProvideMenuResourceAttribute>, который применяется к классу пакета перед выпуском новой версии доменного языка.

 Поскольку класс пакета определяется в созданном классе, обновите атрибут в файле текстового шаблона, из которого создается файл Package.cs.

### <a name="to-update-the-packagett-file"></a>Обновление файла Package.tt

1. В **Обозреватель решений** в проекте **DslPackage** в папке **GeneratedCode** откройте файл Package.tt.

2. Найдите элемент `ProvideMenuResource`.

3. Увеличьте параметр `version` атрибута, который является вторым параметром. При необходимости можно написать имя параметра, прямо указывающее на его назначение. Пример.

     `[VSShell::ProvideMenuResource("1000.ctmenu", version: 2 )]`

## <a name="define-the-behavior-of-the-command"></a><a name="CommandSet"></a> Определение поведения команды

В доменном языке уже имеются некоторые команды, внедренные в разделяемый класс, который был объявлен в файле DslPackage\GeneratedCode\CommandSet.cs. Чтобы добавить новые команды, необходимо расширить этот класс, создав новый файл с частичным объявлением того же класса. Обычно используется имя класса *\<YourDslName>* `CommandSet` . Полезно начать с проверки имени класса и проверки его содержимого.

Класс набора команд производится из <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet>.

### <a name="extend-the-commandset-class"></a>Расширение класса команд

1. В Обозревателе решений в проекте DslPackage откройте папку GeneratedCode, найдите раздел CommandSet.tt и откройте созданный в нем файл CommandSet.cs. Запомните пространство имен и имя первого определенного здесь класса. Например:

     `namespace Company.Language1`

     `{ ...  internal partial class Language1CommandSet : ...`

2. В **DslPackage** создайте папку с именем **Пользовательский код**. В этой папке создайте новый файл класса с именем `CommandSet.cs` .

3. В новом файле напишите частичное объявление, используя то же пространство имен и имя, что и в созданном частичном классе. Пример.

     `namespace Company.Language1 /* Make sure this is correct */`

     `{ internal partial class Language1CommandSet { ...`

     > [!NOTE]
     > Если для создания нового файла использовался шаблон класса, необходимо исправить как пространство имен, так и имя класса.

Код наборов команд обычно требуется для импорта следующих пространств имен:

```csharp
using System;
using System.Collections.Generic;
using System.ComponentModel.Design;
using System.Linq;
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Diagrams;
using Microsoft.VisualStudio.Modeling.Shell;
```

Исправьте пространство имен и имя класса в соответствии с созданным файлом CommandSet.cs:

```csharp
namespace Company.Language1 /* Make sure this is correct */
{
  // Same class as the generated class.
  internal partial class Language1CommandSet
  {
```

Необходимо определить два метода: один, чтобы определить, когда команда будет видна в контекстном меню правой кнопкой мыши, а другая — для выполнения команды. Эти методы не переопределяются. Наоборот, их нужно зарегистрировать в списке команд.

### <a name="define-when-the-command-will-be-visible"></a>Определение условий для отображения команды
 Для каждой команды Определите `OnStatus...` метод, который определяет, будет ли команда отображаться в меню и будет ли она включена или серым цветом. Задайте `Visible` Свойства и `Enabled` для `MenuCommand` , как показано в следующем примере. Этот метод вызывается для создания контекстного меню каждый раз, когда пользователь щелкает схему правой кнопкой мыши, поэтому должен работать быстро.

 В данном примере команда отображается, только когда пользователь выбирает определенный тип фигуры, и включается, только когда хотя бы один из выбранных элементов находится в определенном состоянии. Пример основан на шаблоне схем классов доменного языка, а типы ClassShape и ModelClass определяются в доменном языке.

```csharp
private void OnStatusMyContextMenuCommand(object sender, EventArgs e)
{
  MenuCommand command = sender as MenuCommand;
  command.Visible = command.Enabled = false;
  foreach (object selectedObject in this.CurrentSelection)
  {
    ClassShape shape = selectedObject as ClassShape;
    if (shape != null)
    {
      // Visibility depends on what is selected.
      command.Visible = true;
      ModelClass element = shape.ModelElement as ModelClass;
      // Enabled depends on state of selection.
      if (element != null && element.Comments.Count == 0)
      {
        command.Enabled = true;
        return; // seen enough
} } } }
```

Следующие фрагменты часто используются в методах OnStatus:

- `this.CurrentSelection`. Фигура, которую пользователь щелкает правой кнопкой мыши, всегда включается в этот список. Если пользователь щелкает пустую область схемы, схема становится единственным членом списка.

- `this.IsDiagramSelected()` - `true` значение, если пользователь щелкнул пустую часть диаграммы.

- `this.IsCurrentDiagramEmpty()`

- `this.IsSingleSelection()` — пользователь не выберет несколько объектов

- `this.SingleSelection` — Фигура или схема, которую пользователь щелкнул правой кнопкой мыши

- `shape.ModelElement as MyLanguageElement` — элемент модели, представленный фигурой.

Как правило, свойство `Visible` должно определяться выбранным параметром, а свойство `Enabled` — состоянием выбранных элементов.

Метод OnStatus не должен менять состояние Магазина.

### <a name="define-what-the-command-does"></a>Определение действий команды
 Для каждой команды определите метод `OnMenu...`, выполняющий необходимое действие при выборе этой команды в меню.

 Если изменения вносятся в элементы моделей, необходимо делать это внутри транзакции. Дополнительные сведения см. [в разделе инструкции. Изменение стандартной команды меню](../modeling/how-to-modify-a-standard-menu-command-in-a-domain-specific-language.md).

 В данном примере типы `ClassShape`, `ModelClass` и `Comment` определяются в доменном языке, который производится из шаблона схем классов DSL.

```csharp
private void OnMenuMyContextMenuCommand(object sender, EventArgs e)
{
  MenuCommand command = sender as MenuCommand;
  Store store = this.CurrentDocData.Store;
  // Changes to elements and shapes must be performed in a Transaction.
  using (Transaction transaction =
       store.TransactionManager.BeginTransaction("My command"))
  {
    foreach (object selectedObject in this.CurrentSelection)
    {
      // ClassShape is defined in my DSL.
      ClassShape shape = selectedObject as ClassShape;
      if (shape != null)
      {
        // ModelClass is defined in my DSL.
        ModelClass element = shape.ModelElement as ModelClass;
        if (element != null)
        {
          // Do required action here - for example:

          // Create a new element. Comment is defined in my DSL.
          Comment newComment = new Comment(element.Partition);
          // Every element must be the target of an embedding link.
          element.ModelRoot.Comments.Add(newComment);
          // Set properties of new element.
          newComment.Text = "This is a comment";
          // Create a reference link to existing object.
          element.Comments.Add(newComment);
        }
      }
    }
    transaction.Commit(); // Don't forget this!
  }
}
```

 Дополнительные сведения о переходе от объекта к объекту в модели и о создании объектов и ссылок см. в разделе [как изменить стандартную команду меню](../modeling/how-to-modify-a-standard-menu-command-in-a-domain-specific-language.md).

### <a name="register-the-command"></a>Регистрация команды
 Повторите в C# объявления значений GUID и идентификаторов, которые были сделаны в разделе "Символы" CommandSet.vsct:

```csharp
private Guid guidCustomMenuCmdSet =
    new Guid("00000000-0000-0000-0000-000000000000");
private const int grpidMyMenuGroup = 0x01001;
private const int cmdidMyContextMenuCommand = 1;
```

 Используйте то же значение GUID, которое было вставлено в **Commands. vsct**.

> [!NOTE]
> В случае изменений в разделе "Символы" VSCT-файла для сопоставления нужно будет также изменить эти объявления. Кроме того, необходимо увеличить номер версии в Package.tt

 Зарегистрируйте команды меню как часть данного набора команд. `GetMenuCommands()` вызывается один раз при инициализации схемы:

```csharp
protected override IList<MenuCommand> GetMenuCommands()
{
  // Get the list of generated commands.
  IList<MenuCommand> commands = base.GetMenuCommands();
  // Add a custom command:
  DynamicStatusMenuCommand myContextMenuCommand =
    new DynamicStatusMenuCommand(
      new EventHandler(OnStatusMyContextMenuCommand),
      new EventHandler(OnMenuMyContextMenuCommand),
      new CommandID(guidCustomMenuCmdSet, cmdidMyContextMenuCommand));
  commands.Add(myContextMenuCommand);
  // Add more commands here.
  return commands;
}
```

## <a name="test-the-command"></a>Тестирование команды
 Постройте и запустите доменный язык в экспериментальном экземпляре Visual Studio. Команда должна отображаться в контекстном меню в указанных вами ситуациях.

### <a name="to-exercise-the-command"></a>Выполнение команды

1. На панели инструментов **Обозреватель решений** нажмите кнопку **преобразовать все шаблоны**.

2. Нажмите клавишу **F5** , чтобы перестроить решение, и начните отладку предметно-ориентированного языка в экспериментальной сборке.

3. В экспериментальном построении откройте пример схемы.

4. Щелкните несколько элементов в схеме правой кнопкой мыши, чтобы проверить, правильно ли включается и отключается команда, а также правильно ли работает ее отображение или скрытие в зависимости от выбранного элемента.

## <a name="troubleshoot"></a>Диагностика

**Команда не отображается в меню.**

- Пока вы не установите пакет доменного языка, команда будет отображаться только в экземплярах отладки Visual Studio. Дополнительные сведения см. в разделе [Развертывание решения на предметно-ориентированном языке](msi-and-vsix-deployment-of-a-dsl.md).

- Убедитесь, что экспериментальный язык имеет правильное расширение имени файла для этого доменного языка. Чтобы проверить расширение имени файла, откройте DslDefinition.dsl в основном экземпляре Visual Studio. Затем в Обозревателе DSL щелкните узел "Редактор" правой кнопкой мыши и выберите "Свойства". В окне "Свойства" проверьте свойство FileExtension.

- Вы [увеличили номер версии пакета](#version)?

- Установите точку останова в начале метода OnStatus. Он должен останавливаться при щелчке правой кнопкой мыши по любой части схемы.

**Метод OnStatus не вызывается**:

- Убедитесь, что GUID и идентификаторы в коде CommandSet совпадают с идентификаторами в разделе "Символы" файла Commands.vsct.

- В файле Commands.vsct убедитесь, что GUID и идентификаторы в каждом родительском узле указывают на правильную родительскую группу.

- В командной строке Visual Studio введите devenv /rootsuffix exp /setup. Затем перезапустите экземпляр отладки Visual Studio.

- Выполните метод OnStatus и убедитесь, что command.Visible и command.Enabled имеют значение true.

**Отображается неправильный текст меню, или команда отображается в неправильном месте**:

- Убедитесь, что комбинация GUID и идентификатора уникальна для данной команды.

- Убедитесь, что более ранние версии пакета удалены.

## <a name="see-also"></a>См. также

- [Написание кода для настройки предметно-ориентированного языка](../modeling/writing-code-to-customise-a-domain-specific-language.md)
- [Как изменить стандартную команду меню](../modeling/how-to-modify-a-standard-menu-command-in-a-domain-specific-language.md)
- [Развертывание решений на предметно-ориентированном языке](msi-and-vsix-deployment-of-a-dsl.md)
- [Пример кода: схемы цепи](https://code.msdn.microsoft.com/Visualization-Modeling-SDK-763778e8)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]
