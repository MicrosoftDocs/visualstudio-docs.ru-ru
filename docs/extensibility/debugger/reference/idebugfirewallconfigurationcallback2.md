---
description: Включает модуль отладки, использующий DCOM для запроса пользовательского интерфейса Visual Studio, чтобы убедиться, что брандмауэр не блокирует удаленную отладку.
title: IDebugFirewallConfigurationCallback2 | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugFirewallConfigurationCallback2 interface
ms.assetid: 0827361c-b97c-4851-9898-ab6d88c81811
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: bf8659a1bc4af55a9809a3c85548b971a7193b26
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102166532"
---
# <a name="idebugfirewallconfigurationcallback2"></a>IDebugFirewallConfigurationCallback2
Включает модуль отладки, использующий DCOM для запроса [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] пользовательского интерфейса, чтобы убедиться, что брандмауэр не блокирует удаленную отладку.

## <a name="syntax"></a>Синтаксис

```
IDebugFirewallConfigurationCallback2 : IUnknown
```

## <a name="notes-for-implementers"></a>Примечания для разработчиков
 Реализуется объектом Port диспетчера отладки сеанса.

## <a name="methods"></a>Методы
 В следующей таблице показаны методы `IDebugFirewallConfigurationCallback2` .

|Метод|Описание|
|------------|-----------------|
|[EnsureDCOMUnblocked](../../../extensibility/debugger/reference/idebugfirewallconfigurationcallback2-ensuredcomunblocked.md)|Запрашивает, чтобы брандмауэр не блокировал удаленную отладку.|

## <a name="requirements"></a>Требования
 Заголовок: Мсдбг. h

 Пространство имен: Microsoft. VisualStudio. Debugger. Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll
