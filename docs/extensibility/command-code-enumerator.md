---
title: Перечислитель кода команды | Документация Майкрософт
description: Перечислитель кода команды используется в параметрах SccGetCommandOptions и Сккпопулателистто для указания команды, для которой указаны параметры.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- command code enumerator
- source control plug-ins, command code enumeration
ms.assetid: 5d2c360c-59e4-4da8-bcb4-dd07c7441e40
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: b97d5083c4f262ae2d86aeef5ee2627fdc854bcb
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/25/2021
ms.locfileid: "112901387"
---
# <a name="command-code-enumerator"></a>Перечислитель кода команды
Этот перечислитель используется в параметрах [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md) и [сккпопулателист](../extensibility/sccpopulatelist-function.md)для указания команды, для которой указаны параметры.

## <a name="syntax"></a>Синтаксис

```
enum SCCCOMMAND {
   SCC_COMMAND_GET,
   SCC_COMMAND_CHECKOUT,
   SCC_COMMAND_CHECKIN,
   SCC_COMMAND_UNCHECKOUT,
   SCC_COMMAND_ADD,
   SCC_COMMAND_REMOVE,
   SCC_COMMAND_DIFF,
   SCC_COMMAND_HISTORY,
   SCC_COMMAND_RENAME,
   SCC_COMMAND_PROPERTIES,
   SCC_COMMAND_OPTIONS
};
```

## <a name="members"></a>Участники
SCC_COMMAND_GET соответствует [сккжет](../extensibility/sccget-function.md).

SCC_COMMAND_CHECKOUT соответствует [сккчеккаут](../extensibility/scccheckout-function.md).

SCC_COMMAND_CHECKIN соответствует [сккчеккин](../extensibility/scccheckin-function.md).

SCC_COMMAND_UNCHECKOUT соответствует [сккунчеккаут](../extensibility/sccuncheckout-function.md).

SCC_COMMAND_ADD соответствует [сккадд](../extensibility/sccadd-function.md).

SCC_COMMAND_REMOVE соответствует [сккремове](../extensibility/sccremove-function.md).

SCC_COMMAND_DIFF соответствует [сккдифф](../extensibility/sccdiff-function.md).

SCC_COMMAND_HISTORY соответствует [скчистори](../extensibility/scchistory-function.md).

SCC_COMMAND_RENAME соответствует [сккренаме](../extensibility/sccrename-function.md).

SCC_COMMAND_PROPERTIES соответствует [сккпропертиес](../extensibility/sccproperties-function.md).

SCC_COMMAND_OPTIONS соответствует [скксетоптион](../extensibility/sccsetoption-function.md).

## <a name="see-also"></a>См. также
- [Подключаемые модули системы управления версиями](../extensibility/source-control-plug-ins.md)
- [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md)
- [SccPopulateList](../extensibility/sccpopulatelist-function.md)
