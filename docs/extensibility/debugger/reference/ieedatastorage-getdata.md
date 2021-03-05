---
description: Извлекает указанное число байтов из объекта.
title: 'Иидатастораже:: GetData | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEEDataStorage::GetData
helpviewer_keywords:
- IEEDataStorage::GetData
ms.assetid: 4d384039-73d4-40b4-ace6-a2474c546397
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f28533ad07bc7626f1576ef4422d6d20725b9450
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102227311"
---
# <a name="ieedatastoragegetdata"></a>IEEDataStorage::GetData
Извлекает указанное число байтов из объекта.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetData(
   ULONG  dataSize,
   ULONG* sizeGotten,
   BYTE*  data
);
```

```csharp
int GetData(
   uint     dataSize,
   out uint sizeGotten,
   byte[]   data
);
```

## <a name="parameters"></a>Параметры
`dataSize`\
окне Число извлекаемых байтов ( `data` массив должен содержать по крайней мере это число байтов).

`sizeGotten`\
заполняет Возвращает число фактически извлеченных байтов.

`data`\
[вход, выход] Массив, в который заполняются запрошенные данные.

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Комментарии
 Этот метод рекомендуется использовать для извлечения всех байтов данных в локальный массив, так как в процессе извлечения невозможно пропускать байты. В этом случае параметр `dataSize` должен быть значением, возвращаемым методом метода [resize](../../../extensibility/debugger/reference/ieedatastorage-getsize.md) .

## <a name="see-also"></a>См. также раздел
- [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)
- [GetSize](../../../extensibility/debugger/reference/ieedatastorage-getsize.md)
