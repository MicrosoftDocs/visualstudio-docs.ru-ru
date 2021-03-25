---
description: Задает значение свойства из заданной строки.
title: 'IDebugProperty2:: Сетвалуеасстринг | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty2::SetValueAsString
helpviewer_keywords:
- IDebugProperty2::SetValueAsString
ms.assetid: 9e6a5054-41b7-4223-b509-b93689d366a5
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1e3a80c6d5c6e9f3b7f5d9b68ed08dd0b39d940e
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105064744"
---
# <a name="idebugproperty2setvalueasstring"></a>IDebugProperty2::SetValueAsString
Задает значение свойства из заданной строки.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT SetValueAsString ( 
   LPCOLESTR pszValue,
   UINT      nRadix,
   DWORD     dwTimeout
);
```

```csharp
int SetValueAsString ( 
   string pszValue,
   uint   nRadix,
   uint   dwTimeout
);
```

## <a name="parameters"></a>Параметры
`pszValue`\
окне Строка, содержащая значение, которое должно быть задано.

`nRadix`\
окне Основание системы счисления, используемое для интерпретации любой числовой информации. Это значение может быть равно 0, чтобы автоматически определить основание системы счисления.

`dwTimeout`\
окне Указывает максимальное время ожидания (в миллисекундах) перед возвратом из этого метода. Используйте `INFINITE` для бесконечного ожидания.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает `S_OK` ; в противном случае возвращает код ошибки. В следующей таблице показаны другие возможные значения.

|Значение|Описание|
|-----------|-----------------|
|`E_SETVALUE_VALUE_CANNOT_BE_SET`|Не удалось преобразовать строку в значение свойства, или не удалось задать значение свойства.|
|`E_SETVALUE_VALUE_IS_READONLY`|свойство доступно только для чтения.|

## <a name="see-also"></a>См. также
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
