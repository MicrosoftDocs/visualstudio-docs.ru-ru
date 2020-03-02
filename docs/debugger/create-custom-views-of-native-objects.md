---
title: Создание пользовательских представлений для объектов C++
description: Использование платформы Natvis для настройки способа отображения собственных типов в отладчике в Visual Studio
ms.date: 10/31/2018
ms.topic: conceptual
f1_keywords:
- natvis
dev_langs:
- C++
ms.assetid: 2d9a177a-e14b-404f-a6af-49498eff0bd7
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: 9c26c35c09353d740f6db9745222bb66db40e7ba
ms.sourcegitcommit: 1efb6b219ade7c35068b79fbdc573a8771ac608d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/28/2020
ms.locfileid: "78167758"
---
# <a name="create-custom-views-of-c-objects-in-the-debugger-using-the-natvis-framework"></a>Создание пользовательских представлений C++ объектов в отладчике с помощью платформы Natvis

Инфраструктура *Natvis* Visual Studio настраивает способ отображения собственных типов в окнах переменных отладчика, таких как **локальные переменные** и окна **контрольных значений** , а также в **подсказках**. Визуализации Natvis позволяют сделать типы, которые вы создадите более видимыми во время отладки.

Natvis заменяет файл *аутоексп. dat* в более ранних версиях Visual Studio синтаксисом XML, улучшенной диагностикой, управлением версиями и поддержкой нескольких файлов.

> [!NOTE]
> Настройки Natvis работают с классами и структурами, но не typedefs.

## <a name="BKMK_Why_create_visualizations_"></a>Визуализации Natvis

Платформа Natvis используется для создания правил визуализации для создаваемых типов, чтобы разработчики могли легко видеть их во время отладки.

Например, на следующем рисунке показана переменная типа [Windows:: UI:: XAML:: Controls:: TextBox](/uwp/api/Windows.UI.Xaml.Controls.TextBox) в окне отладчика без примененных пользовательских визуализаций.

![Визуализация по умолчанию для текстового поля](../debugger/media/dbg_natvis_textbox_default.png "Визуализация элемента TextBox по умолчанию")

В выделенной строке показано свойство `Text` класса `TextBox` . Сложная иерархия классов затрудняет поиск этого свойства. Отладчик не знает, как интерпретировать пользовательский строковый тип, поэтому строка, удерживаемая внутри текстового поля, не видна.

То же самое `TextBox` выглядит гораздо проще в окне переменных при применении правил настраиваемого визуализатора Natvis. Важные элементы класса отображаются вместе, и отладчик отображает базовое строковое значение типа настраиваемой строки.

![Данные текстового поля с помощью визуализатора](../debugger/media/dbg_natvis_textbox_visualizer.png "Данные TextBox с использованием визуализатора")

## <a name="BKMK_Using_Natvis_files"></a>Использование natvis файлов в C++ проектах

Natvis использует *natvis* файлы для указания правил визуализации. Файл *natvis* — это XML-файл с расширением *natvis* . Схема Natvis определяется в *%всинсталлдир%\ксмл\счемас\натвис.КССД*.

Базовая структура *natvis* -файла — это один или несколько элементов `Type`, представляющих записи визуализации. Полное имя каждого элемента `Type` задается в его `Name` атрибуте.

```xml
<?xml version="1.0" encoding="utf-8"?>
<AutoVisualizer xmlns="http://schemas.microsoft.com/vstudio/debugger/natvis/2010">
  <Type Name="MyNamespace::CFoo">
    .
    .
  </Type>

  <Type Name="...">
    .
    .
  </Type>
</AutoVisualizer>
```

Visual Studio предоставляет некоторые файлы *natvis* в папке *%VSINSTALLDIR%\Common7\Packages\Debugger\Visualizers* Эти файлы имеют правила визуализации для многих распространенных типов и могут использоваться в качестве примеров для написания визуализаций для новых типов.

### <a name="add-a-natvis-file-to-a-c-project"></a>Добавление natvis-файла в C++ проект

Можно добавить *natvis* -файл в любой C++ проект.

**Чтобы добавить новый *natvis* -файл, сделайте следующее:**

1. Выберите узел C++ проекта в **Обозреватель решений**и выберите **проект** > **Добавить новый элемент**, или щелкните проект правой кнопкой мыши и выберите **Добавить** > **новый элемент**.

1. В диалоговом окне **Добавление нового элемента** выберите **Visual C++**  > **служебная программа** > **файл визуализации отладчика (. natvis)** .

1. Присвойте файлу имя и нажмите кнопку **Добавить**.

   Новый файл добавляется в **Обозреватель решений**и открывается в области документа Visual Studio.

Отладчик Visual Studio автоматически загружает *natvis* -файлы в C++ проектах, и по умолчанию также включает их в *pdb* -файл при сборке проекта. При отладке созданного приложения отладчик загружает *natvis* -файл из *pdb* -файла, даже если проект не открыт. Если вы не хотите, чтобы *natvis* -файл включался в файл *pdb*, его можно исключить из созданного *pdb* -файла.

**Чтобы исключить *natvis* -файл из *pdb*-файла, выполните следующие действия.**

1. Выберите *natvis* -файл в **Обозреватель решений**и щелкните значок **Свойства** или щелкните файл правой кнопкой мыши и выберите пункт **Свойства**.

1. Раскройте стрелку рядом с полем **исключено из сборки** и выберите **Да**, а затем нажмите кнопку **ОК**.

>[!NOTE]
>Для отладки исполняемых проектов Используйте элементы решения, чтобы добавить файлы *natvis* , которые не находятся в *pdb*-файле, так как нет доступных C++ проектов.

>[!NOTE]
>Правила Natvis, загруженные из файла *pdb* , применяются только к типам в модулях, на которые ссылается *pdb* -файл. Например, если *Module1. pdb* имеет элемент Natvis для типа с именем `Test`, он применяется только к классу `Test` в файле *Module1. dll*. Если другой модуль также определяет класс с именем `Test`, то элемент Natvis *. pdb* не применяется к нему.

**Чтобы установить и зарегистрировать *natvis* -файл с помощью пакета VSIX, выполните следующие действия.**

Пакет VSIX позволяет устанавливать и регистрировать *natvis* -файлы. Независимо от того, где они установлены, все зарегистрированные *natvis* файлы автоматически выбираются во время отладки.

1. Включите *natvis* – файл в пакет VSIX. Например, для следующего файла проекта:
   ```xml
   <?xml version="1.0" encoding="utf-8"?>
   <Project DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003" ToolsVersion="14.0">
     <ItemGroup>
       <VSIXSourceItem Include="Visualizer.natvis" />
     </ItemGroup>
   </Project>
   ```

2. Зарегистрируйте *natvis* в файле *source. extension. vsixmanifest* :
   ```xml
   <?xml version="1.0" encoding="utf-8"?>
   <PackageManifest Version="2.0.0" xmlns="http://schemas.microsoft.com/developer/vsx-schema/2011" xmlns:d="http://schemas.microsoft.com/developer/vsx-schema-design/2011">
     <Assets>
       <Asset Type="NativeVisualizer" Path="Visualizer.natvis"  />
     </Assets>
   </PackageManifest>
   ```

### <a name="BKMK_natvis_location"></a>Расположение файлов Natvis

Можно добавить *natvis* -файлы в каталог пользователя или в системный каталог, если они должны применяться к нескольким проектам.

Файлы *natvis* оцениваются в следующем порядке:

1. Все *natvis* -файлы, внедренные в отлаживаемый файл *pdb* , если в загруженном проекте не существует файла с таким же именем.

2. Любые *natvis* -файлы, которые находятся в загруженном C++ проекте или решении верхнего уровня. Эта группа включает все загруженные C++ проекты, включая библиотеки классов, но не проекты на других языках.

3. Все *natvis* -файлы, установленные и зарегистрированные с помощью пакета VSIX.

::: moniker range="vs-2017"

4. Каталог Natvis конкретного пользователя (например, *%UserProfile%\Documents\Visual Studio 2017\Visualizers*).

::: moniker-end

::: moniker range=">= vs-2019"

4. Каталог Natvis конкретного пользователя (например, *%UserProfile%\Documents\Visual Studio 2019\Visualizers*).

::: moniker-end

5. Каталог Natvis всей системы ( *%VSINSTALLDIR%\Common7\Packages\Debugger\Visualizers*). Этот каталог содержит файлы *natvis* , которые устанавливаются вместе с Visual Studio. При наличии разрешений администратора можно добавить файлы в этот каталог.

## <a name="modify-natvis-files-while-debugging"></a>Изменение natvis файлов во время отладки

Можно изменить *natvis* -файл в интегрированной среде разработки во время отладки проекта. Откройте файл в том же экземпляре Visual Studio, в котором выполняется отладка, измените его и сохраните. Как только файл будет сохранен, в окне " **Контрольные значения** и **локальные** " появится обновление Windows, отражающее изменение.

Можно также добавлять или удалять *natvis* -файлы в решении, в котором выполняется отладка, и Visual Studio добавляет или удаляет соответствующие визуализации.

Невозможно обновить *natvis* -файлы, внедренные в *pdb* -файлы во время отладки.

Если изменить *natvis* – файл за пределами Visual Studio, изменения не вступят в силу автоматически. Чтобы обновить окна отладчика, можно выполнить повторное вычисление команды **. натвисрелоад** в окне **Контрольные значения** . После этого изменения вступят в силу без перезапуска сеанса отладки.

Также используйте команду **. натвисрелоад** , чтобы обновить *natvis* -файл до более новой версии. Например, *natvis* файл может быть возвращен в систему управления версиями, и вы хотите выбрать последние изменения, внесенные другим пользователем.

## <a name="BKMK_Expressions_and_formatting"></a> Выражения и форматирование
Визуализации Natvis используют выражения C++ для указания элементов данных для отображения. В дополнение к улучшениям и ограничениям C++ выражений в отладчике, которые описаны в [операторе контекста (C++)](../debugger/context-operator-cpp.md), следует учитывать следующее:

- Выражения Natvis вычисляются в контексте визуализируемого объекта, а не текущего кадра стека. Например, `x` в выражении Natvis ссылается на поле с именем **x** в объекте, для которого выполняется визуализация, а не на локальную переменную с именем **x** в текущей функции. Доступ к локальным переменным в выражениях Natvis невозможен, хотя можно получить доступ к глобальным переменным.

- Выражения Natvis не допускают вычисления функции или побочные эффекты. Вызовы функций и операторы присваивания игнорируются. Поскольку [встроенные функции отладчика](../debugger/expressions-in-the-debugger.md#BKMK_Using_debugger_intrinisic_functions_to_maintain_state) не зависимы от побочных эффектов, их можно свободно вызывать из любого выражения Natvis, даже если другие вызовы функций запрещены.

- Для управления отображением выражения можно использовать любой из описателей формата, описанных в разделе [описатели формата в C++ ](format-specifiers-in-cpp.md#BKMK_Visual_Studio_2012_format_specifiers). Описатели формата игнорируются при внутреннем использовании элемента Natvis, например `Size` выражении в [расширении ArrayItems](../debugger/create-custom-views-of-native-objects.md#BKMK_ArrayItems_expansion).

## <a name="natvis-views"></a>Представления Natvis

Можно определить различные представления Natvis для отображения типов различными способами. Например, ниже приведена визуализация `std::vector`, которая определяет упрощенное представление с именем `simple`. `DisplayString` и элементы `ArrayItems` отображаются в представлении по умолчанию и представлении `simple`, а элементы `[size]` и `[capacity]` не отображаются в представлении `simple`.

```xml
<Type Name="std::vector&lt;*&gt;">
    <DisplayString>{{ size={_Mylast - _Myfirst} }}</DisplayString>
    <Expand>
        <Item Name="[size]" ExcludeView="simple">_Mylast - _Myfirst</Item>
        <Item Name="[capacity]" ExcludeView="simple">_Myend - _Myfirst</Item>
        <ArrayItems>
            <Size>_Mylast - _Myfirst</Size>
            <ValuePointer>_Myfirst</ValuePointer>
        </ArrayItems>
    </Expand>
</Type>
```

В окне **Контрольные значения** используйте описатель формата **представления,** чтобы указать альтернативное представление. Простое представление отображается как **передать VEC, View (Simple)** :

![окно контрольных значений с простым представлением](../debugger/media/watch-simpleview.png "Окно контрольных значений с простым представлением")

## <a name="BKMK_Diagnosing_Natvis_errors"></a>Ошибки Natvis

Когда отладчик обнаруживает ошибки в записи визуализации, он пропускает их. Он либо отображает тип в его необработанном виде, либо выбирает другую подходящую визуализацию. Можно использовать диагностику Natvis, чтобы понять, почему отладчик проигнорировал запись визуализации, и просмотреть синтаксические ошибки и синтаксический анализ.

**Чтобы включить диагностику Natvis, выполните следующие действия.**

- В разделе **сервис** > **Параметры** (или **Параметры** > **отладки** ) **> Отладка** > **окно вывода**, установите для **диагностических сообщений Natvis (C++ только) значение "** **Ошибка**", " **предупреждение**" или " **подробно**", а затем нажмите кнопку **ОК**.

Ошибки отображаются в окне **вывод** .

## <a name="BKMK_Syntax_reference"></a> Справочник по синтаксису Natvis

### <a name="BKMK_AutoVisualizer"></a> Элемент AutoVisualizer
Элемент `AutoVisualizer` — это корневой узел *NATVIS*-файла, который содержит атрибут `xmlns:` пространства имен.

```xml
<?xml version="1.0" encoding="utf-8"?>
<AutoVisualizer xmlns="http://schemas.microsoft.com/vstudio/debugger/natvis/2010">
.
.
</AutoVisualizer>
```

Элемент `AutoVisualizer` может иметь дочерние элементы [Type](#BKMK_Type), [HRESULT](#BKMK_HResult), [UIVisualizer](#BKMK_UIVisualizer)и [CustomVisualizer](#BKMK_CustomVisualizer) .

### <a name="BKMK_Type"></a> Элемент Type

Базовый `Type` выглядит как в следующем примере:

```xml
<Type Name="[fully qualified type name]">
  <DisplayString Condition="[Boolean expression]">[Display value]</DisplayString>
  <Expand>
    ...
  </Expand>
</Type>
```

 Элемент `Type` указывает:

1. Тип, для которого следует использовать визуализацию (атрибут `Name`).

2. Как должно выглядеть значение объекта этого типа (элемент `DisplayString` ).

3. Как должны выглядеть элементы типа, когда пользователь расширяет тип в окне переменной (`Expand` узле).

#### <a name="templated-classes"></a>Шаблонные классы
Атрибут `Name` элемента `Type` принимает звездочку `*` как подстановочный знак, который можно использовать для шаблонов имен классов.

В следующем примере одна и та же визуализация используется независимо от того, является ли объект `CAtlArray<int>` или `CAtlArray<float>`. Если для `CAtlArray<float>`определена конкретная запись визуализации, она имеет приоритет над универсальным.

```xml
<Type Name="ATL::CAtlArray&lt;*&gt;">
    <DisplayString>{{Count = {m_nSize}}}</DisplayString>
</Type>
```

Вы можете ссылаться на параметры шаблона в записи визуализации с помощью макросов $T 1, $T 2 и т. д. Чтобы найти примеры этих макросов, см. *NATVIS*-файлы, поставляемые в комплекте с Visual Studio.

#### <a name="BKMK_Visualizer_type_matching"></a> Сопоставление типов визуализатора
Если запись визуализации не удается проверить, используется следующая доступная визуализация.

#### <a name="inheritable-attribute"></a>Атрибут Inheritable
Необязательный атрибут `Inheritable` указывает, применяется ли визуализация только к базовому типу или к базовому типу и всем производным типам. Значение `Inheritable` по умолчанию — `true`.

В следующем примере визуализация применяется только к типу `BaseClass`:

```xml
<Type Name="Namespace::BaseClass" Inheritable="false">
    <DisplayString>{{Count = {m_nSize}}}</DisplayString>
</Type>
```

#### <a name="priority-attribute"></a>Атрибут Priority

Необязательный атрибут `Priority` указывает порядок использования альтернативных определений, если определение не удается проанализировать. Возможные значения `Priority`: `Low`, `MediumLow`,`Medium`, `MediumHigh`и `High`. Значение по умолчанию — `Medium`. Атрибут `Priority` различает только приоритеты в одном *natvis* – файле.

В следующем примере сначала анализируется запись, соответствующая 2015 STL. Если не удается выполнить синтаксический анализ, он использует альтернативную запись для версии 2013 библиотеки STL:

```xml
<!-- VC 2013 -->
<Type Name="std::reference_wrapper&lt;*&gt;" Priority="MediumLow">
     <DisplayString>{_Callee}</DisplayString>
    <Expand>
        <ExpandedItem>_Callee</ExpandedItem>
    </Expand>
</Type>

<!-- VC 2015 -->
<Type Name="std::reference_wrapper&lt;*&gt;">
    <DisplayString>{*_Ptr}</DisplayString>
    <Expand>
        <Item Name="[ptr]">_Ptr</Item>
    </Expand>
</Type>
```

### <a name="optional-attribute"></a>Атрибут Optional
Атрибут `Optional` можно разместить на любом узле. Если часть выражения внутри необязательного узла не удается проанализировать, отладчик игнорирует этот узел, но применяет остальные правила `Type`. В следующем типе `[State]` является обязательным, а `[Exception]` — необязательным.  Если `MyNamespace::MyClass` имеет поле с именем _`M_exceptionHolder`, отображаются как узел `[State]`, так и `[Exception]` узел, но если `_M_exceptionHolder` поле отсутствует, отображается только узел `[State]`.

```xml
<Type Name="MyNamespace::MyClass">
    <Expand>
      <Item Name="[State]">_M_State</Item>
      <Item Name="[Exception]" Optional="true">_M_exceptionHolder</Item>
    </Expand>
</Type>
```

### <a name="BKMK_Condition_attribute"></a> Атрибут Condition

Необязательный атрибут `Condition` доступен для многих элементов визуализации и указывает, когда следует использовать правило визуализации. Если выражение в атрибуте Condition разрешается в `false`, правило визуализации не применяется. Если он имеет значение `true`или отсутствует атрибут `Condition`, то применяется визуализация. Этот атрибут можно использовать для логики if-else в записях визуализации.

Например, следующая визуализация содержит два элемента `DisplayString` для типа интеллектуального указателя. Если элемент `_Myptr` пуст, условие первого элемента `DisplayString` разрешается в `true`, поэтому отображается форма. Если элемент `_Myptr` не пуст, условие принимает значение `false`, а второй элемент `DisplayString` отображается.

```xml
<Type Name="std::auto_ptr&lt;*&gt;">
  <DisplayString Condition="_Myptr == 0">empty</DisplayString>
  <DisplayString>auto_ptr {*_Myptr}</DisplayString>
  <Expand>
    <ExpandedItem>_Myptr</ExpandedItem>
  </Expand>
</Type>
```

### <a name="includeview-and-excludeview-attributes"></a>Атрибут IncludeView и ExcludeView

Атрибуты `IncludeView` и `ExcludeView` указывают элементы, которые должны отображаться или не отображаться в конкретных представлениях. Например, в следующей спецификации Natvis `std::vector``simple` представление не отображает элементы `[size]` и `[capacity]`.

```xml
<Type Name="std::vector&lt;*&gt;">
    <DisplayString>{{ size={_Mylast - _Myfirst} }}</DisplayString>
    <Expand>
        <Item Name="[size]" ExcludeView="simple">_Mylast - _Myfirst</Item>
        <Item Name="[capacity]" ExcludeView="simple">_Myend - _Myfirst</Item>
        <ArrayItems>
            <Size>_Mylast - _Myfirst</Size>
            <ValuePointer>_Myfirst</ValuePointer>
        </ArrayItems>
    </Expand>
</Type>
```

Атрибуты `IncludeView` и `ExcludeView` можно использовать для типов и отдельных членов.

### <a name="BKMK_Versioning"></a> Элемент Version
Элемент `Version` ограничивает запись визуализации конкретным модулем и версией. Элемент `Version` помогает избежать конфликтов имен, сокращает непреднамеренное несовпадение и позволяет использовать различные визуализации для разных версий типов.

Если общий файл заголовка, используемый различными модулями, определяет тип, то версия визуализации отображается только в том случае, если тип находится в указанной версии модуля.

В следующем примере визуализация применима только для типа `DirectUI::Border`, находящегося в `Windows.UI.Xaml.dll` от версии 1,0 до 1,5.

```xml
<Type Name="DirectUI::Border">
  <Version Name="Windows.UI.Xaml.dll" Min="1.0" Max="1.5"/>
  <DisplayString>{{Name = {*(m_pDO->m_pstrName)}}}</DisplayString>
  <Expand>
    <ExpandedItem>*(CBorder*)(m_pDO)</ExpandedItem>
  </Expand>
</Type>
```

`Min` и `Max`не требуются. Они являются необязательными атрибутами. Подстановочные знаки не поддерживаются.

Атрибут `Name` имеет формат *filename. ext*, например *Hello. exe* или *Some. dll*. Имена путей не допускаются.

### <a name="BKMK_DisplayString"></a>Элемент DisplayString
Элемент `DisplayString` указывает строку, которая будет отображаться как значение переменной. Принимает произвольные строки в сочетании с выражениями. Весь код внутри фигурных скобок интерпретируется как выражение. Например, следующая запись `DisplayString`:

```xml
<Type Name="CPoint">
  <DisplayString>{{x={x} y={y}}}</DisplayString>
</Type>
```

Означает, что переменные типа `CPoint` отображаются, как показано на рисунке ниже.

 ![Использование элемента DisplayString](../debugger/media/dbg_natvis_cpoint_displaystring.png "Использование элемента DisplayString")

В `DisplayString` выражении `x` и `y`, которые являются элементами `CPoint`, находятся внутри фигурных скобок, поэтому их значения оцениваются. В примере также показано, как можно поэкранировать фигурные скобки с помощью двойных фигурных скобок (`{{` или `}}`).

> [!NOTE]
> Элемент `DisplayString` является единственным элементом, который принимает произвольные строки и синтаксис фигурных скобок. Все остальные элементы визуализации принимают только те выражения, которые могут вычисляться отладчиком.

### <a name="BKMK_StringView"></a>Стрингвиев, элемент

Элемент `StringView` определяет значение, которое отладчик может отправить во встроенный визуализатор текста. Например, для типа `ATL::CStringT` указана следующая визуализация:

```xml
<Type Name="ATL::CStringT&lt;wchar_t,*&gt;">
  <DisplayString>{m_pszData,su}</DisplayString>
</Type>
```

Объект `CStringT` отображается в окне переменных, как в следующем примере:

![CStringT DisplayString, элемент](../debugger/media/dbg_natvis_displaystring_cstringt.png "Элемент CStringT DisplayString")

Добавление элемента `StringView` сообщает отладчику, что он может отображать значение как визуализацию текста.

```xml
<Type Name="ATL::CStringT&lt;wchar_t,*&gt;">
  <DisplayString>{m_pszData,su}</DisplayString>
  <StringView>m_pszData,su</StringView>
</Type>
```

Во время отладки можно выбрать значок лупы рядом с переменной, а затем выбрать **Визуализатор текста** для отображения строки, на которую **m_pszData** указывает.

 ![CStringT данных с помощью визуализатора Стрингвиев](../debugger/media/dbg_natvis_stringview_cstringt.png "Данные CStringT с визуализатором StringView")

Выражение `{m_pszData,su}` содержит описатель C++ формата **SU**для вывода значения в виде строки Юникода. Дополнительные сведения см. [в разделе описатели формата в C++ ](../debugger/format-specifiers-in-cpp.md).

### <a name="BKMK_Expand"></a>Элемент Expand

Необязательный `Expand` узел настраивает дочерние элементы визуального типа при развертывании типа в окне переменной. Узел `Expand` принимает список дочерних узлов, которые определяют дочерние элементы.

- Если в записи визуализации не указан `Expand` узел, то дочерние элементы используют правила расширения по умолчанию.

- Если узел `Expand` указан без дочерних узлов, тип не может быть расширен в окнах отладчика.

#### <a name="BKMK_Item_expansion"></a> Расширение элемента

 Элемент `Item` является самым базовым и общим элементом в `Expand` узле. `Item` определяет один дочерний элемент. Например, класс `CRect` с полями `top`, `left`, `right`и `bottom` имеет следующую запись визуализации:

```xml
<Type Name="CRect">
  <DisplayString>{{top={top} bottom={bottom} left={left} right={right}}}</DisplayString>
  <Expand>
    <Item Name="Width">right - left</Item>
    <Item Name="Height">bottom - top</Item>
  </Expand>
</Type>
```

В окне отладчика тип `CRect` выглядит как в следующем примере:

![Крект с расширением элемента Item](../debugger/media/dbg_natvis_expand_item_crect1.png "CRect с расширением элемента Item")

Отладчик вычисляет выражения, указанные в элементах `Width` и `Height`, и показывает значения в столбце **значение** окна переменная.

Отладчик автоматически создает узел **[RAW View]** для каждого пользовательского расширения. На предыдущем снимке экрана показан развернутый узел **[необработанное представление]** , чтобы показать, как необработанное представление по умолчанию объекта отличается от его визуализации Natvis. Расширение по умолчанию создает поддерево для базового класса и перечисляет все члены данных базового класса как дочерние элементы.

> [!NOTE]
> Если выражение элемента Point указывает на сложный тип, то сам узел **элемента** можно развернуть.

#### <a name="BKMK_ArrayItems_expansion"></a> ArrayItems expansion
Используйте узел `ArrayItems` , чтобы отладчик Visual Studio интерпретировал тип как массив и отображал его отдельные элементы. Хорошим примером является визуализация для `std::vector` :

```xml
<Type Name="std::vector&lt;*&gt;">
  <DisplayString>{{size = {_Mylast - _Myfirst}}}</DisplayString>
  <Expand>
    <Item Name="[size]">_Mylast - _Myfirst</Item>
    <Item Name="[capacity]">(_Myend - _Myfirst)</Item>
    <ArrayItems>
      <Size>_Mylast - _Myfirst</Size>
      <ValuePointer>_Myfirst</ValuePointer>
    </ArrayItems>
  </Expand>
</Type>
```

`std::vector` указывает его отдельные элементы, когда он развернут в окне переменных:

![std:: Vector с использованием расширения ArrayItems](../debugger/media/dbg_natvis_expand_arrayitems_stdvector.png "std::vector с использованием расширения ArrayItems")

Узел `ArrayItems` должен иметь:

- Выражение `Size` (которое должно вычисляться с получением целого числа) для отладчика, чтобы понять длину массива.
- `ValuePointer` выражение, которое указывает на первый элемент (который должен быть указателем на тип элемента, который не `void*`).

Значение по умолчанию нижней границы массива — 0. Чтобы переопределить это значение, используйте элемент `LowerBound`. К *natvis* файлам, поставляемым с Visual Studio, относятся примеры.

>[!NOTE]
>Можно использовать оператор `[]`, например `vector[i]`, с любой визуализацией одномерного массива, которая использует `ArrayItems`, даже если сам тип (например, `CATLArray`) не разрешает этот оператор.

Можно также указать многомерные массивы. В этом случае отладчику требуется несколько дополнительных сведений для правильного вывода дочерних элементов:

```xml
<Type Name="Concurrency::array&lt;*,*&gt;">
  <DisplayString>extent = {_M_extent}</DisplayString>
  <Expand>
    <Item Name="extent">_M_extent</Item>
    <ArrayItems Condition="_M_buffer_descriptor._M_data_ptr != 0">
      <Direction>Forward</Direction>
      <Rank>$T2</Rank>
      <Size>_M_extent._M_base[$i]</Size>
      <ValuePointer>($T1*) _M_buffer_descriptor._M_data_ptr</ValuePointer>
    </ArrayItems>
  </Expand>
</Type>
```

- `Direction` указывает, находится ли массив в основном или построчном порядке.
- `Rank` указывает ранг массива.
- Элемент `Size` принимает неявный параметр `$i`, вместо которого подставляет индекс измерения для нахождения длины массива в этом измерении. В предыдущем примере выражение `_M_extent.M_base[0]` должно предоставить длину 0-го измерения, `_M_extent._M_base[1]` 1-й и т. д.

Вот как двухмерный `Concurrency::array` объект выглядит в окне отладчика:

![Двухмерный массив с расширением ArrayItems](../debugger/media/dbg_natvis_expand_arrayitems_2d.png "Двухмерный массив с расширением ArrayItems")

#### <a name="BKMK_IndexListItems_expansion"></a> Расширение IndexListItems

Расширение `ArrayItems` можно использовать только в том случае, если элементы массива располагаются последовательно в памяти. Отладчик получает к следующему элементу, просто увеличивая его указатель. Если необходимо управлять индексом в узле значение, используйте `IndexListItems` узлы. Ниже приведена Визуализация с `IndexListItems` узлом:

```xml
<Type Name="Concurrency::multi_link_registry&lt;*&gt;">
  <DisplayString>{{size = {_M_vector._M_index}}}</DisplayString>
  <Expand>
    <Item Name="[size]">_M_vector._M_index</Item>
    <IndexListItems>
      <Size>_M_vector._M_index</Size>
      <ValueNode>*(_M_vector._M_array[$i])</ValueNode>
    </IndexListItems>
  </Expand>
</Type>
```

Единственное различие между `ArrayItems` и `IndexListItems` — `ValueNode`, что подразумевает полное выражение с<sup>элементом i с</sup> неявным параметром `$i`.

>[!NOTE]
>Можно использовать оператор `[]`, например `vector[i]`, с любой визуализацией одномерного массива, которая использует `IndexListItems`, даже если сам тип (например, `CATLArray`) не разрешает этот оператор.

#### <a name="BKMK_LinkedListItems_expansion"></a> Расширение LinkedListItems

Если визуализированный тип представляет связанный список, отладчик может отображать его дочерние элементы с помощью узла `LinkedListItems` . Следующая визуализация для типа `CAtlList` использует `LinkedListItems`:

```xml
<Type Name="ATL::CAtlList&lt;*,*&gt;">
  <DisplayString>{{Count = {m_nElements}}}</DisplayString>
  <Expand>
    <Item Name="Count">m_nElements</Item>
    <LinkedListItems>
      <Size>m_nElements</Size>
      <HeadPointer>m_pHead</HeadPointer>
      <NextPointer>m_pNext</NextPointer>
      <ValueNode>m_element</ValueNode>
    </LinkedListItems>
  </Expand>
</Type>
```

Элемент `Size` ссылается на длину списка. `HeadPointer` указывает на первый элемент, `NextPointer` ссылается на следующий элемент, а `ValueNode` ссылается на значение элемента.

Отладчик вычисляет `NextPointer` и `ValueNode` выражения в контексте элемента `LinkedListItems` Node, а не типа родительского списка. В предыдущем примере `CAtlList` имеет класс `CNode` (находится в `atlcoll.h`), который является узлом связанного списка. `m_pNext` и `m_element` являются полями этого `CNode` класса, а не класса `CAtlList`.

`ValueNode` можно оставить пустым или использовать `this` для ссылки на сам узел `LinkedListItems`.

#### <a name="customlistitems-expansion"></a>Расширение LinkedListItems
Расширение `CustomListItems` позволяет записывать настраиваемую логику для обхода структуры данных, например хэш-таблицы. Используйте `CustomListItems` для визуализации структур данных, которые могут использовать C++ выражения для всех элементов, которые необходимо оценить, но не определение для `ArrayItems`, `IndexListItems`или `LinkedListItems`.

Следующий визуализатор для `CAtlMap` — отличный пример, где подходит `CustomListItems`.

```xml
<Type Name="ATL::CAtlMap&lt;*,*,*,*&gt;">
    <AlternativeType Name="ATL::CMapToInterface&lt;*,*,*&gt;"/>
    <AlternativeType Name="ATL::CMapToAutoPtr&lt;*,*,*&gt;"/>
    <DisplayString>{{Count = {m_nElements}}}</DisplayString>
    <Expand>
      <CustomListItems MaxItemsPerView="5000" ExcludeView="Test">
        <Variable Name="iBucket" InitialValue="-1" />
        <Variable Name="pBucket" InitialValue="m_ppBins == nullptr ? nullptr : *m_ppBins" />
        <Variable Name="iBucketIncrement" InitialValue="-1" />

        <Size>m_nElements</Size>
        <Exec>pBucket = nullptr</Exec>
        <Loop>
          <If Condition="pBucket == nullptr">
            <Exec>iBucket++</Exec>
            <Exec>iBucketIncrement = __findnonnull(m_ppBins + iBucket, m_nBins - iBucket)</Exec>
            <Break Condition="iBucketIncrement == -1" />
            <Exec>iBucket += iBucketIncrement</Exec>
            <Exec>pBucket = m_ppBins[iBucket]</Exec>
          </If>
          <Item>pBucket,na</Item>
          <Exec>pBucket = pBucket->m_pNext</Exec>
        </Loop>
      </CustomListItems>
    </Expand>
</Type>
```

`Exec` можно использовать для выполнения кода внутри `CustomListItems` расширения с помощью переменных и объектов, определенных в расширении. С помощью `Exec`можно использовать логические операторы, арифметические операторы и операторы присваивания. Для вычисления функций нельзя использовать `Exec`.

`CustomListItems` поддерживает следующие встроенные функции:

- `strlen`, `wcslen`, `strnlen`, `wcsnlen`, `strcmp`, `wcscmp`, `_stricmp`, `_strcmpi`, `_wcsicmp`, `strncmp`, `wcsncmp`, `_strnicmp`, `_wcsnicmp`, `memcmp`, `memicmp`, `wmemcmp`, `strchr`, `wcschr`, `memchr`, `wmemchr`, `strstr`, `wcsstr`, `__log2`, `__findNonNull`
- `GetLastError`, `TlsGetValue`, `DecodeHString`, `WindowsGetStringLen`, `WindowsGetStringRawBuffer`, `WindowsCompareStringOrdinal`, `RoInspectCapturedStackBackTrace`, `CoDecodeProxy`, `GetEnvBlockLength`, `DecodeWinRTRestrictedException`, `DynamicMemberLookup`, `DecodePointer`, `DynamicCast`
- `ConcurrencyArray_OperatorBracket_idx // Concurrency::array<>::operator[index<>] and operator(index<>)`
- `ConcurrencyArray_OperatorBracket_int // Concurrency::array<>::operator(int, int, ...)`
- `ConcurrencyArray_OperatorBracket_tidx // Concurrency::array<>::operator[tiled_index<>] and operator(tiled_index<>)`
- `ConcurrencyArrayView_OperatorBracket_idx // Concurrency::array_view<>::operator[index<>] and operator(index<>)`
- `ConcurrencyArrayView_OperatorBracket_int // Concurrency::array_view<>::operator(int, int, ...)`
- `ConcurrencyArrayView_OperatorBracket_tidx // Concurrency::array_view<>::operator[tiled_index<>] and operator(tiled_index<>)`
- `Stdext_HashMap_Int_OperatorBracket_idx`
- `Std_UnorderedMap_Int_OperatorBracket_idx`
- `TreeTraverse_Init // Initializes a new tree traversal`
- `TreeTraverse_Next // Returns nodes in a tree`
- `TreeTraverse_Skip // Skips nodes in a pending tree traversal`

#### <a name="BKMK_TreeItems_expansion"></a> Расширение TreeItems
 Если визуализированный тип представляет дерево, отладчик может пройти дерево отображать его дочерние элементы с помощью узла `TreeItems` . Ниже приведена визуализация для типа `std::map` с помощью `TreeItems` узла:

```xml
<Type Name="std::map&lt;*&gt;">
  <DisplayString>{{size = {_Mysize}}}</DisplayString>
  <Expand>
    <Item Name="[size]">_Mysize</Item>
    <Item Name="[comp]">comp</Item>
    <TreeItems>
      <Size>_Mysize</Size>
      <HeadPointer>_Myhead->_Parent</HeadPointer>
      <LeftPointer>_Left</LeftPointer>
      <RightPointer>_Right</RightPointer>
      <ValueNode Condition="!((bool)_Isnil)">_Myval</ValueNode>
    </TreeItems>
  </Expand>
</Type>
```

Синтаксис похож на узел `LinkedListItems`. `LeftPointer`, `RightPointer`и `ValueNode` оцениваются в контексте класса узла дерева. `ValueNode` можно оставить пустым или использовать `this` для ссылки на сам узел `TreeItems`.

#### <a name="BKMK_ExpandedItem_expansion"></a> Расширение ExpandedItem
 Элемент `ExpandedItem` создает агрегированное дочернее представление, отображая свойства базовых классов или элементов данных, как если бы они были дочерними элементами визуального типа. Отладчик вычисляет указанное выражение и добавляет дочерние узлы результата в список дочерних элементов визуального типа.

Например, тип интеллектуального указателя `auto_ptr<vector<int>>` обычно отображается как:

 ![Автоматическое&#95;расширение&#60;типа&#60;int&#62; &#62; по умолчанию для векторного прерывания](../debugger/media/dbg_natvis_expand_expandeditem_default.png "Расширение по умолчанию")

 Чтобы увидеть значения вектора, необходимо детализировать два уровня в окне переменных, передавая элемент `_Myptr`. При добавлении элемента `ExpandedItem` можно исключить переменную `_Myptr` из иерархии и просмотреть непосредственно элементы вектора elements:

```xml
<Type Name="std::auto_ptr&lt;*&gt;">
  <DisplayString>auto_ptr {*_Myptr}</DisplayString>
  <Expand>
    <ExpandedItem>_Myptr</ExpandedItem>
  </Expand>
</Type>
```

 ![Автоматическое&#95;расширение&#60;типа&#60;int&#62; &#62; расширение expandeditem](../debugger/media/dbg_natvis_expand_expandeditem_visualized.png "Расширение ExpandedItem")

В следующем примере показано, как выполнить статистическую обработку свойств базового класса в производном классе. Предположим, класс `CPanel` является производным от `CFrameworkElement`. Вместо повторения свойств, поступающих от базового класса `CFrameworkElement`, Визуализация `ExpandedItem` узла добавляет эти свойства к дочернему списку класса `CPanel`.

```xml
<Type Name="CPanel">
  <DisplayString>{{Name = {*(m_pstrName)}}}</DisplayString>
  <Expand>
    <Item Name="IsItemsHost">(bool)m_bItemsHost</Item>
    <ExpandedItem>*(CFrameworkElement*)this,nd</ExpandedItem>
  </Expand>
</Type>
```

Здесь необходим спецификатор формата **nd**, который отключает сопоставление визуализации для производного класса. В противном случае выражение `*(CFrameworkElement*)this` приведет к повторному применению визуализации `CPanel`, так как правила сопоставления типов визуализации по умолчанию считают его наиболее подходящим. Используйте описатель формата **ND** , чтобы указать отладчику использовать визуализацию базового класса, или расширение по умолчанию, если базовый класс не имеет визуализации.

#### <a name="BKMK_Synthetic_Item_expansion"></a> Расширение синтетического элемента
 Там, где элемент `ExpandedItem` предоставляет более плоское представление данных, устраняя иерархии, узел `Synthetic` делает обратное. Он позволяет создать искусственный дочерний элемент, который не является результатом выражения. Искусственный элемент может иметь собственные дочерние элементы. В следующем примере визуализация для типа `Concurrency::array` использует узел `Synthetic` , чтобы показать диагностическое сообщение пользователю.

```xml
<Type Name="Concurrency::array&lt;*,*&gt;">
  <DisplayString>extent = {_M_extent}</DisplayString>
  <Expand>
    <Item Name="extent" Condition="_M_buffer_descriptor._M_data_ptr == 0">_M_extent</Item>
    <ArrayItems Condition="_M_buffer_descriptor._M_data_ptr != 0">
      <Rank>$T2</Rank>
      <Size>_M_extent._M_base[$i]</Size>
      <ValuePointer>($T1*) _M_buffer_descriptor._M_data_ptr</ValuePointer>
    </ArrayItems>
    <Synthetic Name="Array" Condition="_M_buffer_descriptor._M_data_ptr == 0">
      <DisplayString>Array members can be viewed only under the GPU debugger</DisplayString>
    </Synthetic>
  </Expand>
</Type>
```

 ![Concurrency:: Array с расширением искусственного элемента](../debugger/media/dbg_natvis_expand_synthetic.png "Concurrency:: Array с расширением искусственного элемента")

### <a name="BKMK_HResult"></a>HResult, элемент
 Элемент `HResult` позволяет настроить сведения, отображаемые для **HRESULT** в окнах отладчика. Элемент `HRValue` должен содержать 32-разрядное значение **HRESULT**, который требуется настроить. Элемент `HRDescription` содержит сведения, отображаемые в окне отладчика.

```xml

<HResult Name="MY_E_COLLECTION_NOELEMENTS">
  <HRValue>0xABC0123</HRValue>
  <HRDescription>No elements in the collection.</HRDescription>
</HResult>
```

### <a name="BKMK_UIVisualizer"></a>UIVisualizer, элемент
Элемент `UIVisualizer` регистрирует подключаемый модуль графического визуализатора в отладчике. Графический Визуализатор создает диалоговое окно или другой интерфейс, который отображает переменную или объект способом, согласованным с типом данных. Подключаемый модуль визуализатора должен быть создан как [VSPackage](../extensibility/internals/vspackages.md)и должен предоставлять службу, которую может использовать отладчик. *Natvis* -файл содержит сведения о регистрации для подключаемого модуля, такие как имя, идентификатор GUID предоставляемой службы и типы, которые она может визуализировать.

Здесь приведен пример элемента UIVisualizer:

```xml
<?xml version="1.0" encoding="utf-8"?>
<AutoVisualizer xmlns="http://schemas.microsoft.com/vstudio/debugger/natvis/2010">
    <UIVisualizer ServiceId="{5452AFEA-3DF6-46BB-9177-C0B08F318025}"
        Id="1" MenuName="Vector Visualizer"/>
    <UIVisualizer ServiceId="{5452AFEA-3DF6-46BB-9177-C0B08F318025}"
        Id="2" MenuName="List Visualizer"/>
.
.
</AutoVisualizer>
```

- `ServiceId` - `Id` пара атрибутов определяет `UIVisualizer`. `ServiceId` является идентификатором GUID службы, предоставляемой пакетом визуализатора. `Id` — это уникальный идентификатор, отличающий визуализаторы, если служба предоставляет более одного. В предыдущем примере одна и та же служба визуализатора предоставляет два визуализатора.

- Атрибут `MenuName` определяет имя визуализатора, которое будет отображаться в раскрывающемся списке рядом со значком лупы в отладчике. Например:

  ![Контекстное меню меню UIVisualizer](../debugger/media/dbg_natvis_vectorvisualizer.png "Контекстное меню UIVisualizer")

Каждый тип, определенный в *natvis* – файле, должен явным образом перечислять все ВИЗУАЛИЗАТОРЫ пользовательского интерфейса, которые могут отображать его. Отладчик сопоставляет ссылки визуализатора в записях типа с зарегистрированными визуализаторами. Например, следующая запись типа для `std::vector` ссылается на `UIVisualizer` в предыдущем примере.

```xml
<Type Name="std::vector&lt;int,*&gt;">
  <UIVisualizer ServiceId="{5452AFEA-3DF6-46BB-9177-C0B08F318025}" Id="1" />
</Type>
```

 Вы можете увидеть пример `UIVisualizer` в расширении [просмотра изображения](https://marketplace.visualstudio.com/search?term=%22Image%20Watch%22&target=VS&category=All%20categories&vsVersion=&sortBy=Relevance) , используемом для просмотра растровых изображений в памяти.

### <a name="BKMK_CustomVisualizer"></a>Элемент CustomVisualizer
 `CustomVisualizer` — это точка расширяемости, которая указывает расширение VSIX, которое вы пишете для управления визуализациями в Visual Studio Code. Дополнительные сведения о создании расширений VSIX см. в [пакете SDK для Visual Studio](../extensibility/visual-studio-sdk.md).

Написание пользовательского визуализатора по сравнению с определением XML Natvis гораздо больше, но у вас нет ограничений на то, что такое Natvis делает или не поддерживает. Пользовательские визуализаторы имеют доступ к полному набору API-интерфейсов расширения отладчика, которые могут запрашивать и изменять отлаживаемый процесс или взаимодействовать с другими частями Visual Studio.

 Для элементов `CustomVisualizer` можно использовать атрибуты `Condition`, `IncludeView`и `ExcludeView`.

 ## <a name="limitations"></a>Ограничения

Настройки Natvis работают с классами и структурами, но не typedefs.

Natvis не поддерживает визуализаторы для типов-примитивов (например, `int`, `bool`) или для указателей на примитивные типы. В этом сценарии одним из вариантов является использование [описателя формата](../debugger/format-specifiers-in-cpp.md) , соответствующего Вашему варианту использования. Например, если в коде используется `double* mydoublearray`, то можно использовать описатель формата массива в окне **контрольных значений** отладчика, например выражение `mydoublearray, [100]`, которое показывает первые 100 элементов.
