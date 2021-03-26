---
description: Задает тип объекта из средства оценки выражений.
title: OBJECT_TYPE | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- OBJECT_TYPE
helpviewer_keywords:
- OBJECT_TYPE enumeration
ms.assetid: c4d246f9-8a98-44ec-b2bb-ff5c684f668e
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 80ef6cce37967d61611ac48f60aaf5b2a1d184f1
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105082393"
---
# <a name="object_type"></a>Object_Type
Задает тип объекта из средства оценки выражений.

## <a name="syntax"></a>Синтаксис

```cpp
enum enum_OBJECT_TYPE { 
   OBJECT_TYPE_BOOLEAN = 0x0,
   OBJECT_TYPE_CHAR    = 0x1,
   OBJECT_TYPE_I1      = 0x2,
   OBJECT_TYPE_U1      = 0x3,
   OBJECT_TYPE_I2      = 0x4,
   OBJECT_TYPE_U2      = 0x5,
   OBJECT_TYPE_I4      = 0x6,
   OBJECT_TYPE_U4      = 0x7,
   OBJECT_TYPE_I8      = 0x8,
   OBJECT_TYPE_U8      = 0x9,
   OBJECT_TYPE_R4      = 0xa,
   OBJECT_TYPE_R8      = 0xb,
   OBJECT_TYPE_OBJECT  = 0xc,
   OBJECT_TYPE_NULL    = 0xd,
   OBJECT_TYPE_CLASS   = 0xe
};
typedef DWORD OBJECT_TYPE;
```

```csharp
public enum enum_OBJECT_TYPE { 
   OBJECT_TYPE_BOOLEAN = 0x0,
   OBJECT_TYPE_CHAR    = 0x1,
   OBJECT_TYPE_I1      = 0x2,
   OBJECT_TYPE_U1      = 0x3,
   OBJECT_TYPE_I2      = 0x4,
   OBJECT_TYPE_U2      = 0x5,
   OBJECT_TYPE_I4      = 0x6,
   OBJECT_TYPE_U4      = 0x7,
   OBJECT_TYPE_I8      = 0x8,
   OBJECT_TYPE_U8      = 0x9,
   OBJECT_TYPE_R4      = 0xa,
   OBJECT_TYPE_R8      = 0xb,
   OBJECT_TYPE_OBJECT  = 0xc,
   OBJECT_TYPE_NULL    = 0xd,
   OBJECT_TYPE_CLASS   = 0xe
};
```

## <a name="fields"></a>Поля
 `OBJECT_TYPE_BOOLEAN`\
 Указывает, что объект является логическим значением.

 `OBJECT_TYPE_CHAR`\
 Указывает, что объект является символом.

 `OBJECT_TYPE_I1`\
 Указывает, что объект является однобайтовым целым числом со знаком.

 `OBJECT_TYPE_U1`\
 Указывает, что объект является однобайтовым беззнаковым целым числом.

 `OBJECT_TYPE_I2`\
 Указывает, что объект является двухбайтовым целым числом со знаком.

 `OBJECT_TYPE_U2`\
 Указывает, что объект представляет собой Двухбайтовое беззнаковое целое число.

 `OBJECT_TYPE_I4`\
 Указывает, что объект является четырехзначным целым числом со знаком.

 `OBJECT_TYPE_U4`\
 Указывает, что объект представляет собой целое число без знака длиной 4 байта.

 `OBJECT_TYPE_I8`\
 Указывает, что объект является 8-байтовым целым числом со знаком.

 `OBJECT_TYPE_U8`\
 Указывает, что объект является 8-байтовым целым числом без знака.

 `OBJECT_TYPE_R4`\
 Указывает, что объект является четырьмя-байтовым числом с плавающей запятой.

 `OBJECT_TYPE_R8`\
 Указывает, что объект является 8-байтовым числом с плавающей запятой.

 `OBJECT_TYPE_OBJECT`\
 Указывает, что объект является объектом.

 `OBJECT_TYPE_NULL`\
 Указывает, что объект имеет значение NULL.

 `OBJECT_TYPE_CLASS`\
 Указывает, что объект является классом.

## <a name="remarks"></a>Remarks
 Передается в качестве аргумента методам [креатепримитивеобжект](../../../extensibility/debugger/reference/idebugfunctionobject-createprimitiveobject.md) и [креатеаррайобжект](../../../extensibility/debugger/reference/idebugfunctionobject-createarrayobject.md) .

## <a name="requirements"></a>Требования
 Заголовок: ee. h

 Пространство имен: Microsoft. VisualStudio. Debugger. Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [CreatePrimitiveObject](../../../extensibility/debugger/reference/idebugfunctionobject-createprimitiveobject.md)
- [CreateArrayObject](../../../extensibility/debugger/reference/idebugfunctionobject-createarrayobject.md)
