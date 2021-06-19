---
title: Настройка полей с текстом и изображениями
description: Сведения о настройке текстовых и графических файлов. Также изучите, что при определении декоратора текста в фигуре оно представлено объектом TextField.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: f52c4deda5b934a9b55c5ecfeec95ca633edf15e
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2021
ms.locfileid: "112389271"
---
# <a name="customizing-text-and-image-fields"></a>Настройка полей с текстом и изображениями
При определении декоратора текста в фигуре он представляется объектом TextField. Примеры инициализации TextField и других ShapeFields см. в подсистеме Дсл\женератедкоде\шапес.КС в решении DSL.

 TextField — это объект, управляющий областью внутри фигуры, например пространство, назначенное метке. Один экземпляр TextField совместно используется многими фигурами одного класса. Экземпляр TextField не сохраняет текст метки отдельно для каждого экземпляра: вместо этого `GetDisplayText(ShapeElement)` метод принимает форму в качестве параметра и может выполнять поиск текста, зависящего от текущего состояния фигуры и ее элемента модели.

## <a name="how-the-appearance-of-a-text-field-is-determined"></a>Как определяется внешний вид текстового поля
 `DoPaint()`Метод вызывается для отображения поля на экране. Можно либо переопределить значение по умолчанию, `DoPaint(),` либо переопределить некоторые методы, которые он вызывает. Следующая упрощенная версия методов по умолчанию может помочь вам понять, как переопределить поведение по умолчанию.

```csharp
// Simplified version:
public override void DoPaint(DiagramPaintEventArgs e, ShapeElement parentShape)
{
  string text = GetDisplayText(shape);
  StringFormat format = GetStringFormat(parentShape);
  Brush brush = GetTextBrush(e.View, shape);
  using (Font font = GetFont(shape))
  {
    e.Graphics.DrawString(text, font, brush, format);
  }
}
// StringFormat determines whether the string is centered etc.
// To customize statically for all instances of this shape field,
// assign to DefaultStringFormat.
// To customize dynamically or per shape, override this:
public virtual StringFormat GetStringFormat(ShapeElement shape)
{ return DefaultStringFormat; }

// Override to customize the displayed string:
public virtual string GetDisplayText(ShapeElement shape)
{ return this.GetValue(shape).ToString(); }

// Brush determines the text color.
// To change the brush for every field, change the shape's styleset.
// To customize to a brush in the style set, override GetTextBrushId.
// To change the brush to non-standard color, override this.
// Should take account of whether selected.
public virtual Brush GetTextBrush(DiagramClientView view, ShapeElement shape)
{ return shape.StyleSet.GetBrush(this.GetTextBrushId(view, shape)); }

// Brush ID selects a brush from a StyleSet.
// Either return a member of DiagramBrushes
// or add your own brush to the shape or application's styleset.
// Override this to change dynamically or per instance.
// To change statically, just assign to default values.
public virtual StyleSetResourceId GetTextBrushId(DiagramClientView view, ShapeElement shape)
{ return IsSelected(view, shape) ? (view.Focused ? DefaultSelectedTextBrushId
: DefaultInactiveSelectedTextBrushId ) : DefaultTextBrushId ;
}

// Font determines the shape and size of the text.
// To change the font for every field, change the shape's styleset.
// To customize to a font in the style set, override GetFontId.
// To change the font to a non-standard font, override this.
public virtual Font GetFont(ShapeElement shape)
{ return shape.StyleSet.GetFont(GetFontId(shape)); }

// Selects a font from a styleset.
// Either return a member of DiagramFonts or
// add your own font to the shape or application's styleset.
// To change statically for all instances of this field,
// assign to DefaultFontId.
// To change per shape or dynamically, override this.
public virtual StyleSetResourceId GetFontId(ShapeElement parentShape)
{ return DefaultFontId; }
```

 Существует несколько других пар `Get` методов и `Default` свойств, таких как `DefaultMultipleLine/GetMultipleLine()` . Можно присвоить значение свойству по умолчанию, чтобы изменить значение для всех экземпляров поля Shape. Чтобы значение отличалось от одного экземпляра формы к другому или зависит от состояния фигуры или ее элемента модели, переопределите `Get` метод.

## <a name="static-customizations"></a>Статические настройки
 Если вы хотите изменить каждый экземпляр поля Shape, сначала определите, можно ли задать свойство в определении DSL. Например, можно задать размер и стиль шрифта в окно свойств.

 Если нет, переопределите `InitializeShapeFields` метод класса Shape и присвойте значение соответствующему `Default...` свойству текстового поля.

