---
description: Отладчику Visual Studio не удается подключиться к удаленному компьютеру.
title: RPC требуется проверка подлинности | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: error-reference
f1_keywords:
- vs.debug.error.rpc_requires_authentication
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: f22998bc1c71a242b985739b2b92ba9743535d83
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102146721"
---
# <a name="error-rpc-requires-authentication"></a>Ошибка: RPC требуется проверка подлинности
Отладчику Visual Studio не удается подключиться к удаленному компьютеру. На локальном компьютере включена политика RPC, запрещающая удаленную отладку.

### <a name="to-correct-this-error"></a>Исправление ошибки

1. Запустите `\`*windir*`\system32\regedt32.exe`.

2. Найдите и удалите `HKEY_LOCAL_MACHINE\Software\Policies\Microsoft\Windows NT\RPC\RestrictRemoteClients`.

3. Перезагрузите компьютер, чтобы изменения в реестре вступили в силу.

4. При повторении ошибки обратитесь к администратору домена по поводу настройки групповой политики **Конфигурация компьютера > Административные шаблоны > Система > Удаленный вызов процедур (RPC) > Ограничения для не прошедших проверку подлинности RPC-клиентов**.
