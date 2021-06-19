---
title: Customize code maps by editing the DGML files
description: Узнайте, как настроить карту кода путем редактирования файла. DGML на языке разметки графов.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- dependency graphs, creating path aliases
- dependency graphs, linking items to nodes
- graph documents, creating path aliases
- dependency graphs, grouping nodes
- graph documents, editing
- graph documents, linking items to nodes
- graph documents, customizing
- graph documentings, assigning categories and properties
- dependency graphs, editing
- dependency graphs, customizing
- graph documents, grouping nodes
- dependency graphs, assigning categories and properties
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 5b7c94834aeb6aa82efdb53dead97e26daa667c0
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2021
ms.locfileid: "112389492"
---
# <a name="customize-code-maps-by-editing-the-dgml-files"></a>Customize code maps by editing the DGML files

Чтобы настроить карту кода, можно изменить его файл на языке разметки (. DGML). Например, можно изменить элементы, чтобы указать пользовательские стили, назначить свойства и категории кодовым точкам и связям либо связать узлы с документы или URL-адреса с кодовыми точками или связями. Дополнительные сведения об элементах DGML см. в разделе [Справочник по языку для направляемых графов (DGML)](../modeling/directed-graph-markup-language-dgml-reference.md).

Измените DGML-файл карты кода в текстовом редакторе или редакторе XML. Если схема является частью решения Visual Studio, выберите ее в **Обозреватель решений**, откройте контекстное меню и выберите пункт **Открыть с помощью** **редактора XML (текстовый редактор)**.

> [!NOTE]
> Для создания карт кода необходимо иметь Visual Studio Enterprise Edition. Когда карта кода редактируется в Visual Studio, эта программа удаляет все неиспользуемые DGML-элементы и атрибуты при сохранении DGML-файла. Она также создает кодовые точки автоматически при добавлении новых связей вручную. При сохранении DGML-файла все атрибуты, добавляемые к элементу, могут самостоятельно упорядочиться в алфавитном порядке.

## <a name="group-code-elements"></a><a name="OrganizeNodes"></a> Элементы кода группы
 Можно добавить новые группы или преобразовать существующие узлы в группу.

1. Откройте DGML-файл в текстовом редакторе или редакторе XML.

2. Чтобы преобразовать кодовую точку в группу, найдите элемент `<Node/>` для этой кодовой точки.

    \- или -

    Чтобы добавить новую группу, найдите раздел `<Nodes>`. Добавьте новый элемент `<Node/>`.

3. В элементе `<Node/>` добавьте атрибут `Group`, чтобы указать разворачивать группу при отображении или нет. Пример.

   ```xml
   <Nodes>
      <Node Id="MyFirstGroup" Group="Expanded" />
      <Node Id="MySecondGroup" Group="Collapsed" />
   </Nodes>
   ```

