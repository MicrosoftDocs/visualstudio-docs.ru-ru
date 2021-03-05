---
description: Содержит данные для расположения точки останова в указанной строке в файле исходного кода.
title: BP_LOCATION_CODE_FILE_LINE | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_LOCATION_CODE_FILE_LINE
helpviewer_keywords:
- BP_LOCATION_CODE_FILE_LINE structure
ms.assetid: 3ff32032-d412-44d3-91bf-870cc354a09e
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
ms.openlocfilehash: 2ad3452e0fce6ec7339fe2d8e67a2aee4585828c
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102144394"
---
# <a name="bp_location_code_file_line"></a>BP_LOCATION_CODE_FILE_LINE
Содержит данные для расположения точки останова в указанной строке в файле исходного кода.

## <a name="syntax"></a>Синтаксис

```cpp
typedef struct _BP_LOCATION_CODE_FILE_LINE {
    BSTR                     bstrContext;
    IDebugDocumentPosition2* pDocPos;
} BP_LOCATION_CODE_FILE_LINE;
```

## <a name="members"></a>Члены
`bstrContext`\
Контекст точки останова, обычно имя метода или функции, как показано в стеке вызовов.

`pDocPos`\
Объект [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md) , представляющий расположение точки останова в документе.

## <a name="remarks"></a>Комментарии
Эта структура является членом структуры [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md) в составе объединения.

## <a name="requirements"></a>Требования
Заголовок: мсдбг. h

Пространство имен: Microsoft. VisualStudio. Debugger. Interop

Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также раздел
- [Структуры и объединения](../../../extensibility/debugger/reference/structures-and-unions.md)
- [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md)
- [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)
