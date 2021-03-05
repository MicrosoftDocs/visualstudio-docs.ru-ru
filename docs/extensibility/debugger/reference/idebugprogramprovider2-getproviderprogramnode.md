---
description: Извлекает узел программы для определенной программы.
title: 'IDebugProgramProvider2:: Жетпровидерпрограмноде | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramProvider2::GetProviderProgramNode
helpviewer_keywords:
- IDebugProgramProvider2::GetProviderProgramNode
ms.assetid: e62e8e83-acbb-4c52-aedf-ffbd4670db29
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9d672c5b8277e418efdde047c7a49bf5e05ec0be
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102167078"
---
# <a name="idebugprogramprovider2getproviderprogramnode"></a>IDebugProgramProvider2::GetProviderProgramNode
Извлекает узел программы для определенной программы.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetProviderProgramNode(
   PROVIDER_FLAGS       Flags,
   IDebugDefaultPort2*  pPort,
   AD_PROCESS_ID        processId,
   REFGUID              guidEngine,
   UINT64               programId,
   IDebugProgramNode2** ppProgramNode
);
```

```csharp
int GetProviderProgramNode(
   enum_PROVIDER_FLAGS    Flags,
   IDebugDefaultPort2     pPort,
   AD_PROCESS_ID          ProcessId,
   ref Guid               guidEngine,
   ulong                  programId,
   out IDebugProgramNode2 ppProgramNode
);
```

## <a name="parameters"></a>Параметры
`Flags`\
окне Сочетание флагов из перечисления [PROVIDER_FLAGS](../../../extensibility/debugger/reference/provider-flags.md) . Для этого вызова обычно используются следующие флаги:

|Flag|Описание|
|----------|-----------------|
|`PFLAG_REMOTE_PORT`|Вызывающий объект работает на удаленном компьютере.|
|`PFLAG_DEBUGGEE`|Выполняется отладка вызывающего объекта (для каждого узла будет возвращена дополнительная информация о маршалинге).|
|`PFLAG_ATTACHED_TO_DEBUGGEE`|Вызывающий объект был подключен к, но не был запущен отладчиком.|

`pPort`\
окне Порт, на котором выполняется вызывающий процесс.

`processId`\
окне Структура [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) , содержащая идентификатор процесса, содержащего рассматриваемую программу.

`guidEngine`\
окне Идентификатор GUID модуля отладки, к которому присоединена программа (если она есть).

`programId`\
окне Идентификатор программы, для которой необходимо получить узел программы.

`ppProgramNode`\
заполняет Объект [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) , представляющий запрошенный узел программы.

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="see-also"></a>См. также раздел
- [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)
- [PROVIDER_FLAGS](../../../extensibility/debugger/reference/provider-flags.md)
- [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md)
- [IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md)
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
