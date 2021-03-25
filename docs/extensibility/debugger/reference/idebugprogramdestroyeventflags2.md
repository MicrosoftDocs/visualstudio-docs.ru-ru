---
description: Позволяет подсистеме отладки переопределять поведение по умолчанию пользовательского интерфейса Visual Studio при завершении сеанса отладки.
title: IDebugProgramDestroyEventFlags2 | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugProgramDestroyEventFlags2 interface
ms.assetid: d384ff71-dc71-40b9-a871-801f8b6a3418
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 6cb54b3a88255f9102f617298ff23c3e117d3cdd
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105084237"
---
# <a name="idebugprogramdestroyeventflags2"></a>IDebugProgramDestroyEventFlags2
Позволяет подсистеме отладки переопределять поведение пользовательского интерфейса по умолчанию [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] при завершении сеанса отладки.

## <a name="syntax"></a>Синтаксис

```
IDebugProgramDestroyEventFlags2 : IUnknown
```

## <a name="notes-for-implementers"></a>Примечания для разработчиков
 Этот интерфейс реализуется механизмами отладки. Это полезно для узлов, которые могут создавать и уничтожать несколько программ в течение всего времени существования процесса.

## <a name="methods"></a>Методы
 В следующей таблице показаны методы `IDebugProgramDestroyEventFlags2` .

|Метод|Описание|
|------------|-----------------|
|[GetFlags](../../../extensibility/debugger/reference/idebugprogramdestroyeventflags2-getflags.md)|Получает флаги удаления программы.|

## <a name="remarks"></a>Remarks
 Поведение пользовательского интерфейса по умолчанию [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] — вернуться в режим конструктора после того, как все программы отправили событие уничтожения программы. Этот интерфейс позволяет механизму отладки изменить это поведение.

## <a name="requirements"></a>Требования
 Заголовок: Мсдбг. h

 Пространство имен: Microsoft. VisualStudio. Debugger. Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll
