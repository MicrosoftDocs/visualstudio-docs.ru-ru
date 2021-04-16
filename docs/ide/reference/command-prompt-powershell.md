---
title: Оболочки командной строки и командная строка для разработчиков
description: Запускается из меню "Инструменты" > "Командная строка". Командная строка разработчика, PowerShell для разработчиков и терминал в Visual Studio позволяют вам удобнее пользоваться инструментами .NET и C++.
ms.date: 04/11/2021
ms.custom: contperf-fy21q4
helpviewer_keywords:
- Visual Studio command prompt
- command prompt, Visual Studio
- Developer Command Prompt
- Developer PowerShell
- Visual Studio terminal
ms.assetid: 94fcf524-9045-4993-bfb2-e2d8bad44219
no-loc: cmdlet
ms.openlocfilehash: 57cbc93f4b6e8cf64dd5149462788e0cde833350
ms.sourcegitcommit: 52b093e000334f53d87c6165d1418347e4f45dec
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/09/2021
ms.locfileid: "107221735"
---
# <a name="visual-studio-developer-command-prompt-and-developer-powershell"></a>Командная строка разработчика и PowerShell для разработчиков в Visual Studio

В Visual Studio 2019 есть две оболочки командной строки для разработчиков:

- **Командная строка разработчика для Visual Studio** — стандартная командная строка с определенными переменными среды, упрощающая работу с инструментами разработки. Доступно с версии Visual Studio 2015.

- **PowerShell для разработчиков Visual Studio** — более функциональное средство, чем командная строка. Например, в нем можно передать результат одной команды (называемой *cmdlet* ) в другой cmdlet. В этой оболочке доступны те же переменные среды, что и в Командной строке разработчика. Доступно с версии Visual Studio 2019.


:::image type="content" source="media/developer-command-prompt-for-vs/command-prompt.png" alt-text="Командная строка разработчика для Visual Studio с информацией об инструменте Clrver":::

Начиная с версии 16.5, в Visual Studio 2019 доступен встроенный **терминал**, где можно работать как с Командной строкой разработчика, так и с PowerShell для разработчиков. Можно открыть несколько вкладок для каждой оболочки. Терминал Visual Studio построен на основе [Терминала Windows](/windows/terminal/). Чтобы открыть терминал в Visual Studio, выберите элементы **Вид** > **Терминал**.

:::image type="content" source="media/developer-command-prompt-for-vs/vs-terminal.png" alt-text="Терминал Visual Studio с несколькими вкладками":::

При запуске в Visual Studio одной из оболочек как отдельного приложения или в окне терминала открывается каталог текущего решения (если оно загружено). Это упрощает выполнение команд для решения или его проектов.

В обеих оболочках заданы определенные переменные среды. Это упрощает работу с инструментами командной строки. Открыв эти оболочки, можно выполнять команды для различных служебных программ, не указывая их расположения. 

|Популярные команды|Описание|
|--|--|
|[`MSBuild`](../../msbuild/msbuild-command-line-reference.md)|Сборка проекта или решения|
|[`clrver`](/dotnet/framework/tools/clrver-exe-clr-version-tool)| [Инструменты .NET Framework](/dotnet/framework/tools/index) для CLR.|
|[`ildasm`](/dotnet/framework/tools/ildasm-exe-il-disassembler)|[Инструменты .NET Framework](/dotnet/framework/tools/index) для дизассемблера.|
|[`dotnet`](/dotnet/core/tools/dotnet)|[Команда CLI .NET](/dotnet/core/tools/index)|
|[`dotnet run`](/dotnet/core/tools/dotnet-run)|[Команда CLI .NET](/dotnet/core/tools/index)|
|[`CL`](/cpp/build/reference/compiler-command-line-syntax)|Средство компиляции C/C++|
|[`NMAKE`](/cpp/build/reference/running-nmake)|Средство компиляции C/C++|
|[`LIB`](/cpp/build/reference/lib-reference)| Средство сборки С/C++|
|[`DUMPBIN`](/cpp/build/reference/dumpbin-reference)| Средство сборки С/C++|


## <a name="start-in-visual-studio"></a>Запуск в Visual Studio

Выполните следующие действия, чтобы открыть в Visual Studio Командную строку разработчика или PowerShell для разработчиков:

1. Запустите Visual Studio.

1. В строке меню выберите элементы **Инструменты** > **Командная строка** > **Командная строка разработчика** или **PowerShell для разработчиков**.

   ![Пункт меню "Командная строка" в Visual Studio](./media/developer-command-prompt-for-vs/vs-menu.png)

## <a name="start-from-windows-menu"></a>Запуск из меню Windows

Другой способ запуска оболочек — из меню "Пуск". В зависимости от версии Visual Studio, дополнительно установленных пакетов SDK и рабочих нагрузок может иметься несколько вариантов командных строк. 

### <a name="windows-10"></a>Windows 10

1. Выберите **Пуск** ![клавишу с логотипом Windows на клавиатуре.](./media/developer-command-prompt-for-vs/windows-logo-key-graphic.png) и прокрутите до буквы **V**.

1. Разверните папку **Visual Studio 2019**.

