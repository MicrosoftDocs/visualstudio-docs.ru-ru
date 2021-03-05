---
description: Содержит дополнительные свойства для объекта System. Threading. Tasks. Task.
title: Класс Континжентпропертиес — внутренние элементы | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- ContingentProperties class [.NET Framework debug engines]
- debug engines, ContingentProperties class [.NET Framework]
ms.assetid: c49d1362-ab1c-4b6d-9950-fcae40e0e66b
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 2303318c7a5f36027ce7709c5b09b5846fc6fab6
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102154981"
---
# <a name="contingentproperties-class---internal-members"></a>Класс Континжентпропертиес — внутренние элементы
Содержит дополнительные свойства <xref:System.Threading.Tasks.Task> объекта.

 **Пространство имен:** <xref:System.Threading.Tasks?displayProperty=fullName>

 **Сборка:** mscorlib (в mscorlib.dll)

 Так как вы не можете получить доступ к этим внутренним членам из платформа .NET Framework, на стандартном промежуточном языке (CIL) приведен следующий синтаксис.

## <a name="syntax"></a>Синтаксис

```csharp
.class auto ansi nested assembly beforefieldinit ContingentProperties
       extends System.Object
```

## <a name="members"></a>Члены

### <a name="fields"></a>Поля

|name|Описание|
|----------|-----------------|
|[m_children](../../extensibility/debugger/m-children-field.md)|Список дочерних задач, зарегистрированных в этой задаче.|

## <a name="remarks"></a>Комментарии
 Платформа .NET Framework инициализирует поля этого класса только в том случае, если они необходимы.

## <a name="see-also"></a>См. также раздел
- [Внутренние модули параллельного расширения для платформа .NET Framework](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)
