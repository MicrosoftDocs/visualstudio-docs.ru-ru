---
description: Возвращает идентификаторы GUID для всех возможных модулей отладки (DE), которые могут отлаживать эту программу.
title: 'IDebugProgramEngines2:: Енумпоссиблингинес | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramEngines2::EnumPossibleEngines
helpviewer_keywords:
- IDebugProgramEngines2::EnumPossibleEngines
ms.assetid: 993d70a4-f6a5-4e47-a603-0b162b9fde00
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2a49a0590a1ec2f0b0e7d2be59fe2161b438154a
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105084211"
---
# <a name="idebugprogramengines2enumpossibleengines"></a>IDebugProgramEngines2::EnumPossibleEngines
Возвращает идентификаторы GUID для всех возможных модулей отладки (DE), которые могут отлаживать эту программу.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT EnumPossibleEngines( 
   DWORD  celtBuffer,
   GUID*  rgguidEngines,
   DWORD* pceltEngines
);
```

```csharp
int EnumPossibleEngines( 
   uint      celtBuffer,
   GUID[]    rgguidEngines,
   ref DWORD pceltEngines
);
```

## <a name="parameters"></a>Параметры
`celtBuffer`\
окне Число возвращаемых ИДЕНТИФИКАТОРов DE. Это также указывает максимальный размер `rgguidEngines` массива.

`rgguidEngines`\
[вход, выход] Массив ИДЕНТИФИКАТОРов DE, которые необходимо заполнить.

`pceltEngines`\
заполняет Возвращает фактическое число возвращаемых ИДЕНТИФИКАТОРов DE.

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки. Возвращает [C++] `HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)` или [C#] 0x8007007A, если буфер недостаточно велик.

## <a name="remarks"></a>Remarks
 Чтобы определить, сколько ядер существует, вызовите этот метод один раз, указав `celtBuffer` для параметра значение 0, а для `rgguidEngines` параметра задается NULL. Этот метод возвращает `HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)` (0x8007007A для C#), а `pceltEngines` параметр возвращает необходимый размер буфера.

## <a name="see-also"></a>См. также
- [IDebugProgramEngines2](../../../extensibility/debugger/reference/idebugprogramengines2.md)
