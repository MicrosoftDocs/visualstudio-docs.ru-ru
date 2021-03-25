---
description: Сообщает пользовательскому интерфейсу отладчика Visual Studio о том, что не удалось найти символы для запущенного исполняемого файла.
title: IDebugNoSymbolsEvent2 | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugNoSymbolsEvent2 interface
ms.assetid: f6fb6388-47f6-4385-9ad5-95d62f9a7592
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 7a060436575d51710fcef9c444ac843aa56195d0
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105058408"
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
