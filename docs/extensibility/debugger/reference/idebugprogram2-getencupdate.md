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
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 02446dba5450b89b769e773563f77cd6d8c1659f
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102159904"
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

## <a name="see-also"></a>См. также раздел
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
