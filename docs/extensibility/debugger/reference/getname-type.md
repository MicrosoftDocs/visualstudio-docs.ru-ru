---
description: Указывает тип имени извлекаемых файлов.
title: GETNAME_TYPE | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- GETNAME_TYPE
helpviewer_keywords:
- GETNAME_TYPE enumeration
ms.assetid: 2f9f1679-e9e8-4c9c-ac90-aa07bfe69914
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9811312188e63017e074d12be6dfa67ab6929aa6
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102162450"
---
# <a name="getname_type"></a>GETNAME_TYPE
Указывает тип имени извлекаемых файлов.

## <a name="syntax"></a>Синтаксис

```cpp
enum enum_GETNAME_TYPE {
    GN_NAME         = 0,
    GN_FILENAME     = 1,
    GN_BASENAME     = 2,
    GN_MONIKERNAME  = 3,
    GN_URL          = 4,
    GN_TITLE        = 5,
    GN_STARTPAGEURL = 6
};
typedef DWORD GETNAME_TYPE;
```

```csharp
public enum enum_GETNAME_TYPE {
    GN_NAME         = 0,
    GN_FILENAME     = 1,
    GN_BASENAME     = 2,
    GN_MONIKERNAME  = 3,
    GN_URL          = 4,
    GN_TITLE        = 5,
    GN_STARTPAGEURL = 6
};
```

## <a name="fields"></a>Поля
`GN_NAME`\
Указывает понятное имя документа или контекста.

`GN_FILENAME`\
Указывает полный путь к документу или контексту.

`GN_BASENAME`\
Указывает базовое имя файла вместо полного пути к документу или контексту.

`GN_MONIKERNAME`\
Задает уникальное имя документа или контекста в виде моникера.

`GN_URL`\
Указывает URL-имя документа или контекста.

`GN_TITLE`\
Указывает заголовок документа, если он существует.

`GN_STARTPAGEURL`\
Возвращает начальный URL-адрес страницы для процессов.

## <a name="remarks"></a>Комментарии
Эти значения передаются в качестве параметров [](../../../extensibility/debugger/reference/idebugdocument2-getname.md)в методы Name [, noreturn](../../../extensibility/debugger/reference/idebugdocumentcontext2-getname.md)и [Name](../../../extensibility/debugger/reference/idebugprocess2-getname.md) , чтобы указать тип возвращаемого имени.

## <a name="requirements"></a>Требования
Заголовок: мсдбг. h

Пространство имен: Microsoft. VisualStudio. Debugger. Interop

Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetName](../../../extensibility/debugger/reference/idebugdocument2-getname.md)
- [GetName](../../../extensibility/debugger/reference/idebugdocumentcontext2-getname.md)
- [GetName](../../../extensibility/debugger/reference/idebugprocess2-getname.md)
