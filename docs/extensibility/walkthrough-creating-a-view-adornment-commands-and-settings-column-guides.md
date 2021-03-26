---
title: Создание элемента оформления представления, команды и параметры | Документация Майкрософт
description: Узнайте, как расширить редактор кода Visual Studio с помощью направляющих столбцов, используя это пошаговое руководство.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 4a2df0a3-42da-4f7b-996f-ee16a35ac922
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 7e0a2111aeb3f0e23cb2c03feadda8accd4a93e1
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105080454"
---
# <a name="walkthrough-create-a-view-adornment-commands-and-settings-column-guides"></a>Пошаговое руководство. Создание элемента оформления, команд и параметров представления (направляющие столбцов)
Вы можете расширить редактор текста и кода Visual Studio с помощью команд и эффектов представления. В этой статье показано, как приступить к работе с популярной функцией расширения, направляющими столбцов. Направляющие столбцов — это визуально неплотные линии, нарисованные в представлении текстового редактора, которые помогают управлять кодом с учетом заданной ширины столбцов. В частности, отформатированный код может быть важен для образцов, включаемых в документы, записи блога или отчеты об ошибках.

В этом пошаговом руководстве описаны следующие операции:
- Создание проекта VSIX
- Добавление оформления представления редактора
- Добавлена поддержка сохранения и получения параметров (для рисования направляющих столбцов и их цвета).
- Добавление команд (Добавление и удаление направляющих столбцов, изменение их цвета)
- Поместите команды в контекстные меню Правка и текстовый документ.
- Добавление поддержки вызова команд из командного окна Visual Studio

  С помощью этого[расширения](https://marketplace.visualstudio.com/items?itemName=PaulHarrington.EditorGuidelines)коллекции Visual Studio можно опробовать версию руководства по столбцам.

  > [!NOTE]
  > В этом пошаговом руководстве вы вставляете большой объем кода в несколько файлов, создаваемых шаблонами расширений Visual Studio. Но в ближайшее время это пошаговое руководство будет ссылаться на завершенное решение на GitHub с другими примерами расширения. Завершенный код немного отличается тем, что он содержит реальные значки команд вместо использования значков женериктемплате.

## <a name="get-started"></a>Приступая к работе
Начиная с Visual Studio 2015, пакет SDK для Visual Studio не устанавливается из центра загрузки. Он входит в состав программы установки Visual Studio как дополнительный компонент. Пакет SDK для VS можно установить и позже. Дополнительные сведения см. [в статье Установка пакета SDK для Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="set-up-the-solution"></a>Настройка решения
Сначала необходимо создать проект VSIX, добавить Оформление представления редактора, а затем добавить команду (которая добавляет VSPackage для собственной команды). Базовая архитектура выглядит следующим образом:
- У вас есть прослушиватель создания текстового представления, который создает `ColumnGuideAdornment` объект для каждого представления. Этот объект прослушивает события, связанные с изменением представления или изменением параметров, при необходимости обновляя или перерисуя направляющие столбцов.
- Есть `GuidesSettingsManager` , который обрабатывает чтение и запись в хранилище параметров Visual Studio. Диспетчер параметров также имеет операции по обновлению параметров, поддерживающих команды пользователя (Добавление столбца, удаление столбца, изменение цвета).
- Существует пакет VSIP, который необходим, если у вас есть пользовательские команды, но это просто стандартный код, который инициализирует объект реализации команд.
- Существует `ColumnGuideCommands` объект, который выполняет пользовательские команды и подключает обработчики команд для команд, объявленных в *vsct* -файле.

  **VSIX**. Используйте команду **File &#124; New...** для создания проекта. Выберите узел **расширяемость** в **C#** в левой области навигации и щелкните **проект VSIX** на правой панели. Введите имя **колумнгуидес** и нажмите кнопку **ОК** , чтобы создать проект.

  **Просмотр оформления**. Нажмите правую кнопку указателя в узле проекта в обозреватель решений. Выберите команду **добавить &#124; новый элемент...** , чтобы добавить новый элемент оформления представления. Выберите **расширяемость &#124; редактор** в левой области навигации и выберите **элемент окно просмотра редактора** в области справа. Введите имя **колумнгуидеадорнмент** в качестве имени элемента и нажмите кнопку **Добавить** , чтобы добавить его.

  Можно увидеть, что этот шаблон элемента добавил два файла в проект (а также ссылки и т. д.): **колумнгуидеадорнмент. CS** и **колумнгуидеадорнменттекствиевкреатионлистенер. CS**. Шаблоны нарисуют сиреневый прямоугольник в представлении. В следующем разделе вы измените пару строк в прослушивателе создания представления и замените содержимое файла **колумнгуидеадорнмент. CS**.

  **Команды**. В **Обозреватель решений** нажмите правую кнопку мыши в узле проекта. Выберите команду **добавить &#124; новый элемент...** , чтобы добавить новый элемент оформления представления. Выберите **расширяемость &#124; VSPackage** в левой области навигации и выберите **Настраиваемая команда** в области справа. Введите имя **колумнгуидекоммандс** в качестве имени элемента и нажмите кнопку **Добавить**. Помимо нескольких ссылок, при добавлении команд и пакета также добавляются **колумнгуидекоммандс. CS**, **колумнгуидекоммандспаккаже. CS** и **колумнгуидекоммандспаккаже. vsct**. В следующем разделе вы замените содержимое первого и последнего файлов, чтобы определить и реализовать команды.

## <a name="set-up-the-text-view-creation-listener"></a>Настройка прослушивателя создания текстового представления
Откройте *колумнгуидеадорнменттекствиевкреатионлистенер. CS* в редакторе. Этот код реализует обработчик для всякий раз, когда Visual Studio создает текстовые представления. Существуют атрибуты, управляющие вызовом обработчика в зависимости от характеристик представления.

Код также должен объявлять слой оформления. Когда редактор обновляет представления, он получает слои оформления для представления и из него получает элементы оформления. Можно объявить порядок слоя относительно других атрибутов. Замените следующую строку:

```csharp
[Order(After = PredefinedAdornmentLayers.Caret)]
```

с этими двумя строками:

```csharp
[Order(Before = PredefinedAdornmentLayers.Text)]
[TextViewRole(PredefinedTextViewRoles.Document)]
```

Замененная строка находится в группе атрибутов, объявляющих слой оформлений. Первая строка, которую вы изменили, изменится только там, где отображаются направляющие столбцов. Рисование линий "до" текст в представлении означает, что они отображаются позади текста или под ним. Во второй строке объявляется, что оформление руководства по столбцам применимо к текстовым сущностям, которые соответствуют определению документа, но можно объявить Оформление, например, для работы только с редактируемым текстом. Дополнительные сведения см. в [точках расширения языковой службы и редактора](../extensibility/language-service-and-editor-extension-points.md) .

## <a name="implement-the-settings-manager"></a>Реализация диспетчера параметров
Замените содержимое файла *гуидессеттингсманажер. CS* следующим кодом (см. описание ниже):

```csharp
using Microsoft.VisualStudio.Settings;
using Microsoft.VisualStudio.Shell;
using Microsoft.VisualStudio.Shell.Settings;
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Windows.Media;

namespace ColumnGuides
{
    internal static class GuidesSettingsManager
    {
        // Because my code is always called from the UI thred, this succeeds.
        internal static SettingsManager VsManagedSettingsManager =
            new ShellSettingsManager(ServiceProvider.GlobalProvider);

        private const int _maxGuides = 5;
        private const string _collectionSettingsName = "Text Editor";
        private const string _settingName = "Guides";
        // 1000 seems reasonable since primary scenario is long lines of code
        private const int _maxColumn = 1000;

        static internal bool AddGuideline(int column)
        {
            if (! IsValidColumn(column))
                throw new ArgumentOutOfRangeException(
                    "column",
                    "The paramenter must be between 1 and " + _maxGuides.ToString());
            var offsets = GuidesSettingsManager.GetColumnOffsets();
            if (offsets.Count() >= _maxGuides)
                return false;
            // Check for duplicates
            if (offsets.Contains(column))
                return false;
            offsets.Add(column);
            WriteSettings(GuidesSettingsManager.GuidelinesColor, offsets);
            return true;
        }

        static internal bool RemoveGuideline(int column)
        {
            if (!IsValidColumn(column))
                throw new ArgumentOutOfRangeException(
                    "column", "The paramenter must be between 1 and 10,000");
            var columns = GuidesSettingsManager.GetColumnOffsets();
            if (! columns.Remove(column))
            {
                // Not present.  Allow user to remove the last column
                // even if they're not on the right column.
                if (columns.Count != 1)
                    return false;

                columns.Clear();
            }
            WriteSettings(GuidesSettingsManager.GuidelinesColor, columns);
            return true;
        }

        static internal bool CanAddGuideline(int column)
        {
            if (!IsValidColumn(column))
                return false;
            var offsets = GetColumnOffsets();
            if (offsets.Count >= _maxGuides)
                return false;
            return ! offsets.Contains(column);
        }

        static internal bool CanRemoveGuideline(int column)
        {
            if (! IsValidColumn(column))
                return false;
            // Allow user to remove the last guideline regardless of the column.
            // Okay to call count, we limit the number of guides.
            var offsets = GuidesSettingsManager.GetColumnOffsets();
            return offsets.Contains(column) || offsets.Count() == 1;
        }

        static internal void RemoveAllGuidelines()
        {
            WriteSettings(GuidesSettingsManager.GuidelinesColor, new int[0]);
        }

        private static bool IsValidColumn(int column)
        {
            // zero is allowed (per user request)
            return 0 <= column && column <= _maxColumn;
        }

        // This has format "RGB(<int>, <int>, <int>) <int> <int>...".
        // There can be any number of ints following the RGB part,
        // and each int is a column (char offset into line) where to draw.
        static private string _guidelinesConfiguration;
        static private string GuidelinesConfiguration
        {
            get
            {
                if (_guidelinesConfiguration == null)
                {
                    _guidelinesConfiguration =
                        GetUserSettingsString(
                            GuidesSettingsManager._collectionSettingsName,
                            GuidesSettingsManager._settingName)
                        .Trim();
                }
                return _guidelinesConfiguration;
            }

            set
            {
                if (value != _guidelinesConfiguration)
                {
                    _guidelinesConfiguration = value;
                    WriteUserSettingsString(
                        GuidesSettingsManager._collectionSettingsName,
                        GuidesSettingsManager._settingName, value);
                    // Notify ColumnGuideAdornments to update adornments in views.
                    var handler = GuidesSettingsManager.SettingsChanged;
                    if (handler != null)
                        handler();
                }
            }
        }

        internal static string GetUserSettingsString(string collection, string setting)
        {
            var store = GuidesSettingsManager
                            .VsManagedSettingsManager
                            .GetReadOnlySettingsStore(SettingsScope.UserSettings);
            return store.GetString(collection, setting, "RGB(255,0,0) 80");
        }

        internal static void WriteUserSettingsString(string key, string propertyName,
                                                     string value)
        {
            var store = GuidesSettingsManager
                            .VsManagedSettingsManager
                            .GetWritableSettingsStore(SettingsScope.UserSettings);
            store.CreateCollection(key);
            store.SetString(key, propertyName, value);
        }

        // Persists settings and sets property with side effect of signaling
        // ColumnGuideAdornments to update.
        static private void WriteSettings(Color color, IEnumerable<int> columns)
        {
            string value = ComposeSettingsString(color, columns);
            GuidelinesConfiguration = value;
        }

        private static string ComposeSettingsString(Color color,
                                                    IEnumerable<int> columns)
        {
            StringBuilder sb = new StringBuilder();
            sb.AppendFormat("RGB({0},{1},{2})", color.R, color.G, color.B);
            IEnumerator<int> columnsEnumerator = columns.GetEnumerator();
            if (columnsEnumerator.MoveNext())
            {
                sb.AppendFormat(" {0}", columnsEnumerator.Current);
                while (columnsEnumerator.MoveNext())
                {
                    sb.AppendFormat(", {0}", columnsEnumerator.Current);
                }
            }
            return sb.ToString();
        }

        // Parse a color out of a string that begins like "RGB(255,0,0)"
        static internal Color GuidelinesColor
        {
            get
            {
                string config = GuidelinesConfiguration;
                if (!String.IsNullOrEmpty(config) && config.StartsWith("RGB("))
                {
                    int lastParen = config.IndexOf(')');
                    if (lastParen > 4)
                    {
                        string[] rgbs = config.Substring(4, lastParen - 4).Split(',');

                        if (rgbs.Length >= 3)
                        {
                            byte r, g, b;
                            if (byte.TryParse(rgbs[0], out r) &&
                                byte.TryParse(rgbs[1], out g) &&
                                byte.TryParse(rgbs[2], out b))
                            {
                                return Color.FromRgb(r, g, b);
                            }
                        }
                    }
                }
                return Colors.DarkRed;
            }

            set
            {
                WriteSettings(value, GetColumnOffsets());
            }
        }

        // Parse a list of integer values out of a string that looks like
        // "RGB(255,0,0) 1, 5, 10, 80"
        static internal List<int> GetColumnOffsets()
        {
            var result = new List<int>();
            string settings = GuidesSettingsManager.GuidelinesConfiguration;
            if (String.IsNullOrEmpty(settings))
                return new List<int>();

            if (!settings.StartsWith("RGB("))
                return new List<int>();

            int lastParen = settings.IndexOf(')');
            if (lastParen <= 4)
                return new List<int>();

            string[] columns = settings.Substring(lastParen + 1).Split(',');

            int columnCount = 0;
            foreach (string columnText in columns)
            {
                int column = -1;
                // VS 2008 gallery extension didn't allow zero, so per user request ...
                if (int.TryParse(columnText, out column) && column >= 0)
                {
                    columnCount++;
                    result.Add(column);
                    if (columnCount >= _maxGuides)
                        break;
                }
            }
            return result;
        }

        // Delegate and Event to fire when settings change so that ColumnGuideAdornments
        // can update.  We need nothing special in this event since the settings manager
        // is statically available.
        //
        internal delegate void SettingsChangedHandler();
        static internal event SettingsChangedHandler SettingsChanged;

    }
}

```

Большая часть этого кода создает и анализирует формат параметров: "RGB ( \<int> , \<int> , \<int> ) \<int> , \<int> ,...".  Целые числа в конце являются столбцами, основанными на единицах, где необходимо использовать направляющие столбцов. Расширение «направляющие столбцов» захватывает все свои параметры в одной строке значений параметров.

В коде стоит выделить некоторые части кода. Следующая строка кода получает управляемую оболочку Visual Studio для хранилища параметров. В большинстве случаев это является абстрактным по сравнению с реестром Windows, но этот API не зависит от механизма хранения.

```csharp
internal static SettingsManager VsManagedSettingsManager =
    new ShellSettingsManager(ServiceProvider.GlobalProvider);
```

В хранилище параметров Visual Studio для уникальной идентификации всех параметров используется идентификатор категории и идентификатор параметра.

```csharp
private const string _collectionSettingsName = "Text Editor";
private const string _settingName = "Guides";
```

В `"Text Editor"` качестве имени категории не нужно использовать. Вы можете выбрать все, что вам нравится.

Первые несколько функций являются точками входа для изменения настроек. Они проверяют высокоуровневые ограничения, такие как максимально допустимое количество руководств.  Затем они вызывают метод `WriteSettings` , который формирует строку параметров и задает свойство `GuideLinesConfiguration` . Задание этого свойства сохраняет значение параметров в хранилище параметров Visual Studio и запускает `SettingsChanged` событие для обновления всех `ColumnGuideAdornment` объектов, каждый из которых связан с представлением текста.

Существует несколько функций точки входа, таких как `CanAddGuideline` , которые используются для реализации команд, изменяющих параметры. Когда Visual Studio отображает меню, он запрашивает реализацию команд, чтобы определить, включена ли команда, какое имя и так далее.  Ниже показано, как подключить эти точки входа для реализации команд. Дополнительные сведения о командах см. в разделе [Расширение меню и команд](../extensibility/extending-menus-and-commands.md).

## <a name="implement-the-columnguideadornment-class"></a>Реализация класса Колумнгуидеадорнмент
`ColumnGuideAdornment`Создается экземпляр класса для каждого текстового представления, которое может содержать декоративные элементы. Этот класс прослушивает события, связанные с изменением представления или изменением параметров, а также по мере необходимости направляющими для обновления или перерисовки столбцов.

Замените содержимое файла *колумнгуидеадорнмент. CS* следующим кодом (см. описание ниже):

```csharp
using System;
using System.Windows.Media;
using Microsoft.VisualStudio.Text.Editor;
using System.Collections.Generic;
using System.Windows.Shapes;
using Microsoft.VisualStudio.Text.Formatting;
using System.Windows;

namespace ColumnGuides
{
    /// <summary>
    /// Adornment class, one instance per text view that draws a guides on the viewport
    /// </summary>
    internal sealed class ColumnGuideAdornment
    {
        private const double _lineThickness = 1.0;
        private IList<Line> _guidelines;
        private IWpfTextView _view;
        private double _baseIndentation;
        private double _columnWidth;

        /// <summary>
        /// Creates editor column guidelines
        /// </summary>
        /// <param name="view">The <see cref="IWpfTextView"/> upon
        /// which the adornment will be drawn</param>
        public ColumnGuideAdornment(IWpfTextView view)
        {
            _view = view;
            _guidelines = CreateGuidelines();
            GuidesSettingsManager.SettingsChanged +=
                new GuidesSettingsManager.SettingsChangedHandler(SettingsChanged);
            view.LayoutChanged +=
                new EventHandler<TextViewLayoutChangedEventArgs>(OnViewLayoutChanged);
            _view.Closed += new EventHandler(OnViewClosed);
        }

        void SettingsChanged()
        {
            _guidelines = CreateGuidelines();
            UpdatePositions();
            AddGuidelinesToAdornmentLayer();
        }

        void OnViewClosed(object sender, EventArgs e)
        {
            _view.LayoutChanged -= OnViewLayoutChanged;
            _view.Closed -= OnViewClosed;
            GuidesSettingsManager.SettingsChanged -= SettingsChanged;
        }

        private bool _firstLayoutDone;

        void OnViewLayoutChanged(object sender, TextViewLayoutChangedEventArgs e)
        {
            bool fUpdatePositions = false;

            IFormattedLineSource lineSource = _view.FormattedLineSource;
            if (lineSource == null)
            {
                return;
            }
            if (_columnWidth != lineSource.ColumnWidth)
            {
                _columnWidth = lineSource.ColumnWidth;
                fUpdatePositions = true;
            }
            if (_baseIndentation != lineSource.BaseIndentation)
            {
                _baseIndentation = lineSource.BaseIndentation;
                fUpdatePositions = true;
            }
            if (fUpdatePositions ||
                e.VerticalTranslation ||
                e.NewViewState.ViewportTop != e.OldViewState.ViewportTop ||
                e.NewViewState.ViewportBottom != e.OldViewState.ViewportBottom)
            {
                UpdatePositions();
            }
            if (!_firstLayoutDone)
            {
                AddGuidelinesToAdornmentLayer();
                _firstLayoutDone = true;
            }
        }

        private static IList<Line> CreateGuidelines()
        {
            Brush lineBrush = new SolidColorBrush(GuidesSettingsManager.GuidelinesColor);
            DoubleCollection dashArray = new DoubleCollection(new double[] { 1.0, 3.0 });
            IList<Line> result = new List<Line>();
            foreach (int column in GuidesSettingsManager.GetColumnOffsets())
            {
                Line line = new Line()
                {
                    // Use the DataContext slot as a cookie to hold the column
                    DataContext = column,
                    Stroke = lineBrush,
                    StrokeThickness = _lineThickness,
                    StrokeDashArray = dashArray
                };
                result.Add(line);
            }
            return result;
        }

        void UpdatePositions()
        {
            foreach (Line line in _guidelines)
            {
                int column = (int)line.DataContext;
                line.X2 = _baseIndentation + 0.5 + column * _columnWidth;
                line.X1 = line.X2;
                line.Y1 = _view.ViewportTop;
                line.Y2 = _view.ViewportBottom;
            }
        }

        void AddGuidelinesToAdornmentLayer()
        {
            // Grab a reference to the adornment layer that this adornment
            // should be added to
            // Must match exported name in ColumnGuideAdornmentTextViewCreationListener
            IAdornmentLayer adornmentLayer =
                _view.GetAdornmentLayer("ColumnGuideAdornment");
            if (adornmentLayer == null)
                return;
            adornmentLayer.RemoveAllAdornments();
            // Add the guidelines to the adornment layer and make them relative
            // to the viewport
            foreach (UIElement element in _guidelines)
                adornmentLayer.AddAdornment(AdornmentPositioningBehavior.OwnerControlled,
                                            null, null, element, null);
        }
    }

}
```

Экземпляры этого класса замещаются в связанный объект <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView> и список объектов, `Line` нарисованных в представлении.

Конструктор (вызываемый из, `ColumnGuideAdornmentTextViewCreationListener` когда Visual Studio создает новые представления) создает объекты руководств по столбцам `Line` .  Конструктор также добавляет обработчики для `SettingsChanged` события (определенного в `GuidesSettingsManager` ), а также событий представления `LayoutChanged` и `Closed` .

Это `LayoutChanged` событие срабатывает из-за нескольких видов изменений в представлении, в том числе при создании представления в Visual Studio. `OnViewLayoutChanged`Обработчик вызывает метод `AddGuidelinesToAdornmentLayer` для выполнения. Код в `OnViewLayoutChanged` определяет, нужно ли обновлять позиции линий на основе таких изменений, как изменение размера шрифта, переплеты представлений, горизонтальная прокрутка и т. д. Код в `UpdatePositions` заставляет направляющие рисоваться между символами или сразу после столбца текста, который находится в указанном смещении в строке текста.

Каждый раз, когда параметры изменяют `SettingsChanged` функцию, просто повторно создает все `Line` объекты с любыми новыми параметрами. После установки позиций строки код удаляет все предыдущие `Line` объекты из `ColumnGuideAdornment` слоя оформлений и добавляет новые.

## <a name="define-the-commands-menus-and-menu-placements"></a>Определение команд, меню и размещений в меню
Объявление команд и меню может быть очень большим, так как они размещают группы команд или меню в различных других меню и присоединяются к обработчикам команд. В этом пошаговом руководстве показано, как работают команды в этом расширении, но для получения более подробных сведений см. раздел [Расширение меню и команд](../extensibility/extending-menus-and-commands.md).

### <a name="introduction-to-the-code"></a>Введение в код
Расширение «направляющие столбцов» показывает объявление группы команд, входящих в состав (Добавление столбца, удаление столбца, изменение цвета линии), и последующее помещение этой группы в подменю контекстного меню редактора.  Расширение «направляющие столбцов» также добавляет команды в главное меню **редактирования** , но оставляет их невидимыми, как показано в общем шаблоне ниже.

Существует три части реализации команд: Колумнгуидекоммандспаккаже. cs, Колумнгуидекоммандспаккаже. vsct и Колумнгуидекоммандс. cs. Код, формируемый шаблонами, помещает в меню **Сервис** команду, которая выводит диалоговое окно в качестве реализации. Вы можете взглянуть на то, как это реализовано в файлах *. vsct* и *колумнгуидекоммандс. CS* , так как это просто. Вы замените код в этих файлах ниже.

Код пакета содержит объявления, необходимые для того, чтобы Visual Studio обнаружил, что расширение предлагает команды и найти место размещения команд. При инициализации пакета создается экземпляр класса реализации Commands. Дополнительные сведения о пакетах, связанных с командами, см. в разделе [Расширение меню и команд](../extensibility/extending-menus-and-commands.md).

### <a name="a-common-commands-pattern"></a>Шаблон общих команд
Команды в расширении руководств по столбцам являются примером очень распространенного шаблона в Visual Studio. Связанные команды помещаются в группу, и вы помещаете эту группу в главное меню, часто с « `<CommandFlag>CommandWellOnly</CommandFlag>` », чтобы сделать команду невидимой.  Размещение команд в главном меню (например, **Edit**) дает им удобные имена (например, **Edit. аддколумнгуиде**), которые полезны для поиска команд при повторном назначении привязок клавиш в **параметрах инструментов**. Это также полезно для получения завершения при вызове команд из **командного окна**.

Затем вы добавляете группу команд в контекстные меню или подменю, в которых пользователь должен использовать эти команды. Visual Studio интерпретируется `CommandWellOnly` как флаг невидимости только для основных меню. При помещении той же группы команд в контекстное меню или в подменю отображаются команды.

В рамках общего шаблона расширение «направляющие столбцов» создает вторую группу, содержащую одно подменю. Подменю, в свою очередь, содержит первую группу с командными группами из четырех столбцов. Вторая группа, содержащая подменю, — это многократно используемый ресурс-контейнер, помещаемый в различные контекстные меню, который помещает подменю в эти контекстные меню.

### <a name="the-vsct-file"></a>Файл vsct
В файле *. vsct* объявляются команды и место их расположения, а также значки и т. д. Замените содержимое файла *vsct* следующим кодом (см. описание ниже):

```xml
<?xml version="1.0" encoding="utf-8"?>
<CommandTable xmlns="http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable" xmlns:xs="http://www.w3.org/2001/XMLSchema">

  <!--  This is the file that defines the actual layout and type of the commands.
        It is divided in different sections (e.g. command definition, command
        placement, ...), with each defining a specific set of properties.
        See the comment before each section for more details about how to
        use it. -->

  <!--  The VSCT compiler (the tool that translates this file into the binary
        format that VisualStudio will consume) has the ability to run a preprocessor
        on the vsct file; this preprocessor is (usually) the C++ preprocessor, so
        it is possible to define includes and macros with the same syntax used
        in C++ files. Using this ability of the compiler here, we include some files
        defining some of the constants that we will use inside the file. -->

  <!--This is the file that defines the IDs for all the commands exposed by
      VisualStudio. -->
  <Extern href="stdidcmd.h"/>

  <!--This header contains the command ids for the menus provided by the shell. -->
  <Extern href="vsshlids.h"/>

  <!--The Commands section is where commands, menus, and menu groups are defined.
      This section uses a Guid to identify the package that provides the command
      defined inside it. -->
  <Commands package="guidColumnGuideCommandsPkg">
    <!-- Inside this section we have different sub-sections: one for the menus, another
    for the menu groups, one for the buttons (the actual commands), one for the combos
    and the last one for the bitmaps used. Each element is identified by a command id
    that is a unique pair of guid and numeric identifier; the guid part of the identifier
    is usually called "command set" and is used to group different command inside a
    logically related group; your package should define its own command set in order to
    avoid collisions with command ids defined by other packages. -->

    <!-- In this section you can define new menu groups. A menu group is a container for
         other menus or buttons (commands); from a visual point of view you can see the
         group as the part of a menu contained between two lines. The parent of a group
         must be a menu. -->
    <Groups>

      <!-- The main group is parented to the edit menu. All the buttons within the group
           have the "CommandWellOnly" flag, so they're actually invisible, but it means
           they get canonical names that begin with "Edit". Using placements, the group
           is also placed in the GuidesSubMenu group. -->
      <!-- The priority 0xB801 is chosen so it goes just after
           IDG_VS_EDIT_COMMANDWELL -->
      <Group guid="guidColumnGuidesCommandSet" id="GuidesMenuItemsGroup"
             priority="0xB801">
        <Parent guid="guidSHLMainMenu" id="IDM_VS_MENU_EDIT" />
      </Group>

      <!-- Group for holding the "Guidelines" sub-menu anchor (the item on the menu that
           drops the sub menu). The group is parented to
           the context menu for code windows. That takes care of most editors, but it's
           also placed in a couple of other windows using Placements -->
      <Group guid="guidColumnGuidesCommandSet" id="GuidesContextMenuGroup"
             priority="0x0600">
        <Parent guid="guidSHLMainMenu" id="IDM_VS_CTXT_CODEWIN" />
      </Group>

    </Groups>

    <Menus>
      <Menu guid="guidColumnGuidesCommandSet" id="GuidesSubMenu" priority="0x1000"
            type="Menu">
        <Parent guid="guidColumnGuidesCommandSet" id="GuidesContextMenuGroup" />
        <Strings>
          <ButtonText>&Column Guides</ButtonText>
        </Strings>
      </Menu>
    </Menus>

    <!--Buttons section. -->
    <!--This section defines the elements the user can interact with, like a menu command or a button
        or combo box in a toolbar. -->
    <Buttons>
      <!--To define a menu group you have to specify its ID, the parent menu and its
          display priority.
          The command is visible and enabled by default. If you need to change the
          visibility, status, etc, you can use the CommandFlag node.
          You can add more than one CommandFlag node e.g.:
              <CommandFlag>DefaultInvisible</CommandFlag>
              <CommandFlag>DynamicVisibility</CommandFlag>
          If you do not want an image next to your command, remove the Icon node or
          set it to <Icon guid="guidOfficeIcon" id="msotcidNoIcon" /> -->

      <Button guid="guidColumnGuidesCommandSet" id="cmdidAddColumnGuide"
              priority="0x0100" type="Button">
        <Parent guid="guidColumnGuidesCommandSet" id="GuidesMenuItemsGroup" />
        <Icon guid="guidImages" id="bmpPicAddGuide" />
        <CommandFlag>CommandWellOnly</CommandFlag>
        <CommandFlag>AllowParams</CommandFlag>
        <Strings>
          <ButtonText>&Add Column Guide</ButtonText>
        </Strings>
      </Button>

      <Button guid="guidColumnGuidesCommandSet" id="cmdidRemoveColumnGuide"
              priority="0x0101" type="Button">
        <Parent guid="guidColumnGuidesCommandSet" id="GuidesMenuItemsGroup" />
        <Icon guid="guidImages" id="bmpPicRemoveGuide" />
        <CommandFlag>CommandWellOnly</CommandFlag>
        <CommandFlag>AllowParams</CommandFlag>
        <Strings>
          <ButtonText>&Remove Column Guide</ButtonText>
        </Strings>
      </Button>

      <Button guid="guidColumnGuidesCommandSet" id="cmdidChooseGuideColor"
              priority="0x0103" type="Button">
        <Parent guid="guidColumnGuidesCommandSet" id="GuidesMenuItemsGroup" />
        <Icon guid="guidImages" id="bmpPicChooseColor" />
        <CommandFlag>CommandWellOnly</CommandFlag>
        <Strings>
          <ButtonText>Column Guide &Color...</ButtonText>
        </Strings>
      </Button>

      <Button guid="guidColumnGuidesCommandSet" id="cmdidRemoveAllColumnGuides"
              priority="0x0102" type="Button">
        <Parent guid="guidColumnGuidesCommandSet" id="GuidesMenuItemsGroup" />
        <CommandFlag>CommandWellOnly</CommandFlag>
        <Strings>
          <ButtonText>Remove A&ll Columns</ButtonText>
        </Strings>
      </Button>
    </Buttons>

    <!--The bitmaps section is used to define the bitmaps that are used for the
        commands.-->
    <Bitmaps>
      <!--  The bitmap id is defined in a way that is a little bit different from the
            others:
            the declaration starts with a guid for the bitmap strip, then there is the
            resource id of the bitmap strip containing the bitmaps and then there are
            the numeric ids of the elements used inside a button definition. An important
            aspect of this declaration is that the element id
            must be the actual index (1-based) of the bitmap inside the bitmap strip. -->
      <Bitmap guid="guidImages" href="Resources\ColumnGuideCommands.png"
              usedList="bmpPicAddGuide, bmpPicRemoveGuide, bmpPicChooseColor" />
    </Bitmaps>

  </Commands>

  <CommandPlacements>

    <!-- Define secondary placements for our groups -->

    <!-- Place the group containing the three commands in the sub-menu -->
    <CommandPlacement guid="guidColumnGuidesCommandSet" id="GuidesMenuItemsGroup"
                      priority="0x0100">
      <Parent guid="guidColumnGuidesCommandSet" id="GuidesSubMenu" />
    </CommandPlacement>

    <!-- The HTML editor context menu, for some reason, redefines its own groups
         so we need to place a copy of our context menu there too. -->
    <CommandPlacement guid="guidColumnGuidesCommandSet" id="GuidesContextMenuGroup"
                      priority="0x1001">
      <Parent guid="CMDSETID_HtmEdGrp" id="IDMX_HTM_SOURCE_HTML" />
    </CommandPlacement>

    <!-- The HTML context menu in Dev12 changed. -->
    <CommandPlacement guid="guidColumnGuidesCommandSet" id="GuidesContextMenuGroup"
                      priority="0x1001">
      <Parent guid="CMDSETID_HtmEdGrp_Dev12" id="IDMX_HTM_SOURCE_HTML_Dev12" />
    </CommandPlacement>

    <!-- Similarly for Script -->
    <CommandPlacement guid="guidColumnGuidesCommandSet" id="GuidesContextMenuGroup"
                      priority="0x1001">
      <Parent guid="CMDSETID_HtmEdGrp" id="IDMX_HTM_SOURCE_SCRIPT" />
    </CommandPlacement>

    <!-- Similarly for ASPX  -->
    <CommandPlacement guid="guidColumnGuidesCommandSet" id="GuidesContextMenuGroup"
                      priority="0x1001">
      <Parent guid="CMDSETID_HtmEdGrp" id="IDMX_HTM_SOURCE_ASPX" />
    </CommandPlacement>

    <!-- Similarly for the XAML editor context menu -->
    <CommandPlacement guid="guidColumnGuidesCommandSet" id="GuidesContextMenuGroup"
                      priority="0x0600">
      <Parent guid="guidXamlUiCmds" id="IDM_XAML_EDITOR" />
    </CommandPlacement>

  </CommandPlacements>

  <!-- This defines the identifiers and their values used above to index resources
       and specify commands. -->
  <Symbols>
    <!-- This is the package guid. -->
    <GuidSymbol name="guidColumnGuideCommandsPkg"
                value="{e914e5de-0851-4904-b361-1a3a9d449704}" />

    <!-- This is the guid used to group the menu commands together -->
    <GuidSymbol name="guidColumnGuidesCommandSet"
                value="{c2bc0047-8bfa-4e5a-b5dc-45af8c274d8e}">
      <IDSymbol name="GuidesContextMenuGroup" value="0x1020" />
      <IDSymbol name="GuidesMenuItemsGroup" value="0x1021" />
      <IDSymbol name="GuidesSubMenu" value="0x1022" />
      <IDSymbol name="cmdidAddColumnGuide" value="0x0100" />
      <IDSymbol name="cmdidRemoveColumnGuide" value="0x0101" />
      <IDSymbol name="cmdidChooseGuideColor" value="0x0102" />
      <IDSymbol name="cmdidRemoveAllColumnGuides" value="0x0103" />
    </GuidSymbol>

    <GuidSymbol name="guidImages" value="{2C99F852-587C-43AF-AA2D-F605DE2E46EF}">
      <IDSymbol name="bmpPicAddGuide" value="1" />
      <IDSymbol name="bmpPicRemoveGuide" value="2" />
      <IDSymbol name="bmpPicChooseColor" value="3" />
    </GuidSymbol>

    <GuidSymbol name="CMDSETID_HtmEdGrp_Dev12"
                value="{78F03954-2FB8-4087-8CE7-59D71710B3BB}">
      <IDSymbol name="IDMX_HTM_SOURCE_HTML_Dev12" value="0x1" />
    </GuidSymbol>

    <GuidSymbol name="CMDSETID_HtmEdGrp" value="{d7e8c5e1-bdb8-11d0-9c88-0000f8040a53}">
      <IDSymbol name="IDMX_HTM_SOURCE_HTML" value="0x33" />
      <IDSymbol name="IDMX_HTM_SOURCE_SCRIPT" value="0x34" />
      <IDSymbol name="IDMX_HTM_SOURCE_ASPX" value="0x35" />
    </GuidSymbol>

    <GuidSymbol name="guidXamlUiCmds" value="{4c87b692-1202-46aa-b64c-ef01faec53da}">
      <IDSymbol name="IDM_XAML_EDITOR" value="0x103" />
    </GuidSymbol>
  </Symbols>

</CommandTable>

```

**Идентификаторы GUID**. Чтобы в Visual Studio можно было найти обработчики команд и вызывать их, необходимо убедиться, что идентификатор GUID пакета, объявленный в файле *колумнгуидекоммандспаккаже. CS* (сформированном из шаблона элемента проекта) соответствует идентификатору GUID пакета, объявленному в *vsct* -файле (скопированному выше). Если вы повторно используете этот пример кода, убедитесь, что у вас есть другой GUID, чтобы не конфликтовать с кем-либо другим, кто мог скопировать этот код.

Найдите эту строку в *колумнгуидекоммандспаккаже. CS* и скопируйте идентификатор GUID из одной кавычки в следующую:

```csharp
public const string PackageGuidString = "ef726849-5447-4f73-8de5-01b9e930f7cd";
```

Затем вставьте GUID в файл *. vsct* , чтобы в объявлениях была следующая строка `Symbols` :

```xml
<GuidSymbol name="guidColumnGuideCommandsPkg"
            value="{ef726849-5447-4f73-8de5-01b9e930f7cd}" />
```

Идентификаторы GUID для набора команд и файл растрового изображения должны быть уникальными для расширений.

```xml
<GuidSymbol name="guidColumnGuidesCommandSet"
            value="{c2bc0047-8bfa-4e5a-b5dc-45af8c274d8e}">
<GuidSymbol name="guidImages" value="{2C99F852-587C-43AF-AA2D-F605DE2E46EF}">
```

Но в этом пошаговом руководстве не нужно изменять набор команд и идентификаторы GUID растровых изображений, чтобы получить код для работы. Идентификатор GUID набора команд должен соответствовать объявлению в файле *колумнгуидекоммандс. CS* , но его содержимое также можно заменить. Таким образом, идентификаторы GUID будут совпадать.

Другие идентификаторы GUID в *vsct* -файле определяют существовавшие ранее меню, к которым добавляются команды направляющих столбцов, поэтому они никогда не изменяются.

**Разделы файла**. *Vsct* содержит три внешних раздела: Commands, Places и Symbols. Раздел команд определяет группы команд, меню, кнопки или элементы меню, а также точечные рисунки для значков. В разделе мест объявляются группы, которые попадают в меню или дополнительные позиции в уже существующие меню. В разделе символов объявляются идентификаторы, используемые в других местах в *vsct* -файле, что делает код *. vsct* более удобочитаемым, чем коды GUID и шестнадцатеричные числа везде.

**Раздел Commands, определения групп**. Раздел Commands First определяет группы команд. Группы команд — это команды, которые отображаются в меню с небольшими серыми линиями, разделяющими группы. Группа также может заполнить все подменю, как в этом примере, и в этом случае не видны серые разделители. *Vsct* -файлы объявляют две группы:, `GuidesMenuItemsGroup` которая является родительской по отношению к `IDM_VS_MENU_EDIT` (главное меню **правки** ), и объект `GuidesContextMenuGroup` , который является родительским по отношению к `IDM_VS_CTXT_CODEWIN` (контекстное меню редактора кода).

Второе объявление группы имеет `0x0600` приоритет:

```xml
<Group guid="guidColumnGuidesCommandSet" id="GuidesContextMenuGroup"
             priority="0x0600">
```

Идея состоит в том, чтобы поместить подменю направляющих столбцов в конец любого контекстного меню, в которое добавляется группа подменю. Но не стоит думать о том, что лучше, и заставить подменю всегда быть последним, используя приоритет `0xFFFF` . Необходимо поэкспериментировать с номером, чтобы увидеть, где находится подменю, в контекстном меню, где оно размещается. В этом случае `0x0600` достаточно высокой степени, чтобы разместить его в конце меню, как можно видеть, но он оставляет место для того, чтобы кто-то еще мог разрабатывать свое расширение ниже, чем расширение руководств по столбцам, если это желательно.

**Раздел команд, определение меню**. Затем раздел команд определяет подменю `GuidesSubMenu` , которое является родительским для `GuidesContextMenuGroup` . `GuidesContextMenuGroup`— Это группа, добавляемая во все соответствующие контекстные меню. В разделе мест код помещает группу с помощью команд с четырьмя столбцами в этом подменю.

**Раздел команд, определения кнопок**. Затем в разделе команды определяются пункты меню или кнопки, которые являются командами с четырьмя столбцами. `CommandWellOnly`, описанный выше, означает, что команды невидимы при помещении в главное меню. Два объявления кнопки пункта меню (добавить руководство и руководство по удалению) также имеют `AllowParams` флаг:

```xml
<CommandFlag>AllowParams</CommandFlag>
```

Этот флаг включает, вместе с главным размещением меню, команду для получения аргументов, когда Visual Studio вызывает обработчик команд.  Если пользователь выполняет команду из командного окна, аргумент передается в обработчик команд в аргументах события.

**Разделы команд, определения растровых изображений**. Наконец, в разделе Commands объявляются точечные рисунки или значки, используемые для команд. Этот раздел представляет собой простое объявление, идентифицирующее ресурс проекта и отображающее индексы, используемые на основе одного из используемых значков. Раздел Symbols файла *. vsct* объявляет значения идентификаторов, используемых в качестве индексов. В этом пошаговом руководстве используется панель растрового изображения, предоставляемая с шаблоном пользовательского элемента команды, добавленным в проект.

**Раздел мест**. После раздела Commands в разделе Places. Первый из них, в котором код добавляет первую группу, описанную выше, содержит команды с четырьмя столбцами в подменю, где отображаются команды:

```xml
<CommandPlacement guid="guidColumnGuidesCommandSet" id="GuidesMenuItemsGroup"
                  priority="0x0100">
  <Parent guid="guidColumnGuidesCommandSet" id="GuidesSubMenu" />
</CommandPlacement>
```

Все остальные места добавления `GuidesContextMenuGroup` (который содержит `GuidesSubMenu` ) в другие контекстные меню редактора. Когда код объявлен `GuidesContextMenuGroup` , он был родительским для контекстного меню редактора кода. Вот почему вы не видите размещение для контекстного меню редактора кода.

**Раздел символов**. Как упоминалось выше, в разделе символов объявляются идентификаторы, используемые в других местах в *vsct* -файле, что делает код *. vsct* более удобочитаемым, чем коды GUID и шестнадцатеричные числа везде. Важные моменты в этом разделе указывают на то, что идентификатор GUID пакета должен быть согласован с объявлением в классе Package. Кроме того, идентификатор GUID набора команд должен быть согласован с объявлением в классе реализации команды.

## <a name="implement-the-commands"></a>Реализация команд
Файл *колумнгуидекоммандс. CS* реализует команды и подключает обработчики. Когда Visual Studio загружает пакет и инициализирует его, пакет в свою очередь вызывает `Initialize` класс реализации Commands. Инициализация команд просто создает экземпляр класса, а конструктор подключает все обработчики команд.

Замените содержимое файла *колумнгуидекоммандс. CS* следующим кодом (см. описание ниже):

```csharp
using System;
using System.ComponentModel.Design;
using System.Globalization;
using Microsoft.VisualStudio.Shell;
using Microsoft.VisualStudio.Shell.Interop;
using Microsoft.VisualStudio.TextManager.Interop;
using Microsoft.VisualStudio.Text.Editor;
using Microsoft.VisualStudio;

namespace ColumnGuides
{
    /// <summary>
    /// Command handler
    /// </summary>
    internal sealed class ColumnGuideCommands
    {

        const int cmdidAddColumnGuide = 0x0100;
        const int cmdidRemoveColumnGuide = 0x0101;
        const int cmdidChooseGuideColor = 0x0102;
        const int cmdidRemoveAllColumnGuides = 0x0103;

        /// <summary>
        /// Command menu group (command set GUID).
        /// </summary>
        static readonly Guid CommandSet =
            new Guid("c2bc0047-8bfa-4e5a-b5dc-45af8c274d8e");

        /// <summary>
        /// VS Package that provides this command, not null.
        /// </summary>
        private readonly Package package;

        OleMenuCommand _addGuidelineCommand;
        OleMenuCommand _removeGuidelineCommand;

        /// <summary>
        /// Initializes the singleton instance of the command.
        /// </summary>
        /// <param name="package">Owner package, not null.</param>
        public static void Initialize(Package package)
        {
            Instance = new ColumnGuideCommands(package);
        }

        /// <summary>
        /// Gets the instance of the command.
        /// </summary>
        public static ColumnGuideCommands Instance
        {
            get;
            private set;
        }

        /// <summary>
        /// Initializes a new instance of the <see cref="ColumnGuideCommands"/> class.
        /// Adds our command handlers for menu (commands must exist in the command
        /// table file)
        /// </summary>
        /// <param name="package">Owner package, not null.</param>
        private ColumnGuideCommands(Package package)
        {
            if (package == null)
            {
                throw new ArgumentNullException("package");
            }

            this.package = package;

            // Add our command handlers for menu (commands must exist in the .vsct file)

            OleMenuCommandService commandService =
                this.ServiceProvider.GetService(typeof(IMenuCommandService))
                    as OleMenuCommandService;
            if (commandService != null)
            {
                // Add guide
                _addGuidelineCommand =
                    new OleMenuCommand(AddColumnGuideExecuted, null,
                                       AddColumnGuideBeforeQueryStatus,
                                       new CommandID(ColumnGuideCommands.CommandSet,
                                                     cmdidAddColumnGuide));
                _addGuidelineCommand.ParametersDescription = "<column>";
                commandService.AddCommand(_addGuidelineCommand);
                // Remove guide
                _removeGuidelineCommand =
                    new OleMenuCommand(RemoveColumnGuideExecuted, null,
                                       RemoveColumnGuideBeforeQueryStatus,
                                       new CommandID(ColumnGuideCommands.CommandSet,
                                                     cmdidRemoveColumnGuide));
                _removeGuidelineCommand.ParametersDescription = "<column>";
                commandService.AddCommand(_removeGuidelineCommand);
                // Choose color
                commandService.AddCommand(
                    new MenuCommand(ChooseGuideColorExecuted,
                                    new CommandID(ColumnGuideCommands.CommandSet,
                                                  cmdidChooseGuideColor)));
                // Remove all
                commandService.AddCommand(
                    new MenuCommand(RemoveAllGuidelinesExecuted,
                                    new CommandID(ColumnGuideCommands.CommandSet,
                                                  cmdidRemoveAllColumnGuides)));
            }
        }

        /// <summary>
        /// Gets the service provider from the owner package.
        /// </summary>
        private IServiceProvider ServiceProvider
        {
            get
            {
                return this.package;
            }
        }

        private void AddColumnGuideBeforeQueryStatus(object sender, EventArgs e)
        {
            int currentColumn = GetCurrentEditorColumn();
            _addGuidelineCommand.Enabled =
                GuidesSettingsManager.CanAddGuideline(currentColumn);
        }

        private void RemoveColumnGuideBeforeQueryStatus(object sender, EventArgs e)
        {
            int currentColumn = GetCurrentEditorColumn();
            _removeGuidelineCommand.Enabled =
                GuidesSettingsManager.CanRemoveGuideline(currentColumn);
        }

        private int GetCurrentEditorColumn()
        {
            IVsTextView view = GetActiveTextView();
            if (view == null)
            {
                return -1;
            }

            try
            {
                IWpfTextView textView = GetTextViewFromVsTextView(view);
                int column = GetCaretColumn(textView);

                // Note: GetCaretColumn returns 0-based positions. Guidelines are 1-based
                // positions.
                // However, do not subtract one here since the caret is positioned to the
                // left of
                // the given column and the guidelines are positioned to the right. We
                // want the
                // guideline to line up with the current caret position. e.g. When the
                // caret is
                // at position 1 (zero-based), the status bar says column 2. We want to
                // add a
                // guideline for column 1 since that will place the guideline where the
                // caret is.
                return column;
            }
            catch (InvalidOperationException)
            {
                return -1;
            }
        }

        /// <summary>
        /// Find the active text view (if any) in the active document.
        /// </summary>
        /// <returns>The IVsTextView of the active view, or null if there is no active
        /// document or the
        /// active view in the active document is not a text view.</returns>
        private IVsTextView GetActiveTextView()
        {
            IVsMonitorSelection selection =
                this.ServiceProvider.GetService(typeof(IVsMonitorSelection))
                                                    as IVsMonitorSelection;
            object frameObj = null;
            ErrorHandler.ThrowOnFailure(
                selection.GetCurrentElementValue(
                    (uint)VSConstants.VSSELELEMID.SEID_DocumentFrame, out frameObj));

            IVsWindowFrame frame = frameObj as IVsWindowFrame;
            if (frame == null)
            {
                return null;
            }

            return GetActiveView(frame);
        }

        private static IVsTextView GetActiveView(IVsWindowFrame windowFrame)
        {
            if (windowFrame == null)
            {
                throw new ArgumentException("windowFrame");
            }

            object pvar;
            ErrorHandler.ThrowOnFailure(
                windowFrame.GetProperty((int)__VSFPROPID.VSFPROPID_DocView, out pvar));

            IVsTextView textView = pvar as IVsTextView;
            if (textView == null)
            {
                IVsCodeWindow codeWin = pvar as IVsCodeWindow;
                if (codeWin != null)
                {
                    ErrorHandler.ThrowOnFailure(codeWin.GetLastActiveView(out textView));
                }
            }
            return textView;
        }

        private static IWpfTextView GetTextViewFromVsTextView(IVsTextView view)
        {

            if (view == null)
            {
                throw new ArgumentNullException("view");
            }

            IVsUserData userData = view as IVsUserData;
            if (userData == null)
            {
                throw new InvalidOperationException();
            }

            object objTextViewHost;
            if (VSConstants.S_OK
                   != userData.GetData(Microsoft.VisualStudio
                                                .Editor
                                                .DefGuidList.guidIWpfTextViewHost,
                                       out objTextViewHost))
            {
                throw new InvalidOperationException();
            }

            IWpfTextViewHost textViewHost = objTextViewHost as IWpfTextViewHost;
            if (textViewHost == null)
            {
                throw new InvalidOperationException();
            }

            return textViewHost.TextView;
        }

        /// <summary>
        /// Given an IWpfTextView, find the position of the caret and report its column
        /// number. The column number is 0-based
        /// </summary>
        /// <param name="textView">The text view containing the caret</param>
        /// <returns>The column number of the caret's position. When the caret is at the
        /// leftmost column, the return value is zero.</returns>
        private static int GetCaretColumn(IWpfTextView textView)
        {
            // This is the code the editor uses to populate the status bar.
            Microsoft.VisualStudio.Text.Formatting.ITextViewLine caretViewLine =
                textView.Caret.ContainingTextViewLine;
            double columnWidth = textView.FormattedLineSource.ColumnWidth;
            return (int)(Math.Round((textView.Caret.Left - caretViewLine.Left)
                                       / columnWidth));
        }

        /// <summary>
        /// Determine the applicable column number for an add or remove command.
        /// The column is parsed from command arguments, if present. Otherwise
        /// the current position of the caret is used to determine the column.
        /// </summary>
        /// <param name="e">Event args passed to the command handler.</param>
        /// <returns>The column number. May be negative to indicate the column number is
        /// unavailable.</returns>
        /// <exception cref="ArgumentException">The column number parsed from event args
        /// was not a valid integer.</exception>
        private int GetApplicableColumn(EventArgs e)
        {
            var inValue = ((OleMenuCmdEventArgs)e).InValue as string;
            if (!string.IsNullOrEmpty(inValue))
            {
                int column;
                if (!int.TryParse(inValue, out column) || column < 0)
                    throw new ArgumentException("Invalid column");
                return column;
            }

            return GetCurrentEditorColumn();
        }

        /// <summary>
        /// This function is the callback used to execute a command when the a menu item
        /// is clicked. See the Initialize method to see how the menu item is associated
        /// to this function using the OleMenuCommandService service and the MenuCommand
        /// class.
        /// </summary>
        private void AddColumnGuideExecuted(object sender, EventArgs e)
        {
            int column = GetApplicableColumn(e);
            if (column >= 0)
            {
                GuidesSettingsManager.AddGuideline(column);
            }
        }

        private void RemoveColumnGuideExecuted(object sender, EventArgs e)
        {
            int column = GetApplicableColumn(e);
            if (column >= 0)
            {
                GuidesSettingsManager.RemoveGuideline(column);
            }
        }

        private void RemoveAllGuidelinesExecuted(object sender, EventArgs e)
        {
            GuidesSettingsManager.RemoveAllGuidelines();
        }

        private void ChooseGuideColorExecuted(object sender, EventArgs e)
        {
            System.Windows.Media.Color color = GuidesSettingsManager.GuidelinesColor;

            using (System.Windows.Forms.ColorDialog picker =
                new System.Windows.Forms.ColorDialog())
            {
                picker.Color = System.Drawing.Color.FromArgb(255, color.R, color.G,
                                                             color.B);
                if (picker.ShowDialog() == System.Windows.Forms.DialogResult.OK)
                {
                    GuidesSettingsManager.GuidelinesColor =
                        System.Windows.Media.Color.FromRgb(picker.Color.R,
                                                           picker.Color.G,
                                                           picker.Color.B);
                }
            }
        }

    }
}

```

**Исправление ссылок**. На этом этапе отсутствует ссылка. Нажмите правую кнопку указателя в узле ссылки в обозреватель решений. Выберите команду **Добавить...** . В правом верхнем углу диалогового окна **Добавление ссылки** есть поле поиска. Введите "Editor" (без двойных кавычек). Выберите элемент **Microsoft. VisualStudio. Editor** (необходимо установить флажок слева от элемента, а не просто выберите элемент) и нажмите кнопку **ОК** , чтобы добавить ссылку.

**Инициализация**.  При инициализации класса Package он вызывает `Initialize` класс реализации Commands. `ColumnGuideCommands`Инициализация создает экземпляр класса и сохраняет экземпляр класса и ссылку на пакет в членах класса.

Рассмотрим один из перехватчиков обработчика команд из конструктора класса:

```csharp
_addGuidelineCommand =
    new OleMenuCommand(AddColumnGuideExecuted, null,
                       AddColumnGuideBeforeQueryStatus,
                       new CommandID(ColumnGuideCommands.CommandSet,
                                     cmdidAddColumnGuide));

```

Создайте `OleMenuCommand` . Visual Studio использует Microsoft Officeую систему команд. Ключевыми аргументами при создании экземпляра `OleMenuCommand` является функция, которая реализует команду ( `AddColumnGuideExecuted` ), функцию, вызываемую, когда Visual Studio отображает меню с командой ( `AddColumnGuideBeforeQueryStatus` ) и идентификатором команды. Visual Studio вызывает функцию состояния запроса перед отображением команды в меню, чтобы команда могла сделать ее невидимой или непрозрачной для конкретного отображения меню (например, отключение **копирования** , если нет выделения), изменить его значок или даже изменить его имя (например, добавить что-нибудь для удаления) и т. д. Идентификатор команды должен соответствовать ИДЕНТИФИКАТОРу команды, объявленному в *vsct* -файле. Строки для набора команд и руководства по столбцам Add должны совпадать между файлом *. vsct* и *колумнгуидекоммандс. CS*.

Следующая строка предоставляет справку, когда пользователи вызывают команду через командное окно (см. описание ниже):

```csharp
_addGuidelineCommand.ParametersDescription = "<column>";
```

 **Состояние запроса**. Функции состояния запроса `AddColumnGuideBeforeQueryStatus` и `RemoveColumnGuideBeforeQueryStatus` Проверьте некоторые параметры (например, максимальное число руководств или столбец max) или, если имеется руководство по столбцам для удаления. Они включают команды, если условия верны.  Функции состояния запросов должны быть эффективными, так как они выполняются каждый раз, когда Visual Studio отображает меню и для каждой команды в меню.

 **Функция аддколумнгуидиксекутед**. Интересной частью добавления руководств является определение текущего представления редактора и положения курсора.  Во-первых, эта функция вызывает метод `GetApplicableColumn` , который проверяет, есть ли в аргументах события обработчика команды аргумент, указанный пользователем, и, если нет, функция проверяет представление редактора:

```csharp
private int GetApplicableColumn(EventArgs e)
{
    var inValue = ((OleMenuCmdEventArgs)e).InValue as string;
    if (!string.IsNullOrEmpty(inValue))
    {
        int column;
        if (!int.TryParse(inValue, out column) || column < 0)
            throw new ArgumentException("Invalid column");
        return column;
    }

    return GetCurrentEditorColumn();
}

```

`GetCurrentEditorColumn` чтобы получить представление кода, необходимо немного подробно изучить <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView> его.  При трассировке с помощью `GetActiveTextView` , `GetActiveView` и `GetTextViewFromVsTextView` можно увидеть, как это сделать. Следующий код является абстрактным и связанным с ним, начиная с текущего выбора, получая рамку выбора, получая DocView кадра как <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> , а затем получая <xref:Microsoft.VisualStudio.TextManager.Interop.IVsUserData> из IVsTextView, получая узел представления и, наконец, IWpfTextView:

```csharp
   IVsMonitorSelection selection =
       this.ServiceProvider.GetService(typeof(IVsMonitorSelection))
           as IVsMonitorSelection;
   object frameObj = null;

ErrorHandler.ThrowOnFailure(selection.GetCurrentElementValue(
                                (uint)VSConstants.VSSELELEMID.SEID_DocumentFrame,
                                out frameObj));

   IVsWindowFrame frame = frameObj as IVsWindowFrame;
   if (frame == null)
       <<do nothing>>;

...
   object pvar;
   ErrorHandler.ThrowOnFailure(frame.GetProperty((int)__VSFPROPID.VSFPROPID_DocView,
                                                  out pvar));

   IVsTextView textView = pvar as IVsTextView;
   if (textView == null)
   {
       IVsCodeWindow codeWin = pvar as IVsCodeWindow;
       if (codeWin != null)
       {
           ErrorHandler.ThrowOnFailure(codeWin.GetLastActiveView(out textView));
       }
   }

...
   if (textView == null)
       <<do nothing>>

   IVsUserData userData = textView as IVsUserData;
   if (userData == null)
       <<do nothing>>

   object objTextViewHost;
   if (VSConstants.S_OK
           != userData.GetData(Microsoft.VisualStudio.Editor.DefGuidList
                                                            .guidIWpfTextViewHost,
                                out objTextViewHost))
   {
       <<do nothing>>
   }

   IWpfTextViewHost textViewHost = objTextViewHost as IWpfTextViewHost;
   if (textViewHost == null)
       <<do nothing>>

   IWpfTextView textView = textViewHost.TextView;

```

После создания IWpfTextView можно получить столбец, в котором находится курсор:

```csharp
private static int GetCaretColumn(IWpfTextView textView)
{
    // This is the code the editor uses to populate the status bar.
    Microsoft.VisualStudio.Text.Formatting.ITextViewLine caretViewLine =
        textView.Caret.ContainingTextViewLine;
    double columnWidth = textView.FormattedLineSource.ColumnWidth;
    return (int)(Math.Round((textView.Caret.Left - caretViewLine.Left)
                                / columnWidth));
}

```

При наличии текущего столбца, в котором пользователь щелкнул, код просто вызывает диспетчер параметров для добавления или удаления столбца. Диспетчер параметров запускает событие, которое `ColumnGuideAdornment` прослушивает все объекты. При возникновении события эти объекты обновляют связанные текстовые представления с помощью новых параметров руководств по столбцам.

## <a name="invoke-command-from-the-command-window"></a>Вызвать команду из командного окна
Образец «направляющие столбцов» позволяет пользователям вызывать две команды из командного окна как форму расширяемости. При использовании команды **просмотреть &#124; другие окна &#124;** командной строки можно увидеть командное окно. Вы можете взаимодействовать с командным окном, введя "Edit.", а с завершением имени команды и указав аргумент 120, у вас есть следующий результат:

```csharp
> Edit.AddColumnGuide 120
>
```

Фрагменты примера, обеспечивающие такое поведение, находятся в объявлении файла *. vsct* , `ColumnGuideCommands` конструкторе класса, когда он подключается к обработчикам команд, а также к реализациям обработчика команд, которые проверяют аргументы события.

Вы видели " `<CommandFlag>CommandWellOnly</CommandFlag>` " в *vsct* файле, а также места размещения в главном меню **редактирования** , даже если команды не отображаются в пользовательском интерфейсе меню " **Правка** ". Наличие этих файлов в главном меню **редактирования** дает им такие имена, как **Edit. аддколумнгуиде**. Объявление группы команд, которое содержит четыре команды, поместили группу в меню **Правка** напрямую:

```xml
<Group guid="guidColumnGuidesCommandSet" id="GuidesMenuItemsGroup"
             priority="0xB801">
        <Parent guid="guidSHLMainMenu" id="IDM_VS_MENU_EDIT" />
      </Group>

```

В разделе Buttons далее объявлены команды, `CommandWellOnly` чтобы они оставались невидимыми в главном меню и были объявлены с помощью `AllowParams` :

```xml
<Button guid="guidColumnGuidesCommandSet" id="cmdidAddColumnGuide"
        priority="0x0100" type="Button">
  <Parent guid="guidColumnGuidesCommandSet" id="GuidesMenuItemsGroup" />
  <Icon guid="guidImages" id="bmpPicAddGuide" />
  <CommandFlag>CommandWellOnly</CommandFlag>
  <CommandFlag>AllowParams</CommandFlag>

```

Вы видели, что обработчик команд разрешил код в `ColumnGuideCommands` конструкторе класса, который предоставил описание разрешенного параметра:

```csharp
_addGuidelineCommand.ParametersDescription = "<column>";

```

Вы видели, что `GetApplicableColumn` функция проверяет `OleMenuCmdEventArgs` наличие значения перед проверкой представления в редакторе для текущего столбца:

```csharp
private int GetApplicableColumn(EventArgs e)
{
    var inValue = ((OleMenuCmdEventArgs)e).InValue as string;
    if (!string.IsNullOrEmpty(inValue))
    {
        int column;
        if (!int.TryParse(inValue, out column) || column < 0)
            throw new ArgumentException("Invalid column");
        return column;
    }

```

## <a name="try-your-extension"></a>Попробуйте расширение
Теперь можно нажать клавишу **F5** , чтобы выполнить расширение руководств по столбцам. Откройте текстовый файл и используйте контекстное меню редактора, чтобы добавить направляющие, удалить их и изменить их цвет. Щелкните текст (не допустить пробела, переданного в конце строки), чтобы добавить подпрограмму столбца, или редактор добавит его в последний столбец в строке. Если вы используете командное окно и вызываете команды с аргументом, можно добавить направляющие столбцов в любом месте.

Если вы хотите попробовать различные размещения команд, изменить имена, изменить значки и т. д. при возникновении каких-либо проблем с Visual Studio, в которых отображается последний код в меню, можно сбросить экспериментальный куст, в котором выполняется отладка. Откройте меню " **Пуск" Windows** и введите "Сброс". Найдите и выполните команду, **сбросьте следующий экспериментальный экземпляр Visual Studio**. Эта команда очищает экспериментальный куст реестра для всех компонентов расширения. Он не очищает параметры от компонентов, поэтому все руководства, которые вы использовали при завершении работы экспериментального куста Visual Studio, остаются там, когда код считывает хранилище параметров при следующем запуске.

## <a name="finished-code-project"></a>Завершенный проект кода
Вскоре будет проект GitHub с примерами расширяемости Visual Studio, и готовым проектом будет. Эта статья будет обновлена, чтобы указать, когда это произойдет. Завершенный пример проекта может иметь разные идентификаторы GUID, и для значков команд будут заданы разные ленты точечных рисунков.

С помощью этого[расширения](https://marketplace.visualstudio.com/items?itemName=PaulHarrington.EditorGuidelines)коллекции Visual Studio можно опробовать версию руководства по столбцам.

## <a name="see-also"></a>См. также
- [Внутри редактора](../extensibility/inside-the-editor.md)
- [Расширение редактора и языковых служб](../extensibility/extending-the-editor-and-language-services.md)
- [Точки расширения языковой службы и редактора](../extensibility/language-service-and-editor-extension-points.md)
- [Расширение меню и команд](../extensibility/extending-menus-and-commands.md)
- [Добавление подменю в меню](../extensibility/adding-a-submenu-to-a-menu.md)
- [Создание расширения с помощью шаблона элемента редактора](../extensibility/creating-an-extension-with-an-editor-item-template.md)
