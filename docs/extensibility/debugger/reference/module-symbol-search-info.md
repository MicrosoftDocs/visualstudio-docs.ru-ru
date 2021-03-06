---
description: Содержит сведения о состоянии для путей поиска символов, которые были просмотрены.
title: MODULE_SYMBOL_SEARCH_INFO | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- MODULE_SYMBOL_SEARCH_INFO
helpviewer_keywords:
- MODULE_SYMBOL_SEARCH_INFO structure
ms.assetid: 432aff03-08a5-4c5a-b2d5-e212090fc70a
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: bc914334fc4b8ebf2dd73f691cdec242e19364a9
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102222293"
---
# <a name="module_symbol_search_info"></a>MODULE_SYMBOL_SEARCH_INFO

Содержит сведения о состоянии для путей поиска символов, которые были просмотрены.

## <a name="syntax"></a>Синтаксис

```cpp
typedef struct _tagSYMBOL_SEARCH_INFO
{
    SYMBOL_SEARCH_INFO_FIELDS dwValidFields;
    BSTR                      bstrVerboseSearchInfo;
} MODULE_SYMBOL_SEARCH_INFO;
```

```csharp
public struct MODULE_SYMBOL_SEARCH_INFO {
    public uint   dwValidFields;
    public string bstrVerboseSearchInfo;
}
```

## <a name="members"></a>Члены

`dwValidFields`\
Сочетание флагов из перечисления [SYMBOL_SEARCH_INFO_FIELDS](../../../extensibility/debugger/reference/symbol-search-info-fields.md) , определяющее тип сведений для поиска, описанных в этой структуре.

`bstrVerboseSearchInfo`\
Путь поиска и результаты, Объединенные в одну строку.

## <a name="remarks"></a>Комментарии

Эта структура возвращается из вызова метода [жетсимболинфо](../../../extensibility/debugger/reference/idebugmodule3-getsymbolinfo.md) .

Если `bstrVerboseSearchInfo` поле не пусто, то оно содержит список путей поиска и результаты этого поискового запроса. Список форматируется с помощью пути, за которым следует многоточие ("..."), а затем результат. Если существует несколько пар результатов пути, каждая пара отделяется парой "\r\n" (возврат каретки или перевод строки). Шаблон выглядит следующим образом:

\<path>...\<result> \r\n \<path> ... \<result> \r\n \<path> ...\<result>

Обратите внимание, что последняя запись не содержит последовательность \r\n.

Ниже приведена возможная `bstrVerboseSearchInfo` строка, отправленная в стандартный выход.

`c:\symbols\user32.pdb... File not found.`

`c:\winnt\symbols\user32.pdb... Version does not match.`

`\\symbols\symbols\user32.dll\0a8sd0ad8ad\user32.pdb... Symbols loaded.`

## <a name="requirements"></a>Требования

Заголовок: мсдбг. h

Пространство имен: Microsoft. VisualStudio. Debugger. Interop

Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также раздел

- [Структуры и объединения](../../../extensibility/debugger/reference/structures-and-unions.md)
- [GetSymbolInfo](../../../extensibility/debugger/reference/idebugmodule3-getsymbolinfo.md)
