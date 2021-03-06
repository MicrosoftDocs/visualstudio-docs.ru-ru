---
title: Ошибки удаленной отладки и их устранение | Документация Майкрософт
description: Просмотрите ссылки на распространенные ошибки удаленной отладки в Visual Studio. Сведения о запуске удаленного отладчика от имени администратора.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- debugger, errors
- debugging errors
- remote debugging, troubleshooting
- troubleshooting remote debugging
- errors [debugger], remote debugging
- remote debugging, errors
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 5d046bfb0801229cd9f317ff2bcc8b715207ac2e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99934589"
---
# <a name="remote-debugging-errors-and-troubleshooting"></a>Ошибки удаленной отладки и их устранение

Во время удаленной отладки возможны перечисленные ниже ошибки.

- [Ошибка: не удалось автоматически перейти в режим пошагового выполнения](../debugger/error-unable-to-automatically-step-into-the-server.md)

- [Ошибка: вероятно, монитор удаленной отладки Microsoft Visual Studio (MSVSMON.EXE) не запущен на удаленном компьютере](error-remote-debugging-monitor-msvsmon-exe-does-not-appear-to-be-running.md)

- [Unable to Connect to the Microsoft Visual Studio Remote Debugging Monitor](../debugger/unable-to-connect-to-the-microsoft-visual-studio-remote-debugging-monitor.md)

- [Ошибка: удаленный компьютер не отображается в диалоговом окне удаленных подключений](../debugger/error-remote-machine-does-not-appear-in-a-remote-connections-dialog.md)

## <a name="run-the-remote-debugger-as-an-administrator"></a>Запуск удаленного отладчика в качестве администратора

Если удаленный отладчик запускается не от имени администратора, могут возникнуть проблемы. Например, возможна следующая ошибка: "У удаленного отладчика Visual Studio(MSVSMON.EXE) недостаточно привилегий для отладки этого процесса". При запуске удаленного отладчика в качестве приложения (а не службы) может возникнуть ошибка, связанная с использованием [другой учетной записи пользователя](error-the-microsoft-visual-studio-remote-debugging-monitor-on-the-remote-computer-is-running-as-a-different-user.md).

### <a name="when-running-the-remote-debugger-as-a-service"></a>Запуск удаленного отладчика как службы

При запуске удаленного отладчика в качестве службы рекомендуется запускать его от имени администратора по нескольким причинам.

- Служба удаленного отладчика допускает подключения только от администраторов, поэтому при запуске от имени администратора **не будет** дополнительных рисков безопасности.

- Могут предотвращаться ошибки, возникающие, когда у пользователя Visual Studio больше прав на отладку процесса, чем у самого удаленного отладчика.

- Это позволяет упростить установку и настройку удаленного отладчика.

Хотя вы можете выполнять отладку, не запуская удаленный отладчик от имени администратора, для этого необходимо соблюсти ряд требований, которые часто требуют дополнительных шагов по настройке службы.

- Учетная запись, используемая на удаленном компьютере, должна иметь право на **вход в качестве службы**. См. инструкции в разделе "Настройка входа в качестве службы" статьи с описанием ошибки [Не удается подключиться](error-the-visual-studio-remote-debugger-service-on-the-target-computer-cannot-connect-back-to-this-computer.md).

- Учетная запись должна иметь права на отладку целевого процесса. Чтобы получить эти права, необходимо запустить удаленный отладчик с той же учетной записью, что и отлаживаемый процесс. (Проще запустить службу от имени администратора.) 

- Учетная запись должна иметь возможность подключения к компьютеру Visual Studio по сети (то есть проверки подлинности на этом компьютере). В домене выполнить подключение проще, если удаленный отладчик выполняется со встроенной учетной записью локальной системы или сетевой службы либо с учетной записью домена. Встроенные учетные записи имеют повышенные права безопасности, из-за чего могут возникать риски для безопасности.

### <a name="when-running-the-remote-debugger-as-an-application-normal-mode"></a>Запуск удаленного отладчика как приложения (обычный режим)

При попытке присоединиться к собственному процессу без повышенных привилегий (например, к обычному приложению) не имеет значения, выполняется ли удаленный отладчик от имени администратора или нет.

Удаленный отладчик желательно запускать от имени администратора в нескольких сценариях:

- Необходимо присоединиться к процессу, запущенному от имени другого пользователя (например, при отладке IIS).

- Вы пытаетесь запустить другой процесс от имени администратора.

Если вы хотите запустить другой процесс **не** от имени администратора, запускать отладчик от имени администратора **не** требуется.

## <a name="see-also"></a>См. также
- [Remote Debugging](../debugger/remote-debugging.md)