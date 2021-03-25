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
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 0e3b78744d67183c368345af8c6c26e57edec8d1
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105058681"
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

## <a name="remarks"></a>Remarks
 При запуске программы, связанной с указанным URL-адресом, указанные модули отладки автоматически запускаются и присоединяются.

## <a name="see-also"></a>См. также
- [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)
