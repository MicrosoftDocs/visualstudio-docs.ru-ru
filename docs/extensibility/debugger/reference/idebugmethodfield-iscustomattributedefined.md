---
description: Определяет, определен ли определенный настраиваемый атрибут.
title: 'Идебугмесодфиелд:: Искустоматтрибутедефинед | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMethodField::IsCustomAttributeDefined
helpviewer_keywords:
- IDebugMethodField::IsCustomAttributeDefined method
ms.assetid: 1b5d95a8-cc87-4acb-9e6a-3928f3632b7c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f7cd9e1ae31e893639b41537bb5b09323cc70ff9
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105081897"
---
# <a name="idebugmethodfieldiscustomattributedefined"></a>IDebugMethodField::IsCustomAttributeDefined
Определяет, определен ли определенный настраиваемый атрибут.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT IsCustomAttributeDefined( 
   LPCOLESTR pszCustomAttributeName
);
```

```csharp
int IsCustomAttributeDefined(
   [In] string pszCustomAttributeName
);
```

## <a name="parameters"></a>Параметры
`pszCustomAttributeName`\
окне Строка, содержащая имя настраиваемого атрибута для поиска.

## <a name="return-value"></a>Возвращаемое значение
 Возвращает S_OK, если для этого метода определен настраиваемый атрибут, в противном случае возвращает значение S_FALSE.

## <a name="see-also"></a>См. также
- [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)
