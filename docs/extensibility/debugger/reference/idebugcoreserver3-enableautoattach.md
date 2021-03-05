---
description: Включает автоматическое присоединение для указанных модулей отладки.
title: 'IDebugCoreServer3:: Енаблеаутоаттач | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCoreServer3::EnableAutoAttach
helpviewer_keywords:
- IDebugCoreServer3::EnableAutoAttach
ms.assetid: 06aa633b-263b-4e08-8844-9a52d5120b94
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 644d238db11c117b9068de8f7903361b9712f3aa
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102163152"
---
# <a name="idebugcoreserver3enableautoattach"></a>IDebugCoreServer3::EnableAutoAttach
Включает автоматическое присоединение для указанных модулей отладки.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT EnableAutoAttach(
   GUID*     rgguidSpecificEngines,
   DWORD     celtSpecificEngines,
   LPCOLESTR pszStartPageUrl,
   BSTR*     pbstrSessionId
);
```

```csharp
int EnableAutoAttach(
   Guid[]     rgguidSpecificEngines,
   uint       celtSpecificEngines,
   string     pszStartPageUrl,
   out string pbstrSessionId
);
```

## <a name="parameters"></a>Параметры
`rgguidSpecificEngines`\
окне Массив идентификаторов GUID для каждого модуля отладки, помечающий как автоматическое присоединение.

`celtSpecificEngines`\
окне Число ядер, указанное в `rgguidSpecificEngines` .

`pszStartPageUrl`\
окне Начальный URL-адрес, используемый при автоматическом присоединении.

`pbstrSessionID`\
заполняет Идентификатор сеанса, к которому был назначен автоматический вход.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает `S_OK` ; в противном случае возвращает код ошибки. Один код ошибки — `E_AUTO_ATTACH_NOT_REGISTERED` , который указывает, что фабрика класса автоматического подключения не зарегистрирована.

## <a name="remarks"></a>Комментарии
 При запуске программы, связанной с указанным URL-адресом, указанные модули отладки автоматически запускаются и присоединяются.

## <a name="see-also"></a>См. также раздел
- [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)
