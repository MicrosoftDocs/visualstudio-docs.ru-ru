---
description: Возвращает имя индексатора по умолчанию.
title: 'Идебугклассфиелд:: Жетдефаултиндексер | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugClassField::GetDefaultIndexer
helpviewer_keywords:
- IDebugClassField::GetDefaultIndexer method
ms.assetid: 47ce4f45-3816-4b40-909c-5032d0692d75
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 8ce8a492ea4d45a54a295617d7863b0623fd6a87
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105088553"
---
# <a name="idebugclassfieldgetdefaultindexer"></a>IDebugClassField::GetDefaultIndexer
Возвращает имя индексатора по умолчанию.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetDefaultIndexer( 
   BSTR* pbstrIndexer
);
```

```csharp
int GetDefaultIndexer(
   out string pbstrIndexer
);
```

## <a name="parameters"></a>Параметры
`pbstrIndexer` заполняет Возвращает строку, содержащую имя индексатора по умолчанию.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает S_OK или возвращает значение S_FALSE, если индексатор по умолчанию отсутствует. В противном случае возвращается код ошибки.

## <a name="remarks"></a>Remarks
 Индексатором по умолчанию для класса является свойство, которое помечено как `Default` свойство для доступа к массиву. Это относится только к [!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)] . Ниже приведен пример индексатора по умолчанию, объявленного в [!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)] и его использования.

```vb
Imports System.Collections;

Public Class Class1
    Private myList as Hashtable

    Default Public Property Item(ByVal Index As Integer) As Integer
        Get
            Return CType(List(Index), Integer)
        End Get
        Set(ByVal Value As Integer)
            List(Index) = Value
        End Set
    End Property
End Class

Function GetItem(Index as Integer) as Integer
    Dim classList as Class1 = new Class1
    Dim value as Integer

    ' Access array through default indexer
    value = classList(2)

    ' Access array through explicit property
    value = classList.Item(2)

    Return value
End Function
```

## <a name="see-also"></a>См. также
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
