---
title: 'Идиастакквалкер:: getEnumFrames2 | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalker2::getEnumFrames2 method
ms.assetid: 73196d3f-112c-4b3a-997b-7c6b815d4afc
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f6de78b5553719def2fd7ef9c6adb55e823aac34
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2019
ms.locfileid: "72741534"
---
# <a name="idiastackwalkergetenumframes2"></a>IDiaStackWalker::getEnumFrames2
Извлекает перечислитель кадров стека для определенного типа платформы.

## <a name="syntax"></a>Синтаксис

```C++

      HRESULT getEnumFrames2( 
   enum  CV_CPU_TYPE_e    cpuid,
   IDiaStackWalkHelper*   pHelper,
   IDiaEnumStackFrames**  ppEnum
);
```

#### <a name="parameters"></a>Параметры
 `cpuid`

окне Значение из перечисления [перечисления CV_CPU_TYPE_e](../../debugger/debug-interface-access/cv-cpu-type-e.md) , указывающее тип платформы.

 `pHelper`

окне Вспомогательный объект [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md) .

 `ppEnum`

заполняет Возвращает объект [идиаенумстаккфрамес](../../debugger/debug-interface-access/idiaenumstackframes.md) , содержащий список объектов [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md) .

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает `S_OK`; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Заметки
 Чтобы получить список кадров стека только для платформы x86, вызовите метод [идиастакквалкер:: жетенумфрамес](../../debugger/debug-interface-access/idiastackwalker-getenumframes.md) .

## <a name="see-also"></a>См. также
- [IDiaStackWalker](../../debugger/debug-interface-access/idiastackwalker.md)
- [Перечисление CV_CPU_TYPE_e](../../debugger/debug-interface-access/cv-cpu-type-e.md)
- [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)
- [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)
- [IDiaStackWalker::getEnumFrames](../../debugger/debug-interface-access/idiastackwalker-getenumframes.md)