---
description: Указывает, что весь документ был уничтожен.
title: 'IDebugDocumentTextEvents2:: OnDestroy | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentTextEvents2::OnDestroy
helpviewer_keywords:
- IDebugDocumentTextEvents2::onDestroy
ms.assetid: 60e4689c-c899-4c14-9d18-96393b741e1f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 011be7f08f6af124dd78e082ce5cd0d38afe982b
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105066299"
---
# <a name="idebugdocumenttextevents2ondestroy"></a>IDebugDocumentTextEvents2::onDestroy
Указывает, что весь документ был уничтожен.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT onDestroy( 
   void 
);
```

```csharp
int onDestroy();
```

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="see-also"></a>См. также
- [IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md)
