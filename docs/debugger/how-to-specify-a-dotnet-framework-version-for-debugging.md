---
title: Указание версии платформы .NET Framework для отладки | Документация Майкрософт
description: Указание более ранней версии платформы .NET Framework для отладки. Отладчик Visual Studio поддерживает отладку как текущей версии .NET Framework, так и более ранних версий этой платформы.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- .NET Framework, specifying version for debugging
- debugging [Visual Studio], specifying .NET Framework version
ms.assetid: 7a4893ba-4620-4774-893f-378d4ca28893
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: 83b30067530b9a48769879f3a222fee2afa725c0
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2021
ms.locfileid: "112384672"
---
# <a name="specify-an-older-net-framework-version-for-debugging-c-visual-basic-f"></a>Указание более ранней версии .NET Framework для отладки (C#, Visual Basic, F#)

Отладчик Visual Studio поддерживает отладку как текущей версии Microsoft .NET Framework, так и старых версий этой платформы. Если запускать приложение из Visual Studio, отладчик всегда может определить правильную версию платформы .NET Framework для отлаживаемого приложения. Но если приложение уже выполняется, в вы запускаете отладку с помощью команды **Присоединиться к**, отладчик не всегда может определить старую версию платформы .NET Framework. В этом случае появится сообщение об ошибке следующего содержания:

``` cmd
The debugger has made an incorrect assumption about the .NET Framework version your application is going to use.
```

В редких случаях, когда возникает эта ошибка, можно задать раздел реестра, чтобы указать отладчику, какую версию использовать.

### <a name="to-specify-a-net-framework-version-for-debugging"></a>Указание версии платформы .NET Framework для отладки

1. Перейдите в каталог "Windows\Microsoft.NET\Framework" и посмотрите, какие версии платформы .NET Framework установлены на компьютере. Номера версий выглядят примерно так:

    `V1.1.4322`

    Определите правильный номер версии и запомните или запишите его.

2. Запустите **Редактор реестра** (regedit).

3. В **редакторе реестра** откройте папку HKEY_LOCAL_MACHINE.

4. Перейдите к: HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\10.0\AD7Metrics\Engine\\{449EC4CC-30D2-4032-9256-EE18EB41B62B}

    Если раздел не существует, щелкните правой кнопкой мыши HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\10.0\AD7Metrics\Engine и выберите команду **Создать раздел**. Присвойте новому разделу имя `{449EC4CC-30D2-4032-9256-EE18EB41B62B}`.

5. После перехода к {449EC4CC-30D2-4032-9256-EE18EB41B62B}, найдите в столбце **Имя** ключ "CLRVersionForDebugging".

   1. Если раздел не существует, щелкните правой кнопкой мыши {449EC4CC-30D2-4032-9256-EE18EB41B62B} и выберите команду **Создать строковый параметр**. Щелкните правой кнопкой мыши созданное строковое значение, выберите **Переименовать** и введите `CLRVersionForDebugging`.

6. Дважды щелкните **CLRVersionForDebugging**.

7. В поле **Изменение строки** введите номер версии платформы .NET Framework в поле **Значение**. Пример: V1.1.4322

8. Нажмите кнопку **ОК**.

9. Закройте **Редактор реестра**.

     Если при запуске отладки по-прежнему возникает сообщение об ошибке, проверьте, что в реестре введен правильный номер версии. Также убедитесь, что используется поддерживаемая Visual Studio версия .NET Framework. Отладчик совместим с текущей версией платформы .NET Framework и предыдущими версиями, но может не обладать прямой совместимостью с будущими версиями.

## <a name="see-also"></a>См. также
- [Параметры отладчика и подготовка](../debugger/debugger-settings-and-preparation.md)