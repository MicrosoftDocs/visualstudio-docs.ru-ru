---
description: Этот интерфейс позволяет подсистеме отладки (DE) или поставщикам пользовательских портов регистрировать программы для отладки.
title: IDebugProgramPublisher2 | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramPublisher2
helpviewer_keywords:
- IDebugProgramPublisher2 interface
ms.assetid: b1d17f63-7146-4076-a588-034cfc6858b9
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: c51fac369ed91f00c91482dd7069362d758b7346
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105065103"
---
# <a name="idebugprogrampublisher2"></a>IDebugProgramPublisher2
Этот интерфейс позволяет подсистеме отладки (DE) или поставщикам пользовательских портов регистрировать программы для отладки.

## <a name="syntax"></a>Синтаксис

```
IDebugProgramPublisher2 : IUnknown
```

## <a name="notes-for-implementers"></a>Примечания для разработчиков
Visual Studio реализует этот интерфейс для регистрации отлаживаемых программ, чтобы сделать их видимыми для отладки между несколькими процессами.

## <a name="notes-for-callers"></a>Примечания для вызывающих объектов
Вызовите `CoCreateInstance` функцию COM с `CLSID_ProgramPublisher` для получения этого интерфейса (см. пример). Поставщик DE или настраиваемого порта использует этот интерфейс для регистрации узлов программы, представляющих отлаживаемые программы.

## <a name="methods-in-vtable-order"></a>Методы в порядке vtable
Этот интерфейс реализует следующие методы.

|Метод|Описание|
|------------|-----------------|
|[PublishProgramNode](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogramnode.md)|Делает узел программы доступным для DEs и диспетчера отладки сеансов (SDM).|
|[UnpublishProgramNode](../../../extensibility/debugger/reference/idebugprogrampublisher2-unpublishprogramnode.md)|Удаляет узел программы, чтобы он стал недоступным.|
|[PublishProgram](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogram.md)|Делает программу доступной для DEs и SDM.|
|[UnpublishProgram](../../../extensibility/debugger/reference/idebugprogrampublisher2-unpublishprogram.md)|Удаляет программу, чтобы она больше не была доступна.|
|[SetDebuggerPresent](../../../extensibility/debugger/reference/idebugprogrampublisher2-setdebuggerpresent.md)|Задает флаг, указывающий на наличие отладчика.|

## <a name="remarks"></a>Remarks
Этот интерфейс делает доступными программы и узлы программ (то есть «публикует их») для использования алгоритмом DEs и диспетчером отладки сеансов (SDM). Для доступа к опубликованным программам и узлам программ используйте интерфейс [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md) . Это единственный способ, которым Visual Studio может распознать, что программа отлаживается.

## <a name="requirements"></a>Требования
Заголовок: мсдбг. h

Пространство имен: Microsoft. VisualStudio. Debugger. Interop

Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="example"></a>Пример
В этом примере показано, как создать экземпляр издателя программы и зарегистрировать узел программы. Это взято из руководства по [публикации узла программы](/previous-versions/bb161795(v=vs.90)).

```cpp
// This is how m_srpProgramPublisher is defined in the class definition:
// CComPtr<IDebugProgramPublisher2> m_srpProgramPublisher.

void CProgram::Start(IDebugEngine2 * pEngine)
{
    m_spEngine = pEngine;

    HRESULT hr = m_srpProgramPublisher.CoCreateInstance(CLSID_ProgramPublisher);
    if ( FAILED(hr) )
    {
        ATLTRACE("Failed to create the program publisher: 0x%x.", hr);
        return;
    }

    // Register ourselves with the program publisher. Note that
    // CProgram implements the IDebgProgramNode2 interface, hence
    // the static cast on "this".
    hr = m_srpProgramPublisher->PublishProgramNode(
        static_cast<IDebugProgramNode2*>(this));
    if ( FAILED(hr) )
    {
        ATLTRACE("Failed to publish the program node: 0x%x.", hr);
        m_srpProgramPublisher.Release();
        return;
    }

    ATLTRACE("Added program node.\n");
}
```

## <a name="see-also"></a>См. также
- [Основные интерфейсы](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)
