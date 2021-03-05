---
description: Создает объект, использующий конструктор заданных параметров флагов оценки и значение времени ожидания.
title: 'IDebugFunctionObject2:: CreateObject | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugFunctionObject2::CreateObject
- CreateObject
ms.assetid: 148de615-941e-4b64-ab11-75b692aae465
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4cd5eb81972af35b84c688e34b8cbc285c4723c2
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102143146"
---
# <a name="idebugfunctionobject2createobject"></a>IDebugFunctionObject2::CreateObject
Создает объект, использующий конструктор заданных параметров флагов оценки и значение времени ожидания.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT CreateObject (
   IDebugFunctionObject* pConstructor,
   DWORD                 dwArgs,
   IDebugObject*         pArgs[],
   DWORD                 dwEvalFlags,
   DWORD                 dwTimeout,
   IDebugObject**        ppObject
);
```

```csharp
int CreateObject (
   IDebugFunctionObject pConstructor,
   uint                 dwArgs,
   IDebugObject[]       pArgs,
   uint                 dwEvalFlags,
   uint                 dwTimeout,
   out IDebugObject**   ppObject
);
```

## <a name="parameters"></a>Параметры
`pConstructor`\
окне Объект [идебугфунктионобжект](../../../extensibility/debugger/reference/idebugfunctionobject.md) , представляющий конструктор создаваемого объекта.

`dwArgs`\
окне Число параметров в `pArg` массиве. Представляет число параметров, передаваемых конструктору.

`pArgs`\
окне Массив объектов [идебугобжект](../../../extensibility/debugger/reference/idebugobject.md) , представляющих параметры, переданные конструктору.

`dwEvalFlags`\
окне Сочетание флагов из перечисления [евалфлагс](../../../extensibility/debugger/reference/evalflags.md) , определяющее способ выполнения вычисления.

`dwTimeout`\
окне Максимальное время ожидания (в миллисекундах) перед возвратом из этого метода. Используйте **бесконечность** для бесконечного ожидания.

`ppObject`\
заполняет Возвращает объект **идебугобжект** , представляющий только что созданный объект.

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Комментарии
 Вызовите этот метод, чтобы создать объект, представляющий экземпляр класса, или другой сложный тип, для которого требуется конструктор, который является параметром.

## <a name="see-also"></a>См. также раздел
- [IDebugFunctionObject2](../../../extensibility/debugger/reference/idebugfunctionobject2.md)
