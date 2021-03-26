---
description: Этот метод задает язык, в котором будет размещаться процесс.
title: 'IDebugProcess3:: Сесостингпроцесслангуаже | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess3::SetHostingProcessLanguage
helpviewer_keywords:
- IDebugProcess3::SetHostingProcessLanguage
ms.assetid: e42f33ed-f29c-4e45-92ce-ab504b72d77c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: bf0551ea8cd855ec301a4e0a4406aa2b1f909727
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105076541"
---
# <a name="idebugprocess3sethostingprocesslanguage"></a>IDebugProcess3::SetHostingProcessLanguage
Этот метод задает язык, в котором будет размещаться процесс. Этот язык затем может использоваться модулем отладки (DE) для загрузки соответствующего средства оценки выражений.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT SetHostingProcessLanguage(
   REFGUID guidLang
);
```

```csharp
int SetHostingProcessLanguage(
   ref Guid guidLang
);
```

## <a name="parameters"></a>Параметры
`guidLang`\
[входные] `GUID` языка, который должен использоваться DE. Укажите `GUID_NULL` (C++) или `Guid.Empty` (C#), чтобы параметр de использовал язык по умолчанию.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает `S_OK` ; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Remarks
- [Жесостингпроцесслангуаже](../../../extensibility/debugger/reference/idebugprocess3-gethostingprocesslanguage.md) можно использовать для получения текущего языкового параметра.

## <a name="see-also"></a>См. также
- [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)
- [GetHostingProcessLanguage](../../../extensibility/debugger/reference/idebugprocess3-gethostingprocesslanguage.md)
