---
description: Структура, идентифицирующая пользовательское средство просмотра или визуализатор типов.
title: DEBUG_CUSTOM_VIEWER | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DEBUG_CUSTOM_VIEWER
helpviewer_keywords:
- DEBUG_CUSTOM_VIEWER structure
ms.assetid: 8e0ef3f0-0107-48e8-a037-6e52b4c4ed9d
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 46133d2b2800977b0819835f578b04569c4f5ce8
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102151061"
---
# <a name="debug_custom_viewer"></a>DEBUG_CUSTOM_VIEWER
Структура, идентифицирующая пользовательское средство просмотра или визуализатор типов.

## <a name="syntax"></a>Синтаксис

```cpp
typedef struct tagDEBUG_CUSTOM_VIEWER {
    DWORD dwID;
    BSTR  bstrMenuName;
    BSTR  bstrDescription;
    GUID  guidLang;
    GUID  guidVendor;
    BSTR  bstrMetric;
} DEBUG_CUSTOM_VIEWER;
```

```csharp
public struct DEBUG_CUSTOM_VIEWER {
    public uint   dwID;
    public string bstrMenuName;
    public string bstrDescription;
    public Guid   guidLang;
    public Guid   guidVendor;
    public string bstrMetric;
};
```

## <a name="members"></a>Члены
`dwID`\
Идентификатор для различения нескольких средств просмотра или визуализаторов, реализованных одним из них `GUID` .

`bstrMenuName`\
Текст, который будет отображаться в раскрывающемся меню.

`bstrDescription`\
Описание пользовательского средства просмотра или визуализатора типов (если оно не используется, должно быть задано значение null).

`guidLang`\
Язык вычислителя выражений.

`guidVendor`\
Поставщик средства оценки выражений.

`bstrMetric`\
Метрика, в которой хранится пользовательское средство просмотра или визуализатор типов `CLSID` .

## <a name="remarks"></a>Комментарии
Список этой структуры возвращается путем вызова метода [жеткустомвиеверлист](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) (и, по расширению, метода [жеткустомвиеверлист](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md) ).

## <a name="requirements"></a>Требования
Заголовок: мсдбг. h

Пространство имен: Microsoft. VisualStudio. Debugger. Interop

Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также раздел
- [Структуры и объединения](../../../extensibility/debugger/reference/structures-and-unions.md)
- [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md)
- [GetCustomViewerList](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md)
