---
description: Задает поставщик служб.
title: 'Идебугпортпиккер:: SetSite | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugPortPicker::SetSite
ms.assetid: 7319e187-adfe-4b3f-aec9-521356fb5a8a
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 8a442c438f233187265c90e724f57e8681b95556
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105072264"
---
# <a name="idebugportpickersetsite"></a>IDebugPortPicker::SetSite
Задает поставщик служб.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT SetSite(
   IServiceProvider * pSP
);
```

```csharp
public int SetSite(
   IServiceProvider pSP
);
```

## <a name="parameters"></a>Параметры
`pSP`\
окне Ссылка на интерфейс поставщика услуг.

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Remarks
 Этот метод будет вызываться до вызова любых других методов.

## <a name="see-also"></a>См. также
- [IDebugPortPicker](../../../extensibility/debugger/reference/idebugportpicker.md)
