---
title: Создание визуализатора на Visual Basic | Документация Майкрософт
description: Пошаговое руководство по созданию простого визуализатора на Visual Basic. Вы также создадите тестовое окружение для тестирования визуализатора.
ms.custom: SEO-VS-2020
ms.date: 05/27/2020
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- visualizers, writing
- walkthroughs [Visual Studio], visualizers
ms.assetid: c93bf5a1-3e5e-422f-894e-bd72c9bc1b57
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: b1a4fc7d6f33d1bdfd469ec352674b08dd2495e6
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2021
ms.locfileid: "112385010"
---
# <a name="walkthrough-writing-a-visualizer-in-visual-basic"></a>Пошаговое руководство. Написание визуализатора на Visual Basic

В данном пошаговом руководстве демонстрируется создание простого визуализатора с помощью [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]. Визуализатор, который будет создан в данном пошаговом руководстве, отображает содержимое строки с помощью окна сообщения Windows Forms. Этот строковый визуализатор – простой пример, на основе которого можно создавать визуализаторы для других типов данных, более подходящих для ваших проектов.

> [!NOTE]
> Отображаемые диалоговые окна и команды меню могут отличаться от описанных в справке в зависимости от действующих параметров или выпуска среды. Чтобы изменить параметры, в меню **Сервис** выберите команду **Импорт и экспорт**. Дополнительные сведения см. в разделе [Сброс параметров](../ide/environment-settings.md#reset-settings).

Код визуализатора должен быть помещен в библиотеку DLL, которая будет использоваться отладчиком. Первым шагом является создание проекта библиотеки классов для библиотеки DLL.

## <a name="create-and-prepare-a-class-library-project"></a>Создание и подготовка проекта библиотеки классов

### <a name="to-create-a-class-library-project"></a>Создание проекта библиотеки классов

1. Создайте новый проект библиотеки классов.

    ::: moniker range=">=vs-2019"
    Нажмите клавишу **ESC**, чтобы закрыть окно запуска. Нажмите **CTRL + Q**, чтобы открыть поле поиска, введите **visual basic**, выберите **Шаблоны** и затем **Create new Class Library (.NET Framework)** (Создание библиотеки классов — .NET Framework). В появившемся диалоговом окне выберите **Создать**.
    ::: moniker-end
    ::: moniker range="vs-2017"
    В верхней строке меню последовательно выберите **Файл**  > **Создать**  > **Проект**. В левой области диалогового окна **Новый проект** в разделе **Visual Basic** выберите **.NET Standard**, а затем в средней области выберите **Библиотека классов (.NET Standard)** .
    ::: moniker-end

2. Введите соответствующее имя для библиотеки класса, например `MyFirstVisualizer`, а затем нажмите **Создать** или **ОК**.

   После создания библиотеки классов необходимо добавить ссылку на библиотеку Microsoft.VisualStudio.DebuggerVisualizers.DLL, чтобы иметь возможность использовать определенные там классы. Но сначала следует присвоить проекту понятное имя.

### <a name="to-rename-class1vb-and-add-microsoftvisualstudiodebuggervisualizers"></a>Переименование Class1.vb и добавление Microsoft.VisualStudio.DebuggerVisualizers

1. В **обозревателе решений** щелкните правой кнопкой мыши на **Class1.vb** и в контекстном меню выберите команду **Переименовать**.

2. Измените имя с Class1.vb на что-нибудь более осмысленное, например DebuggerSide.vb.

   > [!NOTE]
   > [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] автоматически изменит объявление класса в DebuggerSide.vb в соответствии с новым именем файла.

3. В **обозревателе решений** щелкните правой кнопкой мыши **My First Visualizer** и в контекстном меню выберите команду **Добавить ссылку**.

4. В диалоговом окне **Добавление ссылки** на вкладке **Обзор** выберите **Обзор** и найдите Microsoft.VisualStudio.DebuggerVisualizers.DLL.

    Библиотеку DLL можно найти в подкаталоге *\<Visual Studio Install Directory>\Common7\IDE\PublicAssemblies* в каталоге установки Visual Studio.

5. Нажмите кнопку **ОК**.

6. В файле DebuggerSide.vb добавьте следующий оператор к операторам импорта `Imports`:

   ```vb
   Imports Microsoft.VisualStudio.DebuggerVisualizers
   ```

## <a name="add-the-debugger-side-code"></a>Добавление кода для отладчика
 Теперь можно приступить к написанию кода для отладчика. Этот код запускается отладчиком для отображения информации, которую требуется визуализировать. Во-первых, необходимо изменить объявление объекта `DebuggerSide` таким образом, чтобы он наследовал базовый класс `DialogDebuggerVisualizer`.

### <a name="to-inherit-from-dialogdebuggervisualizer"></a>Наследование от DialogDebuggerVisualizer

1. В файле DebuggerSide.vb перейдите к следующей строке:

   ```vb
   Public Class DebuggerSide
   ```

2. Измените код следующим образом:

   ```vb
   Public Class DebuggerSide
   Inherits DialogDebuggerVisualizer
   ```

   `DialogDebuggerVisualizer` имеет один абстрактный метод `Show`, который необходимо переопределить.

### <a name="to-override-the-dialogdebuggervisualizershow-method"></a>Переопределение метода DialogDebuggerVisualizer.Show

- Добавьте следующий метод в класс `public class DebuggerSide`:

  ```vb
  Protected Overrides Sub Show(ByVal windowService As Microsoft.VisualStudio.DebuggerVisualizers.IDialogVisualizerService, ByVal objectProvider As Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider)

      End Sub
  ```

  Код метода `Show` отвечает за создание диалогового окна визуализатора или другого пользовательского интерфейса, а также за отображение информации, которая была передана визуализатору из отладчика. Необходимо вручную добавить код, который создает диалоговое окно и отображает информацию. В данном пошаговом руководстве для этого используется окно сообщения Windows Forms. Во-первых, необходимо добавить ссылку и оператор `Imports` для импорта пространства имен <xref:System.Windows.Forms>.

### <a name="to-add-systemwindowsforms"></a>Добавление пространства имен System.Windows.Forms

1. В **обозревателе решений** щелкните правой кнопкой мыши **Ссылки** и выберите команду **Добавить ссылку** в контекстном меню.

2. В диалоговом окне **Добавление ссылки** на вкладке **Обзор** выберите **Обзор** и найдите файл System.Windows.Forms.DLL.

    Библиотеку DLL можно найти в *C:\Windows\Microsoft.NET\Framework\v4.0.30319*.

3. Нажмите кнопку **ОК**.

4. В файле DebuggerSide.cs добавьте следующий оператор к операторам `Imports`:

    ```vb
    Imports System.Windows.Forms
    ```

## <a name="create-your-visualizers-user-interface"></a>Создание пользовательского интерфейса визуализатора
 Сейчас необходимо добавить код для создания и отображения пользовательского интерфейса визуализатора. Поскольку это всего лишь пример, мы ограничимся написанием простого пользовательского интерфейса с использованием стандартного окна сообщений.

### <a name="to-show-the-visualizer-output-in-a-dialog-box"></a>Вывод данных визуализатора в диалоговом окне

1. Добавьте следующую строку кода в метод `Show`:

    ```vb
    MessageBox.Show(objectProvider.GetObject().ToString())
    ```

     В этом примере отсутствует код для обработки ошибок. В реальном визуализаторе, как и в приложении любого другого типа, код обработки ошибок должен присутствовать.

2. В меню **Сборка** выберите команду **Построить MyFirstVisualizer**. Построение проекта должно пройти без ошибок. Если при построении все же возникнут ошибки, исправьте их, прежде чем продолжить.

## <a name="add-the-necessary-attribute"></a>Добавление необходимого атрибута
 Код для отладчика написан. Тем не менее, необходимо выполнить еще одно действие: добавить атрибут, который сообщает отлаживаемому объекту, какой набор классов формирует визуализатор.

### <a name="to-add-the-type-to-visualize-for-the-debuggee-side-code"></a>Добавление типа для визуализации кода на стороне отлаживаемого объекта

В коде на стороне отладчика тип для визуализации (источник объекта) для отлаживаемого кода указывается с помощью атрибута <xref:System.Diagnostics.DebuggerVisualizerAttribute>. Свойство `Target` задает тип для визуализации.

1. Добавьте следующий код атрибута в файл DebuggerSide.vb, после операторов `Imports`, но перед `namespace MyFirstVisualizer`:

    ```vb
    <Assembly: System.Diagnostics.DebuggerVisualizer(GetType(MyFirstVisualizer.DebuggerSide), GetType(VisualizerObjectSource), Target:=GetType(System.String), Description:="My First Visualizer")>
    ```

2. В меню **Сборка** выберите команду **Построить MyFirstVisualizer**. Построение проекта должно пройти без ошибок. Если при построении все же возникнут ошибки, исправьте их, прежде чем продолжить.

## <a name="create-a-test-harness"></a>Создание тестового окружения
 На этом написание вашего первого визуализатора окончено. Если вы правильно следовали описанной выше процедуре, можно построить визуализатор и установить его в [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Однако перед установкой визуализатора в [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] следует проверить, что он работает правильно. Для этого следует создать тестовое окружение, в котором визуализатор будет запускаться без установки в [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].

### <a name="to-add-a-test-method-to-show-the-visualizer"></a>Добавление тестового метода для демонстрации визуализатора

1. Добавьте следующий метод в класс `public DebuggerSide`:

   ```vb
   Shared Public Sub TestShowVisualizer(ByVal objectToVisualize As Object)
       Dim visualizerHost As New VisualizerDevelopmentHost(objectToVisualize, GetType(DebuggerSide))
   visualizerHost.ShowVisualizer()
   End Sub
   ```

2. В меню **Сборка** выберите команду **Построить MyFirstVisualizer**. Построение проекта должно пройти без ошибок. Если при построении все же возникнут ошибки, исправьте их, прежде чем продолжить.

   Далее необходимо создать проект исполняемого файла, из которого будет вызваться библиотека DLL визуализатора. Для простоты выберите проект консольного приложения.

### <a name="to-add-a-console-application-project-to-the-solution"></a>Добавление проекта консольного приложения в решение

1. В обозревателе решений щелкните правой кнопкой мыши решение, выберите пункт **Добавить**, а затем щелкните **Новый проект**.

    ::: moniker range=">=vs-2019"
    В поле поиска, введите **visual basic**, выберите **Шаблоны** и затем **Create new Console App (.NET Framework)** (Создание консольного приложения — .NET Framework). В появившемся диалоговом окне выберите **Создать**.
    ::: moniker-end
    ::: moniker range="vs-2017"
    В верхней строке меню последовательно выберите **Файл**  > **Создать**  > **Проект**. В левой области диалогового окна **Новый проект** в разделе **Visual Basic** выберите **Рабочий стол Windows**, а затем в средней области выберите **Консольное приложение (.NET Framework)** .
    ::: moniker-end

2. Введите соответствующее имя для библиотеки класса, например `MyTestConsole`, а затем нажмите **Создать** или **ОК**.

   Теперь необходимо добавить необходимые ссылки, чтобы программа MyTestConsole могла вызывать MyFirstVisualizer.

### <a name="to-add-necessary-references-to-mytestconsole"></a>Добавление необходимых ссылок в MyTestConsole

1. В **обозревателе решений** щелкните правой кнопкой мыши **MyTestConsole** и выберите команду **Добавить ссылку** в контекстном меню.

2. На вкладке **Обзор** диалогового окна **Добавить ссылку** выберите Microsoft.VisualStudio.DebuggerVisualizers.

3. Нажмите кнопку **ОК**.

4. Щелкните правой кнопкой мыши **MyTestConsole**, после чего щелкните **Добавить ссылку** еще раз.

5. В диалоговом окне **Добавить ссылку** перейдите на вкладку **Проекты** и выберите MyFirstVisualizer.

6. Нажмите кнопку **ОК**.

## <a name="finish-your-test-harness-and-test-your-visualizer"></a>Доводка тестового окружения и тестирование визуализатора
 Теперь нужно добавить код, которым завершится создание тестового окружения.

### <a name="to-add-code-to-mytestconsole"></a>Добавление кода в MyTestConsole

1. В **обозревателе решений** щелкните правой кнопкой мыши **Program.vb** и выберите в контекстном меню команду **Переименовать**.

2. Измените имя Module1.vb на какое-нибудь более подходящее, например **TestConsole.vb**.

    Обратите внимание на то, что [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] автоматически изменяет объявление класса в TestConsole.vb в соответствии с новым именем файла.

3. В консоли TestConsole. vb, добавьте следующий оператор `Imports`:

   ```vb
   Imports MyFirstVisualizer
   ```

4. В метод `Main` добавьте следующий код:

   ```vb
   Dim myString As String = "Hello, World"
   DebuggerSide.TestShowVisualizer(myString)
   ```

   Теперь все готово для проверки примера визуализатора.

### <a name="to-test-the-visualizer"></a>Тестирование визуализатора

1. В **обозревателе решений** щелкните правой кнопкой мыши **MyTestConsole** и выберите в контекстном меню команду **Сделать запускаемым проектом**.

2. В меню **Отладка** выберите команду **Запуск**.

    Будет запущено консольное приложение. Появится окно визуализатора, в котором будет выведена строка "Hello, World".

   Поздравляем! Вы только что создали и протестировали ваш первый визуализатор.

   Если вам удобнее вызывать визуализатор из [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], а не из специально подготовленной тестовой программы, визуализатор необходимо установить. Дополнительные сведения см. в разделе [Практическое руководство. установить визуализатор](../debugger/how-to-install-a-visualizer.md).

## <a name="see-also"></a>См. также

- [Архитектура визуализатора](../debugger/visualizer-architecture.md)
- [Практическое руководство. Установка визуализатора](../debugger/how-to-install-a-visualizer.md)
- [Создание настраиваемых визуализаторов](../debugger/create-custom-visualizers-of-data.md)