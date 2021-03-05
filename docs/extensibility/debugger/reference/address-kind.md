---
description: Указывает типы адресов.
title: ADDRESS_KIND | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- ADDRESS_KIND
helpviewer_keywords:
- ADDRESS_KIND enumeration
ms.assetid: 3a12fbec-7088-4cf9-8f6f-ad8ddec6009a
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 12a47edf2b9eca9cd99a5b11531f78e080572d54
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102144654"
---
# <a name="address_kind"></a>ADDRESS_KIND
Указывает типы адресов.

## <a name="syntax"></a>Синтаксис

```cpp
enum enum_ADDRESS_KIND {
    ADDRESS_KIND_NATIVE                  = 0x0001,
    ADDRESS_KIND_UNMANAGED_THIS_RELATIVE = 0x0002,
    ADDRESS_KIND_UNMANAGED_PHYSICAL      = 0x0005,
    ADDRESS_KIND_METADATA_METHOD         = 0x0010,
    ADDRESS_KIND_METADATA_FIELD          = 0x0011,
    ADDRESS_KIND_METADATA_LOCAL          = 0x0012,
    ADDRESS_KIND_METADATA_PARAM          = 0x0013,
    ADDRESS_KIND_METADATA_ARRAYELEM      = 0x0014,
    ADDRESS_KIND_METADATA_RETVAL         = 0x0015,
};
typedef DWORD ADDRESS_KIND;
```

```csharp
public enum enum_ADDRESS_KIND {
    ADDRESS_KIND_NATIVE                  = 0x0001,
    ADDRESS_KIND_UNMANAGED_THIS_RELATIVE = 0x0002,
    ADDRESS_KIND_UNMANAGED_PHYSICAL      = 0x0005,
    ADDRESS_KIND_METADATA_METHOD         = 0x0010,
    ADDRESS_KIND_METADATA_FIELD          = 0x0011,
    ADDRESS_KIND_METADATA_LOCAL          = 0x0012,
    ADDRESS_KIND_METADATA_PARAM          = 0x0013,
    ADDRESS_KIND_METADATA_ARRAYELEM      = 0x0014,
    ADDRESS_KIND_METADATA_RETVAL         = 0x0015,
};
```

## <a name="fields"></a>Поля
`ADDRESS_KIND_NATIVE`\
Собственный адрес, представленный структурой [NATIVE_ADDRESS](../../../extensibility/debugger/reference/native-address.md) .

`ADDRESS_KIND_UNMANAGED_THIS_RELATIVE`\
Неуправляемый адрес относительно `this` `Me` указателя (в Visual Basic), представленный структурой [UNMANAGED_ADDRESS_THIS_RELATIVE](../../../extensibility/debugger/reference/unmanaged-address-this-relative.md) .

`ADDRESS_KIND_UNMANAGED_PHYSICAL`\
Неуправляемый физический адрес, представленный структурой [UNMANAGED_ADDRESS_PHYSICAL](../../../extensibility/debugger/reference/unmanaged-address-physical.md) .

`ADDRESS_KIND_METHOD`\
Метод класса, представленный структурой [METADATA_ADDRESS_METHOD](../../../extensibility/debugger/reference/metadata-address-method.md) .

`ADDRESS_KIND_FIELD`\
Поле класса, представленное структурой [METADATA_ADDRESS_FIELD](../../../extensibility/debugger/reference/metadata-address-field.md) .

`ADDRESS_KIND_LOCAL`\
Адрес предназначен для локальной переменной и представлен структурой [METADATA_ADDRESS_LOCAL](../../../extensibility/debugger/reference/metadata-address-local.md) .

`ADDRESS_KIND_PARAM`\
Метод или параметр функции, представленный структурой [METADATA_ADDRESS_PARAM](../../../extensibility/debugger/reference/metadata-address-param.md) .

`ADDRESS_KIND_ARRAYELEM`\
Элемент массива, представленный структурой [METADATA_ADDRESS_ARRAYELEM](../../../extensibility/debugger/reference/metadata-address-arrayelem.md) .

`ADDRESS_KIND_RETVAL`\
Возвращаемое значение, представленное структурой [METADATA_ADDRESS_RETVAL](../../../extensibility/debugger/reference/metadata-address-retval.md) .

## <a name="remarks"></a>Комментарии
Метод [метода](../../../extensibility/debugger/reference/idebugaddress-getaddress.md) WebMethod возвращает структуру [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) , содержащую объединение возможных структур, [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md) структуру. `dwKind`Поле `DEBUG_ADDRESS_UNION` структуры содержит `ADDRESS_KIND` значение и описывает способ интерпретации поля объединения.

## <a name="requirements"></a>Требования
Заголовок: sh. h

Пространство имен: Microsoft. VisualStudio. Debugger. Interop

Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md)
- [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)
- [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)
