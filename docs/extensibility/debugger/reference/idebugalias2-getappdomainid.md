---
description: Возвращает идентификатор для домена приложения.
title: 'IDebugAlias2:: Жетаппдомаинид | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- GetAppDomainId
- IDebugAlias2::GetAppDomainId
ms.assetid: 23581aaa-5a53-4859-b264-eca49fc44bcd
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ee1caec6968f9a67a15a31c8064b7795a37a6829
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105059110"
---
# <a name="idebugalias2getappdomainid"></a>IDebugAlias2::GetAppDomainId
Возвращает идентификатор для домена приложения.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetAppDomainId (
   ULONG32* pappDomainId
);
```

```csharp
int GetAppDomainId (
   out uint pappDomainId
);
```

## <a name="parameters"></a>Параметры
`pappDomainId`\
заполняет Возвращает идентификатор домена приложения.

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Remarks
 Идентификатор домена приложения изменяется при каждом перезапуске приложения и создании нового домена приложения.

## <a name="see-also"></a>См. также
- [IDebugAlias2](../../../extensibility/debugger/reference/idebugalias2.md)
