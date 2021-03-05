---
description: Указывает сведения, которые необходимо получить о неудачном разрешении точки останова.
title: BPERESI_FIELDS | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BPERESI_FIELDS
helpviewer_keywords:
- BPERESI_FIELDS enumeration
ms.assetid: dd7dd89c-1043-46a1-a929-099cc039c344
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e26b5a7285c2e5c9135429777b4b58f35252e550
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102162528"
---
# <a name="bperesi_fields"></a>BPERESI_FIELDS
Указывает сведения, которые необходимо получить о неудачном разрешении точки останова.

## <a name="syntax"></a>Синтаксис

```cpp
enum enum_BPERESI_FIELDS {
    PERESI_BPRESLOCATION = 0x0001,
    BPERESI_PROGRAM      = 0x0002,
    BPERESI_THREAD       = 0x0004,
    BPERESI_MESSAGE      = 0x0008,
    BPERESI_TYPE         = 0x0010,
    BPERESI_ALLFIELDS    = 0xffffffff
};
typedef DWORD BPERESI_FIELDS;
```

```csharp
public enum enum_BPERESI_FIELDS {
    PERESI_BPRESLOCATION = 0x0001,
    BPERESI_PROGRAM      = 0x0002,
    BPERESI_THREAD       = 0x0004,
    BPERESI_MESSAGE      = 0x0008,
    BPERESI_TYPE         = 0x0010,
    BPERESI_ALLFIELDS    = 0xffffffff
};
```

## <a name="fields"></a>Поля
`PERESI_BPRESLOCATION`\
Инициализируйте или используйте `bpResLocation` поле (расположение разрешения точки останова) структуры [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md) .

`BPERESI_PROGRAM`\
Инициализируйте или используйте `pProgram` поле `BP_ERROR_RESOLUTION_INFO` структуры.

`BPERESI_THREAD`\
Инициализируйте или используйте `pThread` поле `BP_ERROR_RESOLUTION_INFO` структуры.

`BPERESI_MESSAGE`\
Инициализируйте или используйте `bstrMessage` поле `BP_ERROR_RESOLUTION_INFO` структуры.

`BPERESI_TYPE`\
Инициализируйте или используйте `dwType` поле (тип точки останова) `BP_ERROR_RESOLUTION_INFO` структуры.

`BPERESI_ALLFIELDS`\
Инициализация или использование всех полей `BP_ERROR_RESOLUTION_INFO` структуры.

## <a name="remarks"></a>Комментарии
Передается в качестве параметра в метод [жетресолутионинфо](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md) , чтобы указать, какие поля структуры [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md) должны быть инициализированы.

Эти значения также используются для указания того, какие поля в `BP_ERROR_RESOLUTION_INFO` структуре используются и допустимы при возврате этой структуры.

Эти значения можно объединить с помощью побитовой операции `OR` .

## <a name="requirements"></a>Требования
Заголовок: мсдбг. h

Пространство имен: Microsoft. VisualStudio. Debugger. Interop

Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)
- [GetResolutionInfo](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md)
