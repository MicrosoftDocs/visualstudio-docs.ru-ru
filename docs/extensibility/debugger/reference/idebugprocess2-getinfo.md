---
description: Возвращает описание процесса.
title: IDebugProcess2::/info | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess2::GetInfo
helpviewer_keywords:
- IDebugProcess2::GetInfo
ms.assetid: 46021dce-bb97-46c3-b0cc-e5b3b68acc35
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a6e6b8e0c14cee960d1991ae4f5a482f66e89465
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102169214"
---
# <a name="idebugprocess2getinfo"></a>IDebugProcess2::GetInfo
Возвращает описание процесса.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetInfo(
   PROCESS_INFO_FIELDS  Fields,
   PROCESS_INFO*        pProcessInfo
);
```

```csharp
int GetInfo(
   enum_PROCESS_INFO_FIELDS  Fields,
   PROCESS_INFO[]            pProcessInfo
);
```

## <a name="parameters"></a>Параметры
`Fields`\
окне Сочетание значений из перечисления [PROCESS_INFO_FIELDS](../../../extensibility/debugger/reference/process-info-fields.md) , которое указывает, какие поля `pProcessInfo` параметра должны быть заполнены.

`pProcessInfo`\
заполняет Структура [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md) , которая заполняется описанием процесса.

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="see-also"></a>См. также раздел
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
- [PROCESS_INFO_FIELDS](../../../extensibility/debugger/reference/process-info-fields.md)
- [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md)
