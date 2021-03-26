---
title: Адресация DPI Issues2 | Документация Майкрософт
description: Узнайте о проблемах, связанных с программированием для экранов с высоким разрешением, таких как масштабирование содержимого, проблемы с макетом и использование API масштабирования DPI.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 359184aa-f5b6-4b6c-99fe-104655b3a494
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 9cf7b4fe19cdefe11b77de1418b16454089f45c6
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105097517"
---
# <a name="address-dpi-issues"></a>Устранение проблем с DPI
Увеличение количества устройств поставляются с экранами с высоким разрешением. Обычно эти экраны имеют более 200 пикселей на дюйм (PPI). Для работы с приложением на этих компьютерах потребуется масштабирование содержимого в соответствии с потребностями просмотра содержимого на нормальном уровне просмотра для устройства. Начиная с 2014, основным целевым объектом для отображения высокой плотности являются мобильные вычислительные устройства (планшеты, портативные компьютеры кламшелл и телефоны).

Windows 8.1 и выше содержит несколько функций, позволяющих этим компьютерам работать с экранами и средами, в которых компьютер подключен одновременно к экранам с высокой плотностью и плотности уровня "Стандартный".

- Windows позволяет масштабировать содержимое на устройстве с помощью параметра "увеличить или уменьшить размер текста и других элементов" (доступно с момента выпуска Windows XP).

- Windows 8.1 и выше автоматически масштабирует содержимое для большинства приложений, чтобы оно было согласовано при перемещении между дисплеями различной плотности пикселей. Если основной дисплей имеет высокую плотность (200% масштабирования), а дополнительный дисплей имеет стандартную плотность (100%), Windows автоматически масштабирует содержимое окна приложения на дополнительном дисплее (1 пиксель отображается для каждого 4 пикселя, отображаемого приложением).

- По умолчанию Windows будет правильно масштабироваться по мере увеличения плотности пикселей и расстояния при просмотре (Windows 7 и более поздней версии, настраиваемый изготовителем оборудования).

- Windows может автоматически масштабировать содержимое до 250% на новых устройствах, превышающих 280 PPI (начиная с Windows 8.1 S14).

  Windows имеет способ работы с масштабированием пользовательского интерфейса, чтобы воспользоваться преимуществами увеличения числа пикселей. Приложение переключается на эту систему, объявляя саму себя "Системное разрешение DPI". Приложения, не проявляющиеся этого, масштабируются системой. Это может привести к «нечеткому» интерфейсу, в котором все приложение полностью растянуто в пикселях. Пример:

  ![Проблемы с четкостью DPI](../extensibility/media/dpi-issues-fuzzy.png "Проблемы с четкостью DPI")

  Visual Studio имеет разрешение на масштабирование DPI и, следовательно, не является виртуализированным.

  Windows (и Visual Studio) используют несколько технологий пользовательского интерфейса, которые имеют разные способы работы с коэффициентами масштабирования, заданными системой. Пример:

- WPF измеряет элементы управления независимо от устройства (единицы, а не пикселы). Пользовательский интерфейс WPF автоматически масштабируется для текущего DPI.

- Все размеры текста, независимо от платформы пользовательского интерфейса, выражаются в точках, поэтому они обрабатываются системой как независимые от точек на дюйм. Текст в Win32, WinForms и WPF уже правильно масштабируется при прорисовке на устройстве отображения.

- Диалоговые окна Win32/WinForms и Windows имеют средства для включения макета, который изменяет размер текста (например, с помощью панелей макета сетки, потоков и таблиц). Они позволяют избежать жестко запрограммированных расположений пикселей, которые не масштабируются при увеличении размеров шрифтов.

- Значки, предоставляемые системой или ресурсами на основе системных метрик (например, SM_CXICON и SM_CXSMICON), уже масштабируются.

## <a name="older-win32-gdi-gdi-and-winforms-based-ui"></a>Более старые Win32 (GDI, GDI+) и пользовательский интерфейс на основе WinForms
Хотя WPF уже поддерживает высокое разрешение DPI, большая часть кода на основе Win32/GDI не была первоначально написана с учетом особенностей DPI. Windows предоставляет API масштабирования DPI. Исправления проблем Win32 должны использовать их единообразно в рамках продукта. Visual Studio предоставила вспомогательную библиотеку классов, чтобы избежать дублирования функциональности и обеспечения согласованности по продуктам.

## <a name="high-resolution-images"></a>Изображения с высоким разрешением
Этот раздел предназначен главным образом для разработчиков, расширяющих Visual Studio 2013. Для Visual Studio 2015 используйте службу образов, встроенную в Visual Studio. Кроме того, может оказаться, что вам нужно поддерживать и нацелить многие версии Visual Studio, поэтому использование службы образов в 2015 не является вариантом, поскольку он не существует в предыдущих версиях. Этот раздел также предназначен для вас.

## <a name="scaling-up-images-that-are-too-small"></a>Масштабирование слишком маленьких изображений
Слишком маленькие изображения можно масштабировать и визуализировать в GDI и WPF с помощью некоторых распространенных методов. Управляемые классы поддержки DPI доступны внутренним и внешним интеграторам Visual Studio для адресации значков масштабирования, точечных рисунков, имажестрипс и ImageList. Встроенные вспомогательные функции на основе Win32 C/C + + доступны для масштабирования ХИКОН, ХБИТМАП, ХИМАЖЕЛИСТ и VsUI:: Гдиплусимаже. Для масштабирования растрового изображения обычно требуется только однострочное изменение после включения ссылки на вспомогательную библиотеку. Пример:

```cpp
(Unmanaged) VsUI::DpiHelper::LogicalToDeviceUnits(&hBitmap);
```

```csharp
(WinForms) DpiHelper.LogicalToDeviceUnits(ref image);
```

Масштабирование ImageList зависит от того, заполнено ли ImageList во время загрузки или добавляется во время выполнения. В случае завершения во время загрузки вызовите `LogicalToDeviceUnits()` с ImageList так же, как точечный рисунок. Когда коду необходимо загрузить отдельное растровое изображение, прежде чем создавать ImageList, необходимо масштабировать размер изображения ImageList:

```csharp
imagelist.ImageSize = DpiHelper.LogicalToDeviceUnits(imagelist.ImageSize);
```

В машинном коде измерения можно масштабировать при создании ImageList следующим образом.

```cpp
ImageList_Create(VsUI::DpiHelper::LogicalToDeviceUnitsX(16),VsUI::DpiHelper::LogicalToDeviceUnitsY(16), ILC_COLOR32|ILC_MASK, nCount, 1);
```

Функции в библиотеке позволяют указать алгоритм изменения размера. При масштабировании изображений для размещения в ImageList обязательно укажите цвет фона, используемый для прозрачности, или используйте масштабирование Неарестнеигхбор (что приведет к искажениям в 125% и 150%).

Обратитесь к <xref:Microsoft.VisualStudio.PlatformUI.DpiHelper> документации на MSDN.

В следующей таблице приведены примеры масштабирования изображений по соответствующим коэффициентам масштабирования DPI. Изображения, приведенные в оранжевой части, обозначают нашу рекомендацию на Visual Studio 2013 (масштабирование 100%-200% DPI):

![Масштабирование в проблемах с DPI](../extensibility/media/dpi-issues-scaling.png "Масштабирование в проблемах с DPI")

## <a name="layout-issues"></a>Проблемы с макетом
Распространенные проблемы с макетом можно избежать в первую очередь, сохраняя точки в пользовательском интерфейсе и относительные, а не используя абсолютные расположения (в частности, в пикселных единицах). Пример:

- Положение макета или текста должно быть настроено для учета масштабируемых изображений.

- Ширина столбцов в сетках должна быть скорректирована для масштабируемого текста.

- Также необходимо выполнить масштабирование жестко запрограммированных размеров или пространства между элементами. Размеры, основанные только на текстовых измерениях, обычно хорошо, так как шрифты автоматически масштабируются.

  Вспомогательные функции доступны в классе, <xref:Microsoft.VisualStudio.PlatformUI.DpiHelper> чтобы разрешить масштабирование по осям X и Y:

- Логикалтодевицеунитскс/Логикалтодевицеунитси (функции разрешают масштабирование по оси X и Y)

- int Space = Дпихелпер. Логикалтодевицеунитскс (10);

- int Height = VsUI::D Пихелпер:: Логикалтодевицеунитси (5);

  Существуют перегрузки Логикалтодевицеунитс, позволяющие масштабировать такие объекты, как Rect, Point и Size.

