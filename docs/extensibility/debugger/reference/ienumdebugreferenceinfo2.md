---
description: Этот интерфейс перечисляет структуры DEBUG_REFERENCE_INFO.
title: IEnumDebugReferenceInfo2 | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugReferenceInfo2
helpviewer_keywords:
- IEnumDebugReferenceInfo2
ms.assetid: 7ed01441-686f-4032-8268-a4c750f19f85
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 89dd664d7b54ce451c2d3a303b3da1c7ad2b13e8
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102224178"
---
# <a name="ienumdebugreferenceinfo2"></a>IEnumDebugReferenceInfo2
Этот интерфейс перечисляет структуры [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) .

## <a name="syntax"></a>Синтаксис

```
IEnumDebugReferenceInfo2 : IUnknown
```

## <a name="notes-for-implementers"></a>Примечания для разработчиков
 Модуль отладки (DE) реализует этот интерфейс в рамках поддержки ссылок на объекты в памяти. Этот интерфейс должен быть реализован только в том случае, если поддерживаются ссылки.

## <a name="notes-for-callers"></a>Примечания для вызывающих объектов
 Visual Studio вызывает [енумчилдрен](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md) для получения этого интерфейса.

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
 В следующей таблице показаны методы `IEnumDebugReferenceInfo2` .

|Метод|Описание|
|------------|-----------------|
|[Вперед](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2-next.md)|Извлекает указанное число структур [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) в последовательности перечисления.|
|[Skip](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2-skip.md)|Пропускает указанное число структур [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) в последовательности перечисления.|
|[Сброс](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2-reset.md)|Сбрасывает последовательность перечислений в начало.|
|[Клонировать](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2-clone.md)|Создает перечислитель, который содержит то же состояние перечисления, что и текущий перечислитель.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2-getcount.md)|Возвращает число структур [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) в перечислителе.|

## <a name="remarks"></a>Комментарии
 Ссылка по сути является типом и адресом, а свойство — именем, типом и адресом. Ссылка сохраняется при условии, что объект, на который указывает ссылка, существует в памяти. Дополнительные сведения см. в разделе [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) .

## <a name="requirements"></a>Требования
 Заголовок: мсдбг. h

 Пространство имен: Microsoft. VisualStudio. Debugger. Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также раздел
- [Базовые интерфейсы](../../../extensibility/debugger/reference/core-interfaces.md)
- [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
- [EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md)
