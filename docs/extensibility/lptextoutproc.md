---
title: ЛПТЕКСТАУТПРОК | Документация Майкрософт
description: Сведения о указателе на функцию ЛПТЕКСТАУТПРОК. В интегрированной среде разработки Visual Studio реализована функция для отображения ошибок и состояния.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- LPTEXTOUTPROC
helpviewer_keywords:
- SccMsgDataOnMessage structure
- SccMsgDataOnBeforeGetFile structure
- SccMsgDataIsCancelled structure
- LPTEXTOUTPROC callback function
- SccMsgDataOnAfterGetFile structure
ms.assetid: 2025c969-e3c7-4cf4-a5c5-099d342895ea
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: e014d72fb3ae2b691f4a6eed28f14ff21656ef64
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105073187"
---
# <a name="lptextoutproc"></a>LPTEXTOUTPROC

Когда пользователь выполняет операцию системы управления версиями в интегрированной среде разработки (IDE), подключаемый модуль системы управления версиями может захотеть передать сообщения об ошибке или состоянии, связанные с операцией. Подключаемый модуль может отображать собственные окна сообщений для этой цели. Однако для более простой интеграции подключаемый модуль может передавать строки в интегрированную среду разработки, которая затем отображает их в собственном виде для отображения сведений о состоянии. Механизмом для этого является `LPTEXTOUTPROC` указатель на функцию. В интегрированной среде разработки эта функция реализована (более подробно описывается ниже) для отображения ошибок и состояния.

Интегрированная среда разработки переводит в подключаемый модуль системы управления версиями указатель на функцию в качестве `lpTextOutProc` параметра при вызове [сккопенпрожект](../extensibility/sccopenproject-function.md). В ходе операции SCC, например, в середине вызова [сккжет](../extensibility/sccget-function.md) , включающего много файлов, подключаемый модуль может вызывать `LPTEXTOUTPROC` функцию, периодически передавая строки для вывода. Интегрированная среда разработки может отображать эти строки в строке состояния, в окне вывода или в отдельном окне сообщения, в зависимости от ситуации. При необходимости интегрированная среда разработки может отображать определенные сообщения с помощью кнопки **Отмена** . Это позволяет пользователю отменить операцию и дает интегрированной среде разработки возможность передавать эти сведения обратно в подключаемый модуль.

## <a name="signature"></a>Подпись
 Выходная функция интегрированной среды разработки имеет следующую сигнатуру:

```cpp
typedef LONG (*LPTEXTOUTPROC) (
   LPSTR display_string,
   LONG mesg_type
);
```

## <a name="parameters"></a>Параметры

display_string

Отображаемая текстовая строка. Эта строка не должна завершаться символом возврата каретки или перевода строки.

mesg_type

Тип сообщения. В следующей таблице перечислены поддерживаемые значения для этого параметра.

