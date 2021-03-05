---
description: Этот метод задает значение реестра, известное как метрика.
title: 'IDebugEngine2:: Сетметрик | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine2:::SetMetric
helpviewer_keywords:
- IDebugEngine2:::SetMetric
ms.assetid: dcda4972-c32e-4693-a0e1-25d5c58b9782
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 129067ab94c433b7c4b09e29c65d75df98ce6b68
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102153889"
---
# <a name="idebugengine2setmetric"></a>IDebugEngine2::SetMetric
Этот метод задает значение реестра, известное как метрика.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT SetMetric(
   LPCOLESTR pszMetric,
   VARIANT   varValue
);
```

```csharp
int SetMetric(
   string pszMetric,
   object varValue
);
```

## <a name="parameters"></a>Параметры
`pszMetric`\
окне Имя метрики.

`varValue`\
окне Указывает значение метрики.

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Комментарии
 Метрика — это значение реестра, используемое для изменения поведения модуля отладки или объявления поддерживаемой функциональности. Этот метод может перенаправить вызов в соответствующую форму [вспомогательных методов SDK для функции отладки](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) `SetMetric` .

## <a name="see-also"></a>См. также раздел
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
- [Вспомогательные пакеты SDK для отладки](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)
