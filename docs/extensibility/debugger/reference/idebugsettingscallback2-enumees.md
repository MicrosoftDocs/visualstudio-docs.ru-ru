---
description: Перечисляет доступные средства оценки выражений по идентификаторам языка и поставщика.
title: 'IDebugSettingsCallback2:: Енумис | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugSettingsCallback2::EnumEEs
ms.assetid: 9f884c49-426f-461b-b547-9d909486e73f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 7606bd46587c7141bddea0c822f08459f2d262d9
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105075670"
---
# <a name="idebugsettingscallback2enumees"></a>IDebugSettingsCallback2::EnumEEs
Перечисляет доступные средства оценки выражений по идентификаторам языка и поставщика.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT EnumEEs(
   DWORD  celtBuffer,
   GUID*  rgguidLang,
   GUID*  rgguidVendor,
   DWORD* pceltEEs
);
```

```csharp
public int EnumEEs(
   uint       celtBuffer,
   ref Guid   rgguidLang,
   ref Guid   rgguidVendor,
   ref uint[] pceltEEs
);
```

## <a name="parameters"></a>Параметры
`celtBuffer`\
окне Число элементов в `pceltEEs` буфере.

`rgguidLang`\
[вход, выход] Уникальный идентификатор языка программирования.

`rgguidVendor`\
[вход, выход] Уникальный идентификатор поставщика.

`pceltEEs`\
[вход, выход] Массив средств оценки выражений.

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="see-also"></a>См. также
- [IDebugSettingsCallback2](../../../extensibility/debugger/reference/idebugsettingscallback2.md)
