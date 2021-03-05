---
description: Этот метод запрашивает указанное значение свойства процесса отладки.
title: 'Идебугпроцесскуерипропертиес:: Куерипроперти | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugProcessQueryProperties::QueryProperty
ms.assetid: 9a91707d-a590-44ef-b122-69d9816a7a79
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c18c1abb4946fd207ea859b0f36dd93348126c51
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102166233"
---
# <a name="idebugprocessquerypropertiesqueryproperty"></a>IDebugProcessQueryProperties::QueryProperty
Этот метод запрашивает указанное значение свойства процесса отладки.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT QueryProperty(
   PROCESS_PROPERTY_TYPE  dwPropType,
   VARIANT               *pvarPropValue);
```

```csharp
int QueryProperty(
   enum_PROCESS_PROPERTY_TYPE dwPropType,
   out object                 pvarPropValue);
```

## <a name="parameters"></a>Параметры
`dwPropType`\
окне Определение запрошенного свойства. Значения качества производительности:

- PROCESS_PROPERTY_COMMAND_LINE = 1

- PROCESS_PROPERTY_CURRENT_DIRECTORY = 2

- PROCESS_PROPERTY_ENVIRONMENT_VARIABLES = 3

`pvarPropValue`\
[out] Значение свойства.

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Комментарии
 Этот метод редко используется.

## <a name="see-also"></a>См. также раздел
- [IDebugProcessQueryProperties](../../../extensibility/debugger/reference/idebugprocessqueryproperties.md)
