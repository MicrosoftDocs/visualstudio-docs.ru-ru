---
description: Этот метод получает список псевдонимов из программы.
title: 'IDebugBinder3:: Жеталлалиасес | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBinder3::GetAllAliases
helpviewer_keywords:
- IDebugBinder3::GetAllAliases method
ms.assetid: 1f9ab2ee-2ab3-4a61-8b99-95dd7fdf3511
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 04e4f9887ff8cfa68ad4fd4b09d160e3ec2d1eaf
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105085173"
---
# <a name="idebugbinder3getallaliases"></a>IDebugBinder3::GetAllAliases
Этот метод получает список псевдонимов из программы.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetAllAliases(
   UINT          uRequest,
   IDebugAlias** ppAliases,
   UINT*         puFetched
);
```

```csharp
int GetAllAliases(
   uint          uRequest,
   IDebugAlias[] ppAliases,
   out uint      puFetched
);
```

## <a name="parameters"></a>Параметры
`uRequest`\
окне Максимальное число возвращаемых псевдонимов (задает длину массива, переданного в `ppAliases` ).

`ppAliases`\
[вход, выход] Массив для заполнения псевдонимами (если это значение NULL и `uRequest` равно 0, число возвращаемых псевдонимов будет возвращено `puFetched` ).

`puFetched`\
заполняет Возвращает число полученных псевдонимов.

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="see-also"></a>См. также
- [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)
