---
title: ОПТНАМЕЧАНЖЕПФН | Документация Майкрософт
description: Сведения о функции обратного вызова ОПТНАМЕЧАНЖЕПФН, которая передает изменения имен из подключаемого модуля системы управления версиями в интегрированную среду разработки Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- OPTNAMECHANGEPFN
helpviewer_keywords:
- OPTNAMECHANGEPFN callback function
ms.assetid: 147303f3-c7f1-438a-81b7-db891ea3d076
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 340012663ad7d21c0b5c2ef81283f5d780d6011c
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/25/2021
ms.locfileid: "112901530"
---
# <a name="optnamechangepfn"></a>OPTNAMECHANGEPFN
Это функция обратного вызова, указанная в вызове [скксетоптион](../extensibility/sccsetoption-function.md) (с использованием параметра `SCC_OPT_NAMECHANGEPFN` ) и используемая для передачи изменений имени, сделанных подключаемым модулем системы управления версиями, обратно в интегрированную среду разработки.

## <a name="signature"></a>Подпись

```cpp
typedef void (*OPTNAMECHANGEPFN)(
   LPVOID pvCallerData,
   LPCSTR pszOldName,
   LPCSTR pszNewName
);
```

## <a name="parameters"></a>Параметры
 пвкаллердата

окне Значение пользователя, указанное в предыдущем вызове [скксетоптион](../extensibility/sccsetoption-function.md) (параметр using `SCC_OPT_USERDATA` ).

 псзолднаме

окне Исходное имя файла.

 псзневнаме

окне Имя, в которое был переименован файл.

## <a name="return-value"></a>Возвращаемое значение
 Нет.

## <a name="remarks"></a>Remarks
 Если файл переименовывается во время операции системы управления версиями, подключаемый модуль системы управления версиями может уведомлять интегрированную среду разработки об изменении имени через этот обратный вызов.

 Если интегрированная среда разработки не поддерживает этот обратный вызов, она не будет вызывать [скксетоптион](../extensibility/sccsetoption-function.md) , чтобы указать его. Если подключаемый модуль не поддерживает этот обратный вызов, он будет возвращен `SCC_E_OPNOTSUPPORTED` из функции, `SccSetOption` когда интегрированная среда разработки попытается установить обратный вызов.

## <a name="see-also"></a>См. также
- [Функции обратного вызова, реализованные интегрированной средой разработки](../extensibility/callback-functions-implemented-by-the-ide.md)
- [SccSetOption](../extensibility/sccsetoption-function.md)
