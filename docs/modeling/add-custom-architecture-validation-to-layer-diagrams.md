---
title: Добавление пользовательской проверки архитектуры в схемы зависимостей
description: Содержит сведения о том, как добавить пользовательскую проверку архитектуры в схемы зависимостей.
ms.date: 11/04/2016
ms.topic: how-to
titleSuffix: ''
helpviewer_keywords:
- dependency diagrams, adding custom validation
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.custom: SEO-VS-2020
ms.workload:
- multiple
ms.openlocfilehash: cc00f86bafebd14177400ffa0ee596a733e9fb28
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2021
ms.locfileid: "112384633"
---
# <a name="add-custom-architecture-validation-to-dependency-diagrams"></a>Добавление пользовательской проверки архитектуры в схемы зависимостей

В Visual Studio пользователи могут проверить исходный код в проекте по модели слоев, чтобы они могли проверить, соответствует ли исходный код зависимостям на схеме зависимостей. В программе предусмотрен стандартный алгоритм проверки, однако вы можете определять собственные расширения проверки.

Когда пользователь выбирает команду **Проверить архитектуру** на схеме зависимостей, вызывается стандартный метод проверки, за которым следуют все установленные расширения проверки.

> [!NOTE]
> В схеме зависимостей основное назначение проверки заключается в сравнении схемы с программным кодом в других частях решения.

Расширение проверки слоев можно упаковать в формат Visual Studio Integration Extension (VSIX) и предоставить его другим пользователям Visual Studio. Проверяющий элемент можно разместить в отдельном файле VSIX или объединить с другими расширениями. Код проверяющего элемента необходимо создавать в отдельном проекте Visual Studio, а не в проекте, содержащем другие расширения.

