---
title: 'IDiaFrameData:: Execute | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaFrameData::execute method
ms.assetid: 7a6c7d03-1ff1-4059-bd54-5f407eeebc26
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 88c9af8293dfc6a35e5f0e42d9596494d74b10aa
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2019
ms.locfileid: "72743685"
---
# <a name="idiaframedataexecute"></a>IDiaFrameData::execute
Выполняет очистку стека и возвращает результаты в интерфейсе кадра обхода стека.

## <a name="syntax"></a>Синтаксис

```C++
HRESULT execute ( 
   IDiaStackWalkFrame* frame
);
```

#### <a name="parameters"></a>Параметры
 `frame`

окне Объект [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md) , содержащий состояние регистров кадров.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает `S_OK`; в противном случае возвращает код ошибки. В следующей таблице показаны возможные возвращаемые значения для этого метода.

|значения|Описание|
|-----------|-----------------|
|E_DIA_INPROLOG|Невозможно выполнить кадр стека в коде пролога.|
|E_DIA_SYNTAX|Ошибка синтаксического анализа, обнаруженная в рамке программы.|
|E_DIA_FRAME_ACCESS|Не удается получить доступ к регистрам или памяти.|
|E_DIA_VALUE|Ошибка при вычислении значения (например, деление на ноль).|

## <a name="remarks"></a>Заметки
 Этот метод вызывается во время отладки для очистки стека. Объект [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md) реализуется клиентским приложением для получения обновлений регистров и для предоставления методов, используемых методом `execute`.

## <a name="see-also"></a>См. также
- [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)
- [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md)