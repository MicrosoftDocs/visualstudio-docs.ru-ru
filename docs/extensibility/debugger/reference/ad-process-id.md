---
description: Указывает идентификатор процесса, который может быть либо системным ИДЕНТИФИКАТОРом, либо идентификатором GUID.
title: AD_PROCESS_ID | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- AD_PROCESS_ID
helpviewer_keywords:
- AD_PROCESS_ID union
ms.assetid: 4cb40d12-2e92-4f09-83f4-689928bd65b3
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 479a30c85fe16830d49c3d44dc2daea4eed9f31c
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105094488"
---
# <a name="ad_process_id"></a>AD_PROCESS_ID
Указывает идентификатор процесса, который может быть либо системным ИДЕНТИФИКАТОРом, либо идентификатором GUID.

## <a name="syntax"></a>Синтаксис

```cpp
typedef struct _AD_PROCESS_ID {
    AD_PROCESS_ID_TYPE ProcessIdType;
    union {
        DWORD dwProcessId; 
        GUID  guidProcessId; 
        DWORD dwUnused; 
    } ProcessId;
} AD_PROCESS_ID;
```

```csharp
public struct AD_PROCESS_ID {
    AD_PROCESS_ID_TYPE ProcessIdType;
    DWORD              dwProcessId; 
    GUID               guidProcessId; 
    DWORD              dwUnused; 
};
```

## <a name="members"></a>Участники
`ProcessIdType`\
Значение из перечисления [AD_PROCESS_ID_TYPE](../../../extensibility/debugger/reference/ad-process-id-type.md) , указывающее способ интерпретации `ProcessId` объединения (или для управляемого кода, к которому необходимо получить доступ).

`dwProcessId`\
Идентификатор процесса в виде значения из системы.

`guidProcessId`\
Идентификатор процесса в виде идентификатора GUID.

Заполнение Двунусед.

## <a name="remarks"></a>Remarks
Эта структура передается следующим методам:

- [GetProviderProgramNode](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprogramnode.md)

- [WatchForProviderEvents](../../../extensibility/debugger/reference/idebugprogramprovider2-watchforproviderevents.md)

- [GetProviderProcessData](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md)

- [GetProcess](../../../extensibility/debugger/reference/idebugport2-getprocess.md)

И возвращается из следующих методов:

- [GetPhysicalProcessId](../../../extensibility/debugger/reference/idebugprocess2-getphysicalprocessid.md)

- [GetHostId](../../../extensibility/debugger/reference/idebugprogramhost2-gethostid.md)

## <a name="requirements"></a>Требования
Заголовок: мсдбг. h

Пространство имен: Microsoft. VisualStudio. Debugger. Interop

Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Структуры и объединения](../../../extensibility/debugger/reference/structures-and-unions.md)
- [GetProcess](../../../extensibility/debugger/reference/idebugport2-getprocess.md)
- [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md)
- [AD_PROCESS_ID_TYPE](../../../extensibility/debugger/reference/ad-process-id-type.md)
- [GetPhysicalProcessId](../../../extensibility/debugger/reference/idebugprocess2-getphysicalprocessid.md)
- [GetHostId](../../../extensibility/debugger/reference/idebugprogramhost2-gethostid.md)
- [GetProviderProgramNode](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprogramnode.md)
- [WatchForProviderEvents](../../../extensibility/debugger/reference/idebugprogramprovider2-watchforproviderevents.md)
- [GetProviderProcessData](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md)
