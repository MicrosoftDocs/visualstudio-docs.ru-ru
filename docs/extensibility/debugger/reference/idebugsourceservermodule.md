---
description: Представляет сведения о исходном сервере, содержащиеся в PDB-файле.
title: Идебугсаурцесервермодуле | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugSourceServerModule interface
ms.assetid: 38213060-451d-46e6-8b4a-efc123e01a2c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 5b12e93d52fe841b66baae341a6854e0217dcb00
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105071172"
---
# <a name="idebugsourceservermodule"></a>IDebugSourceServerModule
Представляет сведения о исходном сервере, содержащиеся в PDB-файле.

## <a name="syntax"></a>Синтаксис

```
IDebugSourceServerModule : IUnknown
```

## <a name="notes-for-implementers"></a>Примечания для разработчиков
 Этот интерфейс реализуется механизмами отладчика и используется в пользовательском интерфейсе отладчика.

## <a name="methods"></a>Методы
 В следующей таблице показаны методы `IDebugSourceServerModule` .

|Метод|Описание|
|------------|-----------------|
|[GetSourceServerData](../../../extensibility/debugger/reference/idebugsourceservermodule-getsourceserverdata.md)|Извлекает массив сведений о исходном сервере.|

## <a name="requirements"></a>Требования
 Заголовок: Мсдбг. h

 Пространство имен: Microsoft. VisualStudio. Debugger. Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll
