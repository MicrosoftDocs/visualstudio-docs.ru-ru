---
title: MACHINE_INFO_FIELDS | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- MACHINE_INFO_FIELDS
helpviewer_keywords:
- MACHINE_INFO_FIELDS enumeration
ms.assetid: 2d61d206-7d40-4df1-8c88-1b3c9c78821e
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 70d289315219fd6e49f528a5ec95d560191b5cc4
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99962071"
---
# <a name="machine_info_fields"></a>MACHINE_INFO_FIELDS
Указывает, какой тип сведений следует получить для конкретного компьютера.

## <a name="syntax"></a>Синтаксис

```cpp
enum enum_MACHINE_INFO_FIELDS { 
   MCIF_NAME  = 0x00000001,
   MCIF_FLAGS = 0x00000002,
   MCIF_ALL   = 0x00000003
};
typedef DWORD MACHINE_INFO_FIELDS;
```

```csharp
public enum enum_MACHINE_INFO_FIELDS { 
   MCIF_NAME  = 0x00000001,
   MCIF_FLAGS = 0x00000002,
   MCIF_ALL   = 0x00000003
};
```

## <a name="fields"></a>Поля
 `MCIF_NAME`\
 Инициализируйте или используйте `bstrName` поле в структуре.

 `MCIF_FLAGS`\
 Инициализируйте или используйте `Flags` поле в структуре.

 `MIF_ALL`\
 Инициализация или использование всех полей в структуре.

## <a name="remarks"></a>Remarks
 Эти значения передаются в метод [жетмачинеинфо](../../../extensibility/debugger/reference/idebugcoreserver2-getmachineinfo.md) , чтобы указать, какие члены структуры [MACHINE_INFO](../../../extensibility/debugger/reference/machine-info.md) должны быть инициализированы.

 Также используется в `Fields` члене `MACHINE_INFO` структуры для указания того, какие поля используются и являются допустимыми.

 Эти флаги можно сочетать с помощью побитовой операции `OR` .

## <a name="requirements"></a>Требования
 Заголовок: мсдбг. h

 Пространство имен: Microsoft. VisualStudio. Debugger. Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [MACHINE_INFO](../../../extensibility/debugger/reference/machine-info.md)
- [GetMachineInfo](../../../extensibility/debugger/reference/idebugcoreserver2-getmachineinfo.md)
