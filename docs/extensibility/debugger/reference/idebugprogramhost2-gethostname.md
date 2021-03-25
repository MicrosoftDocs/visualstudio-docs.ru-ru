---
description: Возвращает заголовок, понятное имя или имя файла ведущего процесса этой программы.
title: 'IDebugProgramHost2:: @ HostName | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramHost2::GetHostName
helpviewer_keywords:
- IDebugProgramHost2::GetHostName
ms.assetid: 48bbb089-e59a-471a-9965-24b42a8dabf3
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 53b4d69be1ea24f5c240b6247539f499c9fb00fb
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105084016"
---
# <a name="idebugprogramhost2gethostname"></a>IDebugProgramHost2::GetHostName
Возвращает заголовок, понятное имя или имя файла ведущего процесса этой программы.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetHostName( 
   DWORD dwType,
   BSTR* pbstrHostName
);
```

```csharp
int GetHostName( 
   uint dwType,
   out string pbstrHostName
);
```

## <a name="parameters"></a>Параметры
`dwType`\
окне Значение из перечисления [GETHOSTNAME_TYPE](../../../extensibility/debugger/reference/gethostname-type.md) .

`pbstrHostName`\
заполняет Возвращает запрошенное имя ведущего процесса.

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Remarks
 В обычной реализации этого метода `dwType` параметр игнорируется, и возвращается понятное имя хост-компьютера. Другой возможной реализацией является передача `dwType` параметра в вызов метода- [HostName](../../../extensibility/debugger/reference/idebugprogramnode2-gethostname.md) для получения имени.

## <a name="see-also"></a>См. также
- [IDebugProgramHost2](../../../extensibility/debugger/reference/idebugprogramhost2.md)
- [GetHostName](../../../extensibility/debugger/reference/idebugprogramnode2-gethostname.md)
