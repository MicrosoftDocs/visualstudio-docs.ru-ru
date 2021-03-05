---
description: Извлекает сведения о компьютере, на котором выполняется отладчик.
title: 'IDebugWindowsComputerPort2:: Жеткомпутеринфо | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- GetComputerInfo
- IDebugWindowsComputerPort2::GetComputerInfo
ms.assetid: 654910b2-c239-44c8-92fc-317680a5672f
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 279de593e79629546f0a3a10fe8e329b4b6ec6af
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102227324"
---
# <a name="idebugwindowscomputerport2getcomputerinfo"></a>IDebugWindowsComputerPort2::GetComputerInfo
Извлекает сведения о компьютере, на котором выполняется отладчик.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetComputerInfo(
   COMPUTER_INFO * pInfo
);
```

```csharp
public int GetComputerInfo(
   out COMPUTER_INFO[] pInfo
);
```

## <a name="parameters"></a>Параметры
`pInfo`\
заполняет Ссылка на структуру, содержащую сведения о компьютере.

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="see-also"></a>См. также раздел
- [IDebugWindowsComputerPort2](../../../extensibility/debugger/reference/idebugwindowscomputerport2.md)
- [COMPUTER_INFO](../../../extensibility/debugger/reference/computer-info.md)
