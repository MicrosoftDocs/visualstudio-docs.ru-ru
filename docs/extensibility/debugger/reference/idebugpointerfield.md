---
description: Этот интерфейс представляет тип указателя.
title: Идебугпоинтерфиелд | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPointerField
helpviewer_keywords:
- IDebugPointerField interface
ms.assetid: d51bd5b2-f18e-4e27-b4fb-e6f652fbf635
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 568e442f5294b3aaa4cd8c99d7bbd1f769581ca6
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105087747"
---
# <a name="idebugpointerfield"></a>IDebugPointerField
Этот интерфейс представляет тип указателя.

## <a name="syntax"></a>Синтаксис

```
IDebugPointerField : IDebugContainerField
```

## <a name="notes-for-implementers"></a>Примечания для разработчиков
 Поставщик символов реализует этот интерфейс для представления указателя.

## <a name="notes-for-callers"></a>Примечания для вызывающих объектов
 Используйте [QueryInterface](/cpp/atl/queryinterface) для получения этого интерфейса из интерфейса [идебугфиелд](../../../extensibility/debugger/reference/idebugfield.md) , если метод [Kind](../../../extensibility/debugger/reference/idebugfield-getkind.md) возвращает `FIELD_TYPE_POINTER` .

## <a name="methods-in-vtable-order"></a>Методы в порядке vtable
 Помимо методов в `IDebugField` `IDebugContainerField` интерфейсах и, этот интерфейс реализует следующий метод:

|Метод|Описание|
|------------|-----------------|
|[GetDereferencedField](../../../extensibility/debugger/reference/idebugpointerfield-getdereferencedfield.md)|Возвращает [идебугфиелд](../../../extensibility/debugger/reference/idebugfield.md) , описывающий цель указателя.|

## <a name="remarks"></a>Remarks
 В C/C++ указатель может быть контейнером, если он используется с нотацией массива. Например, `char *pString` `pString` имеет тип указателя на `char` . `pString[3]` имеет тип контейнера, который является указателем на `char` , ссылающийся на четвертый элемент этого контейнера.

## <a name="requirements"></a>Требования
 Заголовок: sh. h

 Пространство имен: Microsoft. VisualStudio. Debugger. Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Интерфейсы поставщика символов](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)
