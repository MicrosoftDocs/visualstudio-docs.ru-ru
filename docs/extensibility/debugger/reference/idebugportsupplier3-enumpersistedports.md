---
description: Этот метод извлекает объект, позволяющий перечислить список сохраненных портов.
title: 'IDebugPortSupplier3:: Енумперсистедпортс | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortSupplier3::EnumPersistedPorts
helpviewer_keywords:
- IDebugPortSupplier3::EnumPersistedPorts
ms.assetid: 1c3dead3-5d6c-4067-8418-4015f0b0dd07
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 582849f0dd859d5155b4d3ee5653cefff6396780
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102150423"
---
# <a name="idebugportsupplier3enumpersistedports"></a>IDebugPortSupplier3::EnumPersistedPorts
Этот метод извлекает объект, позволяющий перечислить список сохраненных портов.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT EnumPersistedPorts(
   BSTR_ARRAY         PortNames,
   IEnumDebugPorts2** ppEnum
);
```

```csharp
int EnumPersistedPorts(
   BSTR_ARRAY           PortNames,
   out IEnumDebugPorts2 ppEnum
);
```

## <a name="parameters"></a>Параметры
`PortNames`\
окне Структура [BSTR_ARRAY](../../../extensibility/debugger/reference/bstr-array.md) , содержащая список имен портов для поиска и возврата между постоянными портами. Будут возвращены только сохраненные порты с этими именами.

`ppEnum`\
заполняет Объект, реализующий интерфейс [IEnumDebugPorts2](../../../extensibility/debugger/reference/ienumdebugports2.md) .

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Комментарии
 Сохраненные порты загружаются при создании экземпляра поставщика порта и сохраняются при уничтожении поставщика порта.

## <a name="see-also"></a>См. также раздел
- [IDebugPortSupplier3](../../../extensibility/debugger/reference/idebugportsupplier3.md)
- [IEnumDebugPorts2](../../../extensibility/debugger/reference/ienumdebugports2.md)
- [BSTR_ARRAY](../../../extensibility/debugger/reference/bstr-array.md)
