---
description: Этот метод определяет, устарело ли состояние "изменить и продолжить" данного объекта или родительского контейнера.
title: 'IDebugObject2:: Исенкаутдатед | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject2::IsEncOutdated
helpviewer_keywords:
- IDebugObject2::IsEncOutdated method
ms.assetid: d3a8c02d-895b-478c-9957-d663130f308e
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 583b77ed4f3fbfc81bb595ddde025b8c08f169dd
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102170020"
---
# <a name="idebugobject2isencoutdated"></a>IDebugObject2::IsEncOutdated
Этот метод определяет, устарело ли состояние "изменить и продолжить" данного объекта или родительского контейнера. Пользовательский оценщик выражений не реализует этот метод и всегда возвращает `E_NOTIMPL` .

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT IsEncOutdated(
   BOOL* pfEncOutdated
);
```

```csharp
int IsEncOutdated(
   out int pfEncOutdated
);
```

## <a name="parameters"></a>Параметры
`pfEncOutdated`\
заполняет Ненулевое значение ( `TRUE` ), если состояние "изменить и продолжить" устарело, ноль ( `FALSE` ), если нет.

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

> [!NOTE]
> Пользовательский оценщик выражений должен всегда возвращать значение `E_NOTIMPL` .

## <a name="see-also"></a>См. также раздел
- [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)
