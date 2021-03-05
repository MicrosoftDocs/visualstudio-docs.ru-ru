---
description: Определяет метаданные, которые могут быть получены от поставщика порта.
title: PORT_SUPPLIER_DESCRIPTION_FLAGS | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- PORT_SUPPLIER_DESCRIPTION_FLAGS enumeration
ms.assetid: 5acee0ee-3a20-41c9-a7dc-0dadae6a5ba5
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5f1806e75a8481fddef5118f594452393a1cef77
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102225452"
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

## <a name="remarks"></a>Комментарии

Это перечисление возвращается методом метода [Description](../../../extensibility/debugger/reference/idebugportsupplierdescription2-getdescription.md) .

## <a name="requirements"></a>Требования

Заголовок: Мсдбг. h

Пространство имен: Microsoft. VisualStudio. Debugger. Interop

Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также

- [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetDescription](../../../extensibility/debugger/reference/idebugportsupplierdescription2-getdescription.md)
