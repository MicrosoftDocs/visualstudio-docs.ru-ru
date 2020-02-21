---
title: IDiaStackWalkHelper::p ut_registerValue | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkHelper2::put_registerValue method
ms.assetid: 8f02ce54-ef59-455f-8aa6-dc26761c7aff
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 619ed78584a9fe897b19d6ac2ffd4c28838c61ab
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2019
ms.locfileid: "72741374"
---
# <a name="idiastackwalkhelperput_registervalue"></a>IDiaStackWalkHelper::put_registerValue
Задает значение регистра.

## <a name="syntax"></a>Синтаксис

```C++
HRESULT put_registerValue ( 
   DWORD     index,
   ULONGLONG NewVal
);
```

#### <a name="parameters"></a>Параметры
 `index`

окне Значение из перечисления [перечисления CV_HREG_e](../../debugger/debug-interface-access/cv-hreg-e.md) , указывающее регистр для записи.

 `NewVal`

окне Новое значение регистра.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает `S_OK`; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Заметки
 Несмотря на размер значения, реализация должна хранить только то, что обычно хранится регистр. Например, 8-разрядный регистр будет содержать только самые низкие 8-разрядные биты заданного значения.

## <a name="see-also"></a>См. также
- [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)
- [Перечисление CV_HREG_e](../../debugger/debug-interface-access/cv-hreg-e.md)