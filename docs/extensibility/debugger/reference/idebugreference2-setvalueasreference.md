---
description: Задает значение ссылки из другой ссылки.
title: 'IDebugReference2:: Сетвалуеасреференце | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugReference2::SetValueAsReference
helpviewer_keywords:
- IDebugReference2::SetValueAsReference
ms.assetid: 94a545d2-16b9-45e9-b2e7-4e49ff90aad0
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c78da74368285c3dcfe06c13fdf8e665da0b7947
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105075787"
---
# <a name="idebugreference2setvalueasreference"></a>IDebugReference2::SetValueAsReference
Задает значение ссылки из другой ссылки. Зарезервировано для последующего использования.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT SetValueAsReference ( 
   IDebugReference2** rgpArgs,
   DWORD              dwArgCount,
   IDebugReference2*  pValue,
   DWORD              dwTimeout
);
```

```cpp
int SetValueAsReference ( 
   IDebugReference2[] rgpArgs,
   uint               dwArgCount,
   IDebugReference2   pValue,
   uint               dwTimeout
);
```

## <a name="parameters"></a>Параметры
`rgpArgs`\
окне Массив объектов [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) , используемый для определения способа установки эталонного значения.

`dwArgCount`\
окне Число ссылок в массиве.

`pValue`\
окне Объект [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) , из которого задается значение свойства.

`dwTimeout`\
окне Максимальное время ожидания (в миллисекундах) перед возвратом из этого метода. Используйте `INFINITE` для бесконечного ожидания.

## <a name="return-value"></a>Возвращаемое значение
 Всегда возвращает значение `E_NOTIMPL`.

## <a name="see-also"></a>См. также
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
