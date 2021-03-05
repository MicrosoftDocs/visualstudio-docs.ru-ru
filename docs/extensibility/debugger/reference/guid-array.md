---
description: Описывает массив уникальных идентификаторов для доступных модулей отладки.
title: GUID_ARRAY | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- GUID_ARRAY structure
ms.assetid: 9e12500c-2c1c-49b1-a0ba-e08366c97eb8
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: cbdc8465bef0795649fef5b169a221a3e7b7178c
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102162424"
---
# <a name="guid_array"></a>GUID_ARRAY
Описывает массив уникальных идентификаторов для доступных модулей отладки.

## <a name="syntax"></a>Синтаксис

```cpp
typedef struct tagGUID_ARRAY
{
    DWORD dwCount;
    GUID *Members;
} GUID_ARRAY;
```

```csharp
public struct GUID_ARRAY
{
    public uint dwCount;
    public Guid Members;
}
```

## <a name="members"></a>Члены
`dwCount`\
Число уникальных идентификаторов в массиве.

`Members`\
Массив, содержащий уникальные идентификаторы.

## <a name="remarks"></a>Комментарии
Эта структура возвращается методом [жетенгинефилтер](../../../extensibility/debugger/reference/idebugprocess3-getenginefilter.md) .

## <a name="requirements"></a>Требования
Заголовок: Мсдбг. h

Пространство имен: Microsoft. VisualStudio. Debugger. Interop

Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также раздел
- [Структуры и объединения](../../../extensibility/debugger/reference/structures-and-unions.md)
- [GetEngineFilter](../../../extensibility/debugger/reference/idebugprocess3-getenginefilter.md)
