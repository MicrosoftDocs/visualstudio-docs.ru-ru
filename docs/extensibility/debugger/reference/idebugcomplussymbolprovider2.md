---
description: Представляет поставщик символов COM+ с методами, специфичными для управляемого кода, и расширяет Идебугкомплуссимболпровидер.
title: IDebugComPlusSymbolProvider2 | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugComPlusSymbolProvider2 interface
ms.assetid: fa2f9b49-03ad-43c7-92d6-6dcb9c3d0531
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 975dc6df875866a16fffc5d044ae82c996b84e35
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105077971"
---
# <a name="idebugcomplussymbolprovider2"></a>IDebugComPlusSymbolProvider2
Представляет поставщик символов COM+ с методами, специфичными для управляемого кода, и расширяет [Идебугкомплуссимболпровидер](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md) **идебугкомплуссимболпровидер**.

## <a name="syntax"></a>Синтаксис

```
IDebugComPlusSymbolProvider2 : IDebugComPlusSymbolProvider
```

## <a name="methods"></a>Методы
 В дополнение к методам в интерфейсе [идебугкомплуссимболпровидер](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md) этот интерфейс реализует следующие методы:

|Метод|Описание|
|------------|-----------------|
|[FunctionHasLineInfo](../../../extensibility/debugger/reference/idebugcomplussymbolprovider2-functionhaslineinfo.md)|Определяет, содержит ли указанный метод сведения о строке.|
|[GetTypesByName](../../../extensibility/debugger/reference/idebugcomplussymbolprovider2-gettypesbyname.md)|Извлекает тип по заданному имени.|
|[GetTypeFromToken](../../../extensibility/debugger/reference/idebugcomplussymbolprovider2-gettypefromtoken.md)|Извлекает тип с учетом его токена.|
|[IsAddressSequencePoint](../../../extensibility/debugger/reference/idebugcomplussymbolprovider2-isaddresssequencepoint.md)|Определяет, является ли указанный адрес отладки точкой следования.|
|[LoadSymbolsFromCallback](../../../extensibility/debugger/reference/idebugcomplussymbolprovider2-loadsymbolsfromcallback.md)|Загружает отладочные символы с помощью указанного метода обратного вызова.|
|[LoadSymbolsFromStreamWithCorModule](../../../extensibility/debugger/reference/idebugcomplussymbolprovider2-loadsymbolsfromstreamwithcormodule.md)|Загрузка отладочных символов из потока данных по заданному объекту **ICorDebugModule** .|
|[LoadSymbolsWithCorModule](../../../extensibility/debugger/reference/idebugcomplussymbolprovider2-loadsymbolswithcormodule.md)|Загружает символы отладки по заданному объекту **ICorDebugModule** .|

## <a name="requirements"></a>Требования
 Заголовок: sh. h

 Пространство имен: Microsoft. VisualStudio. Debugger. Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll
