---
description: Этот метод получает обновление изменения и продолжения (ENC) для этой программы.
title: 'IDebugProgram2:: Жетенкупдате | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::GetENCUpdate
helpviewer_keywords:
- IDebugProgram2::GetENCUpdate
ms.assetid: 9832aac8-6320-4fd8-91dd-2a0852febb00
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 6d6b60c8b17a8db1420222a7242164ce1c0eedd1
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105075930"
---
# <a name="idebugprogram2getencupdate"></a>IDebugProgram2::GetENCUpdate
Этот метод получает обновление изменения и продолжения (ENC) для этой программы. Пользовательский обработчик отладки всегда возвращает `E_NOTIMPL`.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetENCUpdate( 
   IUnknown** ppUpdate
);
```

```csharp
int GetENCUpdate(
   out object ppUpdate
);
```

## <a name="parameters"></a>Параметры
`ppUpdate`\
заполняет Возвращает внутренний интерфейс, который может использоваться для обновления этой программы.

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

> [!NOTE]
> Пользовательский модуль отладки должен всегда возвращать значение `E_NOTIMPL` .

## <a name="see-also"></a>См. также
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
