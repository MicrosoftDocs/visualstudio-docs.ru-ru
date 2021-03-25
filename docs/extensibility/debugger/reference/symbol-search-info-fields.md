---
description: Указывает тип символьных сведений для извлечения.
title: SYMBOL_SEARCH_INFO_FIELDS | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SYMBOL_SEARCH_INFO_FIELDS
helpviewer_keywords:
- SYMBOL_SEARCH_INFO_FIELDS enumeration
ms.assetid: bce35af0-722d-46d4-afa6-eaae598c51ff
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 893cc51767be8977c6c298b56ffffee60c93bbbc
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105070912"
---
# <a name="symbol_search_info_fields"></a>SYMBOL_SEARCH_INFO_FIELDS
Указывает тип символьных сведений для извлечения.

## <a name="syntax"></a>Синтаксис

```cpp
enum enum_SYMBOL_SEARCH_INFO_FIELDS
{
   SSIF_NONE                = 0x00000000,
   SSIF_VERBOSE_SEARCH_INFO = 0x00000001
};
typedef DWORD SYMBOL_SEARCH_INFO_FIELDS;
```

```csharp
public enum enum_SYMBOL_SEARCH_INFO_FIELDS
{
   SSIF_NONE                = 0x00000000,
   SSIF_VERBOSE_SEARCH_INFO = 0x00000001
};

```

## <a name="fields"></a>Поля
 `SSIF_NONE`\
 Указывает отсутствие флагов

 `SSIF_VERBOSE_SEARCH_INFO`\
 Возвращает все пути поиска, используемые для поиска символов

## <a name="remarks"></a>Remarks
 Эти флаги передаются в метод [жетсимболинфо](../../../extensibility/debugger/reference/idebugmodule3-getsymbolinfo.md) в качестве параметра, чтобы определить объем возвращаемой информации.

> [!NOTE]
> В настоящее время `SSIF_VERBOSE_SEARCH_INFO` поддерживается только, и его необходимо указать в качестве `dwFlags` параметра `IDebugModule3::GetSymbolInfo` . Все остальные значения возвращают ошибку.

## <a name="requirements"></a>Требования
 Заголовок: мсдбг. h

 Пространство имен: Microsoft. VisualStudio. Debugger. Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetSymbolInfo](../../../extensibility/debugger/reference/idebugmodule3-getsymbolinfo.md)
