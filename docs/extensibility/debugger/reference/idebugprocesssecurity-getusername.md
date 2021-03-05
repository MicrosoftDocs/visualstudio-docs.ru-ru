---
description: Возвращает имя пользователя от поставщика порта.
title: 'Идебугпроцесссекурити:: имя_пользователя | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugProcessSecurity::GetUserName
ms.assetid: c73c60ac-da6e-45ae-8f04-95353a24ca3e
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 04ad8bf6ba572a1f9e14e26ef2ca37d021f6e3a0
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102166207"
---
# <a name="idebugprocesssecuritygetusername"></a>IDebugProcessSecurity::GetUserName
Возвращает имя пользователя от поставщика порта.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetUserName(
    BSTR *pbstrUserName
);
```

```csharp
int GetUserName (
    string pbstrUserName
);
```

## <a name="parameters"></a>Параметры
`pbstrUserName`\
заполняет Строка, содержащая имя пользователя.

## <a name="return-value"></a>Возвращаемое значение
 Если метод завершается успешно, возвращает значение `S_OK`. В противном случае возвращается код ошибки.

## <a name="remarks"></a>Комментарии
 `GetUserName` Возвращает имя пользователя, отображаемое в столбце **имя пользователя** диалогового окна **Присоединение к процессу** . Чтобы открыть диалоговое окно **Присоединение к процессу** , щелкните **присоединить к процессу** в меню **Сервис** в [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] интегрированной среде разработки (IDE).

## <a name="see-also"></a>См. также раздел
- [IDebugProcessSecurity](../../../extensibility/debugger/reference/idebugprocesssecurity.md)