> [!WARNING]
> Для переопределения `InitializeShapeFields()` необходимо установить свойство **Generated Double производного** класса Shape в `true` Определение DSL.

 В этом примере фигура содержит текстовое поле, которое будет использоваться для комментариев пользователя. Мы хотим использовать стандартный шрифт комментария. Так как это стандартный шрифт из набора стилей, можно задать идентификатор шрифта по умолчанию:

```csharp

 partial class ExampleShape
{   protected override void InitializeShapeFields(IList<ShapeField> shapeFields)
    {
      // Fields set up according to DSL Definition:
      base.InitializeShapeFields(shapeFields);
      // Find and update comment field:
      TextField commentField = ShapeElement.FindShapeField(shapeFields, "CommentDecorator") as TextField;
      // Use the standard font for comments:
      commentField.DefaultFontId = DiagramFonts.CommentText;
```

## <a name="dynamic-customizations"></a>Динамические настройки
 Чтобы внешний вид изменяться в зависимости от состояния фигуры или ее элемента модели, следует создать собственный подкласс класса `TextField` и переопределить один или несколько `Get...` методов. Необходимо также переопределить метод Инитиализешапефиелдс фигуры и заменить экземпляр TextField экземпляром собственного класса.

 В следующем примере шрифт текстового поля становится зависимым от состояния логического свойства домена элемента модели фигуры.

 Чтобы выполнить этот пример кода, создайте новое решение DSL с использованием шаблона минимального языка. Добавьте логическое свойство домена `AlternateState` в доменный класс ексамплилемент. Добавьте декоратор значка в класс Ексамплешапе и присвойте его образу растровый файл. Щелкните **преобразовать все шаблоны**. Добавьте новый файл кода в проект DSL и вставьте следующий код.

 Чтобы протестировать код, нажмите клавишу F5, а затем в решении отладки Откройте образец схемы. Должно отобразиться состояние значка по умолчанию. Выберите фигуру и в окно свойств измените значение свойства **алтернатестате** . Шрифт имени элемента должен измениться.

```csharp
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Diagrams;
...

  partial class ExampleShape
  {
    /// <summary>
    /// Compose a list of the fields in this shape.
    /// Called once for each shape class.
    /// </summary>
    protected override void InitializeShapeFields(IList<ShapeField> shapeFields)
    {
      // Fields set up according to DSL Definition:
      base.InitializeShapeFields(shapeFields);
      // Replace the text field for NameDecorator:
      TextField oldField = ShapeElement.FindShapeField(shapeFields, "NameDecorator") as TextField;
      shapeFields.Remove(oldField);
      // Replace with my text field based on DSL Definition values:
      MyTextField newField = new MyTextField(oldField);
      shapeFields.Add(newField);
    }
  }
  /// <summary>
  /// Dynamic font depends on state of model element.
  /// </summary>
  public class MyTextField : TextField
  {
    public MyTextField(TextField prototype)
      : base(prototype.Name)
    {
      DefaultText = prototype.DefaultText;
      DefaultFocusable = prototype.DefaultFocusable;
      DefaultAutoSize = prototype.DefaultAutoSize;
      AnchoringBehavior.MinimumHeightInLines = prototype.AnchoringBehavior.MinimumHeightInLines;
      AnchoringBehavior.MinimumWidthInCharacters = prototype.AnchoringBehavior.MinimumWidthInCharacters;
      DefaultAccessibleState = prototype.DefaultAccessibleState;
    }

    public override System.Drawing.Font GetFont(ShapeElement parentShape)
    {
      // Access the Boolean domain property of the model element:
      if ((parentShape.ModelElement as ExampleElement).AlternateState)
        return new System.Drawing.Font("Callisto", 14.0f,
               System.Drawing.FontStyle.Italic |
               System.Drawing.FontStyle.Bold);
      else
        return base.GetFont(parentShape);
    }

  }
```

## <a name="style-sets"></a>Наборы стилей
 В предыдущем примере показано, как можно изменить текстовое поле на любой доступный шрифт. Однако предпочтительным методом является изменение его на один из набора стилей, связанных с фигурой или с приложением. Для этого необходимо переопределить <xref:Microsoft.VisualStudio.Modeling.Diagrams.TextField.GetFontId%2A> или жеттекстбрушид ().

 Кроме того, попробуйте изменить набор стилей фигуры, переопределив его <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement.InitializeResources%2A> . Это влияет на изменение шрифтов и кистей для всех полей фигур.

