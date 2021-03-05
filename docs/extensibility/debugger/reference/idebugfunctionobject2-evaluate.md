---
description: 'IDebugFunctionObject2:: Evaluate вызывает функцию и возвращает результирующее значение в виде объекта.'
title: 'IDebugFunctionObject2:: Evaluate | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugFunctionObject2::Evaluate
ms.assetid: bc54c652-904b-4297-a6db-faa329684881
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 777553e1889e751cf84f6e4c58691e0c5f446648
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102166467"
---
# <a name="idebugfunctionobject2evaluate"></a>IDebugFunctionObject2::Evaluate
Вызывает функцию и возвращает результирующее значение в виде объекта.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT Evaluate (
   IDebugObject** ppParams,
   DWORD          dwParams,
   DWORD          dwEvalFlags,
   DWORD          dwTimeout,
   IDebugObject** ppResult
);
```

```csharp
int Evaluate (
   IDebugObject     ppParams,
   uint             dwParams,
   uint             dwEvalFlags,
   uint             dwTimeout,
   out IDebugObject ppResult
);
```

## <a name="parameters"></a>Параметры
`ppParams`\
окне Массив объектов [идебугобжект](../../../extensibility/debugger/reference/idebugobject.md) , представляющих входные параметры. Каждый из этих параметров был создан с помощью одного из методов create в этом интерфейсе.

`dwParams`\
окне Число параметров в `ppParams` массиве.

`dwEvalFlags`\
окне Сочетание флагов из перечисления [евалфлагс](../../../extensibility/debugger/reference/evalflags.md) , определяющее способ выполнения вычисления.

`dwTimeout`\
окне Указывает максимальное время ожидания (в миллисекундах) перед возвратом из этого метода. Используйте **бесконечность** для бесконечного ожидания.

`ppResult`\
заполняет Возвращает объект **идебугобжект** , представляющий значение функции в виде объекта.

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="see-also"></a>См. также раздел
- [IDebugFunctionObject2](../../../extensibility/debugger/reference/idebugfunctionobject2.md)
