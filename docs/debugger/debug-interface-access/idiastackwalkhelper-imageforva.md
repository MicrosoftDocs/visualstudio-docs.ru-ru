---
title: 'Идиастакквалкхелпер:: imageForVA | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkHelper::imageForVA method
ms.assetid: 8d4edabf-3c01-4fef-8b61-4779f3371067
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 609a9370181937323f2bc3e8ca0a0765cd1f4a12
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2019
ms.locfileid: "72741384"
---
# <a name="idiastackwalkhelperimageforva"></a>IDiaStackWalkHelper::imageForVA
Возвращает начало образа исполняемого объекта в памяти по заданному виртуальному адресу в пространстве памяти исполняемого файла.

## <a name="syntax"></a>Синтаксис

```C++
HRESULT imageForVA(
   ULONGLONG  vaContext,
   ULONGLONG *pvaImageStart
);
```

#### <a name="parameters"></a>Параметры
 `vaContext`

окне Виртуальный адрес, который находится где-то в пространстве исполняемого файла.

 `pvaImageStart`

заполняет Возвращает начальный виртуальный адрес образа исполняемого файла.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает `S_OK`; в противном случае возвращает код ошибки.

## <a name="see-also"></a>См. также
- [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)