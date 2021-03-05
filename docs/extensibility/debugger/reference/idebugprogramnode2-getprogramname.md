---
description: 'IDebugProgramNode2:: Жетпрограмнаме возвращает имя программы.'
title: 'IDebugProgramNode2:: Жетпрограмнаме | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramNode2::GetProgramName
helpviewer_keywords:
- IDebugProgramNode2::GetProgramName
ms.assetid: 510c7f5d-48ff-4d9f-ad79-fbad9f15239d
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 88a4bc58f5d91cdb52482f4dc862446cfc9e7eb1
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102161389"
---
# <a name="idebugprogramnode2getprogramname"></a>IDebugProgramNode2::GetProgramName
Возвращает имя программы.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetProgramName (
    BSTR* pbstrProgramName
);
```

```csharp
int GetProgramName (
    out string pbstrProgramName
);
```

## <a name="parameters"></a>Параметры
`pbstrProgramName`\
заполняет Возвращает имя программы.

## <a name="return-value"></a>Возвращаемое значение
Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Комментарии
Имя программы не совпадает с путем к программе, хотя имя программы может быть частью такого пути:.

## <a name="example"></a>Пример
В следующем примере показано, как реализовать этот метод для простого `CProgram` объекта, реализующего интерфейс [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) . `MakeBstr`Функция выделяет копию указанной строки в виде BSTR.

```cpp
HRESULT CProgram::GetProgramName(BSTR* pbstrProgramName) {
    if (!pbstrProgramName)
        return E_INVALIDARG;

    // Assign the member program name to the passed program name.
    *pbstrProgramName = MakeBstr(m_pszProgramName);
    return NOERROR;
}
```

## <a name="see-also"></a>См. также раздел
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
