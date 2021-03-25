---
description: Этот метод сопоставляет контекст документа с массивом адресов отладки.
title: 'Идебугсимболпровидер:: Жетаддрессесфромконтекст | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugSymbolProvider::GetAddressesFromContext
helpviewer_keywords:
- IDebugSymbolProvider::GetAddressesFromContext method
ms.assetid: a3124883-a255-4543-a5ec-e1c7a97beb69
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e9748e2e2cf7f82724398afe25624f2d1762363c
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105087136"
---
# <a name="idebugsymbolprovidergetaddressesfromcontext"></a>IDebugSymbolProvider::GetAddressesFromContext
Этот метод сопоставляет контекст документа с массивом адресов отладки.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetAddressesFromContext( 
   IDebugDocumentContext2* pDocContext,
   BOOL                    fStatmentOnly,
   IEnumDebugAddresses**   ppEnumBegAddresses,
   IEnumDebugAddresses**   ppEnumEndAddresses
);
```

```csharp
int GetAddressesFromContext(
   IDebugDocumentContext2  pDocContext,
   bool                    fStatmentOnly,
   out IEnumDebugAddresses ppEnumBegAddresses,
   out IEnumDebugAddresses ppEnumEndAddresses
);
```

## <a name="parameters"></a>Параметры
`pDocContext`\
окне Контекст документа.

`fStatmentOnly`\
окне Если значение — TRUE, адреса отладки ограничиваются одной инструкцией.

`ppEnumBegAddresses`\
заполняет Возвращает перечислитель для начальных адресов отладки, связанных с данной инструкцией или строкой.

`ppEnumEndAddresses`\
заполняет Возвращает перечислитель [иенумдебугаддрессес](../../../extensibility/debugger/reference/ienumdebugaddresses.md) для конечных адресов отладки, связанных с данной инструкцией или строкой.

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Remarks
 Контекст документа обычно указывает на диапазон исходных строк. Этот метод предоставляет начальный и конечный отладочные адреса, связанные с этими строками. Некоторые языки разрешают операторы, охватывающие несколько строк, или строки, содержащие более одной инструкции. Этот метод предоставляет флаг для ограничения адресов отладки одной инструкцией.

 Одна инструкция может иметь несколько отладочных адресов, как в случае с шаблонами.

## <a name="see-also"></a>См. также
- [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)
- [GetAddressesFromPosition](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromposition.md)
- [IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md)
