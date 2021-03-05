---
description: Возвращает структуру DEBUG_PROPERTY_INFO, описывающую свойство.
title: 'IDebugProperty2:: GetPropertyInfo | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty2::GetPropertyInfo
helpviewer_keywords:
- IDebugProperty2::GetPropertyInfo
ms.assetid: 39d6e942-df72-4c84-a5d9-a386d112714c
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: deb8dbe5b055f42f21c087dcb2cc7a14e16858f9
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102166780"
---
# <a name="idebugproperty2getpropertyinfo"></a>IDebugProperty2::GetPropertyInfo
Возвращает структуру [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) , описывающую свойство.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetPropertyInfo ( 
   DEBUGPROP_INFO_FLAGS dwFields,
   DWORD                nRadix,
   DWORD                dwTimeout,
   IDebugReference2**   rgpArgs,
   DWORD                dwArgCount,
   DEBUG_PROPERTY_INFO* pPropertyInfo
);
```

```cpp
int GetPropertyInfo ( 
   enum_DEBUGPROP_INFO_FLAGS dwFields,
   uint                      nRadix,
   uint                      dwTimeout,
   IDebugReference2[]        rgpArgs,
   uint                      dwArgCount,
   DEBUG_PROPERTY_INFO[]     pPropertyInfo
);
```

## <a name="parameters"></a>Параметры
`dwFields`\
окне Сочетание значений из перечисления [DEBUGPROP_INFO_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md) , которое указывает, какие поля должны быть заполнены в `pPropertyInfo` структуре.

`nRadix`\
окне Основание системы счисления, используемое для форматирования любых числовых данных.

`dwTimeout`\
окне Указывает максимальное время ожидания (в миллисекундах) перед возвратом из этого метода. Используйте `INFINITE` для бесконечного ожидания.

`rgpArgs`\
[вход, выход] Зарезервировано для будущего использования; Задайте для значение null.

`dwArgCount`\
окне Зарезервировано для будущего использования; присвойте ему значение 0.

`pPropertyInfo`\
заполняет Структура [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) , которая заполняется описанием свойства.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает `S_OK` ; в противном случае возвращает код ошибки.

## <a name="see-also"></a>См. также раздел
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [DEBUGPROP_INFO_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md)
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
- [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)