1. Выберите вариант **Developer Command Prompt for VS 2019** (Командная строка разработчика для VS 2019) или **Developer PowerShell for VS 2019** (PowerShell для разработчиков для VS 2019).

   Кроме того, вы можете начать вводить имя оболочки в поле поиска на панели задач и выбрать нужный результат, так как в списке результатов начнут отображаться найденные совпадения.

   ![GIF с анимацией, показывающий поведение поиска в Windows 10](./media/developer-command-prompt-for-vs/windows-10-search.gif)

### <a name="windows-81"></a>Windows 8.1

1. Перейдите на экран **Пуск**, нажав клавишу с логотипом Windows ![Клавиша с логотипом Windows на клавиатуре.](./media/developer-command-prompt-for-vs/windows-logo-key-graphic.png) на клавиатуре, например.

1. На **начальном экране** нажмите **Ctrl**+**Tab**, чтобы открыть список **приложений**, а затем нажмите **V**. Появится список, включающий все установленные командные строки Visual Studio.

1. Выберите вариант **Developer Command Prompt for VS 2019** (Командная строка разработчика для VS 2019) или **Developer PowerShell for VS 2019** (PowerShell для разработчиков для VS 2019).

### <a name="windows-7"></a>Windows 7

1. Выберите **Пуск** а затем разверните **Все программы**.

1. Выберите элементы **Visual Studio 2019** > **Инструменты Visual Studio** > **Developer Command Prompt for VS 2019 (Командная строка разработчика для VS 2019)** или **Developer PowerShell for VS 2019 (PowerShell для разработчиков для VS 2019)** .

   ![Меню "Пуск" в Windows 7 с выделенной командной строкой](./media/developer-command-prompt-for-vs/windows-7-menu.png)

Если установлены другие пакеты SDK, например, [пакет SDK для Windows 10](https://developer.microsoft.com/windows/downloads/windows-10-sdk) или [предыдущих версий](https://developer.microsoft.com/windows/downloads/sdk-archive), могут появиться дополнительные командные строки. Требуемая версия командной строки указана в документации по соответствующим инструментам.

## <a name="start-from-file-browser"></a>Запуск из обозревателя файлов 

Обычно ярлыки для установленных оболочек помещаются в папку **меню "Пуск"** для Visual Studio, например в *%ProgramData%\Microsoft\Windows\Start Menu\Programs\Visual Studio 2019\Visual Studio Tools*. Но если поиск командной строки не дает ожидаемых результатов, попробуйте вручную найти нужные файлы на компьютере.

### <a name="developer-command-prompt"></a>Командная строка разработчика

Выполните поиск файла командной строки (*VsDevCmd.bat*) или перейдите в папку "Инструменты" Visual Studio ( *%ProgramFiles(x86)%\Microsoft Visual Studio\2019\Community\Common7\Tools* — путь зависит от версии Visual Studio, выпуска и расположения установки).

Когда вы найдете файл командной строки, откройте его. Для этого введите следующую команду в стандартном окне командной строки:

```cmd
"%ProgramFiles(x86)%\Microsoft Visual Studio\2019\Community\Common7\Tools\VsDevCmd.bat"
```

Кроме того, вы можете ввести следующую команду в диалоговом окне Windows **Выполнить**:

```cmd
%comspec% /k "C:\Program Files (x86)\Microsoft Visual Studio\2019\Community\Common7\Tools\VsDevCmd.bat"
```

> [!TIP]
> Вам необходимо изменить путь в соответствии с расположением установки Visual Studio.

### <a name="developer-powershell"></a>PowerShell для разработчиков

Найдите файл скрипта PowerShell с именем *Launch-VsDevShell.ps1* или перейдите в папку "Инструменты" Visual Studio ( *%ProgramFiles(x86)%\Microsoft Visual Studio\2019\Community\Common7\Tools*). Путь зависит от версии, выпуска и расположения установки Visual Studio. После этого выполните следующую команду в командной строке Windows PowerShell или PowerShell 6:

```powershell
& 'C:\Program Files (x86)\Microsoft Visual Studio\2019\Community\Common7\Tools\Launch-VsDevShell.ps1'
```

По умолчанию PowerShell для разработчиков запускается с конфигурацией для той версии Visual Studio, путь установки к которой указан в файле *Launch-VsDevShell.ps1*.

> [!TIP]
> Чтобы выполнить cmdlet, нужно задать [политику выполнения](/powershell/module/microsoft.powershell.core/about/about_execution_policies).

## <a name="see-also"></a>См. также

- [PowerShell для разработчиков](https://devblogs.microsoft.com/visualstudio/the-powershell-you-know-and-love-now-with-a-side-of-visual-studio/)
- [Новый терминал Visual Studio](https://devblogs.microsoft.com/visualstudio/say-hello-to-the-new-visual-studio-terminal/)
- [Терминал Windows](/windows/terminal/)
- [Инструменты .NET Framework](/dotnet/framework/tools/index)
- [Управление внешними инструментами](../managing-external-tools.md)
- [Использование набора инструментов C++ Microsoft из командной строки](/cpp/build/building-on-the-command-line)