4. В разделе `<Links>` убедитесь, что элемент `<Link/>` со следующими атрибутами существует для каждой связи между кодовой точкой группы и дочерними кодовыми точками:

   - Атрибут `Source`, который определяет кодовую точку группы

   - Атрибут `Target`, который определяет дочернюю кодовую точку

   - Атрибут `Category`, который определяет отношение `Contains` между кодовой точкой группы и ее дочерней кодовой точкой

     Пример.

   ```xml
   <Links>
      <Link Category="Contains" Source="MyFirstNewGroup" Target="FirstGroupChildOne" />
      <Link Category ="Contains" Source="MyFirstNewGroup" Target="FirstGroupChildTwo" />
      <Link Category ="Contains" Source="MySecondNewGroup" Target="SecondGroupChildOne" />
      <Link Category="Contains" Source="MySecondNewGroup" Target="SecondGroupChildTwo" />
   </Links>
   ```

    Дополнительные сведения об `Category` атрибуте см. в разделе [Назначение категорий элементам кода и ссылкам](#AssignCategories).

## <a name="change-the-style-of-the-map"></a><a name="ChangeGraphStyle"></a> Изменение стиля схемы
 Цвет фона и цвет границы карты можно изменить в DGML-файле. Сведения об изменении стиля элементов кода и ссылок см. в разделе [Изменение стиля элементов кода и ссылок](#Highlight).

1. Откройте DGML-файл в текстовом редакторе или редакторе XML.

2. В элементе `<DirectedGraph>` добавьте следующие атрибуты, чтобы изменить его стиль:

     Цвет фона

    ```xml
    Background="ColorNameOrHexadecimalValue"
    ```

     Цвет границ

    ```xml
    Stroke="StrokeValue"
    ```

     Пример.

    ```xml
    <DirectedGraph Background="Green" xmlns="http://schemas.microsoft.com/vs/2009/dgml" >
       ...
       ...
    </DirectedGraph>
    ```

## <a name="change-the-style-of-code-elements-and-links"></a><a name="Highlight"></a> Изменение стиля элементов кода и ссылок

### <a name="CreateCustomStyles"></a>
 Пользовательские стили можно применять к следующим кодовым точкам:

- Отдельные кодовые точки и связи

- Группы кодовых точек и связей

- Группы кодовых точек и связей на основании определенных условий

> [!TIP]
> При наличии повторяющихся стилей в большом числе кодовых точек и связей рекомендуется применить категорию к этим кодовым точкам и связям, а затем применить стиль к этой категории. Дополнительные сведения см. в разделах [Назначение категорий элементам кода и ссылки](#AssignCategories) и [Назначение свойств для элементов кода и ссылок](#AssignProperties).

##### <a name="to-apply-a-custom-style-to-a-single-code-element"></a>Применение пользовательского стиля к отдельной кодовой точке

1. Откройте DGML-файл в текстовом редакторе или редакторе XML.

2. Найдите элемент `<Node/>` кодовой точки. Добавьте любой из этих атрибутов, чтобы настроить его стиль:

     Цвет фона

    ```xml
    Background="ColorNameOrHexadecimalValue"
    ```

     Контур

    ```xml
    Stroke="ColorNameOrHexadecimalValue"
    ```

     Толщина контура

    ```xml
    StrokeThickness="StrokeValue"
    ```

     Цвет текста

    ```xml
    Foreground="ColorNameOrHexadecimalValue"
    ```

     Значок

    ```xml
    Icon="IconFilePathLocation"
    ```

     Размер текста

    ```xml
    FontSize="FontSizeValue"
    ```

     Тип текста

    ```xml
    FontFamily="FontFamilyName"
    ```

     Начертание шрифта

    ```xml
    FontWeight="FontWeightValue"
    ```

     Стиль текста

    ```xml
    FontStyle="FontStyleName"
    ```

     Например, можно назначить `Italic` в качестве стиля текста.

     Текстура

    ```xml
    Style="Glass"
    ```

     - или

    ```xml
    Style="Plain"
    ```

     Фигурная

     Чтобы заменить фигуру на значок, задайте для свойства `Shape` значение `None`, а для свойства `Icon` — путь к файлу значка.

    ```xml
    Shape="ShapeFilePathLocation"
    ```

     Пример.

    ```xml
    <Nodes>
       <Node Id="MyNode" Background="#FF008000" Stroke="#FF000000"
       Foreground="#FFFFFFFF" Icon="...\Icons\Globe.png"/>
    </Nodes>
    ```

##### <a name="to-apply-a-custom-style-to-a-single-link"></a>Применение пользовательского стиля к единичной ссылке

1. Откройте DGML-файл в текстовом редакторе или редакторе XML.

2. Найдите элемент `<Link/>`, содержащий имена исходной и целевой кодовых точек.

3. В элементе `<Link/>` добавьте следующие атрибуты, чтобы настроить его стиль:

     Цвет контура и наконечника стрелки

    ```xml
    Stroke="ColorNameOrHexadecimalValue"
    ```

     Толщина контура

    ```xml
    StrokeThickness="StrokeValue"
    ```

     Стиль контура

    ```xml
    StrokeDashArray="StrokeArrayValues"
    ```

     Пример.

    ```xml
    <Links>
       <Link Source="MyFirstNode" Target="MySecondNode" Background="Green" Stroke="#FF000000" StrokeDashArray="2,2"/>
    </Links>
    ```

##### <a name="to-apply-custom-styles-to-a-group-of-code-elements-or-links"></a>Применение пользовательских стилей к группе кодовых точек и связей

1. Откройте DGML-файл в текстовом редакторе или редакторе XML.

2. Если элемент `<Styles></Styles>` не существует, добавьте его под элементом `<DirectedGraph></DirectedGraph>` за элементом `<Links></Links>`.

3. В элементе `<Styles></Styles>` под элементом `<Style/>` и укажите следующие атрибуты:

   - `TargetType="Node` &#124; `Link | Graph"`

   - `GroupLabel="`*Намеинлежендбокс*`"`

   - `ValueLabel="`*Намеинстилепиккербокс*`"`

     Чтобы применить пользовательский стиль ко всем типам целевого объекта не следует использовать это условие.

##### <a name="to-apply-a-conditional-style-to-groups-of-code-elements-or-links"></a>Применение условного стиля к группам кодовых точек и связей

1. Откройте DGML-файл в текстовом редакторе или редакторе XML.

2. В элементе `<Style/>` добавьте элемент `<Condition/>`, который содержит атрибут `Expression`, чтобы указать выражение, возвращающее логическое значение.

    Пример.

   ```xml
   <Condition Expression="MyCategory"/>
   ```

    - или

   ```xml
   <Condition Expression="MyCategory > 100"/>
   ```

    - или

   ```xml
   <Condition Expression="HasCategory('MyCategory')"/>
   ```

    Это выражение использует следующий синтаксис "Формы Бэкуса-Наура" (BNF):

    \<Expression> :: = \<BinaryExpression> &#124; \<UnaryExpression> &#124; "(" \<Expression> ")" &#124; \<MemberBindings> &#124; \<Literal> &#124; \<Number>

    \<BinaryExpression>::= \<Expression> \<Operator>\<Expression>

    \<UnaryExpression> ::= "!" \<Expression> &#124; "+" \<Expression> &#124; "-" \<Expression>

    \<Operator> :: = "<" &#124; " \<=" &#124; "=" &#124; "> =" &#124; ">" &#124; "! =" &#124; "или" &#124; "и" &#124; "+" &#124; "*" &#124; "/" &#124; "-"

    \<MemberBindings> :: = \<MemberBindings> &#124; \<MemberBinding> "." \<MemberBinding>

    \<MemberBinding> :: = \<MethodCall> &#124; \<PropertyGet>

    \<MethodCall> ::= \<Identifier> "(" \<MethodArgs> ")"

    \<PropertyGet> :: = Идентификатор

    \<MethodArgs> :: = \<Expression> &#124; \<Expression> "," \<MethodArgs> &#124; \<empty>

    \<Identifier> ::= [^. ]*

    \<Literal> :: = строковый литерал с одинарным или двойным кавычками

    \<Number> :: = строка цифр с необязательной десятичной запятой

    Можно указать несколько `<Condition/>` элементов, которые должны иметь значение true, чтобы применить стиль.

3. В следующей строке после элемента `<Condition/>` добавьте один или несколько элементов `<Setter/>`, чтобы указать атрибут `Property` и фиксированный атрибут `Value` или вычисляемый атрибут `Expression`, чтобы применить к карте, кодовым точкам или связям, удовлетворяющим условию.

    Пример.

   ```xml
   <Setter Property="BackGround" Value="Green"/>
   ```

   Завершенным, простым примером является следующее условие, которое указывает, что кодовая точка отображается зеленым или красным цветом в зависимости от значения ее категории `Passed` — `True` или `False`:

```xml
<?xml version="1.0" encoding="utf-8"?>
<DirectedGraph xmlns="http://schemas.microsoft.com/vs/2009/dgml">
   <Nodes>
      <Node Id="MyFirstNode" Passed="True" />
      <Node Id="MySecondNode" Passed="False" />
   </Nodes>
   <Links>
   </Links>
   <Styles>
      <Style TargetType="Node" GroupLabel="Passed" ValueLabel="True">
         <Condition Expression="Passed='True'"/>
         <Setter Property="Background" Value="Green"/>
      </Style>
      <Style TargetType="Node" GroupLabel="Passed" ValueLabel="False">
         <Condition Expression="Passed='False'"/>
         <Setter Property="Background" Value="Red"/>
      </Style>
   </Styles>
</DirectedGraph>
```

 В следующей таблице приведены некоторые примеры используемых условий:

 Задайте размер шрифта в качестве функции количества строк кода, который также изменяет размер кодовой точки. В этом примере используется выражение с одним условием для задания нескольких свойств `FontSize` и `FontFamily`.

```xml
<?xml version="1.0" encoding="utf-8"?>
<DirectedGraph xmlns="http://schemas.microsoft.com/vs/2009/dgml">
<Nodes>
   <Node Id="Class1" LinesOfCode ="200" />
   <Node Id="Class2" LinesOfCode ="1000" />
   <Node Id="Class3" LinesOfCode ="20" />
</Nodes>
<Properties>
   <Property Id="LinesOfCode" Label="LinesOfCode" Description="LinesOfCode" DataType="System.Int32" />
</Properties>
<Styles>
   <Style TargetType="Node" GroupLabel="LinesOfCode" ValueLabel="Function">
      <Condition Expression="LinesOfCode > 0" />
      <Setter Property="FontSize" Expression="Math.Max(9,Math.Sqrt(LinesOfCode))" />
      <Setter Property="FontFamily" Value="Papyrus" />
   </Style>
</Styles>
</DirectedGraph>
```

 Задайте цвет фона кодовой точки на основании свойства `Coverage`. Стили выполняются в порядке их появления, аналогично операторам `if-else`.

 В данном примере:

1. Если `Coverage` имеет значение > 80, задайте `Background` для свойства значение Green.

2. Иначе `Coverage` , если имеет значение > 50, задайте `Background` для свойства оттенок оранжевый на основе значения `Coverage` Свойства.

3. В противном случае установите для свойства `Background` оттенок красного на основании значения свойства `Coverage`.

```xml
<?xml version="1.0" encoding="utf-8"?>
<DirectedGraph xmlns="http://schemas.microsoft.com/vs/2009/dgml">
<Nodes>
   <Node Id="Class1" Coverage="58" />
   <Node Id="Class2" Coverage="95" />
   <Node Id="Class3" Coverage="32" />
</Nodes>
<Properties>
   <Property Id="Coverage" Label="Coverage" Description="Code coverage as a percentage of blocks" DataType="Double" />
</Properties>
<Styles>
   <Style TargetType="Node" GroupLabel="Coverage" ValueLabel="Good">
      <Condition Expression="Coverage > 80" />
      <Setter Property="Background" Value="Green" />
   </Style>
   <Style TargetType="Node" GroupLabel="Coverage" ValueLabel="OK">
      <Condition Expression="Coverage > 50" />
      <Setter Property="Background" Expression="Color.FromRgb(180 * Math.Max(1, (80 - Coverage) / 30), 180, 0)" />
   </Style>
   <Style TargetType="Node" GroupLabel="Coverage" ValueLabel="Bad">
      <Setter Property="Background" Expression="Color.FromRgb(180, 180 * Coverage / 50, 0)" />
   </Style>
</Styles>
</DirectedGraph>
```

 Для свойства `Shape` установите значение `None`, чтобы значок изменил фигуру. С помощью свойства `Icon` можно задать расположение значка.

```xml
<DirectedGraph xmlns="http://schemas.microsoft.com/vs/2009/dgml">
<Nodes>
   <Node Id="Automation" Category="Test" Label="Automation" />
   <Node Id="C# Provider" Category="Provider" Label="C# Provider" />
</Nodes>
<Categories>
   <Category Id="Provider" Icon="...\Icons\Module.png" Shape="None" />
   <Category Id="Test" Icon="...\Icons\Page.png" Shape="None" />
</Categories>
<Properties>
   <Property Id="Icon" DataType="System.String" />
   <Property Id="Label" Label="Label" Description="Displayable label of an Annotatable object" DataType="System.String" />
   <Property Id="Shape" DataType="System.String" />
</Properties>
<Styles>
   <Style TargetType="Node" GroupLabel="Group" ValueLabel="Has category">
      <Condition Expression="HasCategory('Group')" />
      <Setter Property="Background" Value="#80008080" />
   </Style>
   <Style TargetType="Node">
      <Setter Property="HorizontalAlignment" Value="Center" />
   </Style>
</Styles>
</DirectedGraph>
```

## <a name="assign-properties-to-code-elements-and-links"></a><a name="AssignProperties"></a> Назначение свойств элементам кода и ссылкам
 Организовать кодовые точки и связи можно, назначив им свойства. Например, можно выбрать кодовые точки с определенными свойствами, чтобы можно было сгруппировать их, скрыть или изменить их стиль.

#### <a name="to-assign-a-property-to-a-code-element"></a>Присвоение свойства кодовой точке

1. Откройте DGML-файл в текстовом редакторе или редакторе XML.

2. Найдите элемент `<Node/>` для этой кодовой точки. Укажите имя свойства и его значение. Пример.

    ```xml
    <Nodes>
       <Node Id="MyNode" MyPropertyName="PropertyValue" />
    </Nodes>
    ```

3. Добавьте элемент `<Property/>` в раздел `<Properties>`, чтобы указать атрибуты, такие как видимое имя и тип данных:

    ```xml
    <Properties>
       <Property Id="MyPropertyName" Label="My Property" DataType="System.DataType"/>
    </Properties>
    ```

#### <a name="to-assign-a-property-to-a-link"></a>Присвоение свойства ссылке

1. Откройте DGML-файл в текстовом редакторе или редакторе XML.

2. Найдите элемент `<Link/>`, содержащий имена исходной и целевой кодовых точек.

3. В элементе `<Node/>` укажите имя свойства и его значение. Пример.

    ```xml
    <Links>
       <Link Source="MyFirstNode" Target="MySecondNode" MyPropertyName="PropertyValue" />
    </Links>
    ```

4. Добавьте элемент `<Property/>` в раздел `<Properties>`, чтобы указать атрибуты, такие как видимое имя и тип данных:

    ```xml
    <Properties>
       <Property Id="MyPropertyName" Label="My Property Name" DataType="System.DataType"/>
    </Properties>
    ```

## <a name="assign-categories-to-code-elements-and-links"></a><a name="AssignCategories"></a> Назначение категорий элементам кода и ссылкам
 В следующих разделах описано, как можно организовать кодовые точки, присвоив им категории, и как можно создать иерархические категории, которые помогут упорядочить кодовые точки и добавить атрибуты в дочерние категории с помощью наследования.

#### <a name="to-assign-a-category-to-a-code-element"></a>Присвоение категории кодовой точке

- Откройте DGML-файл в текстовом редакторе или редакторе XML.

- Найдите элемент `<Node/>` для нужной кодовой точки.

- В элементе `<Node/>` добавьте атрибут `Category`, чтобы указать имя категории. Пример.

    ```xml
    <Nodes>
       <Node Id="MyNode" Category="MyCategory" />
    </Nodes>
    ```

     Добавьте элемент `<Category/>` в раздел `<Categories>`, чтобы можно было воспользоваться атрибутом `Label` для определения отображения текста для категории:

    ```xml
    <Categories>
       <Category Id="MyCategory" Label="My Category" />
    </Categories>
    ```

#### <a name="to-assign-a-category-to-a-link"></a>Присвоение категории ссылке

1. Откройте DGML-файл в текстовом редакторе или редакторе XML.

2. Найдите элемент `<Link/>`, содержащий имена исходной и целевой кодовых точек.

3. В элементе `<Link/>` добавьте атрибут `Category`, чтобы указать имя категории. Пример.

    ```xml
    <Links>
       <Link Source="MyFirstNode" Target="MySecondNode" Category="MyCategory"
    </Links>
    ```

4. Добавьте элемент `<Category/>` в раздел `<Categories>`, чтобы можно было воспользоваться атрибутом `Label` для определения отображения текста для категории:

    ```xml
    <Categories>
       <Category Id="MyCategory" Label="My Category" />
    </Categories>
    ```

#### <a name="to-create-hierarchical-categories"></a>Создание иерархических категорий

1. Откройте DGML-файл в текстовом редакторе или редакторе XML.

2. Добавьте элемент `<Category/>` для родительской категории, затем добавьте атрибут `BasedOn` к элементу дочерней категории `<Category/>`.

     Пример.

    ```xml
    <Nodes>
       <Node Id="MyFirstNode" Label="My First Node" Category= "MyCategory" />
       <Node Id="MySecondNode" Label="My Second Node" />
    </Nodes>
    <Links>
       <Link Source="MyFirstNode" Target="MySecondNode" />
    </Links>
    <Categories>
       <Category Id="MyCategory" Label="My Category" BasedOn="MyParentCategory"/>
       <Category Id="MyParentCategory" Label="My Parent Category" Background="Green"/>
    </Categories>
    ```

     В этом примере фон `MyFirstNode` зеленый, так как его атрибут `Category` наследует атрибут `Background``MyParentCategory`.

## <a name="link-documents-or-urls-to-code-elements-and-links"></a><a name="AddReferences"></a> Связывание документов или URL-адресов с элементами кода и ссылками
 Чтобы связать документы или URL-адреса с кодовыми точками или связями, можно изменить DGML-файл карты и добавить атрибут `Reference` в элемент `<Node/>` для кодовой точки или элемент `<Link/>` для связи. Затем из этой кодовой точки или связи можно открывать и просматривать содержимое. Атрибут `Reference` задает путь к данному содержимому. Этот путь может относится к расположению DGML-файла или к абсолютному пути.

> [!CAUTION]
> При использовании относительных путей и перемещении DGML-файла в другое расположение эти пути становятся недопустимыми. При попытке открыть и просмотреть связанное содержимое отображается сообщение об ошибке, уведомляющее о том, что не удается просмотреть содержимое.

 Например, может потребоваться попробовать связать следующие кодовые точки:

- Чтобы описать изменения класса, можно связать URL-адрес рабочей кодовой точки, документа или другого DGML-файла с кодовой точкой для класса.

- Схему зависимостей можно связать с элементом кода группы, который представляет слой в логической архитектуре программного обеспечения.

- Схему компонентов можно связать с кодовой точкой интерфейса, чтобы показать больше сведений о компоненте, представляемом этим интерфейсом.

- Свяжите кодовую точку с рабочим элементом или ошибкой Team Foundation Server либо с другой информацией, касающейся этой кодовой точки.

#### <a name="to-link-a-document-or-url-to-a-code-element"></a>Связывание документа или URL-адреса с кодовой точкой

1. Откройте DGML-файл в текстовом редакторе или редакторе XML.

2. Найдите элемент `<Node/>` для нужной кодовой точки.

3. Выполните одну из задач, представленных в следующей таблице:

    Отдельная кодовая точка

   - В элементе `<Node/>` или `<Link/>` добавьте атрибут `Reference`, чтобы указать расположение кодовой точки.

     > [!NOTE]
     > У элемента может быть только один атрибут `Reference`.

     Пример.

   ```xml
   <Nodes>
      <Node Id="MyNode" Reference="MyDocument.txt" />
   </Nodes>
   <Properties>
      <Property Id="Reference" Label="My Document" DataType="System.String" IsReference="True" />
   </Properties>
   ```

    Несколько кодовых точек

   1. В элементе `<Node/>` или `<Link/>` добавьте новый атрибут, чтобы указать расположение каждой ссылки.

   2. В разделе `<Properties>`:

      1. Добавьте элемент `<Property/>` для каждого нового типа ссылки.

      2. Присвойте атрибуту `Id` имя нового атрибута ссылки.

      3. Добавьте `IsReference` атрибут и задайте для него значение, `True` чтобы ссылка отображалась в контекстном меню **перехода** к элементу кода.

      4. Используйте `Label` атрибут, чтобы указать отображаемый текст в контекстном меню **Перейти к ссылке** на элемент кода.

      Пример.

   ```xml
   <Nodes>
      <Node Id="MyNode" SequenceDiagram="MySequenceDiagram.sequencediagram" ActiveBugs="MyActiveBugs.wiq"/>
   </Nodes>
   <Properties>
      <Property Id="SequenceDiagram" Label="My Sequence Diagram" DataType="System.String" IsReference="True" />
      <Property Id="ActiveBugs" Label="Active Bugs" DataType="System.String" IsReference="True" />
   </Properties>
   ```

    На карте имя кодовой точки отображается подчеркнутым. При открытии контекстного меню для элемента кода или ссылки отображается контекстное меню **Перейти к ссылке** , содержащее связанные элементы кода, которые вы хотите выбрать.

4. Воспользуйтесь атрибутом `ReferenceTemplate`, чтобы указать общую строку, такую как URL-адрес, используемую несколькими ссылками, вместо повторения этой строки в ссылке.

    Атрибут `ReferenceTemplate` указывает заполнитель для значения ссылки. В следующем примере заполнитель `{0}` в атрибуте `ReferenceTemplate` будет заменен значениями атрибутов `MyFirstReference` и `MySecondReference` в элементе `<Node/>` для получения полного пути:

   ```xml
   <Nodes>
      <Node Id="MyNode" MyFirstReference="MyFirstDocument" MySecondReference="MySecondDocument"/>
      <Node Id="MySecondNode" MyFirstReference="AnotherFirstDocument" MySecondReference="AnotherSecondDocument"/>
   </Nodes>
   <Properties>
      <Property Id="MyFirstReference" Label="My First Document" DataType="System.String" IsReference="True" ReferenceTemplate="http://www.Fabrikam.com/FirstDocuments/{0}.asp"/>
      <Property Id="MySecondReference" Label="My Second Document" DataType="System.String" IsReference="True" ReferenceTemplate=" http://www.Fabrikam.com/SecondDocuments/{0}.asp"/>
   </Properties>
   ```

5. Чтобы просмотреть кодовую точку, на которую указывает ссылка, или кодовые точки на карте, откройте контекстное меню кодовой точки или связи. Выберите **Переход к ссылке** , а затем элемент Code.

## <a name="see-also"></a>См. также

- [Сопоставление зависимостей во всех решениях](../modeling/map-dependencies-across-your-solutions.md)
- [Использование карт кода для отладки приложений](../modeling/use-code-maps-to-debug-your-applications.md)
- [Поиск потенциальных проблем с помощью анализаторов карт кода](../modeling/find-potential-problems-using-code-map-analyzers.md)
- [Просмотр и реорганизация карт кода](../modeling/browse-and-rearrange-code-maps.md)
- [Справочник по языку DGML](../modeling/directed-graph-markup-language-dgml-reference.md)
