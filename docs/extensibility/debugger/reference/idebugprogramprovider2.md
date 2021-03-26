---
description: Этот зарегистрированный интерфейс позволяет диспетчеру отладки сеансов (SDM) получать сведения о программах, опубликованных с помощью интерфейса IDebugProgramPublisher2.
title: IDebugProgramProvider2 | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramProvider2
helpviewer_keywords:
- IDebugProgramProvider2 interface
ms.assetid: a9ec7b3e-a59c-4069-b2ee-6f45916eeb78
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 5bead60e23c708d8a23fcd382b4db0f3f9f7e4c1
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105065246"
---
# <a name="idebugprogramprovider2"></a>IDebugProgramProvider2
Этот зарегистрированный интерфейс позволяет диспетчеру отладки сеансов (SDM) получать сведения о программах, опубликованных через интерфейс [IDebugProgramPublisher2](../../../extensibility/debugger/reference/idebugprogrampublisher2.md) .

## <a name="syntax"></a>Синтаксис

```
IDebugProgramProvider2 : IUnknown
```

## <a name="notes-for-implementers"></a>Примечания для разработчиков
Модуль отладки (DE) реализует этот интерфейс для предоставления сведений о отлаживаемой программе. Этот интерфейс регистрируется в разделе DE реестра с использованием метрики `metricProgramProvider` , как описано в [вспомогательных средствах SDK для отладки](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md).

## <a name="notes-for-callers"></a>Примечания для вызывающих объектов
Вызовите `CoCreateInstance` функцию COM с помощью `CLSID` поставщика программы, полученного из реестра. См. пример.

## <a name="methods-in-vtable-order"></a>Методы в порядке vtable

|Метод|Описание|
|------------|-----------------|
|[GetProviderProcessData](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md)|Получение сведений о выполняющихся и фильтруемых программах различными способами.|
|[GetProviderProgramNode](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprogramnode.md)|Возвращает узел программы по указанному ИДЕНТИФИКАТОРу процесса.|
|[WatchForProviderEvents](../../../extensibility/debugger/reference/idebugprogramprovider2-watchforproviderevents.md)|Устанавливает обратный вызов для отслеживания событий поставщика, связанных с определенными видами процессов.|
|[Pragma](../../../extensibility/debugger/reference/idebugprogramprovider2-setlocale.md)|Устанавливает языковой стандарт для всех зависящих от языка ресурсов, необходимых для DE.|

## <a name="remarks"></a>Remarks
Как правило, процесс использует этот интерфейс, чтобы узнать о программах, выполняющихся в этом процессе.

## <a name="requirements"></a>Требования
Заголовок: мсдбг. h

Пространство имен: Microsoft. VisualStudio. Debugger. Interop

Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="example"></a>Пример

```cpp
IDebugProgramProvider2 *GetProgramProvider(GUID *pDebugEngineGuid)
{
    // This is typically defined globally. For this example, it is
    // defined here.
    static const WCHAR strRegistrationRoot[] = L"Software\\Microsoft\\VisualStudio\\8.0Exp";
    IDebugProgramProvider2 *pProvider = NULL;
    if (pDebugEngineGuid != NULL) {
        CLSID clsidProvider = { 0 };
        ::GetMetric(NULL,
                    metrictypeEngine,
                    *pDebugEngineGuid,
                    metricProgramProvider,
                    &clsidProvider,
                    strRegistrationRoot);
        if (!IsEqualGUID(clsidProvider,GUID_NULL)) {
            CComPtr<IDebugProgramProvider2> spProgramProvider;
            spProgramProvider.CoCreateInstance(clsidProvider);
            if (spProgramProvider != NULL) {
                pProvider = spProgramProvider.Detach();
            }
        }
    }
    return(pProvider);
}
```

## <a name="see-also"></a>См. также
- [Основные интерфейсы](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgramPublisher2](../../../extensibility/debugger/reference/idebugprogrampublisher2.md)
- [Вспомогательные пакеты SDK для отладки](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)