## <a name="using-the-dpihelper-libraryclass-to-scale-images-and-layout"></a>Использование библиотеки или класса Дпихелпер для масштабирования изображений и макета
Вспомогательная библиотека DPI в Visual Studio доступна в собственных и управляемых формах и может использоваться вне оболочки Visual Studio другими приложениями.

Чтобы использовать библиотеку, перейдите к [примерам расширяемости Visual Studio VSSDK](https://github.com/Microsoft/VSSDK-Extensibility-Samples) и выполните клонирование образца High-DPI_Images_Icons.

В исходные файлы включите *всуидпихелпер. h* и вызовите статические функции `VsUI::DpiHelper` класса:

```cpp
#include "VsUIDpiHelper.h"

int cxScaled = VsUI::DpiHelper::LogicalToDeviceUnitsX(cx);
VsUI::DpiHelper::LogicalToDeviceUnits(&hBitmap);

```

> [!NOTE]
> Не используйте вспомогательные функции в статических переменных уровня модуля или класса. Библиотека также использует статические элементы для синхронизации потоков и может быть вызвана проблемами инициализации порядка. Либо преобразуйте эти статические значения в нестатические переменные-члены, либо заключите их в функцию (чтобы они создавались при первом доступе).

Для доступа к вспомогательным функциям DPI из управляемого кода, которые будут выполняться в среде Visual Studio:

- Проект использования должен ссылаться на последнюю версию оболочки MPF. Пример:

    ```csharp
    <Reference Include="Microsoft.VisualStudio.Shell.14.0.dll" />
    ```

- Убедитесь, что проект содержит ссылки на **System. Windows. Forms**, **PresentationCore** и **пресентатионуи**.

- В коде используйте пространство имен **Microsoft. VisualStudio. платформуи** и вызовите статические функции класса дпихелпер. Для поддерживаемых типов (точек, размеров, прямоугольников и т. д.) предусмотрены функции расширения, возвращающие новые масштабируемые объекты. Пример:

    ```csharp
    using Microsoft.VisualStudio.PlatformUI;
    double x = DpiHelper.LogicalToDeviceUnitsX(posX);
    Point ptScaled = ptOriginal.LogicalToDeviceUnits();
    DpiHelper.LogicalToDeviceUnits(ref bitmap);

    ```

## <a name="dealing-with-wpf-image-fuzziness-in-zoomable-ui"></a>Работа с нечеткими изображениями WPF в пользовательском интерфейсе масштабируемый
В WPF размер точечных рисунков автоматически изменяется в WPF для текущего масштаба DPI с помощью высококачественного алгоритма бикубический (по умолчанию), который хорошо подходит для изображений или крупных снимков экрана, но не подходит для значков пунктов меню, так как в нем реализовано восприятное нечеткое представление.

Рекомендации

- Для изображения логотипа и баннеров <xref:System.Windows.Media.BitmapScalingMode> можно использовать режим изменения размера по умолчанию.

- Для пунктов меню и изображений иконографи <xref:System.Windows.Media.BitmapScalingMode> следует использовать, если это не вызывает других артефактов искажения для исключения нечеткости (в 200% и 300%).

- Для крупных уровней масштабирования, не кратных 100% (например, 250% или 350%), масштабирование иконографи изображений с помощью бикубический приводит к нечеткому, размытому пользовательскому интерфейсу. Лучший результат достигается путем первого масштабирования изображения с Неарестнеигхбор до самого большого числа, кратного 100% (например, 200% или 300%). и масштабирование с бикубический. Дополнительные сведения см. в разделе особый случай: предмасштабирование изображений WPF для крупных точек на дюйм.

  Класс Дпихелпер в пространстве имен Microsoft. VisualStudio. платформуи предоставляет элемент <xref:System.Windows.Media.BitmapScalingMode> , который можно использовать для привязки. Это позволит оболочке Visual Studio управлять режимом масштабирования растрового изображения по всему продукту, в зависимости от коэффициента масштабирования DPI.

  Чтобы использовать его в XAML, добавьте:

```xaml
xmlns:vsui="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.14.0"

<Setter Property="RenderOptions.BitmapScalingMode" Value="{x:Static vs:DpiHelper.BitmapScalingMode}" />

```

Оболочка Visual Studio уже устанавливает это свойство в окнах и диалоговых окнах верхнего уровня. Пользовательский интерфейс на основе WPF, выполняющийся в Visual Studio, уже наследует его. Если параметр не распространяется на определенные элементы пользовательского интерфейса, его можно задать в корневом элементе пользовательского интерфейса XAML или WPF. Места, где это происходит, включают всплывающие окна, элементы с родительскими элементами Win32 и окна конструктора, которые выполняются вне процесса, например Blend.

Некоторые элементы пользовательского интерфейса могут масштабироваться независимо от уровня масштабирования DPI на уровне системы, например текстового редактора Visual Studio и конструкторов на основе WPF (классических приложений WPF и магазина Windows). В таких случаях не следует использовать Дпихелпер. BitmapScalingMode. Чтобы устранить эту проблему в редакторе, Группа разработки IDE создала пользовательское свойство с именем RenderOptions. BitmapScalingMode. Задайте для этого свойства значение Хигхкуалити или Неарестнеигхбор в зависимости от общего уровня масштабирования системы и пользовательского интерфейса.

## <a name="special-case-prescaling-wpf-images-for-large-dpi-levels"></a>Особый случай: предмасштабирование изображений WPF для уровней с большим значением DPI
Для очень больших уровней масштаба, которые не кратны 100% (например, 250%, 350% и т. д.), масштабирование иконографи изображений с бикубический приводит к нечеткому пользовательскому интерфейсу. Впечатление, что эти изображения обходиться рядом с четким текстом, почти так же, как и для оптической иллюзии. Изображения выглядят ближе к глазу и не имеют фокуса относительно текста. Результат масштабирования в этом увеличенном размере можно улучшить, увеличив масштаб изображения с Неарестнеигхбор до самого большого числа, кратного 100% (например, 200% или 300%). и масштабирование с бикубический на остаток (дополнительный 50%).

Ниже приведен пример различий в результатах, где первое изображение масштабируется с помощью улучшенного алгоритма двойного масштабирования 100%->200%->250%, а второй — только с бикубический 100%->250%.

![Вопросы DPI пример двойного масштабирования](../extensibility/media/dpi-issues-double-scaling-example.png "Вопросы DPI пример двойного масштабирования")

Чтобы разрешить пользовательскому интерфейсу использовать это двойное масштабирование, разметка XAML для отображения каждого элемента изображения потребуется изменить. В следующих примерах демонстрируется использование двойного масштабирования в WPF в Visual Studio с помощью библиотеки Дпихелпер и оболочки. 12/14.

Шаг 1. масштабирование образа до 200%, 300% и т. д. с помощью Неарестнеигхбор.

Предобразировать изображение можно с помощью преобразователя, примененного к привязке, или с расширением разметки XAML. Пример:

```xaml
<vsui:DpiPrescaleImageSourceConverter x:Key="DpiPrescaleImageSourceConverter" />

<Image Source="{Binding Path=SelectedImage, Converter={StaticResource DpiPrescaleImageSourceConverter}}" Width="16" Height="16" />

<Image Source="{vsui:DpiPrescaledImage Images/Help.png}" Width="16" Height="16" />

```

Если образ также должен быть темой (большинство, если не все, должен), разметка может использовать другой преобразователь, который сначала выполняет их, а затем предварительно масштабирует. Разметка может использовать либо <xref:Microsoft.VisualStudio.PlatformUI.DpiPrescaleThemedImageConverter> или <xref:Microsoft.VisualStudio.PlatformUI.DpiPrescaleThemedImageSourceConverter> , в зависимости от требуемого выхода преобразования.

```xaml
<vsui:DpiPrescaleThemedImageSourceConverter x:Key="DpiPrescaleThemedImageSourceConverter" />

<Image Width="16" Height="16">
  <Image.Source>
    <MultiBinding Converter="{StaticResource DpiPrescaleThemedImageSourceConverter}">
      <Binding Path="Icon" />
      <Binding Path="(vsui:ImageThemingUtilities.ImageBackgroundColor)"
               RelativeSource="{RelativeSource Self}" />
      <Binding Source="{x:Static vsui:Boxes.BooleanTrue}" />
    </MultiBinding>
  </Image.Source>
</Image>
```

Шаг 2. Убедитесь, что конечный размер правильный для текущего DPI.

Поскольку WPF масштабирует пользовательский интерфейс для текущего DPI, используя свойство BitmapScalingMode, заданное для UIElement, элемент управления Image с использованием предмасштабированного изображения, так как его источник будет выглядеть вдвое или в три раза больше, чем должно. Ниже приведены два способа определения этого результата.

- Если известно измерение исходного изображения в 100%, можно указать точный размер элемента управления изображения. Эти размеры будут отражать размер пользовательского интерфейса до применения масштабирования.

    ```xaml
    <Image Source="{Binding Path=SelectedImage, Converter={StaticResource DpiPrescaleImageSourceConverter}}" Width="16" Height="16" />
    ```

- Если размер исходного изображения неизвестен, можно использовать LayoutTransform для масштабирования объекта окончательного изображения. Пример:

    ```xaml
    <Image Source="{Binding Path=SelectedImage, Converter={StaticResource DpiPrescaleImageSourceConverter}}" >
        <Image.LayoutTransform>
            <ScaleTransform
                ScaleX="{x:Static vsui:DpiHelper.PreScaledImageLayoutTransformScale}"
                ScaleY="{x:Static vsui:DpiHelper.PreScaledImageLayoutTransformScale}" />
        </Image.LayoutTransform>
    </Image>
    ```

## <a name="enabling-hdpi-support-to-the-weboc"></a>Включение поддержки HDPI для Вебок
По умолчанию элементы управления Вебок (например, элемент управления WebBrowser в WPF или интерфейс IWebBrowser2) не поддерживают обнаружение и поддержку HDPI. Результатом будет встроенный элемент управления с отображаемым содержимым, которое слишком мало на дисплее с высоким разрешением. Ниже описано, как включить поддержку высокого DPI в определенном экземпляре веб-Вебок.

Реализуйте интерфейс Идочостуихандлер (см. статью MSDN в разделе [идочостуихандлер](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753260(v=vs.85)):

```idl
[ComImport, InterfaceType(ComInterfaceType.InterfaceIsIUnknown),
 Guid("BD3F23C0-D43E-11CF-893B-00AA00BDCE1A")]
public interface IDocHostUIHandler
{
    [return: MarshalAs(UnmanagedType.I4)]
    [PreserveSig]
    int ShowContextMenu(
        [In, MarshalAs(UnmanagedType.U4)] int dwID,
        [In] POINT pt,
        [In, MarshalAs(UnmanagedType.Interface)] object pcmdtReserved,
        [In, MarshalAs(UnmanagedType.IDispatch)] object pdispReserved);
    [return: MarshalAs(UnmanagedType.I4)]
    [PreserveSig]
    int GetHostInfo([In, Out] DOCHOSTUIINFO info);
    [return: MarshalAs(UnmanagedType.I4)]
    [PreserveSig]
    int ShowUI(
        [In, MarshalAs(UnmanagedType.I4)] int dwID,
        [In, MarshalAs(UnmanagedType.Interface)] object activeObject,
        [In, MarshalAs(UnmanagedType.Interface)] object commandTarget,
        [In, MarshalAs(UnmanagedType.Interface)] object frame,
        [In, MarshalAs(UnmanagedType.Interface)] object doc);
    [return: MarshalAs(UnmanagedType.I4)]
    [PreserveSig]
    int HideUI();
    [return: MarshalAs(UnmanagedType.I4)]
    [PreserveSig]
    int UpdateUI();
    [return: MarshalAs(UnmanagedType.I4)]
    [PreserveSig]
    int EnableModeless([In, MarshalAs(UnmanagedType.Bool)] bool fEnable);
    [return: MarshalAs(UnmanagedType.I4)]
    [PreserveSig]
    int OnDocWindowActivate([In, MarshalAs(UnmanagedType.Bool)] bool fActivate);
    [return: MarshalAs(UnmanagedType.I4)]
    [PreserveSig]
    int OnFrameWindowActivate([In, MarshalAs(UnmanagedType.Bool)] bool fActivate);
    [return: MarshalAs(UnmanagedType.I4)]
    [PreserveSig]
    int ResizeBorder(
        [In] COMRECT rect,
        [In, MarshalAs(UnmanagedType.Interface)] object doc,
        bool fFrameWindow);
    [return: MarshalAs(UnmanagedType.I4)]
    [PreserveSig]
    int TranslateAccelerator(
        [In] ref MSG msg,
        [In] ref Guid group,
        [In, MarshalAs(UnmanagedType.I4)] int nCmdID);
    [return: MarshalAs(UnmanagedType.I4)]
    [PreserveSig]
    int GetOptionKeyPath(
        [Out, MarshalAs(UnmanagedType.LPArray)] string[] pbstrKey,
        [In, MarshalAs(UnmanagedType.U4)] int dw);
    [return: MarshalAs(UnmanagedType.I4)]
    [PreserveSig]
    int GetDropTarget(
        [In, MarshalAs(UnmanagedType.Interface)] IOleDropTarget pDropTarget,
        [MarshalAs(UnmanagedType.Interface)] out IOleDropTarget ppDropTarget);
    [return: MarshalAs(UnmanagedType.I4)]
    [PreserveSig]
    int GetExternal([MarshalAs(UnmanagedType.IDispatch)] out object ppDispatch);
    [return: MarshalAs(UnmanagedType.I4)]
    [PreserveSig]
    int TranslateUrl(
        [In, MarshalAs(UnmanagedType.U4)] int dwTranslate,
        [In, MarshalAs(UnmanagedType.LPWStr)] string strURLIn,
        [MarshalAs(UnmanagedType.LPWStr)] out string pstrURLOut);
    [return: MarshalAs(UnmanagedType.I4)]
    [PreserveSig]
    int FilterDataObject(
        IDataObject pDO,
        out IDataObject ppDORet);
    }
```

При необходимости реализуйте интерфейс Икустомдок (см. статью MSDN в разделе [икустомдок](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753272(v=vs.85)):

```idl
[InterfaceType(ComInterfaceType.InterfaceIsIUnknown),
 Guid("3050F3F0-98B5-11CF-BB82-00AA00BDCE0B")]
public interface ICustomDoc
{
    void SetUIHandler(IDocHostUIHandler pUIHandler);
}
```

Свяжите класс, реализующий Идочостуихандлер, с документом Вебок. Если вы реализовали интерфейс Икустомдок выше, то как только свойство документа Вебок является допустимым, приведите его к Икустомдок и вызовите метод Сетуихандлер, передав класс, реализующий Идочостуихандлер.

```csharp
// "this" references that class that owns the WebOC control and in this case also implements the IDocHostUIHandler interface
ICustomDoc customDoc = (ICustomDoc)webBrowser.Document;
customDoc.SetUIHandler(this);

```

Если вы не реализовали интерфейс Икустомдок, то как только свойство документа Вебок является допустимым, необходимо привести его к Иолеобжект и вызвать `SetClientSite` метод, передав класс, реализующий идочостуихандлер. Установите флаг DOCHOSTUIFLAG_DPI_AWARE для ДОЧОСТУИИНФО, переданного в `GetHostInfo` вызов метода:

```csharp
public int GetHostInfo(DOCHOSTUIINFO info)
{
    // This is what the default site provides.
    info.dwFlags = (DOCHOSTUIFLAG)0x5a74012;
    // Add the DPI flag to the defaults
    info.dwFlags |=.DOCHOSTUIFLAG.DOCHOSTUIFLAG_DPI_AWARE;
    return S_OK;
}
```

Это должно быть все, что необходимо для получения элемента управления Вебок для поддержки ХПДИ.

## <a name="tips"></a>Советы

1. Если свойство Document элемента управления Вебок изменяется, может потребоваться повторно связать документ с классом Идочостуихандлер.

2. Если приведенный выше объект не работает, существует известная ошибка, связанная с Вебок, не изменяя флаг DPI. Самый надежный способ устранения этой проблемы — переключить оптический масштаб Вебок, то есть два вызова с двумя разными значениями для масштабирования в процентах. Кроме того, если это решение требуется, может потребоваться выполнить его при каждом вызове функции навигации.

    ```csharp
    // browser2 is a SHDocVw.IWebBrowser2 in this case
    // EX: Call the Exec twice with DPI%-1 and then DPI% as the zoomPercent values
    IOleCommandTarget cmdTarget = browser2.Document as IOleCommandTarget;
    if (cmdTarget != null)
    {
        object commandInput = zoomPercent;
        cmdTarget.Exec(IntPtr.Zero,
                       OLECMDID_OPTICAL_ZOOM,
                       OLECMDEXECOPT_DONTPROMPTUSER,
                       ref commandInput,
                       ref commandOutput);
    }
    ```