## <a name="customizing-image-fields"></a>Настройка полей изображений
 При определении декоратора изображения в фигуре и при определении фигуры изображения область, в которой отображается фигура, управляется с помощью Имажефиелд. Примеры инициализации Имажефиелдс и других ShapeFields см. в Дсл\женератедкоде\шапес.КС в решении DSL.

 Имажефиелд — это объект, управляющий областью внутри фигуры, например пространство, назначенное декоратору. Один экземпляр Имажефиелд является общим для многих фигур одного класса Shape. Экземпляр Имажефиелд не сохраняет отдельный образ для каждой фигуры: вместо этого `GetDisplayImage(ShapeElement)` метод принимает форму в качестве параметра и может выполнять поиск изображения, зависящего от текущего состояния фигуры и ее элемента модели.

 Если требуется специальное поведение, например изображение переменной, можно создать собственный класс, производный от Имажефиелд.

#### <a name="to-create-a-subclass-of-imagefield"></a>Создание подкласса Имажефиелд

1. Задайте свойство **Generated Double производного** класса родительской фигуры в определении DSL.

2. Переопределите `InitializeShapeFields` метод класса Shape.

    - Создайте новый файл кода в проекте DSL и запишите определение разделяемого класса для класса Shape. Переопределите здесь определение метода.

3. Проверка кода `InitializeShapeFields` в дсл\женератедкоде\шапес.КС.

     В методе переопределения вызовите базовый метод, а затем создайте экземпляр собственного класса поля Image. Используйте этот параметр, чтобы заменить стандартное поле изображения в `shapeFields` списке.

## <a name="dynamic-icons"></a>Динамические значки
 В этом примере изменяется значок, зависящий от состояния элемента модели фигуры.

> [!WARNING]
> В этом примере показано, как создать декоратор динамического изображения. Но если вы хотите переключаться между одним или двумя изображениями в зависимости от состояния переменной модели, проще всего создать несколько декораторов изображений, поместить их в одну и ту же точку на фигуре, а затем установить фильтр видимости в зависимости от определенных значений переменной модели. Чтобы установить этот фильтр, выберите карту фигур в определении DSL, откройте окно "сведения о DSL" и перейдите на вкладку декораторы.

 Чтобы выполнить этот пример кода, создайте новое решение DSL с использованием шаблона минимального языка. Добавьте логическое свойство домена `AlternateState` в доменный класс ексамплилемент. Добавьте декоратор значка в класс Ексамплешапе и присвойте его образу растровый файл. Щелкните **преобразовать все шаблоны**. Добавьте новый файл кода в проект DSL и вставьте следующий код.

 Чтобы протестировать код, нажмите клавишу F5, а затем в решении отладки Откройте образец схемы. Должно отобразиться состояние значка по умолчанию. Выберите фигуру и в окно свойств измените значение свойства **алтернатестате** . Значок должен отображаться на этой фигуре с поворотом на 90 градусов.

```csharp
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Diagrams;
...
partial class ExampleShape
{
    /// <summary>
    /// Compose a list of the fields in this shape.
    /// Called once for each shape class.
    /// </summary>
    /// <param name="shapeFields"></param>
    protected override void InitializeShapeFields(IList<ShapeField> shapeFields)
    {
      // Fields set up according to DSL Definition:
      base.InitializeShapeFields(shapeFields);

      // Replace the image field:
      ShapeField oldField = ShapeElement.FindShapeField(shapeFields, "IconDecorator");
      shapeFields.Remove(oldField);
      // Must keep the same name:
      MyImageField newField = new MyImageField(oldField.Name);
      shapeFields.Add(newField);
      newField.DefaultImage = (oldField as ImageField).DefaultImage.Clone() as System.Drawing.Image;
    }
  }

  public class MyImageField : ImageField
  {
    public MyImageField(string tag) : base(tag) { }

    /// <summary>
    /// Get the image for this field in the given shape.
    /// </summary>
    public override System.Drawing.Image GetDisplayImage(ShapeElement parentShape)
    {
      ExampleElement element = parentShape.ModelElement as ExampleElement;
      if (element.AlternateState == true)
        return AlternateImage;
      else
        return base.GetDisplayImage(parentShape);
    }

    private System.Drawing.Image alternateImage;
    public System.Drawing.Image AlternateImage
    {
      get
      {
        if (alternateImage == null)
        {
          // Alternate image is a copy of the default, rotated by 90 degrees:
          alternateImage = this.DefaultImage.Clone() as System.Drawing.Image;
          alternateImage.RotateFlip(System.Drawing.RotateFlipType.Rotate90FlipNone);
        }
        return alternateImage;
      }
    }
  }
}
```

## <a name="see-also"></a>См. также

- [Определение фигур и соединителей](../modeling/defining-shapes-and-connectors.md)
- [Задание фонового изображения схемы](../modeling/setting-a-background-image-on-a-diagram.md)
- [Перемещение по модели и обновление модели в коде программы](../modeling/navigating-and-updating-a-model-in-program-code.md)
- [Написание кода для настройки доменного языка](../modeling/writing-code-to-customise-a-domain-specific-language.md)