---
title: Интеллисенсехостфлагс | Документация Майкрософт
description: Перечисление Интеллисенсехостфлагс указывает флаги узла IntelliSense. В этой статье описываются значения перечисления.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IntellisenseHostFlags
helpviewer_keywords:
- IntelliSense, IntellisenseHostFlags enumeration
- IntellisenseHostFlags enumeration
ms.assetid: 0930640b-eb84-48ef-a8f7-d4268f55c99c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 83a3911670a10710ad6ae5cd6496fb76af6c27bb
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105079141"
---
# <a name="intellisensehostflags"></a>IntelliSenseHostFlags
Указывает флаги узла IntelliSense.

## <a name="syntax"></a>Синтаксис

```cpp
enum IntellisenseHostFlags
{
    IHF_READONLYCONTEXT      = 0x00000001
    IHF_NOSEPARATESUBJECT    = 0x00000002
    IHF_SINGLELINESUBJECT    = 0x00000004
    IHF_FORCECOMMITTOCONTEXT = 0x00000008
    IHF_OVERTYPE             = 0x00000010
};
```

### <a name="parameters"></a>Параметры

|Элементы|Описание|
|-------------|-----------------|
|`IHF_READONLYCONTEXT`|Буфер контекста доступен только для чтения.|
|`IHF_NOSEPARATESUBJECT`|Нет текста темы. Буфер контекста содержит IntelliSense-Target (подразумевается `!IHF_READONLYCONTEXT` ).|
|`IHF_SINGLELINESUBJECT`|Текст темы не поддерживает несколько строк.|
|`IHF_FORCECOMMITTOCONTEXT`|Эквивалентно `CanCommitIntoReadOnlyBuffer`.|
|`IHF_OVERTYPE`|Редактирование (в теме или контексте) должно выполняться в режиме переввода.|

## <a name="requirements"></a>Требования
 Синглефилидитор. idl

## <a name="see-also"></a>См. также
- <xref:Microsoft.VisualStudio.TextManager.Interop>
