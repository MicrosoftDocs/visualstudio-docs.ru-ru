---
description: Записывает дамп в файл.
title: 'IDebugProgram2:: Вритедумп | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::WriteDump
helpviewer_keywords:
- IDebugProgram2::WriteDump
ms.assetid: 375afb8c-882d-44db-bfa7-e2c9eb555122
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d0e4c90034d19635993196a0cd00ffcb06f26433
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102171931"
---
# <a name="idebugprogram2writedump"></a>IDebugProgram2::WriteDump
Записывает дамп в файл.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT WriteDump( 
   DUMPTYPE  DumpType,
   LPCOLESTR pszDumpUrl
);
```

```csharp
int WriteDump( 
   enum_DUMPTYPE  DumpType,
   string         pszDumpUrl
);
```

## <a name="parameters"></a>Параметры
`DumpType`\
окне Значение из перечисления [думптипе](../../../extensibility/debugger/reference/dumptype.md) , указывающее тип дампа, например short или long.

`pszDumpUrl`\
окне URL-адрес для записи дампа. Как правило, он имеет вид `file://c:\path\filename.ext` , но может быть любым допустимым URL-адресом.

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Комментарии
 Дамп программы обычно включает текущий кадр стека, стек, список потоков, выполняющихся в программе, и, возможно, любой объем памяти, который владеет программой.

## <a name="see-also"></a>См. также раздел
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