|Значение|Описание|
|-----------|-----------------|
|`SCC_MSG_INFO, SCC_MSG_WARNING, SCC_MSG_ERROR`|Сообщение считается сведениями, предупреждениями или ошибками.|
|`SCC_MSG_STATUS`|В сообщении отображается состояние и может отображаться в строке состояния.|
|`SCC_MSG_DOCANCEL`|Отправлено без строки сообщения.|
|`SCC_MSG_STARTCANCEL`|Начинает отображение кнопки **"Отмена"** .|
|`SCC_MSG_STOPCANCEL`|Останавливает отображение кнопки **"Отмена"** .|
|`SCC_MSG_BACKGROUND_IS_CANCELLED`|Запрашивает интегрированную среду разработки, если фоновая операция должна быть отменена: среда IDE возвращает `SCC_MSG_RTN_CANCEL` значение, если операция была отменена. в противном случае возвращает `SCC_MSG_RTN_OK` . `display_string`Параметр приводится к структуре [сккмсгдатаисканцеллед](#LinkSccMsgDataIsCancelled) , которая предоставляется подключаемым модулем системы управления версиями.|
|`SCC_MSG_BACKGROUND_ON_BEFORE_GET_FILE`|Сообщает интегрированной среде разработки о файле, прежде чем он будет извлечен из системы управления версиями. `display_string`Параметр приводится к структуре [сккмсгдатаонбефорежетфиле](#LinkSccMsgDataOnBeforeGetFile) , которая предоставляется подключаемым модулем системы управления версиями.|
|`SCC_MSG_BACKGROUND_ON_AFTER_GET_FILE`|Сообщает интегрированной среде разработки о файле после его получения из системы управления версиями. `display_string`Параметр приводится к структуре [сккмсгдатаонафтержетфиле](#LinkSccMsgDataOnAfterGetFile) , которая предоставляется подключаемым модулем системы управления версиями.|
|`SCC_MSG_BACKGROUND_ON_MESSAGE`|Сообщает интегрированной среде разработки о текущем состоянии фоновой операции. `display_string`Параметр приводится к структуре [сккмсгдатаонмессаже](#LinkSccMsgDataOnMessage) , которая предоставляется подключаемым модулем системы управления версиями.|

## <a name="return-value"></a>Возвращаемое значение

|Значение|Описание|
|-----------|-----------------|
|SCC_MSG_RTN_OK|Строка была отображена, или операция была успешно выполнена.|
|SCC_MSG_RTN_CANCEL|Пользователь хочет отменить операцию.|

## <a name="example"></a>Пример
 Предположим, что интегрированная среда разработки вызывает [сккжет](../extensibility/sccget-function.md) с двадцатью именами файлов. Подключаемый модуль системы управления версиями хочет предотвратить отмену операции в середине файла Get. После получения каждого файла он вызывает `lpTextOutProc` , передает ему сведения о состоянии для каждого файла и отправляет `SCC_MSG_DOCANCEL` сообщение, если у него нет состояния для отчета. Если в любой момент, когда подключаемый модуль получает возвращаемое значение `SCC_MSG_RTN_CANCEL` из интегрированной среды разработки, операция получения немедленно отменяется, поэтому файлы больше не извлекаются.

## <a name="structures"></a>Структуры

### <a name="sccmsgdataiscancelled"></a><a name="LinkSccMsgDataIsCancelled"></a> сккмсгдатаисканцеллед

```cpp
typedef struct {
   DWORD dwBackgroundOperationID;
} SccMsgDataIsCancelled;
```

 Эта структура отправляется вместе с `SCC_MSG_BACKGROUND_IS_CANCELLED` сообщением. Он используется для передачи идентификатора отмененной фоновой операции.

### <a name="sccmsgdataonbeforegetfile"></a><a name="LinkSccMsgDataOnBeforeGetFile"></a> сккмсгдатаонбефорежетфиле

```cpp
typedef struct {
   DWORD dwBackgroundOperationID;
   PCSTR szFile;
} SccMsgDataOnBeforeGetFile;
```

 Эта структура отправляется вместе с `SCC_MSG_BACKGROUND_ON_BEFORE_GET_FILE` сообщением. Он используется для сообщения имени извлекаемого файла и идентификатора фоновой операции, выполняющей извлечение.

### <a name="sccmsgdataonaftergetfile"></a><a name="LinkSccMsgDataOnAfterGetFile"></a> сккмсгдатаонафтержетфиле

```cpp
typedef struct {
   DWORD dwBackgroundOperationID;
   PCSTR szFile;
   SCCRTN sResult;
} SccMsgDataOnAfterGetFile;
```

 Эта структура отправляется вместе с `SCC_MSG_BACKGROUND_ON_AFTER_GET_FILE` сообщением. Он используется для передачи результата получения указанного файла, а также идентификатора фоновой операции, которая была извлечена. См. возвращаемые значения для [сккжет](../extensibility/sccget-function.md) , что может быть получено в результате.

### <a name="sccmsgdataonmessage"></a><a name="LinkSccMsgDataOnMessage"></a> сккмсгдатаонмессаже

```cpp
typedef struct {
   DWORD dwBackgroundOperationID;
   PCSTR szMessage;
   BOOL bIsError;
} SccMsgDataOnMessage;
```

 Эта структура отправляется вместе с `SCC_MSG_BACKGROUND_ON_MESSAGE` сообщением. Он используется для передачи текущего состояния фоновой операции. Состояние выражается в виде строки, отображаемой интегрированной средой разработки, и `bIsError` указывает серьезность сообщения ( `TRUE` для сообщения об ошибке, `FALSE` предупреждения или информационное сообщение). Также задается идентификатор фоновой операции, отправляющей состояние.

## <a name="code-example"></a>Пример кода
 Ниже приведен краткий пример вызова `LPTEXTOUTPROC` для отправки `SCC_MSG_BACKGROUND_ON_MESSAGE` сообщения, в котором показано, как выполнить приведение структуры для вызова.

```cpp
LONG SendStatusMessage(
    LPTEXTOUTPROC pTextOutProc,
    DWORD         dwBackgroundID,
    LPCTSTR       pStatusMsg,
    BOOL          bIsError)
{
    SccMsgDataOnMessage msgData = { 0 };
    LONG                result  = 0;

    msgData.dwBackgroundOperationID = dwBackgroundID;
    msgData.szMessage               = pStatusMsg;
    msgData.bIsError                = bIsError;

    result = pTextOutProc(reinterpret_cast<LPCTSTR>(&msgData), SCC_MSG_BACKGROUND_ON_MESSAGE);
    return result;
}
```

## <a name="see-also"></a>См. также
- [Функции обратного вызова, реализованные интегрированной средой разработки](../extensibility/callback-functions-implemented-by-the-ide.md)
- [Подключаемые модули системы управления версиями](../extensibility/source-control-plug-ins.md)
