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
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e5719728637f26ed61283578565470b39fc60455
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102151588"
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

## <a name="remarks"></a>Комментарии
 Чтобы определить, сколько ядер существует, вызовите этот метод один раз, указав `celtBuffer` для параметра значение 0, а для `rgguidEngines` параметра задается NULL. Этот метод возвращает `HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)` (0x8007007A для C#), а `pceltEngines` параметр возвращает необходимый размер буфера.

## <a name="see-also"></a>См. также раздел
- [IDebugProgramEngines2](../../../extensibility/debugger/reference/idebugprogramengines2.md)
