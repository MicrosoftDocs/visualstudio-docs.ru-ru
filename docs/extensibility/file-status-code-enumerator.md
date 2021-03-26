---
title: Перечислитель кода состояния файла | Документация Майкрософт
description: Перечислитель Сккстатус содержит постоянные значения, указывающие состояние файла в системе управления версиями и используемое Скккуеринфо и ПОПЛИСТФУНК.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- named constants, SccStatus enumerator
- source control plug-ins, file status enumeration
- SccStatus enumerator
- file status code enumerator
ms.assetid: 5c37876b-c83c-4ca1-837b-57cd465a879a
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: af2ff3293a55dc76925aedd7a029e1bfdd367186
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105074955"
---
# <a name="file-status-code-enumerator"></a>Перечислитель кода состояния файла
`SccStatus`Перечислитель содержит именованные постоянные значения, которые определяют состояние файла в системе управления версиями. Это перечисление используется [скккуеринфо](../extensibility/sccqueryinfo-function.md) и `POPLISTFUNC` функцией обратного вызова (Дополнительные сведения см. в разделе [поплистфунк](../extensibility/poplistfunc.md) ).

## <a name="syntax"></a>Синтаксис

```
enum SccStatus {
   SCC_STATUS_INVALID          = -1L,
   SCC_STATUS_NOTCONTROLLED    = 0x0000L,
   SCC_STATUS_CONTROLLED       = 0x0001L,
   SCC_STATUS_CHECKEDOUT       = 0x0002L,
   SCC_STATUS_OUTOTHER         = 0x0004L,
   SCC_STATUS_OUTEXCLUSIVE     = 0x0008L,
   SCC_STATUS_OUTMULTIPLE      = 0x0010L,
   SCC_STATUS_OUTOFDATE        = 0x0020L,
   SCC_STATUS_DELETED          = 0x0040L,
   SCC_STATUS_LOCKED           = 0x0080L,
   SCC_STATUS_MERGED           = 0x0100L,
   SCC_STATUS_SHARED           = 0x0200L,
   SCC_STATUS_PINNED           = 0x0400L,
   SCC_STATUS_MODIFIED         = 0x0800L,
   SCC_STATUS_OUTBYUSER        = 0x1000L
   SCC_STATUS_NOMERGE          = 0x2000L
   SCC_STATUS_RESERVED_1       = 0x4000L
   SCC_STATUS_RESERVED_2       = 0x8000L
};
```

## <a name="members"></a>Участники
 Не удалось получить состояние SCC_STATUS_INVALID; не полагайтесь на нее.

 Файл SCC_STATUS_NOTCONTROLLED не находится в системе управления версиями.

 Файл SCC_STATUS_CONTROLLED находится в системе управления версиями.

 SCC_STATUS_CHECKEDOUT извлечен текущим пользователем на локальном диске.

 Файл SCC_STATUS_OUTOTHER извлечен другим пользователем.

 Файл SCC_STATUS_OUTEXCLUSIVE извлечен в монопольном режиме.

 Файл SCC_STATUS_OUTMULTIPLE извлечен несколькими пользователями.

 SCC_STATUS_OUTOFDATE файл не является самым последним.

 Файл SCC_STATUS_DELETED был удален из проекта.

 Файл SCC_STATUS_LOCKED заблокирован; больше нет разрешенных версий.

 Файл SCC_STATUS_MERGED был объединен, но еще не исправлен или проверен.

 Файл SCC_STATUS_SHARED является общим для проектов.

 Файл SCC_STATUS_PINNED является общим для явной версии.

 SCC_STATUS_MODIFIED файл был изменен, поврежден или нарушен.

 Файл SCC_STATUS_OUTBYUSER извлечен текущим пользователем.

 Файл SCC_STATUS_NOMERGE не может быть объединен с и не должен быть сохранен перед ПОЛУЧЕНИЕм.

 SCC_STATUS_RESERVED_1 зарезервировано для внутреннего использования.

 SCC_STATUS_RESERVED_2 зарезервировано для внутреннего использования.

## <a name="see-also"></a>См. также
- [Подключаемые модули системы управления версиями](../extensibility/source-control-plug-ins.md)
- [SccQueryInfo](../extensibility/sccqueryinfo-function.md)
- [POPLISTFUNC](../extensibility/poplistfunc.md)
