---
description: Эта структура используется для задания сведений Жустмикоде для модуля.
title: JMC_CODE_SPEC | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- JMC_CODE_SPEC
helpviewer_keywords:
- JMC_CODE_SPEC structure
ms.assetid: d89498f1-4234-46d9-b4e2-abbcbca5068a
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d9bb05d55268d3f0ef497831616b8e27aae4bb86
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105058083"
---
# <a name="jmc_code_spec"></a>JMC_CODE_SPEC
Эта структура используется для задания сведений Жустмикоде для модуля.

## <a name="syntax"></a>Синтаксис

```cpp
typedef struct _JMC_CODE_SPEC {
    BOOL fIsUserCode;
    BSTR bstrModuleName;
} JMC_CODE_SPEC;
```

```csharp
public struct JMC_CODE_SPEC {
    public int    fIsUserCode;
    public string bstrModuleName;
};
```

## <a name="members"></a>Участники
`fIsUserCode`\
Ненулевое значение ( `TRUE` ), если модуль должен считаться пользовательским кодом; в противном случае — нуль ( `FALSE` ), если модуль должен обрабатываться как внешний код, а не для отладки.

`bstrModuleName`\
Имя рассматриваемого модуля.

## <a name="remarks"></a>Remarks
Эта структура передается в качестве списка таких структур в метод [сетжустмикодестате](../../../extensibility/debugger/reference/idebugengine3-setjustmycodestate.md) .

## <a name="requirements"></a>Требования
Заголовок: мсдбг. h

Пространство имен: Microsoft. VisualStudio. Debugger. Interop

Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Структуры и объединения](../../../extensibility/debugger/reference/structures-and-unions.md)
- [SetJustMyCodeState](../../../extensibility/debugger/reference/idebugengine3-setjustmycodestate.md)
