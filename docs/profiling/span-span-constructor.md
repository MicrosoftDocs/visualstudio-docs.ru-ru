---
description: Инициализирует новый экземпляр класса span.
title: Конструктор span::span | Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- cvmarkersobj/Concurrency::diagnostic::span::span
helpviewer_keywords:
- Concurrency::diagnostic::span constructor
ms.assetid: 8b5578aa-5e5c-4ac7-87c7-ce87c4246e2c
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: fdffdc59b31f5f04817536769d9a712484e6cdd7
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102223866"
---
# <a name="spanspan-constructor"></a>Конструктор span::span

Инициализирует новый экземпляр класса `span`.

## <a name="syntax"></a>Синтаксис

```cpp
span(
   const marker_series& _Series,
   _In_ LPCTSTR _Format,
   ...
);
span(
   const marker_series& _Series,
   marker_importance _Importance,
   _In_ LPCTSTR _Format,
   ...
);
span(
   const marker_series& _Series,
   int _Category,
   _In_ LPCTSTR _Format,
   ...
);
span(
   const marker_series& _Series,
   marker_importance _Importance,
   int _Category,
   _In_ LPCTSTR _Format,
   ...
);
```

#### <a name="parameters"></a>Параметры

`_Series` Допустимый контекст набора маркеров.

`_Format` Строка составного формата, содержащая текст, перемежаемый нулями или другими элементами форматирования, которые соответствуют объектам в списке аргументов.

`_Importance` Уровень важности.

`_Category` Категория.

## <a name="requirements"></a>Требования

**Заголовок:** *cvmarkersobj.h*

**Пространство имен:** Concurrency::diagnostic

## <a name="see-also"></a>См. также

- [Класс span](../profiling/span-class.md)
