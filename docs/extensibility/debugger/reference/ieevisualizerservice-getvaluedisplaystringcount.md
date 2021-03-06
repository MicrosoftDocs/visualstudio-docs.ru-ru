---
description: Извлекает количество строк значений, отображаемых для указанного свойства или поля.
title: 'Иивисуализерсервице:: Жетвалуедисплайстрингкаунт | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IEEVisualizerService::GetValueDisplayStringCount
- GetValueDisplayStringCount
ms.assetid: d683a833-fbfb-4042-84df-6905124a268a
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b77e2537e7581bb15f6458b4515d407fcfa1f827
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102222852"
---
# <a name="ieevisualizerservicegetvaluedisplaystringcount"></a>IEEVisualizerService::GetValueDisplayStringCount
Извлекает количество строк значений, отображаемых для указанного свойства или поля.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetValueDisplayStringCount (
   DWORD         displayKind,
   IDebugField * propertyOrField,
   ULONG *       pcelt
);
```

```csharp
int GetValueDisplayStringCount (
   uint        displayKind,
   IDebugField propertyOrField,
   out ulong   pcelt
);
```

## <a name="parameters"></a>Параметры
`displayKind`\
окне Значение из перечисления [дисплайкинд](../../../extensibility/debugger/reference/displaykind.md) .

`propertyOrField`\
окне Интерфейс [идебугфиелд](../../../extensibility/debugger/reference/idebugfield.md) , представляющий свойство или поле.

`pcelt`\
заполняет Возвращает число отображаемых строк значений.

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="see-also"></a>См. также раздел
- [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md)
