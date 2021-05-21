---
title: Отладка с помощью JIT-отладчика | Документация Майкрософт
description: Отладка с помощью JIT-отладчика в Visual Studio. JIT-отладка автоматически запускает Visual Studio при возникновении ошибок или сбоев в приложении.
ms.custom: SEO-VS-2020
ms.date: 09/24/2018
ms.topic: how-to
helpviewer_keywords:
- debugging [Visual Studio], Just-In-Time
- Just-In-Time debugging
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 3bdd35056706491ace6e5e6b2f7c3f6a45464d2e
ms.sourcegitcommit: a0f5e7188838c5989c9cc78d99fb29bb2813501e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/11/2021
ms.locfileid: "109729251"
---
# <a name="debug-using-the-just-in-time-debugger-in-visual-studio"></a>Отладка с помощью JIT-отладчика в Visual Studio

JIT-отладка автоматически запускает Visual Studio при возникновении ошибок или сбоев в приложении, запущенном вне Visual Studio. С помощью JIT-отладки можно тестировать приложения за пределами Visual Studio и открыть Visual Studio, чтобы начать отладку в случае проблемы.

JIT-отладка работает для классических приложений Windows. Она не работает для универсальных приложений Windows или управляемого кода, размещенного в приложении машинного кода, например для визуализаторов.

> [!TIP]
> Если вы просто хотите запретить отображение диалогового окна JIT-отладчика, но у вас не установлена Visual Studio, см. раздел [Отключение JIT-отладчика](../debugger/just-in-time-debugging-in-visual-studio.md). Если набор средств Visual Studio был ранее установлен, но теперь его нет, придется [отключить JIT-отладку через реестр Windows](#disable-just-in-time-debugging-from-the-windows-registry).

## <a name="enable-or-disable-just-in-time-debugging-in-visual-studio"></a><a name="BKMK_Enabling"></a> Включение или отключение JIT-отладки в Visual Studio

>[!NOTE]
>Чтобы включить или отключить JIT-отладку, необходимо запустить Visual Studio от имени администратора. Включение или отключение JIT-отладки устанавливает раздел реестра. Для его изменения требуются права администратора. Откройте Visual Studio с правами администратора, щелкнув приложение Visual Studio правой кнопкой мыши и выбрав **Запуск от имени администратора**.

JIT-отладку можно настроить в диалоговом окне Visual Studio **Сервис** > **Параметры** (или **Отладка** > **Параметры**).

**Включение или отключение JIT–отладки**

1. В меню **Сервис** или **Отладка** выберите **Параметры** > **Отладка** > **JIT**.

   ![Включение или отключение JIT-отладки](../debugger/media/dbg-jit-enable-or-disable.png "Включение или отключение JIT-отладки")

1. В поле **Включить JIT-отладку для этих типов кода** выберите типы кода, которым требуется JIT-отладка: **Управляемый**, **Собственный** и (или) **Скрипт**.

1. Нажмите кнопку **ОК**.

Если вы включили JIT-отладчик, но он не открывается при сбоях или ошибках приложения, см. раздел [Устранение неполадок с JIT-отладкой](#jit_errors).

## <a name="disable-just-in-time-debugging-from-the-windows-registry"></a>Отключение JIT-отладки из реестра Windows

JIT-отладка может оставаться включенной даже после удаления Visual Studio с компьютера. Если Visual Studio больше не установлена, JIT-отладку можно отключить, отредактировав реестр Windows.

**Отключение JIT-отладки путем редактирования реестра**

1. В меню Windows **Пуск** запустите **редактор реестра** (*regedit.exe*).

2. В окне **Редактор реестра** найдите и удалите следующие записи реестра.

    - **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework\DbgManagedDebugger**

    - **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\AeDebug\Debugger**

    ![Раздел реестра JIT](../debugger/media/dbg-jit-registry.png "Раздел реестра JIT")

3. Если на компьютере установлена 64-разрядная операционная система, также удалите следующие записи реестра.

    - **HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\\.NETFramework\DbgManagedDebugger**

    - **HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Windows NT\CurrentVersion\AeDebug\Debugger**

    Будьте внимательны, чтобы не удалить или не изменить другие разделы реестра.

5. Закройте окно **Редактор реестра**.

## <a name="enable-just-in-time-debugging-of-a-windows-form"></a>Включение JIT-отладки для приложений Windows Forms

По умолчанию в приложениях Windows Forms есть обработчик исключений верхнего уровня, который позволяет приложению продолжить работу, если оно может быть восстановлено. Если приложение Windows Forms выдает необработанное исключение, отображается следующее диалоговое окно:

![Необработанное исключение Windows Forms](../debugger/media/windowsformsunhandledexception.png "Необработанное исключение Windows Forms")

Чтобы включить JIT-отладку вместо стандартной обработки ошибок Windows Forms, добавьте следующие параметры.

- В разделе `system.windows.forms` файла *machine.config* или *\<app name>.exe.config* установите для параметра `jitDebugging` значение `true`:

    ```xml
    <configuration>
        <system.windows.forms jitDebugging="true" />
    </configuration>
    ```

- Для приложений Windows Forms, написанных на языке C++, в файле *CONFIG* или коде также задайте для параметра `DebuggableAttribute` значение `true`. Если компиляция выполняется с атрибутом [/Zi](/cpp/build/reference/z7-zi-zi-debug-information-format), но без [/Og](/cpp/build/reference/og-global-optimizations), компилятор автоматически задаст этот атрибут. Однако если требуется выполнить отладку неоптимизированной сборки выпуска, то необходимо задать `DebuggableAttribute`, добавив следующую строку в файл *AssemblyInfo.cpp* приложения:

   ```cpp
   [assembly:System::Diagnostics::DebuggableAttribute(true, true)];
   ```

   Для получения дополнительной информации см. <xref:System.Diagnostics.DebuggableAttribute>.

## <a name="use-just-in-time-debugging"></a><a name="BKMK_Using_JIT"></a>Использование JIT-отладки
В этом примере рассматривается JIT-отладка, когда приложение выдает ошибку.

- Для выполнения инструкций необходимо установить Visual Studio. Если у вас нет Visual Studio, вы можете скачать бесплатный выпуск [Visual Studio Community](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=Community&rel=15).

- Убедитесь, что JIT-отладка [включена](#BKMK_Enabling) в разделе **Сервис** > **Параметры** > **Отладка** > **JIT**.

В этом примере вы создадите консольное приложение C# в Visual Studio, которое создает исключение [NullReferenceException](/dotnet/api/system.nullreferenceexception).

1. В Visual Studio создайте консольное приложение C# (**Файл** > **Создать** > **Проект** > **Visual C#**  > **Консольное приложение**) с именем *ThrowsNullException*. Сведения о создании проектов в Visual Studio см. в разделе [Пошаговое руководство. Создание простого приложения](../get-started/csharp/tutorial-wpf.md).

1. Когда проект откроется в Visual Studio, откройте файл *Program.cs*. Замените метод Main() следующим кодом, который выводит строку на консоль, а затем создает исключение NullReferenceException:

   ```csharp
   static void Main(string[] args)
   {
       Console.WriteLine("we will now throw a NullReferenceException");
       throw new NullReferenceException("this is the exception thrown by the console app");
   }
   ```

1. Чтобы выполнить сборку решения, выберите конфигурацию **Отладка** (по умолчанию) или **Выпуск**, а затем нажмите **Сборка** > **Перестроить решение**.

   > [!NOTE]
   > - Выберите конфигурацию **Отладка** для полной отладки.
   > - Если выбрана конфигурация [Выпуск](../debugger/how-to-set-debug-and-release-configurations.md), необходимо отключить функцию [Только мой код](../debugger/just-my-code.md). В разделе **Сервис** > **Параметры** > **Отладка** снимите флажок **Включить только мой код**.

   Дополнительные сведения о конфигурациях сборки см. в разделе [Общие сведения о конфигурациях сборки](../ide/understanding-build-configurations.md).

1. Откройте созданное приложение *ThrowsNullException.exe* в папке проекта C# ( *...\ThrowsNullException\ThrowsNullException\bin\Debug* или *...\ThrowsNullException\ThrowsNullException\bin\Release*).

   Вы увидите следующее окно команд:

   ![Снимок экрана: консоль для ThrowsNullException.exe, которая вызывает необработанное исключение, связанное с пустой ссылкой (System.NullReferenceException).](../debugger/media/throwsnullexceptionconsole.png)

1. Откроется диалоговое окно **Выбор JIT-отладчика**.

   ![Снимок экрана: диалоговое окно "Выберите JIT-отладчик", которое появляется сразу же после отображения исключения в окне консоли ThrowsNullException.exe.](../debugger/media/justintimedialog.png)

   В разделе **Доступные отладчики** выберите параметр **Новый экземпляр \<your preferred Visual Studio version/edition>** , если он еще не выбран.

1. Нажмите кнопку **ОК**.

   Проект ThrowsNullException открывается в новом экземпляре Visual Studio, а выполнение остановлено в строке, вызвавшей исключение:

   ![Снимок экрана: проект ThrowsNullException в Visual Studio с выделенной строкой исходного кода, которая вызвала исключение.](../debugger/media/nullreferencesecondinstance.png)

Теперь можно начать отладку. При отладке реального приложения необходимо выяснить, почему код создает исключение.

> [!CAUTION]
> Если приложение содержит ненадежный код, появляется диалоговое окно предупреждения системы безопасности, позволяющее решить, следует ли продолжить отладку. Перед продолжением отладки решите, доверяете ли вы данному коду. Этот код написан вами самостоятельно? Если приложение выполняется на удаленном компьютере, узнаете ли вы имя процесса? Если приложение выполняется локально, учитывайте возможность выполнения такого вредоносного кода на вашем компьютере. Если вы решили, что код заслуживает доверия, нажмите **ОК**. В противном случае нажмите кнопку **Отмена**.

## <a name="troubleshoot-just-in-time-debugging"></a><a name="jit_errors"></a> Устранение неполадок с JIT-отладкой

Если JIT-отладка не запускается при сбое приложения, даже если она включена в Visual Studio:

- Отчеты об ошибках Windows могут взять на себя обработку ошибок на компьютере.

  Чтобы устранить эту проблему, используйте редактор реестра, чтобы добавить **значение DWORD** **Отключено** с параметром **Данные значения**, равным **1**, для следующих разделов реестра:

  - **HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\Windows Error Reporting**

  - (Для 64-разрядных компьютеров): **HKEY_LOCAL_MACHINE\Software\WOW6432Node\Microsoft\Windows\Windows Error Reporting**

  Дополнительные сведения см. в разделе [Параметры .WER](/windows/desktop/wer/wer-settings).

- Известная проблема Windows может привести к сбою JIT-отладчика.

  Исправление состоит в том, чтобы добавить **значение DWORD** из раздела **Видимые** с параметром **Значение данных**, равным **1**, в следующие разделы реестра.

  - **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\AeDebug**

  - (Для 64-разрядных компьютеров): **HKEY_LOCAL_MACHINE\Software\WOW6432Node\Microsoft\Windows NT\CurrentVersion\AeDebug**

Во время JIT-отладки могут отображаться следующие сообщения об ошибках.

- **Не удалось подключиться к аварийному процессу. Указанная программа не является программой Windows или MS–DOS.**

    Отладчик попытался подключиться к процессу, выполняющемуся под именем другого пользователя.

    Чтобы обойти эту проблему, запустите Visual Studio, откройте диалоговое окно **Отладка** > **Присоединение к процессу** (или нажмите сочетание клавиш **CTRL** + **ALT** + **P**) и найдите процесс, для которого требуется выполнить отладку, в списке **Доступные процессы**. Если имя процесса неизвестно, найдите идентификатор процесса в диалоговом окне **JIT-отладчик Visual Studio**. Выберите процесс в списке **Доступные процессы** и щелкните **Присоединить**. Выберите **Нет**, чтобы закрыть диалоговое окно JIT-отладчика.

- **Не удалось запустить отладчик, так как пользователь не вошел в систему.**

    В консоли нет пользователей, выполнивших вход, а также отсутствует сеанс пользователя, в котором следовало бы отображать диалоговое окно JIT-отладки.

    Для решения этой проблемы необходимо войти в компьютер.

- **Класс не зарегистрирован.**

    Отладчик пытался создать класс COM, который не зарегистрирован, вероятно, из-за проблем с установкой.

    Чтобы решить эту проблему, используйте Visual Studio Installer для переустановки или исправления установки Visual Studio.

## <a name="see-also"></a>См. также

- [Безопасность отладчика](../debugger/debugger-security.md)
- [Первое знакомство с отладчиком](../debugger/debugger-feature-tour.md)
- ["Параметры", "Отладка", диалоговое окно "JIT-отладка"](../debugger/just-in-time-debugging-options-dialog-box.md)
- [Предупреждение системы безопасности. Подключение к процессу, который принадлежит пользователю, не являющемуся доверенным, может быть опасным. Если следующие сведения не вызывают доверия, то не следует присоединяться к процессу](../debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user.md)
