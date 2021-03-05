---
description: Получает байты пользовательских атрибутов с учетом имени настраиваемого атрибута.
title: 'IDebugCustomAttributeQuery2:: Жеткустоматтрибутебинаме | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCustomAttributeQuery2::GetCustomAttributeByName
helpviewer_keywords:
- IDebugCustomAttributeQuery2::GetCustomAttributeByName
ms.assetid: 7428dfeb-8929-41b2-9b99-cb343a86c02d
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 8c65abff050af7b7c34161cbca2594431cb119b5
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102150085"
---
# <a name="idebugcustomattributequery2getcustomattributebyname"></a>IDebugCustomAttributeQuery2::GetCustomAttributeByName
Получает байты пользовательских атрибутов с учетом имени настраиваемого атрибута.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetCustomAttributeByName( 
   LPCOLESTR pszCustomAttributeName,
   BYTE*     ppBlob,
   DWORD*    pdwLen
);
```

```csharp
int GetCustomAttributeByName(
   [In] string        pszCustomAttributeName,
   [In, Out] byte[]   ppBlob,
   [In, Out] ref uint pdwLen
);
```

## <a name="parameters"></a>Параметры
`pszCustomAttributeName`\
окне Строка, содержащая имя настраиваемого атрибута для поиска.

`ppBlob`\
[вход, выход] Массив, который заполняется байтами настраиваемого атрибута.

`pdwLen`\
[вход, выход] Указывает максимальное число байтов, возвращаемых в `ppBlob` массиве, и возвращает число байтов, фактически записанных в массив.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает S_OK или возвращает значение, S_FALSE, если пользовательский атрибут не существует. В противном случае возвращается код ошибки.

## <a name="remarks"></a>Комментарии
 Установите `ppBlob` для параметра значение null, чтобы получить количество доступных атрибутов в байтах. Затем выделите массив и передайте этот массив в `ppBlob` параметр.

 Байты атрибутов представляют необработанные данные настраиваемого атрибута.

 Если `ppBlob` `pdwLen` для параметров и задано значение null, этот метод можно использовать, чтобы определить, существует ли пользовательский атрибут. Однако проще альтернативой является вызов метода [искустоматтрибутедефинед](../../../extensibility/debugger/reference/idebugcustomattributequery2-iscustomattributedefined.md) .

## <a name="see-also"></a>См. также раздел
- [IDebugCustomAttributeQuery2](../../../extensibility/debugger/reference/idebugcustomattributequery2.md)
- [IsCustomAttributeDefined](../../../extensibility/debugger/reference/idebugcustomattributequery2-iscustomattributedefined.md)
