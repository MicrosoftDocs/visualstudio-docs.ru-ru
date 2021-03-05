---
description: Сообщает пользовательскому интерфейсу отладчика Visual Studio о том, что не удалось найти символы для запущенного исполняемого файла.
title: IDebugNoSymbolsEvent2 | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugNoSymbolsEvent2 interface
ms.assetid: f6fb6388-47f6-4385-9ad5-95d62f9a7592
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 859c9c1d07a5f4660f2d13dcffac4f19659a2bc2
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102149825"
---
# <a name="idebugnosymbolsevent2"></a>IDebugNoSymbolsEvent2
Сигнализирует [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] пользовательскому интерфейсу отладчика предупредить пользователя о том, что не удалось найти символы для запущенного исполняемого файла.

## <a name="syntax"></a>Синтаксис

```
IDebugNoSymbolsEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Примечания для разработчиков
 Реализован механизмами отладки и используется в [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] пользовательском интерфейсе отладчика.

## <a name="requirements"></a>Требования
 Заголовок: Мсдбг. h

 Пространство имен: Microsoft. VisualStudio. Debugger. Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll
