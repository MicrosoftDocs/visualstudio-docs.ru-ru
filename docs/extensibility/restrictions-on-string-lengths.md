---
title: Ограничения длины строк | Документация Майкрософт
description: Сведения об ограничениях длины строк, используемых различными функциями, накладываемых API подключаемого модуля системы управления версиями.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- source control plug-ins, restrictions on string lengths
ms.assetid: 877173d2-ca27-43b3-b1f4-8379f7c5e268
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 7fd0d88a50f64aee1f0bc5c273d7a3cd50c6f53f
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/25/2021
ms.locfileid: "112900256"
---
# <a name="restrictions-on-string-lengths"></a>Ограничения длины строк
Интерфейс API подключаемого модуля системы управления версиями ограничивает длину строк, используемых в различных функциях.

## <a name="string-length-values"></a>Значения длины строки

|Константа|Значение|
|--------------|-----------|
|`SCC_NAME_LEN`|31|
|`SCC_AUXLABEL_LEN`|31|
|`SCC_USER_LEN`|31|
|`SCC_PRJPATH_LEN`|300|

> [!NOTE]
> Длина не включает в себя завершение `null` . Другие константы с суффиксом "_SIZE" вместо "_LEN" включают пробел для завершения `null` .

|Константа|Значение|
|--------------|-----------|
|SCC_NAME_SIZE|32|
|SCC_AUXLABEL_SIZE|32|
|SCC_USER_SIZE|32|
|SCC_PRJPATH_SIZE|301|

## <a name="see-also"></a>См. также
- [Подключаемые модули системы управления версиями](../extensibility/source-control-plug-ins.md)
