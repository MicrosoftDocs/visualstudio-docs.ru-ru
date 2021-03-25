---
description: Указывает способ интерпретации идентификатора процесса в структуре AD_PROCESS_ID.
title: AD_PROCESS_ID_TYPE | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- AD_PROCESS_ID_TYPE
helpviewer_keywords:
- AD_PROCESS_ID_TYPE enumeration
ms.assetid: 0aab80e9-285a-4697-94ac-c864d42a6aaa
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9ae50fc827debd540faa99c33e10ddd217fc691f
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105094566"
---
# <a name="ad_process_id_type"></a>AD_PROCESS_ID_TYPE
Указывает способ интерпретации идентификатора процесса в структуре [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) .

## <a name="syntax"></a>Синтаксис

```cpp
enum enum_AD_PROCESS_ID {
    AD_PROCESS_ID_SYSTEM = 0,
    AD_PROCESS_ID_GUID   = 1
};
typedef DWORD AD_PROCESS_ID_TYPE;
```

```csharp
public enum enum_AD_PROCESS_ID {
    AD_PROCESS_ID_SYSTEM = 0,
    AD_PROCESS_ID_GUID   = 1
};
```

## <a name="fields"></a>Поля
`AD_PROCESS_ID_SYSTEM`\
Идентификатор процесса является системным идентификатором. Используйте `ProcessId.dwProcessId` поле структуры [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) .

`AD_PROCESS_ID_GUID`\
Идентификатор процесса — это идентификатор GUID. Используйте `ProcessId.guidProcessId` поле `AD_PROCESS_ID` структуры.

## <a name="remarks"></a>Remarks
Используется для `ProcessIdType` элемента структуры [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) для идентификации типа идентификатора процесса, содержащегося в структуре. Определяет способ интерпретации `ProcessId` объединения в структуре.

## <a name="requirements"></a>Требования
Заголовок: мсдбг. h

Пространство имен: Microsoft. VisualStudio. Debugger. Interop

Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md)
