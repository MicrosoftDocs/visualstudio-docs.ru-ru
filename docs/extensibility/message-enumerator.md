---
title: Перечислитель сообщений | Документация Майкрософт
description: Члены этого перечислителя используются для функции ТЕКСТАУТПРОК, которая является функцией обратного вызова, предоставляемой интегрированной средой разработки при вызове Сккопенпрожект.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- message enumerator
- source control plug-ins, message enumeration
ms.assetid: 4a4faa0d-d352-40ea-a21d-c09ea286a8e1
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 113f9fe8470b718a219e967b41bc92ecab2cf3c8
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105063998"
---
# <a name="message-enumerator"></a>Перечислитель сообщений
Следующие флаги используются для `TEXTOUTPROC` функции, которая является функцией обратного вызова, предоставляемой интегрированной средой разработки при вызове [сккопенпрожект](../extensibility/sccopenproject-function.md) (Дополнительные сведения о функции обратного вызова см. в разделе [лптекстаутпрок](../extensibility/lptextoutproc.md) ).

 Если интегрированная среда разработки запрашивает отмену процесса, может появиться одно из сообщений об отмене. В этом случае подключаемый модуль системы управления версиями использует, `SCC_MSG_STARTCANCEL` чтобы задать отображение кнопки **Отмена** в интегрированной среде разработки. После этого можно отправить любой набор обычных сообщений. Если какой-либо из этих `SCC_MSG_RTN_CANCEL` операций возвращает, то подключаемый модуль завершает операцию и возвращает. Подключаемый модуль также периодически опрашивается, `SCC_MSG_DOCANCEL` чтобы определить, была ли отменена операция пользователем. По завершении всех операций или при отмене пользователем подключаемый модуль отправляется `SCC_MSG_STOPCANCEL` . `SCC_MSG_INFO`Типы, SCC_MSG_WARNING и SCC_MSG_ERROR используются для сообщений, которые отображаются в прокручиваемом списке сообщений. `SCC_MSG_STATUS` — Это специальный тип, который указывает, что текст должен отображаться в строке состояния или в временной области отображения. Он не будет постоянно отображаться в списке.

## <a name="syntax"></a>Синтаксис

```
enum { 
   SCC_MSG_RTN_CANCEL = -1, 
   SCC_MSG_RTN_OK = 0, 
   SCC_MSG_INFO = 1 
   SCC_MSG_WARNING, 
   SCC_MSG_ERROR, 
   SCC_MSG_STATUS, 
   SCC_MSG_DOCANCEL, 
   SCC_MSG_STARTCANCEL, 
   SCC_MSG_STOPCANCEL 
};
```

## <a name="members"></a>Участники
 SCC_MSG_RTN_CANCEL возвратить из обратного вызова для указания отмены.

 Чтобы продолжить, SCC_MSG_RTN_OK вернуться из обратного вызова.

 SCC_MSG_INFO сообщение является информационным.

 SCC_MSG_WARNING сообщение является предупреждением.

 SCC_MSG_ERROR сообщение является ошибкой.

 SCC_MSG_STATUS сообщение предназначено для строки состояния.

 SCC_MSG_DOCANCEL нет текста; Интегрированная среда разработки возвращает `SCC_MSG_RTN_OK` или `SCC_MSG_RTN_CANCEL` .

 SCC_MSG_STARTCANCEL начинает цикл отмены.

 SCC_MSG_STOPCANCEL останавливает цикл отмены.

## <a name="see-also"></a>См. также
- [Подключаемые модули системы управления версиями](../extensibility/source-control-plug-ins.md)
- [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)
