---
title: IManagedAddin::Unload
description: Вызывается непосредственно перед выгрузкой управляемой надстройки VSTO.
ms.date: 02/02/2017
ms.topic: interface
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Unload method
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: e45fd9e6385388b9c6bc32098cf59799618d511b
ms.sourcegitcommit: 8590cf6b3351e82827fd21159beefef0c02bf162
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/08/2021
ms.locfileid: "102469714"
---
# <a name="imanagedaddinunload"></a>IManagedAddin::Unload
  Вызывается непосредственно перед выгрузкой управляемой надстройки VSTO.

## <a name="syntax"></a>Синтаксис

```csharp
HRESULT Unload();
```

## <a name="return-value"></a>Возвращаемое значение
 Значение HRESULT, указывающее, успешно ли завершен метод.

## <a name="remarks"></a>Комментарии
 Этот метод не вызывается текущими версиями Microsoft Office. Этот метод зарезервирован для использования в будущем.

## <a name="see-also"></a>См. также раздел
- [Интерфейс IManagedAddin](../vsto/imanagedaddin-interface.md)
- [IManagedAddin::Load](../vsto/imanagedaddin-load.md)