> [!WARNING]
> Создав проект проверки, скопируйте в него [пример кода](#example) , приведенный в конце этого раздела, и внесите в него изменения с учетом своих задач.

## <a name="requirements"></a>Требования

См. раздел [требования](../modeling/extend-layer-diagrams.md#requirements).

## <a name="defining-a-layer-validator-in-a-new-vsix"></a>Определение проверяющего элемента слоя в новом файле VSIX

Самый быстрый способ создать проверяющий элемент — это шаблон проекта. В этом случае код и манифест VSIX размещаются в одном и том же проекте.

### <a name="to-define-an-extension-by-using-a-project-template"></a>Определение расширения с использованием шаблона проекта

1. Создайте новый проект **расширения проверки конструктора слоев** .

    Шаблон создает проект, который содержит небольшой пример.

   > [!WARNING]
   > Чтобы шаблон работал правильно, соблюдайте следующие рекомендации:
   >
   > - Отредактируйте вызовы функции `LogValidationError` , удалив необязательные аргументы `errorSourceNodes` и `errorTargetNodes`.
   > - Если используются пользовательские свойства, примените обновление, упомянутое в статьи [Добавление пользовательских свойств в схемы зависимостей](../modeling/add-custom-properties-to-layer-diagrams.md).

2. Отредактируйте код, чтобы определить проверку. Более подробную информацию см. в разделе [Программная проверка](#programming).

3. Сведения о тестировании расширения см. в разделе [Отладка проверки слоев](#debugging).

   > [!NOTE]
   > Этот метод вызывается только в особых обстоятельствах. Точки останова не срабатывают автоматически. Более подробную информацию см. в разделе [Отладка проверки слоев](#debugging).

::: moniker range="vs-2017"

4. Чтобы установить расширение в основном экземпляре Visual Studio или на другом компьютере, найдите *VSIX* файл в каталоге *bin* . Скопируйте его на компьютер, а затем дважды щелкните его. Чтобы удалить его, выберите **расширения и обновления** в меню **Сервис** .

::: moniker-end

::: moniker range=">=vs-2019"

4. Чтобы установить расширение в основном экземпляре Visual Studio или на другом компьютере, найдите *VSIX* файл в каталоге *bin* . Скопируйте его на компьютер, а затем дважды щелкните его. Чтобы удалить его, выберите **Управление расширениями** в меню **расширения** .

::: moniker-end

## <a name="adding-a-layer-validator-to-a-separate-vsix"></a>Добавление проверяющего элемента слоя в отдельный файл VSIX

Если нужно создать один файл VSIX, который содержит проверяющие элементы слоев, команды и другие расширения, рекомендуется создать один проект для определения VSIX и отдельные проекты для обработчиков.

### <a name="to-add-layer-validation-to-a-separate-vsix"></a>Добавление проверки слоев в отдельный файл VSIX

1. Создайте проект **Библиотека классов**. Этот проект содержит класс проверки слоев.

2. Найдите или создайте **проект VSIX** в решении. Проект VSIX содержит файл с именем **source.extension.vsixmanifest**.

3. В **Обозреватель решений** в контекстном меню проекта VSIX выберите пункт **Назначить запускаемым проектом**.

4. В **source.extension.vsixmanifest** на вкладке **Активы** добавьте проект проверки слоев в качестве компонента MEF:

    1. Выберите **Создать**.

    2. В диалоговом окне **Добавить новый актив** установите следующие параметры:

         **Тип**  =  **Microsoft. VisualStudio. MefComponent**

         **Исходный код**  =  **Проект в текущем решении**

         **Проект Project**  =  *проверяющий проект*

5. Также необходимо добавить его в качестве проверки слоев:

    1. Выберите **Создать**.

    2. В диалоговом окне **Добавить новый актив** установите следующие параметры:

         **Тип**  =  **Microsoft. VisualStudio. арчитектуретулс. Layer. проверяющий элемент управления**. Это значение не указано в раскрывающемся списке. Его необходимо ввести с клавиатуры.

         **Исходный код**  =  **Проект в текущем решении**

         **Проект Project**  =  *проверяющий проект*

6. Вернитесь в проект проверки слоев и добавьте указанные ниже ссылки на проект.

    |**Ссылка**|**Возможности**|
    |-|-|
    |Microsoft.VisualStudio.GraphModel.dll|Чтение графа архитектуры|
    |Microsoft.VisualStudio.ArchitectureTools.Extensibility.CodeSchema.dll|Чтение кода DOM, связанного со слоями|
    |Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.dll|Чтение модели слоев|
    |Microsoft.VisualStudio.ArchitectureTools.Extensibility|Чтение и обновление фигур и схем|
    |System.ComponentModel.Composition|Определение компонента проверки с помощью Managed Extensibility Framework (MEF)|
    |Microsoft.VisualStudio.Modeling.Sdk.[версия]|Определение расширений моделирования|

7. Скопируйте пример кода в конце этого раздела в файл класса в проекте библиотеки проверяющего элемента, чтобы добавить в него код для проверки. Более подробную информацию см. в разделе [Программная проверка](#programming).

8. Сведения о тестировании расширения см. в разделе [Отладка проверки слоев](#debugging).

    > [!NOTE]
    > Этот метод вызывается только в особых обстоятельствах. Точки останова не срабатывают автоматически. Более подробную информацию см. в разделе [Отладка проверки слоев](#debugging).

9. Чтобы установить VSIX в основном экземпляре Visual Studio или на другом компьютере, найдите **VSIX** файл в каталоге **bin** проекта VSIX. Скопируйте его на компьютер, где требуется выполнить установку VSIX. Дважды щелкните файл VSIX в проводнике Windows

## <a name="programming-validation"></a><a name="programming"></a> Проверка программирования

Чтобы определить расширение проверки слоя, необходимо определить класс указанным ниже образом.

- Общая форма объявления должна иметь следующий вид:

  ```csharp
  using System.ComponentModel.Composition;
  using Microsoft.VisualStudio.ArchitectureTools.Extensibility.CodeSchema;
  using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer;
  using Microsoft.VisualStudio.GraphModel;
  ...
   [Export(typeof(IValidateArchitectureExtension))]
    public partial class Validator1Extension :
                    IValidateArchitectureExtension
    {
      public void ValidateArchitecture(Graph graph)
      {
         GraphSchema schema = graph.DocumentSchema;
        ...
    } }
  ```

- При обнаружении ошибки сообщите о ней с помощью функции `LogValidationError()`.

  > [!WARNING]
  > Не используйте необязательные параметры функции `LogValidationError`.

Когда пользователь вызывает команду меню **Проверить архитектуру** , система среды выполнения слоев анализирует слои и их артефакты и формирует граф. Граф состоит из четырех частей:

- Модели слоев решения Visual Studio, представленные в виде узлов и ссылок в графе.

- код, элементы проекта и другие артефакты, определенные в решении и представленные в виде узлов, а также связи, которые представляют зависимости, обнаруженные в процессе анализа;

- связи между узлами слоя и узлами артефактов кода;

- узлы, представляющие ошибки, которые были обнаружены проверяющим элементом.

После создания графа вызывается стандартный метод проверки. После этого все установленные методы проверки расширения вызываются в произвольном порядке. Граф передается каждому методу `ValidateArchitecture` , который может просканировать его и сообщить об обнаруженных ошибках.

> [!NOTE]
> Это не то же самое, что процесс проверки, который можно использовать на предметно-ориентированных языках.

Методы проверки не должны менять проверяемую модель слоев или код.

Модель графа определена в узле <xref:Microsoft.VisualStudio.GraphModel>. Основными классами этого узла являются <xref:Microsoft.VisualStudio.GraphModel.GraphNode> и <xref:Microsoft.VisualStudio.GraphModel.GraphLink>.

Каждый узел и каждая связь имеют одну или несколько категорий, задающих тип элемента или отношения, которое этот узел или связь представляет. Узлы типичного графа имеют следующие категории:

- Dsl.LayerModel

- Dsl.Layer

- Dsl.Reference

- CodeSchema_Type

- CodeSchema_Namespace

- CodeSchema_Type

- CodeSchema_Method

- CodeSchema_Field

- CodeSchema_Property

Связи от слоев к элементам в коде имеют категорию «Представляет».

## <a name="debugging-validation"></a><a name="debugging"></a> Проверка отладки

Чтобы выполнить отладку расширения проверки слоев, нажмите клавиши CTRL+F5. Откроется экспериментальный экземпляр Visual Studio. Откройте или создайте модель слоев в этом экземпляре. Эта модель должна быть связана с кодом и иметь хотя бы одну зависимость.

### <a name="test-with-a-solution-that-contains-dependencies"></a>Тестирование решения, содержащего зависимости

Проверка выполняется только при наличии указанных ниже характеристик.

- На схеме зависимостей имеется по крайней мере одна ссылка на зависимость.

- В модели имеются слои, связанные с элементами кода.

При первом запуске экспериментального экземпляра Visual Studio для тестирования расширения проверки откройте или создайте решение с этими характеристиками.

### <a name="run-clean-solution-before-validate-architecture"></a>Выполнение очистки решения перед проверкой архитектуры

Всякий раз при обновлении кода проверки необходимо использовать команду **Очистить решение** в меню **Сборка** экспериментального решения. Только после этого можно тестировать команду «Проверка». Это связано с тем, что результаты проверки кэшируются. Если вы не обновили диаграмму зависимостей теста или ее код, то методы проверки не будут выполняться.

### <a name="launch-the-debugger-explicitly"></a>Явный запуск отладчика

Проверка выполняется в отдельном процессе. Поэтому точки останова используемого метода проверки не будут активированы. Необходимо явно подключить отладчик к процессу после запуска проверки.

Чтобы подключить отладчик к процессу проверки, вставьте вызов функции `System.Diagnostics.Debugger.Launch()` в начало метода проверки. Когда откроется диалоговое окно Отладка, выберите основной экземпляр Visual Studio.

Кроме того, можно вставить вызов функции `System.Windows.Forms.MessageBox.Show()`. Когда появится окно сообщения, перейдите к основному экземпляру Visual Studio и в меню **Отладка** выберите команду **присоединить к процессу**. Выберите процесс, который называется **Graphcmd.exe**.

Всегда запускайте экспериментальный экземпляр, нажимая клавиши CTRL+F5 (**Запуск без отладки**).

### <a name="deploying-a-validation-extension"></a>Развертывание расширения проверки

Чтобы установить расширение проверки на компьютер, на котором установлена подходящая версия Visual Studio, откройте VSIX-файл на конечном компьютере.

## <a name="example-code"></a><a name="example"></a> Пример кода

```csharp
using System;
using System.ComponentModel.Composition;
using System.Globalization;
using System.Linq;
using System.Text.RegularExpressions;
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.CodeSchema;
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer;
using Microsoft.VisualStudio.GraphModel;

namespace Validator3
{
    [Export(typeof(IValidateArchitectureExtension))]
    public partial class Validator3Extension : IValidateArchitectureExtension
    {
        /// <summary>
        /// Validate the architecture
        /// </summary>
        /// <param name="graph">The graph</param>
        public void ValidateArchitecture(Graph graph)
        {
            if (graph == null) throw new ArgumentNullException("graph");

            // Uncomment the line below to debug this extension during validation
            // System.Windows.Forms.MessageBox.Show("Attach 2 to GraphCmd.exe with process id " + System.Diagnostics.Process.GetCurrentProcess().Id);

            // Get all layers on the diagram
            foreach (GraphNode layer in graph.Nodes.GetByCategory("Dsl.Layer"))
            {
                System.Threading.Thread.Sleep(100);
                // Get the required regex property from the layer node
                string regexPattern = "^[a-zA-Z]+$"; //layer[customPropertyCategory] as string;
                if (!string.IsNullOrEmpty(regexPattern))
                {
                    Regex regEx = new Regex(regexPattern);

                    // Get all referenced types in this layer including those from nested layers so each
                    // type is validated against all containing layer constraints.
                    foreach (GraphNode containedType in layer.FindDescendants().Where(node => node.HasCategory("CodeSchema_Type")))
                    {
                        // Check the type name against the required regex
                        CodeGraphNodeIdBuilder builder = new CodeGraphNodeIdBuilder(containedType.Id, graph);
                        string typeName = builder.Type.Name;
                        if (!regEx.IsMatch(typeName))
                        {
                            // Log an error
                            string message = string.Format(CultureInfo.CurrentCulture, Resources.InvalidTypeNameMessage, typeName);
                            this.LogValidationError(graph, typeName + "TypeNameError", message, GraphErrorLevel.Error, layer);
                        }
                    }
                }

            }

        }
    }
}
```

## <a name="see-also"></a>См. также

- [Расширение схем зависимостей](../modeling/extend-layer-diagrams.md)
