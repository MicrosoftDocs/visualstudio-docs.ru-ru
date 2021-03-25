---
title: INTERCEPT_EXCEPTION_ACTION | Документация Майкрософт
description: Перечисление INTERCEPT_EXCEPTION_ACTION указывает, какое действие следует предпринять при перехвате исключений в отладке Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- INTERCEPT_EXCEPTION_ACTION
helpviewer_keywords:
- INTERCEPT_EXCEPTION_ACTION enumeration
ms.assetid: e647f1eb-2932-4447-8c78-3b0d706fb972
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1c5a3d0d946e05ce249fa4b74dd31e7fef891e7a
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105082625"
---
# <a name="intercept_exception_action"></a>INTERCEPT_EXCEPTION_ACTION
Указывает, какие действия следует предпринять при перехвате исключений.

## <a name="syntax"></a>Синтаксис

```cpp
enum enum_INTERCEPT_EXCEPTION_ACTION
{
    IEA_INTERCEPT = 0x0001
}
typedef DWORD INTERCEPT_EXCEPTION_ACTION;
```

```csharp
public enum enum_INTERCEPT_EXCEPTION_ACTION
{
    IEA_INTERCEPT = 0x0001
}
```

## <a name="parameters"></a>Параметры

`IEA_INTERCEPT`\
Включает перехват текущего исключения. В настоящее время поддерживается только это значение, и его необходимо указать.

## <a name="remarks"></a>Remarks
Эти значения передаются в метод [интерцепткуррентексцептион](../../../extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception.md) .

## <a name="requirements"></a>Требования
Заголовок: мсдбг. h

Пространство имен: Microsoft. VisualStudio. Debugger. Interop

Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [InterceptCurrentException](../../../extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception.md)
