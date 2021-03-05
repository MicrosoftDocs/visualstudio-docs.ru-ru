---
description: Получает расширенные сведения для свойства.
title: 'IDebugProperty2:: Жетекстендединфо | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty2::GetExtendedInfo
helpviewer_keywords:
- IDebugProperty2::GetExtendedInfo
ms.assetid: 0c9c0b2b-7540-4424-adb5-fce7aa37a026
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 004c7d545dbaaa20016fd94febe999420305fc7a
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102171503"
---
# <a name="idebugproperty2getextendedinfo"></a>IDebugProperty2::GetExtendedInfo
Получает расширенные сведения для свойства.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetExtendedInfo ( 
   REFGUID* guidExtendedInfo,
   VARIANT* pExtendedInfo
);
```

```csharp
int GetExtendedInfo ( 
   ref Guid guidExtendedInfo,
   out object pExtendedInfo
);
```

## <a name="parameters"></a>Параметры
`guidExtendedInfo`\
окне Идентификатор GUID, определяющий тип извлекаемой расширенной информации. Дополнительные сведения см. в разделе "Примечания".

`pExtendedInfo`\
заполняет Возвращает `VARIANT` (C++) или объект (C#), который можно использовать для получения сведений о расширенных свойствах. Например, этот параметр может возвращать `IUnknown` интерфейс, для которого можно запросить интерфейс [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md) . Дополнительные сведения см. в разделе "Примечания".

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает `S_OK` ; в противном случае возвращает код ошибки. Возвращает, `S_GETEXTENDEDINFO_NO_EXTENDEDINFO` Если расширенные сведения для извлечения отсутствуют.

## <a name="remarks"></a>Комментарии
 Этот метод существует для получения сведений, которые не извлекаются при вызове метода [GetPropertyInfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) .

 Следующие идентификаторы GUID обычно распознаются этим методом (значения GUID указаны для C#, так как имя недоступно в какой-либо сборке). Дополнительные идентификаторы GUID можно создать для внутреннего использования.

|Имя|Идентификатор GUID|Описание|
|----------|----------|-----------------|
|гуиддокумент|{3f98de84-fee9-11d0-b47f-00a0244a1dd2}|Возвращает `IUnknown` интерфейс в документ. Как правило, интерфейс [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md) можно получить из этого `IUnknown` интерфейса.|
|гуидкодеконтекст|{e2fc65e-56ce-11d1-b528-00aax004a8797}|Возвращает `IUnknown` интерфейс в контекст документа. Как правило, интерфейс [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) можно получить из этого `IUnknown` интерфейса.|
|гуидкустомвиеверсуппортед|{d9c9da31-ffbe-4eeb-9186-23121e3c088c}|Возвращает строку, содержащую идентификатор CLSID пользовательского средства просмотра, обычно реализуемый средством оценки выражений.|
|гуидекстендединфослот|{6df235ad-82c6-4292-9c97-7389770bc42f}|Возвращает 32-разрядное число, представляющее требуемый номер слота, если это свойство представляет локальный адрес управляемого кода.|
|гуидекстендединфосигнатуре|{b5fb6d46-f805-417f-96a3-8ba737073ffd}|Возвращает строку, содержащую сигнатуру переменной, связанной с объектом свойства.|

## <a name="see-also"></a>См. также раздел
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md)
- [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)
