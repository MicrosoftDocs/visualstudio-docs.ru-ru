---
description: Извлекает список запущенных программ из указанного процесса.
title: 'IDebugProgramProvider2:: Жетпровидерпроцессдата | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramProvider2::GetProviderProcessData
helpviewer_keywords:
- IDebugProgramProvider2::GetProviderProcessData
ms.assetid: 90cf7b7f-53d2-487e-b793-94501a6e24dd
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ad388a552a34ebd49819987a20f4876193a96658
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105071484"
---
# <a name="idebugprogramprovider2getproviderprocessdata"></a>IDebugProgramProvider2::GetProviderProcessData
Извлекает список запущенных программ из указанного процесса.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetProviderProcessData(
   PROVIDER_FLAGS         Flags,
   IDebugDefaultPort2*    pPort,
   AD_PROCESS_ID          processId,
   CONST_GUID_ARRAY       EngineFilter,
   PROVIDER_PROCESS_DATA* pProcess
);
```

```csharp
int GetProviderProcessData(
   enum_PROVIDER_FLAGS     Flags,
   IDebugDefaultPort2      pPort,
   AD_PROCESS_ID           ProcessId,
   CONST_GUID_ARRAY        EngineFilter,
   PROVIDER_PROCESS_DATA[] pProcess
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
|`PFLAG_GET_PROGRAM_NODES`|Вызывающий объект запрашивает список узлов программ, которые должны быть возвращены.|

`pPort`\
окне Порт, на котором выполняется вызывающий процесс.

`processId`\
окне Структура [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) , содержащая идентификатор процесса, содержащего рассматриваемую программу.

`EngineFilter`\
окне Массив идентификаторов GUID для модулей отладки, назначенных для отладки этого процесса (они будут использоваться для фильтрации фактически возвращаемых программ в зависимости от того, какие модули поддерживаются. Если не указать ни одного ядра, будут возвращены все программы).

`pProcess`\
заполняет Структура [PROVIDER_PROCESS_DATA](../../../extensibility/debugger/reference/provider-process-data.md) , которая заполняется запрашиваемой информацией.

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Remarks
 Этот метод обычно вызывается процессом для получения списка программ, выполняющихся в этом процессе. Возвращаемые сведения представляют собой список объектов [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) .

## <a name="see-also"></a>См. также
- [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)
- [IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md)
- [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md)
- [CONST_GUID_ARRAY](../../../extensibility/debugger/reference/const-guid-array.md)
- [PROVIDER_FLAGS](../../../extensibility/debugger/reference/provider-flags.md)
- [PROVIDER_PROCESS_DATA](../../../extensibility/debugger/reference/provider-process-data.md)
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
