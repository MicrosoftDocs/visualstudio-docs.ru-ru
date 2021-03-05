---
description: Задает корень реестра для модуля отладки (DE).
title: 'IDebugEngine2:: Сетрегистрирут | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine2::SetRegistryRoot
helpviewer_keywords:
- IDebugEngine2::SetRegistryRoot
ms.assetid: d0d81202-8a4a-4bc3-b297-30a047c5ec60
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 01d43d2891b4ffb6257dfe0a367971022ebb1f99
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102153902"
---
# <a name="idebugengine2setregistryroot"></a>IDebugEngine2::SetRegistryRoot
Задает корень реестра для модуля отладки (DE).

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT SetRegistryRoot( 
   LPCOLESTR pszRegistryRoot
);
```

```csharp
int SetRegistryRoot( 
   string pszRegistryRoot
);
```

## <a name="parameters"></a>Параметры
`pszRegistryRoot`\
окне Используемый корень реестра.

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Комментарии
 Этот метод позволяет [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] указать альтернативный корень реестра, который должен использоваться параметром de для получения параметров реестра, например "HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp".

## <a name="see-also"></a>См. также раздел
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
