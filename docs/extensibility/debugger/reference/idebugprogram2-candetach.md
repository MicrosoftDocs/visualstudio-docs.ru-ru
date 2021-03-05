---
description: Определяет, может ли модуль отладки (DE) отсоединяться от программы.
title: 'IDebugProgram2:: Кандетач | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::CanDetach
helpviewer_keywords:
- IDebugProgram2::CanDetach
ms.assetid: dcd9ab6c-49e5-447e-aa7c-89f571f4a052
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 69bd7950d5b0cb884b8f59ae309265a0273d0944
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102166077"
---
# <a name="idebugprogram2candetach"></a>IDebugProgram2::CanDetach
Определяет, может ли модуль отладки (DE) отсоединяться от программы.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT CanDetach(
   void
);
```

```csharp
int CanDetach();
```

## <a name="return-value"></a>Возвращаемое значение
 Если может отсоединиться, возвращает `S_OK` ; в противном случае возвращает код ошибки. Возвращает `S_FALSE` , если de не может отсоединиться от программы.

## <a name="see-also"></a>См. также раздел
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
