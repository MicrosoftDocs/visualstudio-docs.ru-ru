---
description: Представляет поставщик символов COM+ с методами, характерными для управляемого кода.
title: Идебугкомплуссимболпровидер | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugComPlusSymbolProvider interface
ms.assetid: 5b98e908-fd15-49a6-9010-933c9b948085
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 20ede060901a9aeec591fb17d1f632cb5d228963
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102163477"
---
# <a name="idebugcomplussymbolprovider"></a>IDebugComPlusSymbolProvider
Представляет поставщик символов COM+ с методами, характерными для управляемого кода.

## <a name="syntax"></a>Синтаксис

```
IDebugComPlusSymbolProvider : IDebugSymbolProvider
```

## <a name="notes-for-implementers"></a>Примечания для разработчиков
 Хотя между интерфейсами, которые полезны для оценки выражений (EE) и предназначены для использования ядром отладки (DE), не существует разделения, следующие методы, скорее всего, будут поинтересны только разработчикам: Аресимболслоадед, Жетаддрессесинмодулефромпоситион, Жетентрипоинт, Жетфунктионлинеоффсет, GetLocalVariableLayout, IsFunctionStale, LoadSymbols, LoadSymbolsFromStream, ReplaceSymbols, UnloadSymbols и UpdateSymbols.

## <a name="methods"></a>Методы
 В дополнение к методам в интерфейсе [идебугсимболпровидер](../../../extensibility/debugger/reference/idebugsymbolprovider.md) этот интерфейс реализует следующие методы:

|Метод|Описание|
|------------|-----------------|
|[AreSymbolsLoaded](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-aresymbolsloaded.md)|Определяет, загружаются ли отладочные символы для указанного модуля по заданному идентификатору домена приложения.|
|[CreateTypeFromPrimitive](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-createtypefromprimitive.md)|Создает тип из указанного примитивного типа.|
|[GetAddressesInModuleFromPosition](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getaddressesinmodulefromposition.md)|Сопоставляет расположение документа в указанном модуле с массивом адресов отладки.|
|[GetArrayTypeFromAddress](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getarraytypefromaddress.md)|Извлекает сведения о типе указанного массива по его адресу отладки.|
|[GetAssemblyName](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getassemblyname.md)|Извлекает имя сборки по заданному модулю и домену приложения.|
|[GetAttributedClassesForLanguage](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getattributedclassesforlanguage.md)|Извлекает классы с указанным атрибутом, реализованным на данном языке программирования.|
|[GetAttributedClassesinModule](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getattributedclassesinmodule.md)|Извлекает классы с указанным атрибутом в заданном модуле.|
|[GetEntryPoint](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getentrypoint.md)|Получает точку входа приложения.|
|[GetFunctionLineOffset](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getfunctionlineoffset.md)|Извлекает адрес внутри функции, представляющей заданное смещение строки.|
|[GetLocalVariablelayout](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getlocalvariablelayout.md)|Извлекает макет локальных переменных для набора методов.|
|[GetNameFromToken](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getnamefromtoken.md)|Возвращает имя, связанное с указанным токеном по заданному объекту метаданных.|
|[GetSymAttribute](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getsymattribute.md)|Извлекает отладочные символы с заданным родительским атрибутом для указанного модуля.|
|[GetSymUnmanagedReader](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getsymunmanagedreader.md)|Возвращает средство чтения символов, используемое неуправляемым кодом.|
|[GetTypeFromAddress](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-gettypefromaddress.md)|Возвращает в символьный тип по заданному адресу отладки.|
|[IsFunctionDeleted](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-isfunctiondeleted.md)|Определяет, удаляется ли функция по указанному адресу отладки.|
|[IsFunctionStale](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-isfunctionstale.md)|Определяет, считается ли функция по указанному адресу отладки устаревшей.|
|[IsHiddenCode](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-ishiddencode.md)|Определяет, скрыт ли код в указанном адресе отладчика.|
|[LoadSymbols](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-loadsymbols.md)|Загружает указанные отладочные символы в память.|
|[LoadSymbolsFromStream](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-loadsymbolsfromstream.md)|Загружает отладочные символы по заданному потоку данных.|
|[ReplaceSymbols](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-replacesymbols.md)|Заменяет текущие символы отладки на значения в указанном потоке данных.|
|[UnloadSymbols](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-unloadsymbols.md)|Выгружает отладочные символы для указанного модуля из памяти.|
|[UpdateSymbols](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-updatesymbols.md)|Обновляет отладочные символы в памяти с помощью указанного потока данных.|

## <a name="requirements"></a>Требования
 Заголовок: sh. h

 Пространство имен: Microsoft. VisualStudio. Debugger. Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll
