---
title: Общие цвета для Visual Studio | Документация Майкрософт
description: Узнайте, как использовать общие элементы и темы оболочки Visual Studio для проектирования собственного пользовательского интерфейса, который согласуется с средой Visual Studio.
ms.date: 04/26/2017
ms.topic: conceptual
ms.assetid: 8d11b9a0-6175-4f2e-8e7f-79daee1bfd41
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 8edd16744a6c094ece00ee5e4b8239f3d4f5a92e
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105054040"
---
# <a name="shared-colors-for-visual-studio"></a>Общие цвета для Visual Studio
При проектировании пользовательского интерфейса, использующего общие элементы оболочки Visual Studio, или необходимости соответствия элемента интерфейса аналогичным функциям, используйте существующие имена токенов в файлах определения пакета для выбора и назначения цветов. Таким образом можно обеспечить согласованность пользовательского интерфейса со всей средой Visual Studio и его автоматическое обновление при добавлении или обновлении тем.

В этом разделе описываются стандартные элементы пользовательского интерфейса и используемые ими имена токенов, на которые можно ссылаться при разработке похожего пользовательского интерфейса. Более подробные сведения о доступе к этим токенам цветов см. в разделе [The VSColor Service](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_TheVSColorService).

Используйте имена токенов правильно.

- **Используйте имена токенов в соответствии с функцией, а не самим цветом.** Стандартные общие цвета связаны с определенными элементами интерфейса и предназначены для использования только для аналогичных или похожих функций. Например, не используйте цвет выбранного поля со списком для анимированного индикатора хода выполнения только потому, что вам понравился цвет. Функции поля со списком и анимации различаются, и если цвет, связанный с полем со списком, изменяется, он может больше не быть соответствующим цветом для элемента анимации. Согласованное использование цветов помогает пользователям ориентироваться в интерфейсе и предотвращает путаницу.

- **Используйте цвета фона и текста в правильном сочетании.** Цвет фона, предназначенный для текста, имеет соответствующий цвет текста. Не используйте цвета текста, отличные от тех, которые определены для данного цвета фона. Если нет соответствующего цвета текста, не используйте этот цвет фона для любой поверхности, на которой предполагается отображать текст. Другие сочетания цветов текста и фона могут привести к нечитаемости интерфейса.

- **Используйте цвета элементов управления, соответствующие их расположению.** В некоторых штатах некоторые элементы управления Visual Studio не имеют отдельных цветов границы и фона. Эти цвета наследуются от областей, в которых они расположены. Всегда используйте имена токенов, которые подходят для того места, в котором вы размещаете элементы управления.

> [!IMPORTANT]
> Не используйте токены, найденные в категориях "Начальная страница" или "Cider".

## <a name="common-shared-controls"></a>Стандартные общие элементы управления

Если вы используете стандартную командную строку Visual Studio в своем компоненте, вы получите доступ к стилям элементов управления оболочки. Не следует изменять шаблон этих стандартных элементов управления. Однако если вам нужно создать пользовательскую панель команд, вам также может потребоваться создать пользовательские элементы управления. В этом случае используйте правильные имена токенов для каждого из указанных ниже элементов управления, чтобы ваш пользовательский интерфейс был согласован с остальной средой Visual Studio.

### <a name="button-controls"></a>Элементы управления "Кнопка"

![Красная линия элемента управления "Кнопка"](../../extensibility/ux-guidelines/media/0303-155_buttoncontrolredline.png "0303 — 155_ButtonControlRedline")

| Использовать... | Не используйте... |
| --- | --- |
| ... для кнопок в документе, которые нужно интегрировать с темами Visual Studio (светлое, темное, синее или системное высокая контрастность тему). | ... для кнопок, которые будут отображаться для пользовательского фона, не входящего в тему Visual Studio. |

**Кнопка: стандартное состояние**

![Стандартная кнопка](../../extensibility/ux-guidelines/media/03.03.Button.Standard.png "03.03. Button. Standard")<br />Стандартная кнопка

| Элемент | Имя токена: Category.color |
| --- | --- |
| Кнопка | `CommonControls.Button` |
| Граница кнопки | `CommonControls.ButtonBorder` |

**Кнопка: состояние по умолчанию**

![Кнопка по умолчанию](../../extensibility/ux-guidelines/media/03.03.Button.Default.png "03.03. Button. Default")<br />Кнопка по умолчанию

| Элемент | Имя токена: Category.color |
| --- | --- |
| Кнопка | `CommonControls.ButtonDefault` |
| Граница кнопки | `CommonControls.ButtonBorderDefault` |

**Кнопка: отключенное состояние**

![Кнопка отключена](../../extensibility/ux-guidelines/media/03.03.Button.Disabled.png "03.03. Button. Disabled")<br />Кнопка отключена

| Элемент | Имя токена: Category.color |
| --- | --- |
| Кнопка | `CommonControls.ButtonDisabled` |
| Граница кнопки | `CommonControls.ButtonBorderDisabled` |

**Кнопка: состояние наведения**

![Кнопка при наведении курсора мыши](../../extensibility/ux-guidelines/media/03.03.Button.hover.png "03.03. Button. Наведение")<br />Кнопка при наведении курсора мыши

| Элемент | Имя токена: Category.color |
| --- | --- |
| Кнопка | `CommonControls.ButtonHover` |
| Граница кнопки | `CommonControls.ButtonBorderHover` |

**Кнопка: нажатое состояние**

![Нажатая кнопка](../../extensibility/ux-guidelines/media/03.03.Button.Pressed.png "03.03. Button. Pressed")<br />Нажатая кнопка

| Элемент | Имя токена: Category.color |
| --- | --- |
| Кнопка | `CommonControls.ButtonPressed` |
| Граница кнопки | `CommonControls.ButtonBorderPressed` |

**Кнопка: состояние с сортировкой**

![Кнопка с упором](../../extensibility/ux-guidelines/media/03.03.Button.Focused.png "03.03. Button. Focused")<br />Кнопка с упором

| Элемент | Имя токена: Category.color |
| --- | --- |
| Кнопка | `CommonControls.ButtonFocused` |
| Граница кнопки | `CommonControls.ButtonBorderFocused` |

### <a name="check-box-controls"></a>Элементы управления "Флажок"
![Флажок (красная линия)](../../extensibility/ux-guidelines/media/0303-161_checkboxredline.png "0303 — 161_CheckboxRedline")<br />Флажок (красная линия)

| Использовать... | Не используйте... |
| --- | --- |
| ... для элементов управления "флажок", содержащихся в контейнере документа. | ... для любого пользовательского интерфейса, который не является элементом управления "флажок". |

**Флажок: состояние по умолчанию**

![Флажок](../../extensibility/ux-guidelines/media/0303-162_checkbox.png "0303 — 162_Checkbox")<br />Флажок по умолчанию

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `CommonControls.CheckBoxBackground` |
| Рамка | `CommonControls.CheckBoxBorder` |
| Текст | `CommonControls.CheckBoxText` |
| Глиф | `CommonControls.CheckBoxGlyph` |

**Флажок: отключенное состояние**

![Флажок отключен](../../extensibility/ux-guidelines/media/0303-163_checkboxdisabled.png "0303 — 163_CheckboxDisabled")<br />Флажок отключен

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `CommonControls.CheckBoxBackgroundDisabled` |
| Рамка | `CommonControls.CheckBoxBorderDisabled` |
| Текст | `CommonControls.CheckBoxTextDisabled` |
| Глиф | `CommonControls.CheckBoxGlyphDisabled` |

**Флажок: состояние наведения**

 ![Флажок при наведении курсора мыши](../../extensibility/ux-guidelines/media/0303-164_checkboxhover.png "0303 — 164_CheckboxHover")<br />Флажок при наведении курсора мыши

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `CommonControls.CheckBoxBackgroundHover` |
| Рамка | `CommonControls.CheckBoxBorderHover` |
| Текст | `CommonControls.CheckBoxTextHover` |
| Глиф | `CommonControls.CheckBoxGlyphHover` |

**Флажок: нажатое состояние**

![Флажок нажата](../../extensibility/ux-guidelines/media/0303-165_checkboxpressed.png "0303 — 165_CheckboxPressed")<br />Флажок нажата

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `CommonControls.CheckBoxBackgroundPressed` |
| Рамка | `CommonControls.CheckBoxBorderPressed` |
| Текст | `CommonControls.CheckBoxTextPressed` |
| Глиф | `CommonControls.CheckBoxGlyphPressed` |

**Флажок: состояние с сортировкой**

![Флажок "с сортировкой"](../../extensibility/ux-guidelines/media/0303-166_checkboxfocused.png "0303 — 166_CheckboxFocused")<br />Флажок "с сортировкой"

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `CommonControls.CheckBoxBackgroundFocused` |
| Рамка | `CommonControls.CheckBoxBorderFocused` |
| Текст | `CommonControls.CheckBoxTextFocused` |
| Глиф | `CommonControls.CheckBoxGlyphFocused` |

### <a name="drop-downs-and-combo-boxes"></a>Раскрывающиеся списки и поля со списком
![Раскрывающийся список/поле со списком (красная линия)](../../extensibility/ux-guidelines/media/0303-167_dropdowncomboboxredline.png "0303 — 167_DropDownComboBoxRedline")<br />Раскрывающийся список/поле со списком (красная линия)

| Использовать... | Не используйте... |
| --- | --- |
| ... для раскрывающихся списков и полей со списками в контейнере документа. | ... для любого пользовательского интерфейса, не поддерживающего раскрывающийся список или поле со списком. |
| | ... для [раскрывающихся списков панели команд](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandDropDown) или [полей со списком](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandComboBox). |

**Раскрывающиеся списки и поля со списком: состояние по умолчанию**

![Раскрывающийся список по умолчанию/поле со списком](../../extensibility/ux-guidelines/media/0303-168_dropdowncombobox.png "0303 — 168_DropDownComboBox")<br />Раскрывающийся список по умолчанию/поле со списком

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `CommonControls.ComboBoxBackground` |
| Рамка | `CommonControls.ComboBoxBorder` |
| Текст | `CommonControls.ComboBoxText` |
| Separator | `CommonControls.ComboBoxSeparator` |
| Глиф | `CommonControls.ComboBoxGlyph` |
| Фон глифа | `CommonControls.ComboBoxGlyphBackground` |

**Раскрывающиеся списки и поля со списком: отключенное состояние**

![Отключенное раскрывающийся список/поле со списком](../../extensibility/ux-guidelines/media/0303-169_dropdowncomboboxdisabled.png "0303 — 169_DropDownComboBoxDisabled")<br />Отключенное раскрывающийся список/поле со списком

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `CommonControls.ComboBoxBackgroundDisabled` |
| Рамка | `CommonControls.ComboBoxBorderDisabled` |
| Текст | `CommonControls.ComboBoxTextDisabled` |
| Separator | `CommonControls.ComboBoxSeparatorDisabled` |
| Глиф | `CommonControls.ComboBoxGlyphDisabled` |
| Фон глифа | `CommonControls.ComboBoxGlyphBackgroundDisabled` |

**Раскрывающиеся списки и поля со списком: состояние наведения**

![Раскрывающийся список/поле со списком при наведении курсора мыши](../../extensibility/ux-guidelines/media/0303-170_dropdowncomboboxhover.png "0303 — 170_DropDownComboBoxHover")<br />Раскрывающийся список/поле со списком при наведении курсора мыши

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `CommonControls.ComboBoxBackgroundHover` |
| Рамка | `CommonControls.ComboBoxBorderHover` |
| Текст | `CommonControls.ComboBoxTextHover` |
| Separator | `CommonControls.ComboBoxSeparatorHover` |
| Глиф | `CommonControls.ComboBoxGlyphHover` |
| Фон глифа | `CommonControls.ComboBoxGlyphBackgroundHover` |

**Раскрывающиеся списки и поля со списком: нажатое состояние**

![Кнопка раскрывающегося списка или поля со списком](../../extensibility/ux-guidelines/media/0303-171_dropdowncomboboxpressed.png "0303 — 171_DropDownComboBoxPressed")<br />Кнопка раскрывающегося списка или поля со списком

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `CommonControls.ComboBoxBackgroundPressed` |
| Рамка | `CommonControls.ComboBoxBorderPressed` |
| Текст | `CommonControls.ComboBoxTextPressed` |
| Separator | `CommonControls.ComboBoxSeparatorPressed` |
| Глиф | `CommonControls.ComboBoxGlyphPressed` |
| Фон глифа | `CommonControls.ComboBoxGlyphBackgroundPressed` |

**Раскрывающиеся списки и поля со списком. представление элемента списка: нажатое состояние**

 ![Представление элемента списка с раскрывающимся списком/раскрывающийся список](../../extensibility/ux-guidelines/media/0303-174_dropdowncomboboxlistview.png "0303 — 174_DropDownComboBoxListView")<br />Представление элемента списка с раскрывающимся списком/раскрывающийся список

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `CommonControls.ComboBoxListBackground`<br />`CommonControls.ComboBoxListBackgroundHover`<br />`CommonControls.ComboBoxListItemBackgroundPressed`<br />`CommonControls.ComboBoxListItemBackgroundFocused` |
| Рамка | `CommonControls.ComboBoxListBorder`<br />`CommonControls.ComboBoxListBorderHover`<br />`CommonControls.ComboBoxListBorderPressed`<br />`CommonControls.ComboBoxListBorderFocused` |
| Текст элемента | `CommonControls.ComboBoxListItemText`<br /> `CommonControls.ComboBoxListItemTextHover`<br />`CommonControls.ComboBoxListItemTextPressed`<br />`CommonControls.ComboBoxListItemTextFocused` |
| Фон с тенью | `CommonControls.ComboBoxListBackgroundShadow` |

**Раскрывающиеся списки и поля со списком: состояние "направлено"**

![Раскрывающийся список/поле со списком с фокусом](../../extensibility/ux-guidelines/media/0303-172_dropdowncomboboxfocused.png "0303 — 172_DropDownComboBoxFocused")<br />Раскрывающийся список/поле со списком с фокусом

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `CommonControls.ComboBoxBackgroundFocused` |
| Рамка | `CommonControls.ComboBoxBorderFocused` |
| Текст | `CommonControls.ComboBoxTextFocused` |
| Separator | `CommonControls.ComboBoxSeparatorFocused` |
| Глиф | `CommonControls.ComboBoxGlyphFocused` |
| Фон глифа | `CommonControls.ComboBoxGlyphBackgroundFocused` |

**Раскрывающиеся списки и поля со списком: выбор ввода текста**

![Раскрывающийся список для ввода текста в поле со списком](../../extensibility/ux-guidelines/media/0303-173_dropdowncomboboxtextinput.png "0303 — 173_DropDownComboBoxTextInput")<br />Раскрывающийся список для ввода текста в поле со списком

| Элемент | Имя токена: Category.color |
| --- | --- |
| Выделить | `CommonControls.ComboBoxTextInputSelection` |

### <a name="tabular-data-grid-controls"></a>Табличные элементы управления данными (сетка)
Табличные элементы управления данными, также называемые элементами управления "Сетка", — это стандартные элементы управления Visual Studio, которые можно использовать для представления больших объемов данных в нескольких столбцах. Стандартные табличные элементы управления данными встречаются в Visual Studio в нескольких местах: в окне инструментов "Список ошибок", в отчетах IntelliTrace, в представлении кучи памяти и т. д. Всегда используйте стандартные табличные элементы управления данными. Однако в некоторых редких случаях доступ к стандартным табличным элементам управления данными может отсутствовать. В таких ситуациях используйте указанные ниже имена токенов для обеспечения согласованности пользовательского интерфейса с другими табличными элементами управления данными в Visual Studio.

![Табличные данные и элемент управления Grid (красная линия)](../../extensibility/ux-guidelines/media/0303-197_tabulardatagridcontrolredline.png "0303 — 197_TabularDataGridControlRedline")<br />Табличные данные и элемент управления Grid (красная линия)

| Использовать... | Не используйте... |
| --- | --- |
| ... для табличных элементов управления или сетки. | ... для любого пользовательского интерфейса, который не является табличным элементом управления или сеткой. |

#### <a name="column-headers"></a>Заголовки столбцов
Заголовки столбцов состоят из фона, границы, текста заголовка и необязательного глифа, который обычно используется при сортировке сетки по данному столбцу.

**Заголовок столбца: состояние по умолчанию**

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `Header.Default` |
| Передний план (текст) | `Environment.CommandBarTextActive` |
| Передний план (глиф) | `Header.Glyph` |
| Рамка | `Header.SeparatorLine` |

**Заголовок столбца: состояние наведения**

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `Header.MouseOver` |
| Передний план (текст) | `Environment.CommandBarTextHover` |
| Передний план (глиф) | `Header.MouseOverGlyph` |
| Рамка | `Header.SeparatorLine` |

**Заголовок столбца: состояние "нажато"**

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `CommonControls.CheckBoxBackgroundPressed` |
| Передний план (текст) | `CommonControls.CheckBoxBorderPressed` |
| Передний план (глиф) | `CommonControls.CheckBoxTextPressed` |
| Рамка | `CommonControls.CheckBoxGlyphPressed` |

#### <a name="list-view-items"></a>Элементы представления списка
 Элементы представления списка состоят из фона и содержимого. Содержимым может быть текст, значок или и то и другое.

**Элементы представления списка: состояние по умолчанию**

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | Прозрачный |
| Передний план (текст) | `Environment.CommandBarTextActive` |
| Рамка | Отсутствуют |

**Элементы представления списка: активное состояние**

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `TreeView.SelectedItemActive` |
| Передний план (текст) | `TreeView.SelectedItemActiveText` |
| Рамка | Отсутствуют |

**Элементы представления списка: неактивное состояние**

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `TreeView.SelectedItemInactive` |
| Передний план (текст) | `TreeView.SelectedItemInactiveText` |
| Рамка | Отсутствуют |

### <a name="ui-text"></a>Текст пользовательского интерфейса

#### <a name="instructional-text"></a>Пояснительный текст
Пояснительный текст представляет собой выразительное основное объяснение того, что нужно сделать в диалоговом окне или странице документа.

![Пояснительный текст по умолчанию](../../extensibility/ux-guidelines/media/0303_InstructionalText.png "0303_InstructionalText.png")<br />Пояснительный текст по умолчанию

| Элемент | Имя токена: Category.color |
| --- | --- |
| Передний план (текст) | `Environment.ControlText` |

#### <a name="secondary-instructional-text"></a>Дополнительный пояснительный текст
На страницах документа с большим количеством текста и элементов управления в некоторых пояснительных текстах используется другое значение цвета. Это позволяет передавать наиболее важные сведения и уменьшить общую плотность элементов пользовательского интерфейса. (См. также раздел, посвященный тексту подсказки.)

![Дополнительный пояснительный текст](../../extensibility/ux-guidelines/media/0303_SecondaryInstructionalText.png "0303_SecondaryInstructionalText.png")<br />Дополнительный пояснительный текст

| Элемент | Имя токена: Category.color |
| --- | --- |
| Передний план (текст) | `Environment.ControlEditHintText` |

#### <a name="hint-text"></a>Текст подсказки
Текст подсказки отображается в пустом элементе управления, под элементом управления или на пустой поверхности документа для отображения действий пользователя далее. Текст подсказки можно использовать с фоном окна или элемента управления.

**Текст подсказок по умолчанию**

![Текст подсказок по умолчанию](../../extensibility/ux-guidelines/media/0303_HintText.png "0303_HintText.png")<br />Текст подсказок по умолчанию

| Элемент | Имя токена: Category.color |
| --- | --- |
| Передний план (текст) | `Environment.ControlEditHintText` |

**Обязательный текст подсказки**

![Обязательный текст подсказки](../../extensibility/ux-guidelines/media/0303_RequiredHintText.png "0303_RequiredHintText.png")<br />Обязательный текст подсказки

| Элемент | Имя токена: Category.color |
| --- | --- |
| Передний план (текст) | `Environment.ControlRequiredHintText` |
| Историческая справка | `Environment.ControlRequiredBackground` |

**Текст элемента управления "поле поиска"**

> Дополнительные маркеры цвета, связанные с элементом управления поиском, см. в разделе [поля поиска](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_SearchBoxes) .

![Текст элемента управления "поле поиска"](../../extensibility/ux-guidelines/media/0303_SearchBoxControl.png "0303_SearchBoxControl.png")<br />Текст элемента управления "поле поиска"

| Элемент | Имя токена: Category.color |
| --- | --- |
| Передний план (текст) | `SearchControl.UnfocusedWatermarkText` |

### <a name="hyperlink"></a>Гиперссылка
Гиперссылка — это один элемент управления, у которого нет пары «основной/фон». Во всех случаях используйте цвет гиперссылок переднего плана, который будет правильно отображаться на темном, сером и белом фоне. Если вы не используете маркер цвета для элемента управления HyperLink, вы увидите системный цвет по умолчанию для "нажато", который будет мигать красным. Это сигнал того, что элемент управления не использует правильный маркер цвета среды.

![Гиперссылка (красная линия)](../../extensibility/ux-guidelines/media/0303-133_hyperlinkredline.png "0303 — 133_HyperlinkRedline")<br />Гиперссылка (красная линия)

| Использовать... | Не используйте... |
| --- | --- |
| ... Если необходимо создать пользовательскую гиперссылку. | ... для любых элементов, которые не являются гиперссылками. |

**Гиперссылка: состояние по умолчанию**

![Гиперссылка по умолчанию](../../extensibility/ux-guidelines/media/0303-134_hyperlink.png "0303 — 134_Hyperlink")<br />Гиперссылка по умолчанию

| Элемент | Имя токена: Category.color |
| --- | --- |
| Передний план (текст) | `Environment.PanelHyperlink` |

**Гиперссылка: состояние наведения**

![Гиперссылка при наведении курсора мыши](../../extensibility/ux-guidelines/media/0303-135_hyperlinkhover.png "0303 — 135_HyperlinkHover")<br />Гиперссылка при наведении курсора мыши

| Элемент | Имя токена: Category.color |
| --- | --- |
| Передний план (текст) | `Environment.PanelHyperlinkHover` |

**Гиперссылка: нажатое состояние**

![Нажатая гиперссылка](../../extensibility/ux-guidelines/media/0303-136_hyperlinkpressed.png "0303 — 136_HyperlinkPressed")<br />Нажатая гиперссылка

| Элемент | Имя токена: Category.color |
| --- | --- |
| Передний план (текст) | `Environment.PanelHyperlinkPressed` |

**Гиперссылка: отключенное состояние**

![Отключенная гиперссылка](../../extensibility/ux-guidelines/media/0303-137_hyperlinkdisabled.png "0303 — 137_HyperlinkDisabled")<br />Отключенная гиперссылка

| Элемент | Имя токена: Category.color |
| --- | --- |
| Передний план (текст) | `Environment.PanelHyperlinkDisabled` |

### <a name="infobars"></a>инфобарс
Информационные панели служат для предоставления дополнительной информации о данном контексте и всегда отображаются в верхней части окна документа или окна инструментов.

![Информационная панель (красная линия)](../../extensibility/ux-guidelines/media/0303-138_infobarredline.png "0303 — 138_InfobarRedline")<br />Информационная панель (красная линия)

| Использовать... | Не используйте... |
| --- | --- |
| ... При создании пользовательской инфобарс. | ... для элементов пользовательского интерфейса, которые не похожи на информационную панель. |

**Информационная панель: состояние по умолчанию**

![Информационная панель по умолчанию](../../extensibility/ux-guidelines/media/0303-139_infobar.png "0303 — 139_Infobar")<br />Информационная панель по умолчанию

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `InfoBar.InfoBarBackground` |
| Передний план (текст) | `InfoBar.InfoBar` |
| Рамка | `InfoBar.InfoBarBorder` |

**&times;Кнопка "Закрыть" (): состояние по умолчанию**

![Кнопка панели по умолчанию закрыть ( &times; )](../../extensibility/ux-guidelines/media/0303_InfobarCloseDefault.png "0303_InfobarCloseDefault.png")<br />Кнопка панели по умолчанию закрыть ( &times; )

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `InfoBar.CloseButton` |
| Рамка | `InfoBar.CloseButtonBorder` |
| Глиф | `InfoBar.CloseButtonGlyph` |

**Кнопка панели по закрытию ( &times; ): состояние наведения**

![&times;Кнопка с изображением кнопки "Закрыть" () при наведении указателя](../../extensibility/ux-guidelines/media/0303_InfobarCloseHover.png "0303_InfobarCloseHover.png")<br />&times;Кнопка с изображением кнопки "Закрыть" () при наведении указателя

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `InfoBar.CloseButtonHover` |
| Рамка | `InfoBar.CloseButtonHoverBorder` |
| Глиф | `InfoBar.CloseButtonHoverGlyph` |

**Кнопка "Закрыть" () в панели сведений &times; : нажатое состояние**

![Кнопка закрытия () нажатой панели &times;](../../extensibility/ux-guidelines/media/0303_InfobarClosePressed.png "0303_InfobarClosePressed.png")<br />Кнопка закрытия () нажатой панели &times;

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `InfoBar.CloseButtonDown` |
| Рамка | `InfoBar.CloseButtonDownBorder` |
| Глиф | `InfoBar.CloseButtonDownGlyph` |

**Кнопка гиперссылки на информационной панели: состояние по умолчанию**

![Кнопка ссылки на панель по умолчанию](../../extensibility/ux-guidelines/media/0303_InfobarHyperlinkButtonDefault.png "0303_InfobarHyperlinkButtonDefault.png")<br />Кнопка ссылки на панель по умолчанию

| Элемент | Имя токена: Category.color |
| --- | --- |
| Передний план (текст) | `InfoBar.Hyperlink` |

**Кнопка гиперссылки в информационной панели: состояние наведения**

![Кнопка гиперссылки в информационной панели при наведении указателя](../../extensibility/ux-guidelines/media/0303_InfobarHyperlinkButtonHover.png "0303_InfobarHyperlinkButtonHover.png")<br />Кнопка гиперссылки в информационной панели при наведении указателя

| Элемент | Имя токена: Category.color |
| --- | --- |
| Передний план (текст) | `Infobar.HyperlinkMouseOver`<br />(С подчеркиванием) |

**Кнопка с гиперссылкой на информационную панель: нажатое состояние**

![Кнопка гиперссылки нажатой панели](../../extensibility/ux-guidelines/media/0303_InfobarHyperlinkButtonPressed.png "0303_InfobarHyperlinkButtonPressed.png")<br />Кнопка гиперссылки нажатой панели

| Элемент | Имя токена: Category.color |
| --- | --- |
| Передний план (текст) | `Infobar.HyperlinkMouseDown`<br />(С подчеркиванием) |

**Встроенная гиперссылка в тексте (внутри предложения): состояние по умолчанию**

![Кнопка гиперссылки по умолчанию встроенной информационной панели](../../extensibility/ux-guidelines/media/0303_InfobarHyperlinkButtonDefault.png "0303_InfobarHyperlinkButtonDefault.png")<br />Кнопка гиперссылки по умолчанию встроенной информационной панели

| Элемент | Имя токена: Category.color |
| --- | --- |
| Передний план (текст) | `InfoBar.Hyperlink` |

**Встроенная гиперссылка в тексте (внутри предложения): состояние наведения**

![Кнопка встроенной информационной гиперссылки при наведении указателя](../../extensibility/ux-guidelines/media/0303_InfobarHyperlinkInlineHover.png "0303_InfobarHyperlinkInlineHover.png")<br />Кнопка встроенной информационной гиперссылки при наведении указателя

| Элемент | Имя токена: Category.color |
| --- | --- |
| Передний план (текст) | `Infobar.HyperlinkMouseOver`<br />(С подчеркиванием) |

**Встроенная гиперссылка в тексте (внутри предложения): нажатое состояние**

![Кнопка встроенной информационной панели в нажатой ссылке](../../extensibility/ux-guidelines/media/0303_InfobarHyperlinkInlinePressed.png "0303_InfobarHyperlinkInlinePressed.png")<br />Кнопка встроенной информационной панели в нажатой ссылке

| Элемент | Имя токена: Category.color |
| --- | --- |
| Передний план (текст) | `Infobar.HyperlinkMouseDown`<br />(С подчеркиванием) |

**Кнопка информационной панели: состояние по умолчанию**

![Кнопка панели по умолчанию](../../extensibility/ux-guidelines/media/0303_InfobarButtonDefault.png "0303_InfobarButtonDefault.png")<br />Кнопка панели по умолчанию

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `InfoBar.Button` |
| Передний план (текст) | `InfoBar.Button` |
| Рамка | `InfoBar.ButtonBorder` |

**Кнопка информационной панели: состояние наведения**

![Кнопка информационной панели при наведении указателя](../../extensibility/ux-guidelines/media/0303_InfobarButtonHover.png "0303_InfobarButtonHover.png")<br />Кнопка информационной панели при наведении указателя

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `InfoBar.ButtonMouseOver` |
| Передний план (текст) | `InfoBar.ButtonMouseOver` |
| Рамка | `InfoBar.ButtonMouseOverBorder` |

**Кнопка панели со стрелкой: нажатое состояние**

![Кнопка панели со стрелкой нажатия](../../extensibility/ux-guidelines/media/0303_InfobarButtonPressed.png "0303_InfobarButtonPressed.png")<br />Кнопка панели со стрелкой нажатия

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `InfoBar.ButtonMouseDown` |
| Передний план (текст) | `InfoBar.ButtonMouseDown` |
| Рамка | `InfoBar.ButtonMouseDownBorder` |

**Кнопка информационной панели: отключенное состояние**

![Отключенная информационная кнопка](../../extensibility/ux-guidelines/media/0303_InfobarButtonDisabled.png "0303_InfobarButtonDisabled.png")<br />Отключенная информационная кнопка

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `InfoBar.ButtonDisabled` |
| Передний план (текст) | `InfoBar.ButtonDisabled` |
| Рамка | `InfoBar.ButtonDisabledBorder` |

**Кнопка информационной панели: состояние "в состоянии"**

![Кнопка информационной панели с упором](../../extensibility/ux-guidelines/media/0303_InfobarButtonFocus.png "0303_InfobarButtonFocus.png")<br />Кнопка информационной панели с упором

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `InfoBar.ButtonFocus` |
| Передний план (текст) | `InfoBar.ButtonFocus` |
| Рамка | `InfoBar.ButtonFocusBorder` |

### <a name="scroll-bars"></a>Полосы прокрутки
Полосы прокрутки имеют стиль среды Visual Studio и не должны быть включены в тему. Однако вы можете решить, что вы хотите использовать цвета, используемые в полосах прокрутки, чтобы пользовательский интерфейс всегда соответствовал этой части среды Visual Studio.

![Полоса прокрутки (красная линия)](../../extensibility/ux-guidelines/media/0303-140_scrollbarredline.png "0303 — 140_ScrollbarRedline")<br />Полоса прокрутки (красная линия)

| Использовать... | Не используйте... |
| --- | --- |
| ... При создании пользовательского интерфейса, который требуется сопоставить с полосами прокрутки Visual Studio. | ... для чего вы не хотите всегда сопоставлять пользовательский интерфейс полосы прокрутки. |

**Полоса прокрутки: состояние по умолчанию**

![Полоса прокрутки по умолчанию](../../extensibility/ux-guidelines/media/0303-141_scrollbar.png "0303 — 141_Scrollbar")<br />Полоса прокрутки по умолчанию

| Элемент | Имя токена: Category.color |
| --- | --- |
| полоса прокрутки; | `Environment.ScrollBarBackground` |
| Передний план (бегунок) | `Environment.ScrollBarThumbBackground` |

**Полоса прокрутки: состояние наведения**

![Полоса прокрутки при наведении курсора мыши](../../extensibility/ux-guidelines/media/0303-143_scrollbarhover.png "0303 — 143_ScrollbarHover")<br />Полоса прокрутки при наведении курсора мыши

| Элемент | Имя токена: Category.color |
| --- | --- |
| полоса прокрутки; | `Environment.ScrollBarBackground` |
| Передний план (бегунок) | `Environment.ScrollBarThumbMouseOverBackground` |

*Полоса прокрутки: нажатое состояние**

![Нажатая полоса прокрутки](../../extensibility/ux-guidelines/media/0303-145_scrollbarpressed.png "0303 — 145_ScrollbarPressed")<br />Нажатая полоса прокрутки

| Элемент | Имя токена: Category.color |
| --- | --- |
| полоса прокрутки; | `Environment.ScrollBarBackground` |
| Передний план (бегунок) | `Environment.ScrollBarThumbPressedBackground` |

**Стрелка полосы прокрутки: состояние по умолчанию**

![Стрелка полосы прокрутки по умолчанию](../../extensibility/ux-guidelines/media/0303-142_scrollbararrow.png "0303 — 142_ScrollbarArrow")<br />Стрелка полосы прокрутки по умолчанию

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `Environment.ScrollBarArrowBackground`<br />(Задайте тот же цвет, что и полоса прокрутки.) |
| Передний план (глиф) | `Environment.ScrollBarArrowGlyph` |

**Стрелка полосы прокрутки: состояние наведения**

![Стрелки полосы прокрутки при наведении курсора мыши](../../extensibility/ux-guidelines/media/0303-144_scrollbararrowhover.png "0303 — 144_ScrollbarArrowHover")<br />Стрелки полосы прокрутки при наведении курсора мыши

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `Environment.ScrollBarArrowMouseOverBackground`<br />(Задайте тот же цвет, что и полоса прокрутки.) |
| Передний план (глиф) | `Environment.ScrollBarArrowGlyphMouseOver` |

**Стрелка полосы прокрутки: нажатое состояние**

![Стрелка полосы прокрутки нажата](../../extensibility/ux-guidelines/media/0303-146_scrollbararrowpressed.png "0303 — 146_ScrollbarArrowPressed")<br />Стрелка полосы прокрутки нажата

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `Environment.ScrollBarArrowPressedBackground`<br />(Задайте тот же цвет, что и полоса прокрутки.) |
| Передний план (глиф) | `Environment.ScrollBarArrowGlyphPressed` |

### <a name="search-boxes"></a><a name="BKMK_SearchBoxes"></a>Поля поиска
По возможности используйте стандартный элемент управления поиском, предоставляемый средой Visual Studio. Цвета поля поиска находятся в категории SearchControl в файле **ShellColors.pkgdef** , который содержит имена токенов для поля ввода, управляющей кнопки, кнопки раскрывающегося списка и раскрывающегося меню.

Поле поиска может находиться в одном из нескольких состояний. Некоторые из них взаимоисключающие.

- "С фокусом ввода" или "без фокуса ввода" указывает на то, находится ли курсор в текстовом поле.

- "Активно" или "неактивно" указывает на то, ввел ли пользователь запрос в текстовом поле.

- "При наведении указателя" означает, что пользователь навел указатель мыши на поле поиска (это состояние переопределяет все остальные).

- "Отключено" означает, что функция поиска в текущем контексте отключена.

![Поле поиска (красная линия)](../../extensibility/ux-guidelines/media/0303-110_searchboxredline.png "0303 — 110_SearchBoxRedline")<br />Поле поиска (красная линия)

| Использовать... | Не используйте... |
| --- | --- |
| ... При проектировании пользовательского поля поиска. | ... для любых элементов, которые не являются полем поиска. |
| | ... для всех элементов, которые не нужно всегда сопоставлять пользовательскому интерфейсу поля поиска. |

**Поле ввода для поиска с фокусом**

![Поле ввода для поиска с фокусом](../../extensibility/ux-guidelines/media/0303-111_searchinputfieldfocused.png "0303 — 111_SearchInputFieldFocused")<br />Поле ввода для поиска с фокусом

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `SearchControl.FocusedBackground` |
| Передний план (текст) | `SearchControl.FocusedBackground` |
| Рамка | `SearchControl.FocusedBorder` |
| Separator | `SearchControl.FocusedDropDownSeparator` |

**Нефокусическое поле ввода активного поиска**

![Поле ввода окна поиска без фокуса ввода](../../extensibility/ux-guidelines/media/0303-114_searchinputfieldunfocused.png "0303 — 114_SearchInputFieldUnfocused")<br />Нефокусическое поле ввода активного поиска

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `SearchControl.SearchActiveBackground` |
| Передний план (текст) | `SearchControl.SearchActiveBackground` |
| Рамка | `SearchControl.UnfocusedBorder` |
| Separator | `SearchControl.DropDownSeparator` |

**Нефокусное поле ввода неактивного поиска**

![Нефокусное поле ввода неактивного поиска](../../extensibility/ux-guidelines/media/0303-114-1_searchinputfieldunfocusedinactive.png "0303-114-1_SearchInputFieldUnfocusedInactive")<br />Нефокусное поле ввода неактивного поиска

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `SearchControl.Unfocused` |
| Передний план (текст) | `SearchControl.Unfocused` |
| Рамка | `SearchControl.UnfocusedBorder` |
| Separator | `SearchControl.DropDownSeparator` |

**Выделенное поле ввода для поиска (только текст)**

![Выделенное поле ввода для поиска](../../extensibility/ux-guidelines/media/0303-120_searchinputfieldhighlight.png "0303 — 120_SearchInputFieldHighlight")<br />Выделенное поле ввода для поиска

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `SearchControl.Selection` |
| Передний план (текст) | `SearchControl.FocusedBackground` |
| Рамка | Отсутствуют |
| Separator | `SearchControl.FocusedDropDownSeparator` |

**Отключенное поле ввода для поиска**

![Отключенное поле ввода для поиска](../../extensibility/ux-guidelines/media/0303-121_searchinputfielddisabled.png "0303 — 121_SearchInputFieldDisabled")<br />Отключенное поле ввода для поиска

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `SearchControl.Disabled` |
| Передний план (текст) | `SearchControl.Disabled` |
| Рамка | `SearchControl.DisabledBorder` |
| Separator | `SearchControl.DropDownSeparator` |

**Кнопка действия поиска с сортировкой**

![Кнопка поиска с фокусом ввода](../../extensibility/ux-guidelines/media/0303-112_searchactionbuttonfocused.png "0303 — 112_SearchActionButtonFocused")<br />Кнопка действия поиска с сортировкой

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | Отсутствуют |
| Передний план (глиф поиска) | `SearchControl.SearchGlyph` |
| Передний план (глиф остановки) | `SearchControl.StopGlyph` |
| Передний план (глиф очистки) | `SearchControl.ClearGlyph` |
| Рамка | Н/Д |

**Кнопка "действие поиска нефокуса"**

![Кнопка "действие поиска нефокуса"](../../extensibility/ux-guidelines/media/0303-115_searchactionbuttonunfocused.png "0303 — 115_SearchActionButtonUnfocused")<br />Кнопка "действие поиска нефокуса"

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | Н/Д |
| Передний план (глиф поиска) | `SearchControl.SearchGlyph` |
| Передний план (глиф остановки) | `SearchControl.StopGlyph` |
| Передний план (глиф очистки) | `SearchControl.ClearGlyph` |
| Рамка | Н/Д |

**Кнопка "действие поиска" нажата**

![Кнопка "действие поиска" нажата](../../extensibility/ux-guidelines/media/0303-116-1_searchactionbuttonpressed.png "0303-116-1_SearchActionButtonPressed")<br />Кнопка "действие поиска" нажата

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `SearchControl.ActionButtonMouseDown` |
| Передний план (глиф) | `SearchControl.ActionButtonMouseDownGlyph` |
| Рамка | `SearchControl.ActionButtonMouseDownBorder` |

**Кнопка действия "отключено" для поиска**

![Неактивная кнопка поиска](../../extensibility/ux-guidelines/media/0303-122_searchactionbuttondisabled.png "0303 — 122_SearchActionButtonDisabled")<br />Кнопка действия "отключено" для поиска

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | Отсутствуют |
| Передний план (глиф) | `SearchControl.ActionButtonDisabledGlyph` |
| Рамка | Отсутствуют |

**Кнопка раскрывающегося списка поиска с сортировкой**

![Кнопка раскрывающегося списка поиска с сортировкой](../../extensibility/ux-guidelines/media/0303-113_searchdropdownbuttonfocused.png "0303 — 113_SearchDropdownButtonFocused")<br />Кнопка раскрывающегося списка поиска с сортировкой

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `SearchControl.FocusedDropDownButton` |
| Передний план (глиф) | `SearchControl.FocusedDropDownButtonGlyph` |
| Рамка | `SearchControl.FocusedDropDownButtonBorder` |

**Кнопка раскрывающегося списка нефокусного поиска**

![Кнопка раскрывающегося списка нефокусного поиска](../../extensibility/ux-guidelines/media/0303-116_searchdropdownbuttonunfocused.png "0303 — 116_SearchDropdownButtonUnfocused")<br />Кнопка раскрывающегося списка нефокусного поиска

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `SearchControl.UnfocusedDropDownButton` |
| Передний план (глиф) | `SearchControl.UnfocusedDropDownButtonGlyph` |
| Рамка | `SearchControl.UnfocusedDropDownButtonBorder` |

**Кнопка раскрывающегося списка нажатия кнопки поиска**

![Кнопка раскрывающегося списка нажатия кнопки поиска](../../extensibility/ux-guidelines/media/0303-116-2_searchdropdownbuttonpressed.png "0303-116-2_SearchDropdownButtonPressed")<br />Кнопка раскрывающегося списка нажатия кнопки поиска

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `SearchControl.MouseDownDropDownButton` |
| Передний план (глиф) | `SearchControl.MouseDownDropDownButtonGlyph` |
| Рамка | `SearchControl.MouseDownDropDownButtonBorder` |

**Кнопка раскрывающегося списка отключенных результатов поиска**

![Кнопка раскрывающегося списка отключенных результатов поиска](../../extensibility/ux-guidelines/media/0303-123_searchdropdownbuttondisabled.png "0303 — 123_SearchDropdownButtonDisabled")<br />Кнопка раскрывающегося списка отключенных результатов поиска

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | Отсутствуют |
| Передний план (глиф) | `SearchControl.DisabledDownButtonGlyph` |
| Рамка | Отсутствуют |

#### <a name="search-drop-down-lists"></a>Раскрывающиеся списки поиска
Раскрывающееся меню поля поиска может быть несколько более сложным, чем другие раскрывающиеся меню в Visual Studio. Разделы "предлагаемые поиски" и "Параметры поиска" могут содержаться в меню отдельно или вместе, и каждый из них окрашен раздельно. Если имеются оба этих раздела, они разделяются линией, а все раскрывающееся меню окружено границей.

![Раскрывающийся список поиска (красная линия)](../../extensibility/ux-guidelines/media/0303-124_searchdropdownredline.png "0303 — 124_SearchDropdownRedline")<br />Раскрывающийся список поиска (красная линия)

| Использовать... | Не используйте... |
| --- | --- |
| ... При создании раскрывающегося списка пользовательского поиска. | ... для раскрывающихся списков, которые отображаются в других контекстах. |
| ... правильные имена токенов для правильных компонентов списка. | ... При любом сочетании фона или переднего плана, кроме указанного. |

**Элементы раскрывающегося списка поиска**

| Элемент | Имя токена: Category.color |
| --- | --- |
| Рамка | `SearchControl.PopupBorder` |
| Separator | `SearchControl.PopupSectionHeaderSeparator` |
| Shadow | `Environment.DropShadowBackground` |

**Предлагаемые поиски: состояние по умолчанию**

![Предлагаемые поисковые запросы по умолчанию](../../extensibility/ux-guidelines/media/0303-125_searchsuggested.png "0303 — 125_SearchSuggested")<br />Предлагаемые поисковые запросы по умолчанию

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `SearchControl.PopupItemsListBackgroundGradientBegin`<br />(Ограничения градиента для этого маркера не используются в пользовательском интерфейсе с темой.) |
| Передний план (текст) | `SearchControl.PopupItemText` |

**Предлагаемые поиски: состояние наведения**

![Предлагаемые поиски при наведении указателя мыши](../../extensibility/ux-guidelines/media/0303-128_searchsuggestedhover.png "0303 — 128_SearchSuggestedHover")<br />Предлагаемые поиски при наведении указателя мыши

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `SearchControl.PopupControlMouseOverBackgroundGradientBegin`<br />(Ограничения градиента для этого маркера не используются в пользовательском интерфейсе с темой.) |
| Передний план (текст) | `SearchControl.PopupMouseOverItemText` |
| Рамка | `SearchControl.PopupControlMouseOverBorder` |

**Параметры поиска: состояние по умолчанию**

![Флажок поиска](../../extensibility/ux-guidelines/media/0303-126_searchcheckbox.png "0303 — 126_SearchCheckbox")<br />Параметры поиска по умолчанию (флажок)

![Параметры поиска](../../extensibility/ux-guidelines/media/0303-127_searchoptions.png "0303 — 127_SearchOptions")<br />Параметры поиска по умолчанию (ссылка)

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `SearchControl.PopupSectionBackgroundGradientBegin`<br />(Ограничения градиента для этого маркера не используются в пользовательском интерфейсе с темой.) |
| Передний план (текст флажка) | `SearchControl.PopupCheckboxText` |
| Передний план (текст ссылки) | `SearchControl.PopupButtonText` |
| Фон заголовка | `SearchControl.PopupSectionHeaderGradientBegin`<br />(Ограничения градиента для этого маркера не используются в пользовательском интерфейсе с темой.) |
| Передний план (текст заголовка) | `SearchControl.PopupSectionHeaderText` |

**Параметры поиска: состояние наведения**

![Параметры поиска (флажок) при наведении указателя](../../extensibility/ux-guidelines/media/0303-129_searchcheckboxhover.png "0303 — 129_SearchCheckboxHover")<br />Параметры поиска (флажок) при наведении указателя

![Параметры поиска (ссылка) при наведении указателя](../../extensibility/ux-guidelines/media/0303-130_searchoptionshover.png "0303 — 130_SearchOptionsHover")<br />Параметры поиска (ссылка) при наведении указателя

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `SearchControl.PopupControlMouseOverBackgroundGradientBegin`<br />(Ограничения градиента для этого маркера не используются в пользовательском интерфейсе с темой.) |
| Передний план (текст флажка) | `SearchControl.PopupCheckboxMouseDownText` |
| Передний план (текст ссылки) | `SearchControl.PopupButtonMouseDownText` |
| Рамка | `SearchControl.PopupControlMouseOverBorder` |

**Параметры поиска: нажатое состояние**

![Параметры поиска при нажатии (флажок)](../../extensibility/ux-guidelines/media/0303-131_searchsuggestedpressed.png "0303 — 131_SearchSuggestedPressed")<br />Параметры поиска при нажатии (флажок)

![Параметры поиска в нажатии (ссылка)](../../extensibility/ux-guidelines/media/0303-132_searchoptionspressed.png "0303 — 132_SearchOptionsPressed")<br />Параметры поиска в нажатии (ссылка)

| Элемент | Имя токена: Category.color |
| --- | --- |
| Фон флажка | `SearchControl.PopupControlMouseDownBackgroundGradientBegin`<br />`SearchControl.PopupControlMouseDownBackgroundGradientEnd`<br />(Ограничения градиента для этого маркера не используются в пользовательском интерфейсе с темой.) |
| Передний план (текст флажка) | `SearchControl.PopupCheckboxMouseDownText` |
| Фон ссылки | `SearchControl.PopupButtonMouseDownBackgroundGradientBegin`<br />(Ограничения градиента для этого маркера не используются в пользовательском интерфейсе с темой.) |
| Передний план (текст ссылки) | `SearchControl.PopupButtonMouseDownText` |

### <a name="tree-views"></a><a name="BKMK_TreeView"></a> Представления в виде дерева
Несколько окон инструментов, в том числе обозреватель решений, обозреватель сервера и представление классов, реализуют иерархическую организационную схему, цвета которой управляются именами цветов в `TreeView` категории. Все элементы в иерархическом представлении имеют цвета фона и текста. Элементы с вложенными дочерними элементами также имеют глифы, которые указывают на то, является ли элемент свернутым или развернутым.

![Представление в виде дерева (красная линия)](../../extensibility/ux-guidelines/media/0303-147_treeviewredline.png "0303 — 147_TreeViewRedline")<br />Представление в виде дерева (красная линия)

| Использовать... | Не используйте... |
| --- | --- |
| ... в любом месте необходимо реализовать иерархическое организационное представление. | ... для любых элементов, которые не похожи на представление в виде дерева. |
| | ... При любом сочетании фона или переднего плана, кроме указанного. |

**Элемент представления в виде дерева: состояние по умолчанию**

![Элемент представления в виде дерева по умолчанию](../../extensibility/ux-guidelines/media/0303-148_treeview.png "0303 — 148_TreeView")<br />Элемент представления в виде дерева по умолчанию

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `TreeView.Background` |
| Передний план (текст) | `TreeView.Background` |
| Передний план (глиф) | `TreeView.Glyph` |
| Рамка | Отсутствуют |

**Элемент представления в виде дерева: состояние наведения**

![Элемент представления в виде дерева при наведении указателя мыши](../../extensibility/ux-guidelines/media/0303-149_treeviewhover.png "0303 — 149_TreeViewHover")<br />Элемент представления в виде дерева при наведении указателя мыши

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `TreeView.Background` |
| Передний план (текст) | `TreeView.Background` |
| Передний план (глиф) | `TreeView.GlyphMouseOver` |
| Рамка | Отсутствуют |

**Элемент представления в виде дерева: перетаскивать по состоянию**

![Элемент иерархического представления при перетаскивании](../../extensibility/ux-guidelines/media/0303-150_treeviewdragover.png "0303 — 150_TreeViewDragOver")<br />Элемент иерархического представления при перетаскивании

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `TreeView.DragOverItem` |
| Передний план (текст) | `TreeView.DragOverItem` |
| Передний план (глиф) | `TreeView.DragOverItemGlyph` |
| Рамка | Отсутствуют |

**Элемент представления в виде дерева: выбрано, состояние с сортировкой**

![Выбранное и детализированное представление дерева](../../extensibility/ux-guidelines/media/0303-151_treeviewfocused.png "0303 — 151_TreeViewFocused")<br />Выбранное и детализированное представление дерева

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `TreeView.SelectedItemActive` |
| Передний план (текст) | `TreeView.SelectedItemActive` |
| Передний план (глиф) | `TreeView.SelectedItemActiveGlyph` |
| Рамка | `TreeView.FocusVisualBorder` |

**Элемент представления в виде дерева: выбрано, нефокусное состояние**

![Выделенный и нефокусный элемент представления дерева](../../extensibility/ux-guidelines/media/0303-152_treeviewunfocused.png "0303 — 152_TreeViewUnfocused")<br />Выделенный и нефокусный элемент представления дерева

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `TreeView.SelectedItemInactive` |
| Передний план (текст) | `TreeView.SelectedItemInactive` |
| Передний план (глиф) | `TreeView.SelectedItemInactiveGlyph` |
| Рамка | Отсутствуют |

**Элемент представления в виде дерева: с наведением, выбрано и с состоянием "упор"**

![Выбранное и детализированное представление дерева при наведении указателя мыши](../../extensibility/ux-guidelines/media/0303-153_treeviewfocusedhover.png "0303 — 153_TreeViewFocusedHover")<br />Выбранное и детализированное представление дерева при наведении указателя мыши

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `TreeView.SelectedItemActive` |
| Передний план (текст) | `TreeView.SelectedItemActive` |
| Передний план (глиф) | `TreeView.SelectedItemActiveGlyphMouseOver` |
| Рамка | `TreeView.FocusVisualBorder` |

**Элемент представления в виде дерева: с наведением, с выделением и без фокуса**

![Выделенный и нефокусный элемент представления дерева при наведении указателя мыши](../../extensibility/ux-guidelines/media/0303-154_treeviewunfocusedhover.png "0303 — 154_TreeViewUnfocusedHover")<br />Выделенный и нефокусный элемент представления дерева при наведении указателя мыши

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `TreeView.SelectedItemInactive` |
| Передний план (текст) | `TreeView.SelectedItemInactive` |
| Передний план (глиф) | `TreeView.SelectedItemActiveGlyphMouseOver` |
| Рамка | Отсутствуют |

## <a name="shell-appearance"></a>Внешний вид оболочки

### <a name="background"></a>Историческая справка
Фон среды состоит из двух слоев. Нижний слой представляет собой сплошной цвет, который охватывает всю интегрированную среду разработки. Верхний слой используется под командной полкой и между каналами автоматического скрытия окон инструментов по левому и правому краям интегрированной среды разработки. Верхние и нижние фоновые слои устанавливаются на один и тот же цвет в светлых и темных темах.

![Фон оболочки Visual Studio (красная линия)](../../extensibility/ux-guidelines/media/0303-187_shellbackgroundredline.png "0303 — 187_ShellBackgroundRedline")<br />Фон оболочки Visual Studio (красная линия)

| Использовать... | Не используйте... |
| --- | --- |
| ... для мест, где нужно сопоставить фон среды Visual Studio. | ... в качестве заливки для мест, которые не являются фоновыми поверхности. |
| | ... в качестве фона для размещения элементов переднего плана. |

**Внешний вид оболочки нижнего слоя**

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `Environment.EnvironmentBackground` |

**Внешний вид оболочки верхнего слоя**

> Ограничения градиента устанавливаются в светлой и темной темах Visual Studio 2013 в одно значение цвета.

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `Environment.EnvironmentBackgroundGradientBegin`<br />`Environment.EnvironmentBackgroundGradientEnd`<br />`Environment.EnvironmentBackgroundGradientMiddle1`<br />`Environment.EnvironmentBackgroundGradientMiddle2` |

### <a name="command-shelf"></a>Командная полка
Для фона командной полки используются два набора имен токенов: один для области размещения строки меню, а другой — для области размещения панелей команд. Отдельные группы на панели команд имеют собственные значения цветов фона, которые более подробно рассматриваются в разделе, посвященном панели команд. Цвета текста строки меню и панели команд рассматриваются в разделах, посвященных меню и панели команд.

![Полка команд Visual Studio (красная линия)](../../extensibility/ux-guidelines/media/0303-188_commandshelfredline.png "0303 — 188_CommandShelfRedline")<br />Полка команд Visual Studio (красная линия)

| Использовать... | Не используйте... |
| --- | --- |
| ... для областей, в которых вы размещаете меню или панели инструментов. | ... для областей, которые не похожи на полку команды. |
|... с правильным сочетанием имени маркера фона и переднего плана. | |

**Строка меню полки команды**

> Ограничения градиента устанавливаются в светлой и темной темах Visual Studio 2013 в одно значение цвета.

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `Environment.CommandShelfHighlightGradientBegin`<br /><br />`Environment.CommandShelfHighlightGradientMiddle`<br />`Environment.CommandShelfHighlightGradientEnd` |

**Панель команд полки команды**

> Ограничения градиента устанавливаются в светлой и темной темах Visual Studio 2013 в одно значение цвета.

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `Environment.CommandShelfBackgroundGradientBegin`<br />`Environment.CommandShelfBackgroundGradientMiddle`<br />`Environment.CommandShelfBackgroundGradientEnd` |

## <a name="manifest-designer"></a>Конструктор манифеста
Конструктор манифеста призван упростить редактирование файла манифеста в проектах Windows 8 и Windows Phone 8. Хотя общего готового шаблона нет, рекомендуется обеспечивать соответствие макету и цветам вкладок ориентации и навигации, а также общей структуре. Дополнительные сведения о макете см. в разделе [Layout for Visual Studio](../../extensibility/ux-guidelines/layout-for-visual-studio.md).

![Конструктор манифестов (красная линия)](../../extensibility/ux-guidelines/media/0303-175_manifestdesignerredline.png "0303 — 175_ManifestDesignerRedline")<br />Конструктор манифестов (красная линия)

| Использовать... | Не используйте... |
| --- | --- |
| ... для конструкторов, которые похожи на конструктор манифеста. | ... Если у вас более шести вкладок. |
| ... Вместо использования общих элементов управления "Вкладка" в верхней части редактора в контейнере документа. | ... для любого пользовательского интерфейса, не структурированного как конструктор манифеста. |

**Выбранная вкладка конструктора манифестов: состояние по умолчанию**

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `ManifestDesigner.TabActive` |
| Рамка | Отсутствуют |

**Выбранная панель описания конструктора манифестов: состояние по умолчанию**

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `ManifestDesigner.DescriptionPane` |

**Конструктор манифестов выбранная страница содержимого: состояние по умолчанию**

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `ManifestDesigner.Background` |
| Текст подсказки для диалогового окна | `ManifestDesigner.WatermarkText`<br />(Это имя токена не соответствует его функции.) |

**Вкладка "Конструктор манифестов": невыбранное состояние**

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `ManifestDesigner.Tab.Inactive` |

**Вкладка "Конструктор манифестов": состояние наведения**

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `ManifestDesigner.Tab.Mouseover` |

## <a name="command-structures"></a>Структура команд

### <a name="menus"></a><a name="BKMK_CommandMenus"></a> Ярлык
Меню могут находиться в нескольких местах в Visual Studio: в главной строке меню, внедренной в документ или в окнах инструментов, или при щелчке правой кнопкой мыши в различных местах в интегрированной среде разработки. Реализация меню, связанных с другими элементами пользовательского интерфейса, рассматривается в разделах, посвященных соответствующим элементам. Всегда используйте стандартную реализацию меню, предоставляемую средой Visual Studio. Однако в некоторых редких случаях доступ к стандартным меню Visual Studio может отсутствовать. В таких ситуациях используйте указанные ниже имена токенов для обеспечения согласованности пользовательского интерфейса с другими меню в Visual Studio.

![Меню Visual Studio (красная линия)](../../extensibility/ux-guidelines/media/0303-000_menuredline.png "0303 — 000_MenuRedline")<br />Меню Visual Studio (красная линия)

| Использовать... | Не используйте... |
| --- | --- |
| ... Если необходимо создать пользовательское меню.| ... единственный цвет фона. Всегда используйте определенное сочетание цвета фона и цвета переднего плана. |
| ... При наличии нового компонента пользовательского интерфейса, который необходимо сопоставить с меню Visual Studio.| |

#### <a name="menu-titles"></a>Заголовки меню
Заголовок меню состоит из фона, границы и текста заголовка, а также необязательного глифа (обычно если меню находится на панели команд).

![Заголовок меню (красная линия)](../../extensibility/ux-guidelines/media/0303-001_menutitleredline.png "0303 — 001_MenuTitleRedline")<br />Заголовок меню (красная линия)

| Использовать... | Не используйте... |
| --- | --- |
| ... При создании заголовка пользовательского меню. | ... для любых элементов, которые не всегда должны соответствовать заголовку меню. |
| | ... При любом сочетании фона или переднего плана, кроме указанного. |

**Заголовок меню: состояние по умолчанию**

![Заголовок меню по умолчанию](../../extensibility/ux-guidelines/media/0303-002_menutitledefault.png "0303 — 002_MenuTitleDefault")<br />Заголовок меню по умолчанию

![Заголовок меню по умолчанию с глифом](../../extensibility/ux-guidelines/media/0303-003_menutitlewithglyphdefault.png "0303 — 003_MenuTitleWithGlyphDefault")<br />Заголовок меню по умолчанию с глифом

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | Отсутствуют |
| Передний план (текст) | `Environment.CommandBarTextActive` |
| Передний план (глиф) | `Environment.CommandBarMenuGlyph` |
| Рамка | Отсутствуют |

**Заголовок меню: состояние наведения**

![Заголовок меню при наведении курсора мыши](../../extensibility/ux-guidelines/media/0303-004_menutitlehover.png "0303 — 004_MenuTitleHover")<br />Заголовок меню при наведении курсора мыши

![Заголовок меню с глифом при наведении курсора мыши](../../extensibility/ux-guidelines/media/0303-005_menutitlewithglyphhover.png "0303 — 005_MenuTitleWithGlyphHover")<br />Заголовок меню с глифом при наведении курсора мыши

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `Environment.CommandBarMouseOverBackgroundBegin`<br />(Ограничения градиента для этого маркера не используются в пользовательском интерфейсе с темой.) |
| Передний план (текст) | `Environment.CommandBarTextHover` |
| Передний план (глиф) | `Environment.CommandBarMenuMouseOverGlyph` |
| Рамка | `Environment.CommandBarBorder` |

**Заголовок меню: нажатое состояние**

![Заголовок меню нажатия](../../extensibility/ux-guidelines/media/0303-006_menutitlepressed.png "0303 — 006_MenuTitlePressed")<br />Заголовок меню нажатия

![Заголовок контекстного меню с глифом](../../extensibility/ux-guidelines/media/0303-007_menutitlewithglyphpressed.png "0303 — 007_MenuTitleWithGlyphPressed")<br />Заголовок контекстного меню с глифом

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `Environment.CommandBarMenuBackgroundGradientBegin`<br/>(Ограничения градиента для этого маркера не используются в пользовательском интерфейсе с темой.) |
| Передний план (текст) | `Environment.CommandBarTextActive` |
| Передний план (глиф) | `Environment.CommandBarMenuMouseDownGlyph` |
| Рамка | `Environment.CommandBarMenuBorder`<br />(Только левые, верхняя и правая стороны.) |

**Заголовок меню: отключенное состояние**

![Заголовок меню отключен с глифом](../../extensibility/ux-guidelines/media/0303-008_menutitlewithglyphdisabled.png "0303 — 008_MenuTitleWithGlyphDisabled")<br />Заголовок меню отключен с глифом

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | Отсутствуют |
| Передний план (текст) | `Environment.CommandBarTextInactive` |
| Передний план (глиф) | `Environment.CommandBarTextInactive` |
| Рамка | Отсутствуют |

#### <a name="menu-items"></a>Пункты меню
Отдельный пункт меню состоит из текста и необязательных значка, флажка или глифа подменю. Его цвета фона и текста меняются при наведении указателя. Этот токен цвета представляет собой пару, состоящую из цвета фона и цвета переднего плана.

![Красная линия пунктов меню](../../extensibility/ux-guidelines/media/0303-009_menuitemredline.png "0303 — 009_MenuItemRedline")

| Использовать... | Не используйте... |
|---|---|
| ... для любого раскрывающегося списка, запускаемого из строки меню или панели команд. | ... для любого раскрывающегося списка в другом контексте. |
| | ... При любом сочетании фона или переднего плана, кроме указанного. |

**Пункты меню: состояние по умолчанию**

![Элементы меню по умолчанию](../../extensibility/ux-guidelines/media/0303-010_menudefault.png "0303 — 010_MenuDefault")<br />Элементы меню по умолчанию

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `Environment.CommandBarMenuBackgroundGradientBegin`<br />(Ограничения градиента для этого маркера не используются в пользовательском интерфейсе с темой.) |
| Передний план (текст) | `Environment.CommandBarTextActive` |
| Передний план (глиф подменю) | `Environment.CommandBarMenuSubmenuGlyph` |
| Рамка | `Environment.CommandBarMenuBorder` |
| Фон канала значка | `Environment.CommandBarMenuIconBackground` |
| Separator | `Environment.CommandBarMenuSeparator` |
| Shadow | `Environment.DropShadowBackground` |

**Пункты меню: отмеченные и выбранные состояния**

![Меню с установленным флажком](../../extensibility/ux-guidelines/media/0303-011_menuchecked.png "0303 — 011_MenuChecked")<br />Отмеченный элемент меню

![Выбранное меню](../../extensibility/ux-guidelines/media/0303-012_menuselected.png "0303 — 012_MenuSelected")<br />Выбранный пункт меню

| Элемент | Имя токена: Category.color |
| --- | --- |
| Флажок | `Environment.CommandBarCheckBox` |
| Фон флажка | `Environment.CommandBarSelectedIcon` |
| Фон значка | `Environment.CommandBarSelected` |
| Граница значка | `Environment.CommandBarSelectedBorder` |

**Пункты меню: состояние наведения**

![Меню при наведении курсора мыши](../../extensibility/ux-guidelines/media/0303-013_menuhover.png "0303 — 013_MenuHover")<br />Пункт меню при наведении указателя мыши

![Меню при наведении курсора мыши с установленным флажком ](../../extensibility/ux-guidelines/media/0303-014_menuhoverchecked.png "0303 — 014_MenuHoverChecked")<br />Пункт отмеченного меню при наведении указателя мыши

![Выбранное меню при наведении курсора мыши](../../extensibility/ux-guidelines/media/0303-015_menuhoverselected.png "0303 — 015_MenuHoverSelected")<br />Выбранный пункт меню при наведении указателя

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `Environment.CommandBarMenuItemMouseOver` |
| Передний план (текст) | `Environment.CommandBarMenuItemMouseOverText` |
| Передний план (глиф подменю) | `Environment.CommandBarMenuMouseOverSubmenuGlyph` |
| Флажок | `Environment.CommandBarCheckBoxMouseOver` |
| Фон флажка | `Environment.CommandBarHoverOverSelectedIcon` |
| Фон значка | `Environment.CommandBarHoverOverSelected` |
| Граница значка | `Environment.CommandBarHoverOverSelectedIconBorder` |

**Пункты меню: отключенное состояние**

![Неактивное меню](../../extensibility/ux-guidelines/media/0303-016_menudisabled.png "0303 — 016_MenuDisabled")<br />Элемент меню отключен

![Неактивное меню с установленным флажком](../../extensibility/ux-guidelines/media/0303-017_menudisabledchecked.png "0303 — 017_MenuDisabledChecked")<br />Элемент меню отключен с галочкой

| Элемент | Имя токена: Category.color |
| --- | --- |
| Передний план (текст) | `Environment.CommandBarTextInactive` |
| Передний план (глиф подменю) | `Environment.CommandBarMenuSubmenuGlyph` |
| Флажок | `Environment.CommandBarCheckBoxDisabled` |
| Фон флажка | `Environment.CommandBarSelectedIconDisabled` |

### <a name="command-bars"></a>Панели команд
Панель команд может находиться в нескольких местах в интегрированной среде разработки Visual Studio, особенно в полках команд и внедренных в окнах инструментов или документов.

Как правило, следует всегда использовать стандартную реализацию панели команд, предоставляемую средой Visual Studio. Использование стандартного механизма обеспечивает правильное отображение визуальных элементов и согласованное поведение интерактивных элементов и других элементов управления панели команд Visual Studio. Однако если вам необходимо создать собственную панель команд, следует правильно оформить ее с помощью указанных ниже имен токенов.

![Красная линия командной строки](../../extensibility/ux-guidelines/media/0303-018_commandbarredline.png "0303 — 018_CommandBarRedline")<br />Панель команд (красная линия)

![Красная линия кнопки переполнения](../../extensibility/ux-guidelines/media/0303-019_overflowbuttonredline.png "0303 — 019_OverflowButtonRedline")<br />Кнопка переполнения (красная линия)

| Использовать... | Не используйте... |
| --- | --- |
| ... в местах, где требуется встроенная командная строка, но они не могут использовать стандартную реализацию панели команд Visual Studio. | ... для элементов пользовательского интерфейса, которые не похожи на панель команд. |
| | ... для компонентов панели команд, отличных от тех, для которых указаны имена токенов. |

#### <a name="command-bar-groups"></a>Группы панели команд
Группа панели команд состоит из связанного набора элементов управления панели команд и может содержать любое количество кнопок, разворачивающихся кнопок, раскрывающихся меню, полей со списками или меню. Цвета этих элементов управления определяются отдельными именами токенов, которые рассматриваются в других частях этого руководства. Разделительная линия служит для разделения группы на панели команд в связанные подгруппы.

![Групповая красная линия командной строки](../../extensibility/ux-guidelines/media/0303-020_commandbargroupredline.png "0303 — 020_CommandBarGroupRedline")<br />Группа панели команд (красная линия)

| Использовать... | Не используйте... |
| --- | --- |
| ... в местах, где требуется встроенная командная строка, но они не могут использовать стандартную реализацию панели команд Visual Studio. | ... для элементов пользовательского интерфейса, которые не похожи на панель команд. |
| | ... для компонентов панели команд, отличных от тех, для которых указаны имена токенов. |

**Группа панели команд: состояние по умолчанию**

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `Environment.CommandBarGradientBegin`<br />(Ограничения градиента для этого маркера не используются в пользовательском интерфейсе с темой.) |
| Рамка | `Environment.CommandBarToolBarBorder` |
| Маркер перетаскивания | `Environment.CommandBarDragHandle` |
| Separator | `Environment.CommandBarToolBarSeparator`<br />`Environment.CommandBarToolBarSeparatorHighlight` |

#### <a name="command-icons"></a>Значки команд
![Красная линия значка команды](../../extensibility/ux-guidelines/media/0303-021_commandiconredline1.png "0303 — 021_CommandIconRedline1")<br />Значок команды (красная линия)

![Значок команды с текстом красная линия](../../extensibility/ux-guidelines/media/0303-022_commandiconredline2.png "0303 — 022_CommandIconRedline2")<br />Значок команды с текстом (красная линия)

| Использовать... | Не используйте... |
| --- | --- |
| ... для всех кнопок, которые будут размещены на панели команд. | ... для элементов управления, имеющих собственные имена маркеров. |
| | ... При любом сочетании фона или переднего плана, кроме указанного. |

**Значок команды: состояние по умолчанию**

![Значок команды по умолчанию](../../extensibility/ux-guidelines/media/0303-023_commandicondefault.png "0303 — 023_CommandIconDefault")<br />Значок команды по умолчанию

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | Н/Д (наследуется от фона панели команд) |
| Передний план (текст) | `Environment.CommandBarTextActive` |
| Рамка | Н/Д |

**Значок команды: состояние по умолчанию, выбрано**

![Значок выбранной команды по умолчанию](../../extensibility/ux-guidelines/media/0303-024_commandicondefaultselected.png "0303 — 024_CommandIconDefaultSelected")<br />Значок выбранной команды по умолчанию

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `Environment.CommandBarSelected` |
| Передний план (текст) | `Environment.CommandBarTextSelected` |
| Рамка | `Environment.CommandBarSelectedBorder` |

**Значок команды: состояния наведения или разфокусирования**

![Значок команды при наведении или фокусе](../../extensibility/ux-guidelines/media/0303-025_commandiconhover.png "0303 — 025_CommandIconHover")<br />Значок команды при наведении или фокусе

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `Environment.CommandBarMouseOverBackgroundBegin`<br />(Ограничения градиента для этого маркера не используются в пользовательском интерфейсе с темой.) |
| Передний план (текст) | `Environment.CommandBarTextHover` |
| Рамка | `Environment.CommandBarBorder` |

**Значок команды: состояния наведения или фокусировки, выбранные**

![Значок выбранной команды при наведении или фокусе](../../extensibility/ux-guidelines/media/0303-026_commandiconhoverselected.png "0303 — 026_CommandIconHoverSelected")<br />Значок выбранной команды при наведении или фокусе

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `Environment.CommandBarHoverOverSelected` |
| Передний план (текст) | `Environment.CommandBarTextHoverOverSelected` |
| Рамка | `Environment.CommandBarHoverOverSelectedIconBorder` |

 **Значок команды: состояние "нажато"**

![Активный значок команды](../../extensibility/ux-guidelines/media/0303-027_commandiconpressed.png "0303 — 027_CommandIconPressed")<br />Активный значок команды

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `Environment.CommandBarMouseDownBackgroundBegin`<br />(Ограничения градиента для этого маркера не используются в пользовательском интерфейсе с темой.) |
| Передний план (текст) | `Environment.CommandBarTextMouseDown` |
| Рамка | `Environment.CommandBarBorder` |

**Значок команды: отключенное состояние**

![Неактивный значок команды](../../extensibility/ux-guidelines/media/0303-028_commandicondisabled.png "0303 — 028_CommandIconDisabled")<br />Неактивный значок команды

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | Н/Д (наследуется от фона панели команд) |
| Передний план (текст) | `Environment.CommandBarTextInactive` |
| Рамка | Н/Д |

#### <a name="command-bar-combo-boxes"></a><a name="BKMK_CommandComboBox"></a> Поля со списком для панели команд

> [!IMPORTANT]
> Поле со списком похоже на раскрывающийся список, но включает область для ввода и редактирования текста. Если раскрывающийся список не включает в себя редактируемую область текста, используйте маркеры цвета для раскрывающихся [панелей команд](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandDropDown).

![Поле со списком для панели команд красная линия](../../extensibility/ux-guidelines/media/0303-029_comboboxredline.png "0303 — 029_ComboBoxRedline")<br />Поле со списком для панели команд (красная линия)

| Использовать... | Не используйте... |
| --- | --- |
| ... При создании пользовательских полей со списком. | ... для любых элементов, которые не всегда должны соответствовать пользовательскому интерфейсу панели команд. |
| ... При создании элемента управления панели команд, похожего на поле со списком. | ... При наличии доступа к полю со списком в стиле. |

**Поле ввода поля со списком для панели команд: состояние по умолчанию**

![Поле ввода поля со списком для панели команд](../../extensibility/ux-guidelines/media/0303-030_comboboxinputfield.png "0303 — 030_ComboBoxInputField")<br />Поле ввода поля со списком для панели команд

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `Environment.ComboBoxBackground` |
| Передний план (текст) | `Environment.ComboBoxText` |
| Рамка | `Environment.ComboBoxBorder` |
| Separator | Без разделителя |

**Кнопка раскрывающегося списка на панели команд: состояние по умолчанию**

