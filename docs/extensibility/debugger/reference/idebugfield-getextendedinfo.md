---
description: Этот метод получает расширенные сведения о поле.
title: 'Идебугфиелд:: Жетекстендединфо | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugField::GetExtendedInfo
helpviewer_keywords:
- IDebugField::GetExtendedInfo method
ms.assetid: 46c0dd4d-4fd5-4efd-a908-71e4248e8e8d
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3e17c824d2be7ff12e3e967b953e25359b650b1c
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105077074"
---
# <a name="idebugfieldgetextendedinfo"></a>IDebugField::GetExtendedInfo
Этот метод получает расширенные сведения о поле.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetExtendedInfo( 
   REFGUID guidExtendedInfo,
   BYTE**  prgBuffer,
   DWORD*  pdwLen
);
```

```csharp
int GetExtendedInfo(
   ref Guid guidExtendedInfo,
   IntPtr[] prgBuffer,
   ref uint pdwLen
);
```

## <a name="parameters"></a>Параметры
`guidExtendedInfo`\
окне Выбирает возвращаемые данные. Допустимые значения:

|Значение|Описание|
|-----------|-----------------|
|`guidConstantValue`|Значение в виде последовательности байтов.|
|`guidConstantType`|Тип в виде сигнатуры типа.|

`prgBuffer`\
заполняет Возвращает расширенные сведения.

`pdwLen`\
[вход, выход] Возвращает размер расширенной информации в байтах.

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Remarks
 В настоящее время этот метод возвращает только тип или значение константы. Вызывающий объект должен освободить буфер, возвращенный в `prgBuffer` , вызвав `CoTaskMemFree` функцию com (C++) или <xref:System.Runtime.InteropServices.Marshal.FreeCoTaskMem%2A> (C#).

## <a name="see-also"></a>См. также
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
