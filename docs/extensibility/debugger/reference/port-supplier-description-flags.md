---
description: Определяет метаданные, которые могут быть получены от поставщика порта.
title: PORT_SUPPLIER_DESCRIPTION_FLAGS | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- PORT_SUPPLIER_DESCRIPTION_FLAGS enumeration
ms.assetid: 5acee0ee-3a20-41c9-a7dc-0dadae6a5ba5
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 09c3cb532b7fa9c496ad217c1f5ecacbbf2b8c5c
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105086317"
---
# <a name="port_supplier_description_flags"></a>PORT_SUPPLIER_DESCRIPTION_FLAGS

Определяет метаданные, которые могут быть получены от поставщика порта.

## <a name="syntax"></a>Синтаксис

```cpp
enum enum_PORT_SUPPLIER_DESCRIPTION_FLAGS
{
    PSDFLAG_SHOW_WARNING_ICON = 0x1
};
typedef DWORD PORT_SUPPLIER_DESCRIPTION_FLAGS;
```

```csharp
public enum enum_PORT_SUPPLIER_DESCRIPTION_FLAGS
{
    PSDFLAG_SHOW_WARNING_ICON = 0x1
};
```

## <a name="fields"></a>Поля

`PSDFLAG_SHOW_WARNING_ICON`\
Если этот флажок установлен, в пользовательском интерфейсе будет отображаться значок предупреждения.

## <a name="remarks"></a>Remarks

Это перечисление возвращается методом метода [Description](../../../extensibility/debugger/reference/idebugportsupplierdescription2-getdescription.md) .

## <a name="requirements"></a>Требования

Заголовок: Мсдбг. h

Пространство имен: Microsoft. VisualStudio. Debugger. Interop

Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также

- [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetDescription](../../../extensibility/debugger/reference/idebugportsupplierdescription2-getdescription.md)