![Кнопка раскрывающегося списка&#45;вниз](../../extensibility/ux-guidelines/media/0303-031_comboboxdropdownbutton.png "0303 — 031_ComboBoxDropdownButton")<br />Кнопка раскрывающегося списка панели команд

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | Н/Д (наследуется от фона панели команд) |
| Передний план (глиф) | `Environment.ComboBoxGlyph` |

**Раскрывающийся список панели команд: состояние по умолчанию**

![Раскрывающийся список панели команд](../../extensibility/ux-guidelines/media/0303-032_comboboxdropdownlist.png "0303 — 032_ComboBoxDropdownList")<br />Раскрывающийся список панели команд

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `Environment.ComboBoxPopupBackgroundBegin`<br />(Ограничения градиента для этого маркера не используются в пользовательском интерфейсе с темой.) |
| Передний план (текст) | `Environment.ComboBoxItemText` |
| Рамка | `Environment.ComboBoxPopupBorder` |

**Поле ввода поля со списком для панели команд: состояние наведения**

![Поле ввода поля со списком на панели команд при наведении указателя](../../extensibility/ux-guidelines/media/0303-033_comboboxinputfieldhover.png "0303 — 033_ComboBoxInputFieldHover")<br />Поле ввода поля со списком на панели команд при наведении указателя

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `Environment.ComboBoxMouseOverBackgroundBegin`<br />(Ограничения градиента для этого маркера не используются в пользовательском интерфейсе с темой.) |
| Передний план (текст) | `Environment.ComboBoxMouseOverText` |
| Рамка | `Environment.ComboBoxMouseOverBorder` |
| Separator | `Environment.ComboBoxMouseOverSeparator` |

 **Раскрывающийся список Командная строка: состояние наведения**

![Кнопка раскрывающегося списка в панели команд при наведении указателя](../../extensibility/ux-guidelines/media/0303-034_comboboxdropdownbuttonhover.png "0303 — 034_ComboBoxDropdownButtonHover")<br />Кнопка раскрывающегося списка на панели команд при наведении указателя

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `Environment.ComboBoxButtonMouseOverBackground` |
| Передний план (глиф) | `Environment.ComboBoxMouseOverGlyph` |

**Раскрывающийся список панели команд: состояние наведения**

 ![Раскрывающийся список поля со списком для панели команд при наведении указателя](../../extensibility/ux-guidelines/media/0303-035_comboboxdropdownlisthover.png "0303 — 035_ComboBoxDropdownListHover")<br />Раскрывающийся список панели команд при наведении указателя

| Элемент | Имя токена: Category.color |
| --- | --- |
| Фон (пункт меню) | `Environment.ComboBoxItemMouseOverBackground` |
| Передний план (текст) | `Environment.ComboBoxItemMouseOverText` |
| Граница (пункт меню) | `Environment.ComboBoxItemMouseOverBorder` |

 **Поле ввода поля со списком для панели команд: состояние с фокусом**

![Поле ввода поля со списком для панели команд с фокусом](../../extensibility/ux-guidelines/media/0303-036_comboboxinputfieldfocused.png "0303 — 036_ComboBoxInputFieldFocused")<br />Поле ввода поля со списком для панели команд с фокусом

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `Environment.ComboBoxFocusedBackground` |
| Передний план (текст) | `Environment.ComboBoxFocusedText` |
| Рамка | `Environment.ComboBoxFocusedBorder` |
| Separator | `Environment.ComboBoxFocusedButtonSeparator` |

**Кнопка раскрывающегося списка на панели команд: состояние "направлено"**

![Кнопка раскрывающегося списка с направленной панелью команд](../../extensibility/ux-guidelines/media/0303-037_comboboxdropdownbuttonfocused.png "0303 — 037_ComboBoxDropdownButtonFocused")<br />Кнопка раскрывающегося списка с направленной панелью команд

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `Environment.ComboBoxFocusedButtonBackground` |
| Передний план (глиф) | `Environment.ComboBoxFocusedGlyph` |

 **Поле ввода поля со списком для панели команд: состояние "нажато"**

![Поле ввода поля со списком в нажатой командной строке](../../extensibility/ux-guidelines/media/0303-038_comboboxinputfieldpressed.png "0303 — 038_ComboBoxInputFieldPressed")<br />Поле ввода поля со списком в нажатой командной строке

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `Environment.ComboBoxMouseDownBackground` |
| Передний план (текст) | `Environment.ComboBoxMouseDownText` |
| Рамка | `Environment.ComboBoxMouseDownBorder` |
| Separator | `Environment.ComboBoxMouseDownSeparator` |

**Раскрывающийся список панели команд: состояние "нажато"**

![Кнопка раскрывающегося списка в нажатой строке команды](../../extensibility/ux-guidelines/media/0303-039_comboboxdropdownbuttonpressed.png "0303 — 039_ComboBoxDropdownButtonPressed")<br />Раскрывающийся список нажатой кнопки на панели команд

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `Environment.ComboBoxButtonMouseDownBackground` |
| Передний план (глиф) | `Environment.ComboBoxMouseDownGlyph` |

**Поле ввода поля со списком для панели команд: отключенное состояние**

![Отключенное поле ввода поля со списком для панели команд](../../extensibility/ux-guidelines/media/0303-041_comboboxinputfielddisabled.png "0303 — 041_ComboBoxInputFieldDisabled")<br />Отключенное поле ввода поля со списком для панели команд

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `Environment.ComboBoxDisabledBackground` |
| Передний план (текст) | `Environment.ComboBoxDisabledText` |
| Рамка | `Environment.ComboBoxDisabledBorder` |
| Separator | Без разделителя |

**Раскрывающийся список панели команд: отключенное состояние**

![Кнопка раскрывающегося списка отключенной панели команд](../../extensibility/ux-guidelines/media/0303-040_comboboxdropdownbuttondisabled.png "0303 — 040_ComboBoxDropdownButtonDisabled")<br />Кнопка раскрывающегося списка отключенной панели команд

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | Отсутствуют |
| Передний план (глиф) | `Environment.ComboBoxDisabledGlyph` |

#### <a name="command-bar-drop-downs"></a><a name="BKMK_CommandDropDown"></a> Раскрывающиеся панели команд

> [!IMPORTANT]
> Раскрывающийся список похож на поле со списком, но не имеет области для ввода и редактирования текста. Если раскрывающийся список включает редактируемую область текста, используйте маркеры цвета для [полей со списками командной строки](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandComboBox).

![Раскрывающийся список панели команд (красная линия)](../../extensibility/ux-guidelines/media/0303-042_dropdownredline.png "0303 — 042_DropdownRedline")<br />Раскрывающийся список панели команд (красная линия)

| Использовать... | Не используйте... |
| --- | --- |
| ... При создании настраиваемых элементов управления "раскрывающийся список". | ... для любых элементов, которые не похожи на раскрывающийся список. |
| | ... для полей со списком или кнопок разделения. |

**Раскрывающееся поле выбора панели команд: состояние по умолчанию**

![Раскрывающееся поле выбора панели команд по умолчанию](../../extensibility/ux-guidelines/media/0303-043_dropdownselectionfield.png "0303 — 043_DropdownSelectionField")<br />Раскрывающееся поле выбора панели команд по умолчанию

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `Environment.DropDownBackground` |
| Передний план (текст) | `DropDownText` |
| Рамка | `DropDownBorder` |
| Separator | Без разделителя |

**Кнопка раскрывающегося списка на панели команд: состояние по умолчанию**

![Кнопка раскрывающегося списка на панели команд по умолчанию](../../extensibility/ux-guidelines/media/0303-044_dropdownbutton.png "0303 — 044_DropdownButton")<br />Кнопка раскрывающегося списка на панели команд по умолчанию

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | Отсутствуют |
| Передний план (глиф) | `Environment.DropDownGlyph` |

**Раскрывающийся список панели команд: состояние по умолчанию**

![Раскрывающийся список панели команд по умолчанию](../../extensibility/ux-guidelines/media/0303-045_dropdownlist.png "0303 — 045_DropdownList")<br />Раскрывающийся список панели команд по умолчанию

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `Environment.DropDownPopupBackgroundBegin`<br />(Ограничения градиента для этого маркера не используются в пользовательском интерфейсе с темой.) |
| Передний план (текст) | `Environment.ComboBoxItemText` |
| Рамка | `Environment.DropDownPopupBorder` |
| Shadow | `Environment.DropShadowBackground` |

**Раскрывающееся поле выбора панели команд: состояние наведения**

![Раскрывающееся поле выбора панели команд при наведении указателя](../../extensibility/ux-guidelines/media/0303-046_dropdownselectionfieldhover.png "0303 — 046_DropdownSelectionFieldHover")<br />Раскрывающееся поле выбора панели команд при наведении указателя

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `Environment.DropDownMouseOverBackgroundBegin`<br />(Ограничения градиента для этого маркера не используются в пользовательском интерфейсе с темой.) |
| Передний план (текст) | `Environment.DropDownMouseOverText` |
| Рамка | `Environment.DropDownMouseOverBorder` |
| Separator | `Environment.DropDownButtonMouseOverSeparator` |

**Раскрывающийся список Командная строка: состояние наведения**

![Кнопка раскрывающегося списка на панели команд при наведении указателя](../../extensibility/ux-guidelines/media/0303-047_dropdownbuttonhover.png "0303 — 047_DropdownButtonHover")<br />Кнопка раскрывающегося списка на панели команд при наведении указателя

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `Environment.DropDownButtonMouseOverBackground` |
| Передний план (глиф) | `Environment.DropDownMouseOverGlyph` |

**Раскрывающийся список панели команд: состояние наведения**

![Раскрывающийся список панели команд при наведении указателя](../../extensibility/ux-guidelines/media/0303-048_dropdownlisthover.png "0303 — 048_DropdownListHover")<br />Раскрывающийся список панели команд при наведении указателя

| Элемент | Имя токена: Category.color |
| --- | --- |
| Фон (пункт меню) | `Environment.ComboBoxItemMouseOverBackground` |
| Передний план (текст) | `Environment.ComboBoxItemMouseOverText` |
| Граница (пункт меню) | `Environment.ComboBoxItemMouseOverBorder` |

 **Раскрывающееся поле выбора панели команд: состояние "нажато"**

![Перетащите выделенное поле&#45;вниз](../../extensibility/ux-guidelines/media/0303-049_dropdownselectionfieldpressed.png "0303 — 049_DropdownSelectionFieldPressed")<br />Раскрывающееся поле выбора панели команд нажата

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `Environment.DropDownMouseDownBackground` |
| Передний план (текст) | `Environment.DropDownMouseDownText` |
| Рамка | `Environment.DropDownMouseDownBorder` |
| Separator | `Environment.DropDownButtonMouseDownSeparator` |

**Раскрывающийся список панели команд: состояние "нажато"**

![Раскрывающийся список нажатой кнопки на панели команд](../../extensibility/ux-guidelines/media/0303-050_dropdownbuttonpressed.png "0303 — 050_DropdownButtonPressed")<br />Раскрывающийся список нажатой кнопки на панели команд

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `Environment.DropDownButtonMouseDownBackground` |
| Передний план (глиф) | `Environment.DropDownMouseDownGlyph` |

**Раскрывающееся поле выбора панели команд: отключенное состояние**

![Раскрывающийся список отключенных панелей команд для выбора](../../extensibility/ux-guidelines/media/0303-051_dropdownselectionfielddisabled.png "0303 — 051_DropdownSelectionFieldDisabled")<br />Раскрывающийся список отключенных панелей команд для выбора

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `Environment.DropDownDisabledBackground` |
| Передний план (текст) | `Environment.DropDownDisabledText` |
| Рамка | `Environment.DropDownDisabledBorder` |
| Separator | Без разделителя |

**Раскрывающийся список панели команд: отключенное состояние**

![Кнопка раскрывающегося списка отключенной панели команд](../../extensibility/ux-guidelines/media/0303-052_dropdownbuttondisabled.png "0303 — 052_DropdownButtonDisabled")<br />Кнопка раскрывающегося списка отключенной панели команд

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | Н/Д |
| Передний план (глиф) | `Environment.DropDownDisabledGlyph` |

#### <a name="command-bar-split-buttons"></a>Кнопки разделения панели команд
Для разворачивающихся кнопок используются многие имена токенов, определенные для других элементов управления панели команд, таких как кнопки, меню и текст панели команд. Все необходимые имена токенов для действий и кнопок раскрывающихся списков приводятся здесь еще раз для удобства. Раскрывающиеся списки разворачивающейся кнопки — это реализации [меню панели команд](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandMenus).

![Красная линия разворачивающейся кнопки](../../extensibility/ux-guidelines/media/0303-053_splitbuttonredline.png "0303 — 053_SplitButtonRedline")<br />Кнопка разделения панели команд (красная линия)

| Использовать... | Не используйте... |
| --- | --- |
| ... При создании пользовательской разворачивающейся кнопки. | ... для других видов кнопок. |
| | ... При любом сочетании фона или переднего плана, кроме указанного. |

**Кнопка разделения панели команд: состояние по умолчанию**

![Кнопка разделения панели команд по умолчанию](../../extensibility/ux-guidelines/media/0303-054_splitbutton.png "0303 — 054_SplitButton")<br />Кнопка разделения панели команд по умолчанию

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | Отсутствуют |
| Передний план (текст) | `Environment.CommandBarTextActive` |
| Передний план (глиф) | `Environment.CommandBarSplitButtonGlyph` |
| Рамка | Н/Д |
| Separator | Н/Д |

**Кнопка разделения панели команд: состояние наведения**

![Разворачивающаяся кнопка в панели команд при наведении указателя](../../extensibility/ux-guidelines/media/0303-055_splitbuttonhover.png "0303 — 055_SplitButtonHover")<br />Разворачивающаяся кнопка в панели команд при наведении указателя

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `Environment.CommandBarMouseOverBackgroundBegin`<br />(Ограничения градиента для этого маркера не используются в пользовательском интерфейсе с темой.) |
| Передний план (текст) | `Environment.CommandBarTextHover` |
| Передний план (глиф) | `Environment.CommandBarSplitButtonMouseOverGlyph` |
| Рамка | `Environment.CommandBarBorder` |
| Separator | `Environment.CommandBarSplitButtonSeparator` |

**Кнопка разделения панели команд: состояние "нажато"**

![Нажатая кнопка разделения панели команд](../../extensibility/ux-guidelines/media/0303-056_splitbuttonpressed.png "0303 — 056_SplitButtonPressed")<br />Нажатая кнопка разделения панели команд

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `Environment.CommandBarMouseDownBackgroundBegin`<br />(Ограничения градиента для этого маркера не используются в пользовательском интерфейсе с темой.) |
| Передний план (текст) | `Environment.CommandBarTextMouseDown` |
| Передний план (глиф) | `Environment.CommandBarSplitButtonMouseDownGlyph` |
| Рамка | `Environment.CommandBarBorder` |
| Separator | Н/Д |

**Кнопка разделения панели команд: отключенное состояние**

![Отключенная кнопка разделения панели команд](../../extensibility/ux-guidelines/media/0303-057_splitbuttondisabled.png "0303 — 057_SplitButtonDisabled")<br />Отключенная кнопка разделения панели команд

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | Н/Д |
| Передний план (текст) | `Environment.ComboBoxItemTextInactive` |
| Передний план (глиф) | `Environment.CommandBarTextInactive` |
| Рамка | Н/Д |
| Separator | Н/Д |

#### <a name="command-bar-more-options-and-overflow-buttons"></a>Кнопки "Дополнительные параметры" и "переполнение" в командной строке
Кнопка "Дополнительно" используется, если группа панели команд может настраиваться путем добавления или удаления связанных кнопок. Кнопка "Переполнение" появляется, если панель команд усекается из-за отсутствия места по горизонтали. При ее нажатии открывается меню, содержащее кнопки, которые не поместились на панели команд. Цвета этих двух кнопок определяются одним и тем же набором имен токенов.

![Кнопка "Дополнительные параметры" в строке команд (красная линия)](../../extensibility/ux-guidelines/media/0303-058_moreoptionsredline.png "0303 — 058_MoreOptionsRedline")<br />Кнопка "Дополнительные параметры" в строке команд (красная линия)

| Использовать... | Не используйте... |
| --- | --- |
| ... для настраиваемых кнопок "Дополнительные параметры" или "переполнение". | ... для кнопок, которые не имеют похожих функций на кнопку "Дополнительные параметры" или "переполнение". |

**Кнопки "Дополнительные параметры" и "переполнение" в командной строке: состояние по умолчанию**

![Кнопка "Дополнительные параметры" панели команд по умолчанию](../../extensibility/ux-guidelines/media/0303-059_moreoptions.png "0303 — 059_MoreOptions")<br />Кнопка "Дополнительные параметры" панели команд по умолчанию

![Кнопка "переполнение" панели команд по умолчанию](../../extensibility/ux-guidelines/media/0303-060_overflow.png "0303 — 060_Overflow")<br />Кнопка "переполнение" панели команд по умолчанию

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `Environment.CommandBarOptionsBackground` |
| Передний план (глиф) | `Environment.CommandBarOptionsGlyph` |

**Кнопки "Дополнительные параметры" и "переполнение" в командной строке: состояние наведения**

![Кнопка "Дополнительные параметры" на панели команд при наведении указателя](../../extensibility/ux-guidelines/media/0303-061_moreoptionshover.png "0303 — 061_MoreOptionsHover")<br />Кнопка "Дополнительные параметры" на панели команд при наведении указателя

![Кнопка "переполнение" панели команд при наведении указателя](../../extensibility/ux-guidelines/media/0303-062_overflowoptions.png "0303 — 062_OverflowOptions")<br />Кнопка "переполнение" панели команд при наведении указателя

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `Environment.CommandBarOptionsMouseOverBackgroundBegin`<br />(Ограничения градиента для этого маркера не используются в пользовательском интерфейсе с темой.) |
| Передний план (глиф) | `Environment.CommandBarOptionsMouseDownGlyph` |

**Кнопки "Дополнительные параметры" и "переполнение" в командной строке: состояние "нажато"**

![Нажата кнопка "Дополнительные параметры" в строке команд](../../extensibility/ux-guidelines/media/0303-063_moreoptionspressed.png "0303 — 063_MoreOptionsPressed")<br />Нажата кнопка "Дополнительные параметры" в строке команд

![Активное переполнение](../../extensibility/ux-guidelines/media/0303-064_overflowpressed.png "0303 — 064_OverflowPressed")<br />Нажатая кнопка "переполнение" на панели команд

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `Environment.CommandBarOptionsMouseDownBackgroundBegin`<br />(Ограничения градиента для этого маркера не используются в пользовательском интерфейсе с темой.) |
| Передний план (глиф) | `Environment.CommandBarOptionsMouseDownGlyph` |

## <a name="document-windows"></a>Окна документов
Нет необходимости реплицировать окна документов, так как они предоставляются средой Visual Studio. Однако может потребоваться использовать цвета, применяемые в окнах документов, чтобы ваш пользовательский интерфейс был согласован с этой частью среды Visual Studio.

При использовании маркеров цвета окна документа следует осторожно использовать их только для похожих элементов и всегда в парах. Если этого не сделать, в пользовательском интерфейсе могут возникнуть непредвиденные результаты.

### <a name="document-window-frames"></a>Фреймы окна документа
Окна документов могут быть закрепленными в интегрированной среде разработки или перемещаемыми как отдельные окна. Когда окно документа перемещается за пределы интегрированной среды разработки, оно по-прежнему располагается в документе и имеет цвета фона, границы, текста и табуляции, которые совпадают с цветом, который является частью интегрированной среды разработки. Однако документ размещается внутри рамки, которая имеет собственные цвета фона, границы и текста. Если в контейнере документа закреплены окна инструментов, они наследуют поведение и цвет вкладок от имен токенов окна документа.

![Окно закрепленного документа (красная линия)](../../extensibility/ux-guidelines/media/0303-065_dockeddocumentwindowredline.png "0303 — 065_DockedDocumentWindowRedline")<br />Окно закрепленного документа (красная линия)

![Плавающее окно документа (красная линия)](../../extensibility/ux-guidelines/media/0303-066_floatingdocumentwindowredline.png "0303 — 066_FloatingDocumentWindowRedline")<br />Плавающее окно документа (красная линия)

| Использовать... | Не используйте... |
| --- | --- |
| ... в любом месте вы создаете пользовательский интерфейс, который должен соответствовать окну документа. | ...  для любого пользовательского интерфейса, который не нужно изменять автоматически, если оболочка имеет обновление темы. |

**Окно закрепленного или плавающего документа: состояние по умолчанию**

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | Зависит от типа документа |
| Передний план (текст) | Зависит от типа документа |
| Рамка | `Environment.ToolWindowBorder` |

**Закрепленная рамка окна документа с плавающей точкой: состояние по умолчанию**

![По умолчанию, перемещаемая рамка окна документа с плавающей запятой](../../extensibility/ux-guidelines/media/0303-067_framefocused.png "0303 — 067_FrameFocused")<br />По умолчанию, перемещаемая рамка окна документа с плавающей запятой

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `Environment.ToolWindowFloatingFrame` |
| Передний план (текст) | `Environment.ToolWindowFloatingFrame` |
| Передний план (глиф) | `Environment.RaftedWindowButtonActiveGlyph` |
| Рамка | `Environment.MainWindowActiveDefaultBorder` |
| Граница (глиф) | `Environment.RaftedWindowButtonActiveBorder`<br />(Значение прозрачно) |

**Нефокусическая рамка окна документа с плавающей точкой: состояние по умолчанию**

![Незакрепленная рамка окна документа по умолчанию](../../extensibility/ux-guidelines/media/0303-068_frameunfocused.png "0303 — 068_FrameUnfocused")<br />Незакрепленная рамка окна документа по умолчанию

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `Environment.ToolWindowFloatingFrameInactive` |
| Передний план (текст) | `Environment.ToolWindowFloatingFrameInactive` |
| Передний план (глиф) | `Environment.RaftedWindowButtonInactiveGlyph` |
| Рамка | `Environment.MainWindowInactiveBorder` |
| Граница (глиф) | `Environment.RaftedWindowButtonInactiveBorder`<br />(Значение прозрачно) |

**Закрепленная рамка окна документа с плавающей точкой: состояние наведения**

![Закрепленная рамка окна документа с плавающей точкой при наведении указателя](../../extensibility/ux-guidelines/media/0303-069_framefocusedhover.png "0303 — 069_FrameFocusedHover")<br />Закрепленная рамка окна документа с плавающей точкой при наведении указателя

| Элемент | Имя токена: Category.color |
| --- | --- |
| Фон (глиф) | `Environment.RaftedWindowButtonHoverActive` |
| Передний план (глиф) | `Environment.RaftedWindowButtonHoverActiveGlyph` |
| Граница (глиф) | `Environment.RaftedWindowButtonHoverActiveBorder` |

**Нефокусическая рамка окна документа с плавающей точкой: состояние наведения**

![Без фокуса, плавающая рамка окна документа при наведении указателя мыши](../../extensibility/ux-guidelines/media/0303-070_frameunfocusedhover.png "0303 — 070_FrameUnfocusedHover")<br />Без фокуса, плавающая рамка окна документа при наведении указателя мыши

| Элемент | Имя токена: Category.color |
| --- | --- |
| Фон (глиф) | `EnvironmentRaftedWindowButtonHoverInactive` |
| Передний план (глиф) | `Environment.RaftedWindowButtonHoverInactiveGlyph` |
| Граница (глиф) | `Environment.RaftedWindowButtonHoverInactiveBorder` |

**Закрепленная рамка окна документа с плавающей точкой: состояние "нажато"**

![Закрепленная рамка окна документа с плавающей точкой при нажатии клавиши](../../extensibility/ux-guidelines/media/0303-071_framefocusedpressed.png "0303 — 071_FrameFocusedPressed")<br />Закрепленная рамка окна документа с плавающей точкой при нажатии клавиши

| Элемент | Имя токена: Category.color |
| --- | --- |
| Фон (глиф) | `Environment.RaftedWindowButtonDown` |
| Передний план (глиф) | `Environment.RaftedWindowButtonDownGlyph` |
| Граница (глиф) | `Environment.RaftedWindowButtonDownBorder` |

### <a name="document-tabs"></a>Вкладки документов
Вкладки документов размещаются в канале вкладок и указывают, какие документы в настоящее время открыты, а также какой документ в настоящий момент выбран или активен. Окна инструментов также могут закрепляться в канале вкладок документов, если пользователь размещает их там. В этом случае для них используются те же цвета, что и для окон документов. Если вы создаете пользовательский интерфейс, цвета которого должны всегда соответствовать цветам окна документа (в том числе при обновлении темы или установке новых тем), то используйте ссылки на указанные ниже токены цветов.

![Вкладки документов (красная линия)](../../extensibility/ux-guidelines/media/0303-072_documenttabredline.png "0303 — 072_DocumentTabRedline")<br />Вкладки документов (красная линия)

| Использовать... | Не используйте... |
| --- | --- |
| ... в любом месте вы создаете пользовательский интерфейс, которому нужно сопоставить вкладки документов, и автоматически выберете обновления темы или новые цвета темы. | ... для любого пользовательского интерфейса, который не нужно изменять автоматически при наличии в оболочке обновления темы. |

#### <a name="open-document-tabs"></a>Вкладки открытых документов
Каждый открытый документ имеет вкладку в канале вкладок документов, на которой показано его имя. Документы могут быть либо выбраны, либо открыты в фоновом режиме. На их вкладках указываются перечисленные ниже состояния.

- Выбранная вкладка представляет документ, который в настоящее время отображается в контейнере документа. Выбранная вкладка имеет границу документа, которая располагается по верхнему краю контейнера документа.

- Вкладки «фон» — это любые вкладки документов, не выбранные в данный момент. После нажатия они становятся выбранной вкладкой и получают все цвета фона, границы и текста из этих имен токенов.

![Вкладка "открыть документ" (красная линия)](../../extensibility/ux-guidelines/media/0303-073_opendocumenttabredline.png "0303 — 073_OpenDocumentTabRedline")<br />Вкладка "открыть документ" (красная линия)

| Использовать... | Не используйте... |
| --- | --- |
| ... При создании настраиваемых вкладок документов. | ... для вкладок подготовка (Предварительная версия). |
| | ... для любого пользовательского интерфейса, который вы не хотите изменять автоматически, если оболочка имеет обновление темы. |

**Выбрана вкладка документов с заданной вкладкой**

![Выбрана вкладка документов с заданной вкладкой](../../extensibility/ux-guidelines/media/0303-074_selectedtabfocused.png "0303 — 074_SelectedTabFocused")<br />Выбрана вкладка документов с заданной вкладкой

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `Environment.FileTabSelectedGradientTop`<br />(Ограничения градиента для этого маркера не используются в пользовательском интерфейсе с темой.) |
| Передний план (текст) | `Environment.FileTabSelectedText` |
| Рамка | `Environment.FileTabSelectedBorder`<br />(Задайте тот же цвет, что и фон.) |
| Граница документа | `Environment.FileTabDocumentBorderBackground` |

**Выбранная, нефокусная вкладка документа**

![Выбранная, нефокусная вкладка документа](../../extensibility/ux-guidelines/media/0303-075_selectedtabunfocused.png "0303 — 075_SelectedTabUnfocused")<br />Выбранная, нефокусная вкладка документа

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `Environment.FileTabInactiveGradientTop`<br />(Ограничения градиента для этого маркера не используются в пользовательском интерфейсе с темой.) |
| Передний план (текст) | `Environment.FileTabInactiveText` |
| Рамка | `Environment.FileTabInactiveBorder`<br />(Задайте тот же цвет, что и фон.) |
| Граница документа | `Environment.FileTabInactiveDocumentBorderBackground` |

**Вкладка "фоновый документ": состояние по умолчанию**

![Вкладка документа в фоновом режиме по умолчанию](../../extensibility/ux-guidelines/media/0303-076_backgroundtab.png "0303 — 076_BackgroundTab")<br />Вкладка документа в фоновом режиме по умолчанию

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `Environment.FileTabBackground` |
| Передний план (текст) | `Environment.FileTabText` |
| Рамка | `Environment.FileTabBorder`<br />(Задайте тот же цвет, что и фон.) |

**Вкладка "фоновый документ": состояние наведения**

![Вкладка фонового документа при наведении указателя мыши](../../extensibility/ux-guidelines/media/0303-077_backgroundtabhover.png "0303 — 077_BackgroundTabHover")<br />Вкладка фонового документа при наведении указателя мыши

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `Environment.FileTabHotGradientTop`<br />(Ограничения градиента для этого маркера не используются в пользовательском интерфейсе с темой.) |
| Передний план (текст) | `Environment.FileTabHotText` |
| Рамка | `Environment.FileTabHotBorder`<br />(Задайте тот же цвет, что и фон.) |

#### <a name="preview-tab"></a>Вкладка предварительного просмотра
Также называется "подготовительной" вкладкой. Вкладка Предварительный просмотр отображается в правой части канала вкладки документа, когда пользователь щелкает элемент в окне инструментов обозреватель решений. Она служит для предварительного просмотра документа и дает пользователю возможность сохранять документ открытым в левой части канала вкладок документов. Одновременно может быть открыта только одна вкладка предварительного просмотра. Так же как открытые вкладки, вкладки предварительного просмотра имеют как фоновое, так и выбранное состояния и в активном состоянии могут получать фокус ввода и терять его.

![Вкладка предварительного просмотра (красная линия)](../../extensibility/ux-guidelines/media/0303-078_previewtabredline.png "0303 — 078_PreviewTabRedline")<br />Вкладка предварительного просмотра (красная линия)

| Использовать... | Не используйте... |
| --- | --- |
| ... в любом месте вы создаете предварительную версию и хотите, чтобы некоторые элементы соответствовали текущему цвету вкладки предварительного просмотра. | ... для любого типа документа или вкладки, которые не являются подготовкой (Предварительная версия). |
| | ... для любого пользовательского интерфейса, который вы не хотите изменять автоматически, если оболочка имеет обновление темы. |

**Выбранная вкладка предварительного просмотра**

![Выбранная вкладка предварительного просмотра](../../extensibility/ux-guidelines/media/0303-079_previewtabfocused.png "0303 — 079_PreviewTabFocused")<br />Выбранная вкладка предварительного просмотра

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `Environment.FileTabProvisionalSelectedActive` |
| Передний план (текст) | `Environment.FileTabProvisionalSelectedActiveForeground` |
| Рамка | `Environment.FileTabProvisionalSelectedActiveBorder`<br />(Задайте тот же цвет, что и фон.) |
| Граница документа | `Environment.FileTabProvisionalSelectedActiveBorder` |

**Не фокус, выбранная вкладка предварительного просмотра**

![Не фокус, выбранная вкладка предварительного просмотра](../../extensibility/ux-guidelines/media/0303-080_previewtabunfocused.png "0303 — 080_PreviewTabUnfocused")<br />Не фокус, выбранная вкладка предварительного просмотра

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `Environment.FileTabProvisionalSelectedInactive` |
| Передний план (текст) | `Environment.FileTabProvisionalSelectedInactiveForeground` |
| Рамка | `Environment.FileTabProvisionalSelectedInactiveBorder` |
| Граница документа | `Environment.FileTabProvisionalSelectedInactiveBorder` |

**Вкладка "предварительный просмотр фона": состояние по умолчанию**

![Вкладка предварительного просмотра фона по умолчанию](../../extensibility/ux-guidelines/media/0303-081_previewbackgroundtab.png "0303 — 081_PreviewBackgroundTab")<br />Вкладка предварительного просмотра фона по умолчанию

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `Environment.FileTabProvisionalInactive` |
| Передний план (текст) | `Environment.FileTabProvisionalInactiveForeground` |
| Рамка | `Environment.FileTabProvisionalInactiveBorder`<br />(Задайте тот же цвет, что и фон.) |

**Вкладка "предварительный просмотр фона": состояние наведения**

![Вкладка предварительного просмотра фона при наведении указателя](../../extensibility/ux-guidelines/media/0303-082_previewbackgroundtabhover.png "0303 — 082_PreviewBackgroundTabHover")<br />Вкладка предварительного просмотра фона при наведении указателя

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `Environment.FileTabProvisionalHover` |
| Передний план (текст) | `Environment.FileTabProvisionalHoverForeground` |
| Рамка | `Environment.FileTabProvisionalHoverBorder`<br />(Задайте тот же цвет, что и фон.) |

#### <a name="document-overflow-button"></a>Кнопка переполнения документа
Кнопка переполнения документа присутствует, если открыт один или несколько документов, вне зависимости от того, имеется ли в текущей конфигурации пространство по вертикали для размещения всех вкладок документов. В раскрывающемся меню Переполнение документа, которое управляется цветами [меню панели команд](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandMenus) , отображается список всех открытых документов, как видимых, так и скрытых, а глиф переполнения изменяется в зависимости от того, отображаются ли все открытые документы в канале табуляции.

![Кнопка переполнения документа (красная линия)](../../extensibility/ux-guidelines/media/0303-083_overflowredline.png "0303 — 083_OverflowRedline")<br />Кнопка переполнения документа (красная линия)

| Использовать... | Не используйте... |
| --- | --- |
| ... При создании пользовательской кнопки переполнения документа. | ... для пользовательского интерфейса, не похожего на кнопку переполнения. |
| | ... для кнопок переполнения панели команд. |

**Кнопка переполнения документа: состояние по умолчанию**

![Кнопка переполнения документа по умолчанию](../../extensibility/ux-guidelines/media/0303-084_overflow.png "0303 — 084_Overflow")<br />Кнопка переполнения документа по умолчанию

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `Environment.DocWellOverflowButtonBackground` |
| Передний план (глиф) | `Environment.DocWellOverflowButtonGlyph` |
| Рамка | Н/Д |

**Кнопка переполнения документа: состояние наведения**

![Кнопка переполнения документа при наведении указателя](../../extensibility/ux-guidelines/media/0303-085_overflowhover.png "0303 — 085_OverflowHover")<br />Кнопка переполнения документа при наведении указателя

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `Environment.DocWellOverflowButtonMouseOverBackground` |
| Передний план (глиф) | `Environment.DocWellOverflowButtonMouseOverGlyph` |
| Рамка | `Environment.DocWellOverflowButtonMouseOverBorder` |

**Кнопка переполнения документа: состояние "нажато"**

![Кнопка переполнения документа при нажатии клавиши](../../extensibility/ux-guidelines/media/0303-086_overflowpressed.png "0303 — 086_OverflowPressed")<br />Кнопка переполнения документа при нажатии клавиши

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `Environment.DocWellOverflowButtonMouseDownBackground` |
| Передний план (глиф) | `Environment.DocWellOverflowButtonMouseDownGlyph` |
| Рамка | `Environment.DocWellOverflowButtonMouseDownBorder` |

### <a name="tagging"></a>Добавление тегов
Visual Studio поддерживает добавление тегов, что позволяет пользователю объявлять доступные для поиска ключевые слова в целях отслеживания. Например, руководители проектов и разработчики могут использовать Team Foundation Server (TFS) для добавления тегов к рабочим элементам. В приведенных ниже таблицах представлены имена цветов как для самого тега, так и для глифа (значка закрытия), который появляется при наведении указателя и в некоторых состояниях.

![Добавление тегов в Visual Studio (красная линия)](../../extensibility/ux-guidelines/media/0303-176_taggingredline.png "0303 — 176_TaggingRedline")<br />Добавление тегов в Visual Studio (красная линия)

| Использовать... | Не используйте... |
| --- | --- |
| ... для пользовательского интерфейса, поддерживающего добавление тегов. | ... для любого другого типа пользовательского интерфейса. |

#### <a name="tags"></a>Теги

**Тег: состояние по умолчанию**

![Тег по умолчанию](../../extensibility/ux-guidelines/media/0303-177_tag.png "0303 — 177_Tag")<br />Тег по умолчанию

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `Tag.Background` |
| Передний план (текст) | `Tag.Background` |

**Тег: состояние наведения**

![Тег при наведении указателя мыши](../../extensibility/ux-guidelines/media/0303-178_taghover.png "0303 — 178_TagHover")<br />Тег при наведении указателя мыши

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `Tag.HoverBackground` |
| Передний план (текст) | `Tag.HoverBackgroundText` |

**Тег: состояние "нажато"**

![Нажатый тег](../../extensibility/ux-guidelines/media/0303-179_tagpressed.png "0303 — 179_TagPressed")<br />Нажатый тег

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `Tag.PressedBackground` |
| Передний план (текст) | `Tag.PressedBackgroundText` |

**Тег: выбранное состояние**

![Выбранный тег](../../extensibility/ux-guidelines/media/0303-180_tagselected.png "0303 — 180_TagSelected")<br />Выбранный тег

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `Tag.SelectedBackground` |
| Передний план (текст) | `Tag.SelectedBackgroundText` |

#### <a name="close-times-tag-glyph"></a>Закрыть ( &times; ) глиф тега

**Close ( &times; ) глиф тега: состояние по умолчанию**

![Глиф тега Close () по умолчанию &times;](../../extensibility/ux-guidelines/media/0303-181_tagglyph.png "0303 — 181_TagGlyph")<br />Глиф тега Close () по умолчанию &times;

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | Н/Д |
| Передний план (глиф) | `Tag.TagHoverGlyph` |

**Close ( &times; ) глиф тега: состояние наведения**

![Закрыть ( &times; ) глиф тега при наведении указателя](../../extensibility/ux-guidelines/media/0303-182_tagglyphhover.png "0303 — 182_TagGlyphHover")<br />Закрыть ( &times; ) глиф тега при наведении указателя

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `Tag.TagHoverGlyphHoverBackground` |
| Передний план (глиф) | `Tag.TagHoverGlyphHover` |
| Рамка | `Tag.TagHoverGlyphHoverBorder` |

**Close ( &times; ) глиф тега: нажатое состояние**

![Глиф тега Close () нажатия &times;](../../extensibility/ux-guidelines/media/0303-183_tagglyphpressed.png "0303 — 183_TagGlyphPressed")<br />Глиф тега Close () нажатия &times;

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `Tag.TagHoverGlyphPressedBackground` |
| Передний план (глиф) | `Tag.TagHoverGlyphPressed` |
| Рамка | `Tag.TagHoverGlyphPressedBorder` |

**Выбранный тег с закрывающим ( &times; ) глифом: состояние по умолчанию**

![Выбранный по умолчанию тег с закрывающим ( &times; ) глифом](../../extensibility/ux-guidelines/media/0303-184_tagselected.png "0303 — 184_TagSelected")<br />Выбранный по умолчанию тег с закрывающим ( &times; ) глифом

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | Н/Д |
| Передний план (глиф) | `Tag.TagSelectedGlyph` |

**Выбранный тег с закрывающим ( &times; ) глифом: состояние наведения**

![Выбранный тег с закрывающим ( &times; ) глифом при наведении указателя](../../extensibility/ux-guidelines/media/0303-185_tagselectedhover.png "0303 — 185_TagSelectedHover")<br />Выбранный тег с закрывающим ( &times; ) глифом при наведении указателя

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `Tag.TagSelectedGlyphHoverBackground` |
| Передний план (глиф) | `Tag.TagSelectedGlyphHover` |
| Рамка | `Tag.TagSelectedGlyphHoverBorder` |

**Выбранный тег с закрывающим ( &times; ) глифом: состояние "нажато"**

![Выбрано, нажатый тег с закрывающим ( &times; ) глифом](../../extensibility/ux-guidelines/media/0303-186_tagselectedpressed.png "0303 — 186_TagSelectedPressed")<br />Выбрано, нажатый тег с закрывающим ( &times; ) глифом

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `Tag.TagSelectedGlyphPressedBackground` |
| Передний план (глиф) | `Tag.TagSelectedGlyphPressed` |
| Рамка | `Tag.TagSelectedGlyphPressedBorder` |

## <a name="tool-windows"></a>Окна инструментов
Нет необходимости в репликации окон инструментов, так как они предоставляются средой Visual Studio. Однако может потребоваться использовать цвета, применяемые в окнах инструментов, чтобы ваш пользовательский интерфейс был согласован с этой частью среды Visual Studio.

![Окно инструментов (красная линия)](../../extensibility/ux-guidelines/media/0303-087_toolwindowredline.png "0303 — 087_ToolWindowRedline")<br />Окно инструментов (красная линия)

| Использовать... | Не используйте... |
| --- | --- |
| ... где вы создаете пользовательский интерфейс, которому нужно сопоставить окна инструментов. | ... для любого пользовательского интерфейса, который вы не хотите изменять автоматически, если оболочка имеет обновление темы. |

### <a name="tool-window-frame"></a>Рамка окна инструментов
Окна инструментов в Visual Studio используются для множества различных задач и могут иметь одно из нескольких состояний. Если окно инструментов открыто, оно может быть назначено одной из четырех сторон области документа. Окна инструментов также могут перемещаться за пределы интегрированной среды документов, что позволяет размещать их в любом месте экрана. Перемещаемые окна всегда находятся поверх интегрированной среды разработки. Наконец, окна инструментов могут закрепляться как окна документов и отображаться в виде вкладок в контейнере документа. К окнам инструментов, закрепленным как окна документов, частично применяются имена токенов окна документа.

![Рамка окна инструментов (красная линия)](../../extensibility/ux-guidelines/media/0303-088_toolwindowframeredline.png "0303 — 088_ToolWindowFrameRedline")<br />Рамка окна инструментов (красная линия)

| Использовать... | Не используйте... |
| --- | --- |
| ...  где вы создаете пользовательский интерфейс, которому нужно сопоставить окна инструментов. | ... для любого пользовательского интерфейса, который вы не хотите изменять автоматически, если оболочка имеет обновление темы. |

**Закрепленное окно инструментов**

![Закрепленное окно инструментов](../../extensibility/ux-guidelines/media/0303-089_toolwindowdocked.png "0303 — 089_ToolWindowDocked")<br />Закрепленное окно инструментов

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `Environment.ToolWindowBackground` |
| Рамка | `Environment.ToolWindowBorder` |

**Перемещаемое окно инструментов с плавающей точкой**

![Перемещаемое окно инструментов с плавающей точкой](../../extensibility/ux-guidelines/media/0303-090_toolwindowfocused.png "0303 — 090_ToolWindowFocused")<br />Перемещаемое окно инструментов с плавающей точкой

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `Environment.ToolWindowBackground` |
| Рамка | `Environment.MainWindowActiveDefaultBorder` |

**Плавающее окно инструментов без фокуса**

![Плавающее окно инструментов без фокуса](../../extensibility/ux-guidelines/media/0303-091_toolwindowunfocused.png "0303 — 091_ToolWindowUnfocused")<br />Плавающее окно инструментов без фокуса

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `Environment.ToolWindowBackground` |
| Рамка | `Environment.MainWindowInactiveBorder` |

### <a name="toolbox-like-windows"></a>Панель элементов, как и окна
Область элементов — одно из наиболее часто используемых окон инструментов в Visual Studio. По сути, это элемент управления "дерево" с особой темой и применением стилей.

![Окно, похожее на панель элементов (красная линия)](../../extensibility/ux-guidelines/media/0303-189_toolboxredline.png "0303 — 189_ToolboxRedline")<br />Окно, похожее на панель элементов (красная линия)

| Использовать... | Не используйте... |
| --- | --- |
| ... При проектировании окна инструментов, которое всегда должно быть совместимо с панелью элементов оболочки. | ... для всех, которые не похожи на пользовательский интерфейс панели элементов, или если вы не уверены, возникают ли у пользовательского интерфейса проблемы при изменении цвета панели инструментов оболочки. |

**Узлы панели элементов: состояние по умолчанию**

![Родительский узел панели элементов по умолчанию](../../extensibility/ux-guidelines/media/0303-190_toolboxparentnode.png "0303 — 190_ToolboxParentNode")<br />Родительский узел панели элементов по умолчанию

![Дочерний узел панели элементов по умолчанию](../../extensibility/ux-guidelines/media/0303-191_toolboxchildnode.png "0303 — 191_ToolboxChildNode")<br />Дочерний узел панели элементов по умолчанию

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `Environment.ToolboxContent`<br />Заголовки |
| Историческая справка | `Environment.ToolWindowBackground`<br />(Отдельные элементы или все окно, если нет доступных элементов управления) |
| Рамка | Отсутствуют |
| Передний план (глиф) | `Environment.ToolboxContent` |
| Передний план (текст) | `Environment.ToolboxContent` |

**Дочерние узлы панели элементов: состояние наведения**

![Дочерний узел панели инструментов при наведении указателя мыши](../../extensibility/ux-guidelines/media/0303-192_toolboxchildnodehover.png "0303 — 192_ToolboxChildNodeHover")<br />Дочерний узел панели инструментов при наведении указателя мыши

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `Environment.ToolboxContentMouseOver`<br />(Только для отдельных элементов) |
| Рамка | Отсутствуют |
| Передний план (текст) | `Environment.ToolboxContentMouseOver`<br />(Только для отдельных элементов) |

**Выбранные узлы панели элементов: состояние с сортировкой**

![Выделенный, выбранный родительский узел панели элементов](../../extensibility/ux-guidelines/media/0303-193_toolboxparentnodefocused.png "0303 — 193_ToolboxParentNodeFocused")<br />Выделенный, выбранный родительский узел панели элементов

![Выделенный, дочерний узел панели элементов](../../extensibility/ux-guidelines/media/0303-194_toolboxchildnodefocused.png "0303 — 194_ToolboxChildNodeFocused")<br />Выделенный, дочерний узел панели элементов

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `TreeView.SelectedItemActive`<br />Из категории [Tree view](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) |
| Рамка | `TreeView.FocusVisualBorder`<br />Из категории [Tree view](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) |
| Передний план (глиф) | `TreeView.SelectedItemActive`<br />Из категории [Tree view](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) |
| Передний план (текст) | `TreeView.SelectedItemActive`<br />Из категории [Tree view](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) |

**Выбранные узлы панели элементов: состояние без фокуса**

![Выделенный, нефокусный родительский узел панели элементов](../../extensibility/ux-guidelines/media/0303-195_toolboxparentnodeunfocused.png "0303 — 195_ToolboxParentNodeUnfocused")<br />Выделенный, нефокусный родительский узел панели элементов

![Выбранный, нефокусный дочерний узел панели элементов](../../extensibility/ux-guidelines/media/0303-196_toolboxchildnodeunfocused.png "0303 — 196_ToolboxChildNodeUnfocused")<br />Выбранный, нефокусный дочерний узел панели элементов

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `TreeView.SelectedItemInactive`<br />Из категории [Tree view](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) |
| Рамка | Отсутствуют |
| Передний план (глиф) | `TreeView.SelectedItemInactive`<br />Из категории [Tree view](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) |
| Передний план (текст) | `TreeView.SelectedItemInactive`<br />Из категории [Tree view](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) |

### <a name="tool-window-title-bar"></a>Заголовок окна инструментов
Граница заголовка окна не является истинной границей, она является толстой линией в верхней части строки заголовка. У него нет имени маркера для состояния без фокуса.

![Заголовок окна инструментов (красная линия)](../../extensibility/ux-guidelines/media/0303-092_toolwindowtitlebarredline.png "0303 — 092_ToolWindowTitleBarRedline")<br />Заголовок окна инструментов (красная линия)

| Использовать... | Не используйте... |
| --- | --- |
| ... где вы создаете пользовательский интерфейс, которому нужно сопоставить окна инструментов. | ... для любого пользовательского интерфейса, который вы не хотите изменять автоматически, если оболочка имеет обновление темы. |

**Заголовок окна с фокусом ввода**

![Заголовок окна с фокусом ввода](../../extensibility/ux-guidelines/media/0303-093_titlebarfocused.png "0303 — 093_TitleBarFocused")<br />Заголовок окна с фокусом ввода

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `Environment.TitleBarActiveGradientBegin`<br />(Ограничения градиента для этого маркера не используются в пользовательском интерфейсе с темой.) |
| Передний план (текст) | `Environment.TitleBarActiveText` |
| Рамка | `Environment.TitleBarActiveBorder`<br />(Задайте тот же цвет, что и фон.) |
| Маркер перетаскивания | `Environment.TitleBarDragHandleActive` |

**Заголовок окна без фокуса ввода**

![Панель заголовка без фокуса ввода](../../extensibility/ux-guidelines/media/0303-094_titlebarunfocused.png "0303 — 094_TitleBarUnfocused")<br />Заголовок окна без фокуса ввода

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `Environment.TitleBarInactiveGradientBegin`<br />(Ограничения градиента для этого маркера не используются в пользовательском интерфейсе с темой.) |
| Передний план (текст) | `Environment.TitleBarInactiveText` |
| Рамка | Н/Д |
| Маркер перетаскивания | `Environment.TitleBarDragHandle` |

#### <a name="tool-window-title-bar-buttons"></a>Кнопки в заголовке окна инструментов
![Кнопка заголовка окна (красная линия)](../../extensibility/ux-guidelines/media/0303-095_titlebarbuttonredline.png "0303 — 095_TitleBarButtonRedline")<br />Кнопка заголовка окна (красная линия)

| Использовать... | Не используйте... |
| --- | --- |
| ... для кнопок, которые отображаются в пользовательском интерфейсе, использующем маркеры цвета из заголовков окна инструментов. | ... для кнопок, которые отображаются в других местах. |
| | ... При любом сочетании фона или переднего плана, кроме указанного. |

**Кнопки строки заголовка с упором: состояние по умолчанию**

![Кнопки строки заголовка по умолчанию](../../extensibility/ux-guidelines/media/0303-096_titlebarbuttonfocused.png "0303 — 096_TitleBarButtonFocused")<br />Кнопки строки заголовка по умолчанию

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | Н/Д |
| Передний план (глиф) | `Environment.ToolWindowButtonActiveGlyph` |
| Рамка | Н/Д |

**Кнопки в строке заголовка без фокуса: состояние по умолчанию**

![Кнопки в заголовке окна без фокуса по умолчанию](../../extensibility/ux-guidelines/media/0303-097_titlebarbuttonunfocused.png "0303 — 097_TitleBarButtonUnfocused")<br />Кнопки в заголовке окна без фокуса по умолчанию

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | Н/Д |
| Передний план (глиф) | `Environment.ToolWindowButtonInactiveGlyph` |
| Рамка | Н/Д |

**Кнопки в строке заголовка с упором: состояние наведения**

![Кнопки в строке заголовка с наведением](../../extensibility/ux-guidelines/media/0303-098_titlebarbuttonfocusedhover.png "0303 — 098_TitleBarButtonFocusedHover")<br />Кнопки в строке заголовка с наведением

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `Environment.ToolWindowButtonHoverActive` |
| Передний план (глиф) | `Environment.ToolWindowButtonHoverActiveGlyph` |
| Рамка | `Environment.ToolWindowButtonHoverActiveBorder` |

**Кнопки в строке заголовка без фокуса: состояние наведения**

![Нефокусные кнопки в строке заголовка при наведении указателя](../../extensibility/ux-guidelines/media/0303-099_titlebarbuttonunfocusedhover.png "0303 — 099_TitleBarButtonUnfocusedHover")<br />Нефокусные кнопки в строке заголовка при наведении указателя

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `Environment.ToolWindowButtonHoverInactive` |
| Передний план (глиф) | `Environment.ToolWindowButtonHoverInactiveGlyph` |
| Рамка | `Environment.ToolWindowButtonHoverInactiveBorder` |

**Кнопки строки заголовка с упором: нажатое состояние**

![Кнопки в строке заголовка с упором на нажатие](../../extensibility/ux-guidelines/media/0303-100_titlebarbuttonfocusedpressed.png "0303 — 100_TitleBarButtonFocusedPressed")<br />Кнопки в строке заголовка с упором на нажатие

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `Environment.ToolWindowButtonDown` |
| Передний план (глиф) | `Environment.ToolWindowButtonDownActiveGlyph` |
| Рамка | `Environment.ToolWindowButtonDownBorder` |

**Кнопки в заголовке окна без фокуса: нажатое состояние**

![Кнопки в строке заголовка без фокуса при нажатии клавиши](../../extensibility/ux-guidelines/media/0303-101_titlebarbuttonunfocusedpressed.png "0303 — 101_TitleBarButtonUnfocusedPressed")<br />Кнопки в строке заголовка без фокуса при нажатии клавиши

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `Environment.ToolWindowButtonDown` |
| Передний план (глиф) | `Environment.ToolWindowButtonDownInactiveGlyph` |
| Рамка | `Environment.ToolWindowButtonDownBorder` |

### <a name="tool-window-tabs"></a>Вкладки окна инструментов
![Вкладка "окно инструментов" (красная линия)](../../extensibility/ux-guidelines/media/0303-102_toolwindowtabredline.png "0303 — 102_ToolWindowTabRedline")<br />Вкладка "окно инструментов" (красная линия)

| Использовать... | Не используйте... |
| --- | --- |
| ... где вы создаете пользовательский интерфейс, которому нужно сопоставить окна инструментов. | ... для любого пользовательского интерфейса, который вы не хотите изменять автоматически, если оболочка имеет обновление темы. |

**Выбранная вкладка окна инструментов с фокусом ввода**

![Выбранная вкладка окна инструментов с фокусом ввода](../../extensibility/ux-guidelines/media/0303-103_toolwindowtabfocused.png "0303 — 103_ToolWindowTabFocused")<br />Выбранная вкладка окна инструментов с фокусом ввода

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `Environment.ToolWindowTabSelectedTab` |
| Передний план (текст) | `Environment.ToolWindowTabSelectedActiveText` |
| Рамка | `Environment.ToolWindowTabSelectedBorder`<br />(Задайте тот же цвет, что и фон.) |

**Выбранная вкладка окна инструментов без фокуса ввода**

![Выбранная вкладка окна инструментов без фокуса ввода](../../extensibility/ux-guidelines/media/0303-104_toolwindowtabunfocused.png "0303 — 104_ToolWindowTabUnfocused")<br />Выбранная вкладка окна инструментов без фокуса ввода

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `Environment.ToolWindowTabSelectedTab` |
| Передний план (текст) | `Environment.ToolWindowTabSelectedText` |
| Рамка | `Environment.ToolWindowTabSelectedBorder`<br />(Задайте тот же цвет, что и фон.) |

**Вкладка "окно фонового инструмента": состояние по умолчанию**

![Вкладка окна фонового инструмента по умолчанию](../../extensibility/ux-guidelines/media/0303-105_toolwindowbackgroundtab.png "0303 — 105_ToolWindowBackgroundTab")<br />Вкладка окна фонового инструмента по умолчанию

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `Environment.ToolWindowTabGradientBegin`<br />`Environment.ToolWindowTabGradientEnd`<br />(Для ограничителей градиента задано то же значение цвета, что и в Visual Studio 2013.) |
| Передний план (текст) | `Environment.ToolWindowTabText` |
| Рамка | `Environment.ToolWindowTabBorder` |

**Вкладка "окно фонового инструмента": состояние наведения**

![Фоновая вкладка окна инструментов при наведении указателя](../../extensibility/ux-guidelines/media/0303-106_toolwindowbackgroundtabhover.png "0303 — 106_ToolWindowBackgroundTabHover")<br />Фоновая вкладка окна инструментов при наведении указателя

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `Environment.ToolWindowTabMouseOverBackgroundBegin`<br />`Environment.ToolWindowTabMouseOverBackgroundEnd`<br />(Для ограничителей градиента задано то же значение цвета, что и в Visual Studio 2013.) |
| Передний план (текст) | `Environment.ToolWindowTabMouseOverText` |
| Рамка | `Environment.ToolWindowTabMouseOverBorder`<br />(Задайте тот же цвет, что и фон.) |

### <a name="auto-hide-tabs"></a>Автоматически скрываемые вкладки

![Автоматически скрывать вкладки (красная линия)](../../extensibility/ux-guidelines/media/0303-107_autohideredline.png "0303 — 107_AutoHideRedline") Автоматически скрывать вкладки (красная линия)

| Использовать... | Не используйте... |
| --- | --- |
| ... в любом месте вы создаете пользовательский интерфейс, которому нужно сопоставить автоматические скрытые вкладки окна инструментов. | ... для любого пользовательского интерфейса, который вы не хотите изменять автоматически, если оболочка имеет обновление темы. |

**Автоматически скрывать вкладки: состояние по умолчанию**

![Автоматически скрываемая вкладка по умолчанию](../../extensibility/ux-guidelines/media/0303-108_autohidetab.png "0303 — 108_AutoHideTab")<br />Автоматически скрываемая вкладка по умолчанию

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `Environment.AutoHideTabBackgroundBegin`<br />(Ограничения градиента для этого маркера не используются в пользовательском интерфейсе с темой.) |
| Передний план (текст) | `Environment.AutoHideTabText` |
| Рамка | `Environment.AutoHideTabBorder` |

**Автоматически скрывать вкладки: состояние наведения**

![Вкладка автоматического скрытия при наведении курсора мыши](../../extensibility/ux-guidelines/media/0303-109_autohidetabhover.png "0303 — 109_AutoHideTabHover")<br />Вкладка автоматического скрытия при наведении курсора мыши

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `Environment.AutoHideTabMouseOverBackgroundBegin`<br />(Ограничения градиента для этого маркера не используются в пользовательском интерфейсе с темой.) |
| Передний план (текст) | `Environment.AutoHideTabMouseOverText` |
| Рамка | `Environment.AutoHideTabMouseOverBorder` |
