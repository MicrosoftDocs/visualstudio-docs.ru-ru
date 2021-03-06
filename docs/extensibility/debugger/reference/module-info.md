---
description: Описывает конкретный модуль (DLL, EXE или сборку).
title: MODULE_INFO | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- MODULE_INFO
helpviewer_keywords:
- MODULE_INFO structure
ms.assetid: f2e06180-1ab3-4eb5-a428-7994cceb61b6
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 7d3fd390ca5491aa9dd3e97a0d820c8e02fd0147
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102222358"
---
# <a name="module_info"></a>MODULE_INFO
Описывает конкретный модуль (DLL, EXE или сборку).

## <a name="syntax"></a>Синтаксис

```cpp
typedef struct tagMODULE_INFO { 
   MODULE_INFO_FIELDS dwValidFields;
   BSTR               m_bstrName;
   BSTR               m_bstrUrl;
   BSTR               m_bstrVersion;
   BSTR               m_bstrDebugMessage;
   UINT64             m_addrLoadAddress;
   UINT64             m_addrPreferredLoadAddress;
   DWORD              m_dwSize;
   DWORD              m_dwLoadOrder;
   FILETIME           m_TimeStamp;
   BSTR               m_bstrUrlSymbolLocation;
   MODULE_FLAGS       m_dwModuleFlags;
} MODULE_INFO;
```

```csharp
public struct MODULE_INFO { 
   public uint     dwValidFields;
   public string   m_bstrName;
   public string   m_bstrUrl;
   public string   m_bstrVersion;
   public string   m_bstrDebugMessage;
   public ulong    m_addrLoadAddress;
   public ulong    m_addrPreferredLoadAddress;
   public uint     m_dwSize;
   public uint     m_dwLoadOrder;
   public FILETIME m_TimeStamp;
   public string   m_bstrUrlSymbolLocation;
   public uint     m_dwModuleFlags;
};
```

## <a name="members"></a>Члены
 `dwValidFields`\
 Сочетание флагов из перечисления [MODULE_INFO_FIELDS](../../../extensibility/debugger/reference/module-info-fields.md) , которое указывает, какие поля заполняются.

 `m_bstrName`\
 Имя модуля.

 `m_bstrUrl`\
 URL-адрес модуля.

 `m_bstrVersion`\
 Версия модуля.

 `m_bstrDebugMessage`\
 Необязательное сообщение о модуле, например "не удается загрузить символы".

 `m_addrLoadAddress`\
 Адрес загрузки модуля.

 `m_addrPreferredLoadAddress`\
 Предпочтительный адрес загрузки модуля.

 `m_dwSize`\
 Размер модуля.

 `m_dwLoadOrder`\
 Порядок загрузки модуля.

 `m_TimeStamp`\
 Время последнего изменения файла символов.

 `m_bstrUrlSymbolLocation`\
 Расположение файла символов (например, ". \\ "), указанного в модуле. Используется в качестве начального расположения для поиска символов для модуля.

 `m_dwModuleFlags`\
 Сочетание флагов из перечисления [MODULE_FLAGS](../../../extensibility/debugger/reference/module-flags.md) , которое описывает модуль.

## <a name="remarks"></a>Комментарии
 Эта структура передается в метод " [info](../../../extensibility/debugger/reference/idebugmodule2-getinfo.md) ", где он заполняется.

 Эта структура соответствует каждому модулю, указанному в окне **модули** .

## <a name="requirements"></a>Требования
 Заголовок: мсдбг. h

 Пространство имен: Microsoft. VisualStudio. Debugger. Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также раздел
- [Структуры и объединения](../../../extensibility/debugger/reference/structures-and-unions.md)
- [MODULE_INFO_FIELDS](../../../extensibility/debugger/reference/module-info-fields.md)
- [MODULE_FLAGS](../../../extensibility/debugger/reference/module-flags.md)
- [GetInfo](../../../extensibility/debugger/reference/idebugmodule2-getinfo.md)
