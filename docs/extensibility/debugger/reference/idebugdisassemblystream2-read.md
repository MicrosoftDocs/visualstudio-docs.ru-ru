---
description: Считывает инструкции, начиная с текущей позицией в потоке дизассемблированного кода.
title: 'IDebugDisassemblyStream2:: Read | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDisassemblyStream2::Read
helpviewer_keywords:
- IDebugDisassemblyStream2::Read
ms.assetid: 7db5f6bb-73ee-45bc-b187-c1b6aa2dfdd5
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: bcabd0cc42f013b579ee32deeb33d68cd9d45f5d
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105066923"
---
# <a name="idebugdisassemblystream2read"></a>IDebugDisassemblyStream2::Read
Считывает инструкции, начиная с текущей позицией в потоке дизассемблированного кода.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT Read( 
   DWORD                     dwInstructions,
   DISASSEMBLY_STREAM_FIELDS dwFields,
   DWORD*                    pdwInstructionsRead,
   DisassemblyData*          prgDisassembly
);
```

```csharp
int Read( 
   uint                           dwInstructions,
   enum_DISASSEMBLY_STREAM_FIELDS dwFields,
   out uint                       pdwInstructionsRead,
   DisassemblyData[]              prgDisassembly
);
```

## <a name="parameters"></a>Параметры
`dwInstructions`\
окне Количество инструкций для разсборки. Это значение также является максимальной длиной `prgDisassembly` массива.

`dwFields`\
окне Сочетание флагов из перечисления [DISASSEMBLY_STREAM_FIELDS](../../../extensibility/debugger/reference/disassembly-stream-fields.md) , которые указывают, какие поля должны `prgDisassembly` быть заполнены.

`pdwInstructionsRead`\
заполняет Возвращает количество фактически собранных инструкций.

`prgDisassembly`\
заполняет Массив структур [дисассемблидата](../../../extensibility/debugger/reference/disassemblydata.md) , которые заполняются с помощью разсобранного кода, одной структуры на каждую разобранную инструкцию. Длина этого массива определяется `dwInstructions` параметром.

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Remarks
 Максимальное количество инструкций, доступных в текущей области, можно получить, вызвав [метод метода](../../../extensibility/debugger/reference/idebugdisassemblystream2-getsize.md) superscope.

 Текущую позицию, из которой считывается следующая инструкция, можно изменить, вызвав метод [Seek](../../../extensibility/debugger/reference/idebugdisassemblystream2-seek.md) .

 `DSF_OPERANDS_SYMBOLS`Флаг можно добавить к `DSF_OPERANDS` флагу в `dwFields` параметре, чтобы указать, что при разсборке инструкций следует использовать имена символов.

## <a name="see-also"></a>См. также
- [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)
- [DISASSEMBLY_STREAM_FIELDS](../../../extensibility/debugger/reference/disassembly-stream-fields.md)
- [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)
- [GetSize](../../../extensibility/debugger/reference/idebugdisassemblystream2-getsize.md)
- [Seek](../../../extensibility/debugger/reference/idebugdisassemblystream2-seek.md)
