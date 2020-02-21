---
title: 'IDiaStackWalkHelper:: get_registerValue | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkHelper2::get_registerValue method
ms.assetid: 46ac5eee-73a3-44a1-8635-6c58ba193cb6
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bfb3e219012effe47a2352f7c22c6cf51b4617f9
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2019
ms.locfileid: "72741408"
---
# <a name="idiastackwalkhelperget_registervalue"></a>IDiaStackWalkHelper::get_registerValue
Возвращает значение регистра.

## <a name="syntax"></a>Синтаксис

```C++
HRESULT get_registerValue ( 
   DWORD      index,
   ULONGLONG* pRetVal
);
```

#### <a name="parameters"></a>Параметры
 `index`

окне Значение из перечисления [перечисления CV_HREG_e](../../debugger/debug-interface-access/cv-hreg-e.md) , указывающее, из какого регистра получить значение.

 `pRetVal`

заполняет Возвращает текущее значение регистра.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает `S_OK`; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Заметки
 Несмотря на размер параметра `pRetVal`, реализация должна хранить только то, что обычно имеет регистр. Например, 8-разрядный регистр содержит только самые низкие 8-разрядные биты заданного значения. Это 8-разрядное значение увеличивается до 64 бит при возврате из этого метода.

## <a name="see-also"></a>См. также
- [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)
- [Перечисление CV_HREG_e](../../debugger/debug-interface-access/cv-hreg-e.md)