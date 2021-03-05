---
description: Задает или изменяет число проходов, связанных с этой привязанной точкой останова.
title: 'IDebugBoundBreakpoint2:: Сетпасскаунт | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBoundBreakpoint2::SetPassCount
helpviewer_keywords:
- SetPassCount method
- IDebugBoundBreakpoint2::SetPassCount method
ms.assetid: b32c12f9-b34d-43bd-a1b9-61af6cf8e51b
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ccefd1e3b120ac52801a1163ea8bda814626a0b9
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102167494"
---
# <a name="idebugboundbreakpoint2setpasscount"></a>IDebugBoundBreakpoint2::SetPassCount
Задает или изменяет число проходов, связанных с этой привязанной точкой останова.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT SetPassCount( 
   BP_PASSCOUNT bpPassCount
);
```

```csharp
int SetPassCount( 
   BP_PASSCOUNT bpPassCount
);
```

## <a name="parameters"></a>Параметры
`bpPassCount`\
окне Структура [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md) , указывающая число проходов.

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки. Возвращает `E_BP_DELETED` значение, если состояние привязанного объекта точки останова равно `BPS_DELETED` (часть перечисления [BP_STATE](../../../extensibility/debugger/reference/bp-state.md) ).

## <a name="remarks"></a>Комментарии
 Число проходов определяет время срабатывания точки останова. Текущий проход или число попаданий можно получить, вызвав метод [жеситкаунт](../../../extensibility/debugger/reference/idebugboundbreakpoint2-gethitcount.md) .

 Все счетчики пройденных, которые ранее были связаны с этой точкой останова, теряются.

## <a name="see-also"></a>См. также раздел
- [IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md)
- [GetHitCount](../../../extensibility/debugger/reference/idebugboundbreakpoint2-gethitcount.md)
- [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md)
- [BP_STATE](../../../extensibility/debugger/reference/bp-state.md)
