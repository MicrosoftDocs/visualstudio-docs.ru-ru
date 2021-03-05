---
description: Этот интерфейс используется модулем отладки (DE) для отправки в Visual Studio сообщения, требующего от пользователя ответа.
title: IDebugMessageEvent2 | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMessageEvent2
helpviewer_keywords:
- IDebugMessageEvent2 interface
ms.assetid: a9ff3d00-e9ac-4cd6-bda9-584a4815aff8
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 9c84bf93a50ce9a5e530ebb7143d7b1c69f50360
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102172277"
---
# <a name="idebugmessageevent2"></a>IDebugMessageEvent2
Этот интерфейс используется модулем отладки (DE) для отправки в Visual Studio сообщения, требующего от пользователя ответа.

## <a name="syntax"></a>Синтаксис

```
IDebugMessageEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Примечания для разработчиков
 Метод DE реализует этот интерфейс для отправки сообщения в Visual Studio, требующего ответа пользователя. Интерфейс [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) должен быть реализован на том же объекте, что и этот интерфейс. Модель SDM использует [QueryInterface](/cpp/atl/queryinterface) для доступа к `IDebugEvent2` интерфейсу.

 Реализация этого интерфейса должна передавать вызов Visual Studio [сетреспонсе](../../../extensibility/debugger/reference/idebugmessageevent2-setresponse.md) в de. Например, это можно сделать с помощью сообщения, размещенного в потоке обработки сообщений DE, или объекта, реализующего этот интерфейс, может содержать ссылку на DE и обратный вызов в DE с ответом, переданным в `IDebugMessageEvent2::SetResponse` .

## <a name="notes-for-callers"></a>Примечания для вызывающих объектов
 Параметр DE создает и отправляет этот объект события для вывода сообщения пользователю, которому требуется ответ. Событие отправляется с помощью функции обратного вызова [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) , предоставляемой SDM при присоединении к отлаживаемой программе.

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
 В следующей таблице показаны методы `IDebugMessageEvent2` .

|Метод|Описание|
|------------|-----------------|
|[GetMessage](../../../extensibility/debugger/reference/idebugmessageevent2-getmessage.md)|Возвращает отображаемое сообщение.|
|[SetResponse](../../../extensibility/debugger/reference/idebugmessageevent2-setresponse.md)|Задает ответ, если он есть, из окна сообщения.|

## <a name="remarks"></a>Комментарии
 DE будет использовать этот интерфейс, если ему требуется определенный ответ от пользователя на определенное сообщение. Например, если после попытки удаленного подключения к программе в DE возвращается сообщение "доступ запрещен", программа отправит это сообщение в Visual Studio в `IDebugMessageEvent2` событии с стилем окна сообщения `MB_RETRYCANCEL` . Это позволяет пользователю повторить попытку или отменить операцию присоединения.

 Параметр DE указывает, как должно обрабатываться это сообщение, следуя соглашениям функции Win32 `MessageBox` (Дополнительные сведения см. в [AfxMessageBox](/cpp/mfc/reference/cstring-formatting-and-message-box-display#afxmessagebox) ).

 Используйте интерфейс [IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md) для отправки сообщений в Visual Studio, не требующих ответа от пользователя.

## <a name="requirements"></a>Требования
 Заголовок: мсдбг. h

 Пространство имен: Microsoft. VisualStudio. Debugger. Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также раздел
- [Базовые интерфейсы](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md)
