---
description: Справочный раздел содержит концептуальный обзор API, руководство, в котором показан синтаксис и использование для всех элементов API, а также ассортимент примеров кода.
title: Справочник по API (Отладка Visual Studio) | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- debugging [Debugging SDK], API reference
ms.assetid: e4e429da-3667-41f7-9158-a8207d13e91a
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 47c6697945c6c588a8b4e57ab03d573d45c4d4cf
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102144641"
---
# <a name="api-reference-visual-studio-debugging"></a>Справочник API (отладка Visual Studio)
Справочный раздел содержит концептуальный обзор API, руководство, в котором показан синтаксис и использование для всех элементов API, а также ассортимент примеров кода. Все ссылки перечислены в алфавитном порядке по категориям.

 В следующей таблице показаны общие `HRESULT` значения, возвращаемые методами.

|Имя|Описание|Значение|
|----------|-----------------|-----------|
|S_OK|Успешно.|0x00000000|
|E_UNEXPECTED|Непредвиденный сбой.|0x8000FFFF|
|E_NOTIMPL|Не реализован.|0x80004001|
|E_OUTOFMEMORY|Недостаточно памяти для завершения операции.|0x8007000E|
|E_INVALIDARG|Один или несколько аргументов недопустимы.|0x80070057|
|E_NOINTERFACE|Такой интерфейс не поддерживается.|0x80004002|
|E_POINTER|Недопустимый указатель.|0x80004003|
|E_HANDLE|Недопустимый маркер.|0x80070006|
|E_ABORT|Операция аварийно завершена.|0x80004004|
|E_FAIL|Непредвиденный сбой.|0x80004005|
|E_ACCESSDENIED|Общая ошибка отказа в доступе.|0x80070005|

> [!NOTE]
> При [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] возврате из метода отладки `S_OK` предполагается, что все указатели на параметры являются допустимыми, т `S_OK` . е. при возвращении указателей на параметры не выполняется проверка.
>
> [!NOTE]
> Недопустимые или `NULL` [исходящие] параметры могут привести к сбою интегрированной среды разработки.

## <a name="see-also"></a>См. также раздел
- [Интерфейсы](../../../extensibility/debugger/reference/interfaces-visual-studio-debugging.md)
- [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [Структуры и объединения](../../../extensibility/debugger/reference/structures-and-unions.md)
- [Вспомогательные пакеты SDK для отладки](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)
- [Расширяемость отладчика Visual Studio](../../../extensibility/debugger/visual-studio-debugger-extensibility.md)
