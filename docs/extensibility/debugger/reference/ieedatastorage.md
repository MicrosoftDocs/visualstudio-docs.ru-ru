---
title: Иидатастораже | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEEDataStorage
helpviewer_keywords:
- IEEDataStorage interface
ms.assetid: 704e932d-2325-410e-89c4-ce88c6ec19da
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: dbec27d262e43cb0fcdf8317725ad3c77a1817eb
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99966439"
---
# <a name="ieedatastorage"></a>IEEDataStorage
Этот интерфейс представляет массив байтов.

## <a name="syntax"></a>Синтаксис

```
IEEDataStorage : IUnknown
```

## <a name="notes-for-implementers"></a>Примечания для разработчиков
 Средство оценки выражений (EE) реализует этот интерфейс для представления массива байтов (используемый визуализаторами типов для извлечения и изменения данных через интерфейс [ипропертипроксеесиде](../../../extensibility/debugger/reference/ipropertyproxyeeside.md) ). EE обычно реализует этот интерфейс для поддержки визуализаторов внешних типов.

## <a name="notes-for-callers"></a>Примечания для вызывающих объектов
 Методы в `IPropertyProxyEESide` интерфейсе возвращают этот интерфейс. Вызовите [жетпропертипрокси](../../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md) , чтобы получить интерфейс [ипропертипроксеесиде](../../../extensibility/debugger/reference/ipropertyproxyeeside.md) . Вызовите [QueryInterface](/cpp/atl/queryinterface) в интерфейсе [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) , чтобы получить интерфейс [ипропертипроксипровидер](../../../extensibility/debugger/reference/ipropertyproxyprovider.md) .

## <a name="methods-in-vtable-order"></a>Методы в порядке vtable
 `IEEDataStorage`Интерфейс реализует следующие методы:

|Метод|Описание|
|------------|-----------------|
|[GetData](../../../extensibility/debugger/reference/ieedatastorage-getdata.md)|Извлекает указанное число байтов данных в указанный буфер.|
|[GetSize](../../../extensibility/debugger/reference/ieedatastorage-getsize.md)|Возвращает число доступных байтов данных.|

## <a name="remarks"></a>Remarks
 Этот интерфейс используется визуализатором типов для доступа к данным, удерживаемым конкретным объектом. Данные обрабатываются как массив байтов, что позволяет визуализатору типов манипулировать им любым способом, необходимым для представления пользователю.

 Пользовательское средство просмотра также может использовать этот интерфейс, если это необходимо, хотя обычно в пользовательском средстве просмотра используется пользовательский интерфейс [жетмеморибитес](../../../extensibility/debugger/reference/idebugproperty2-getmemorybytes.md) или [жетстрингчарс](../../../extensibility/debugger/reference/idebugproperty3-getstringchars.md) (для строковых данных).

## <a name="requirements"></a>Требования
 Заголовок: мсдбг. h

 Пространство имен: Microsoft. VisualStudio. Debugger. Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также раздел
- [Базовые интерфейсы](../../../extensibility/debugger/reference/core-interfaces.md)
- [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)
- [Визуализатор типов и пользовательское средство просмотра](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)
