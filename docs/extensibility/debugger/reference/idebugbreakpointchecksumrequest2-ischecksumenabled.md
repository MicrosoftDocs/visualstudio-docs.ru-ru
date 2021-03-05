---
description: Определяет, включена ли контрольная сумма для этого документа.
title: 'IDebugBreakpointChecksumRequest2:: Исчекксуменаблед | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugBreakpointChecksumRequest2::IsChecksumEnabled
ms.assetid: 8b1853b5-745c-4cd6-88a9-ce0673971bb0
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 697ad612595b869d0f7b4836ffb15357b9a2e77f
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102143445"
---
# <a name="idebugbreakpointchecksumrequest2ischecksumenabled"></a>IDebugBreakpointChecksumRequest2::IsChecksumEnabled
Определяет, включена ли контрольная сумма для этого документа.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT IsChecksumEnabled(
   BOOL *pfChecksumEnabled
);
```

```csharp
public int IsChecksumEnabled(
   out int pfChecksumEnabled
);
```

## <a name="parameters"></a>Параметры
`pfChecksumEnabled`\
заполняет Возвращает значение TRUE, если контрольная сумма включена. в противном случае возвращает значение FALSE.

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="see-also"></a>См. также раздел
- [IDebugBreakpointChecksumRequest2](../../../extensibility/debugger/reference/idebugbreakpointchecksumrequest2.md)
