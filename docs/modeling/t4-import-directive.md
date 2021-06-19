---
title: Директива Import T4
description: Узнайте, что в текстовом шаблоне Visual Studio T4 Директива import позволяет ссылаться на элементы в другом пространстве имен, не указывая полное имя.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: d0d441ec5a62dfa5266a17a06ac8fe33941136c6
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2021
ms.locfileid: "112386323"
---
# <a name="t4-import-directive"></a>Директива Import T4

В блоках кода текстового шаблона T4 Visual Studio `import` директива позволяет ссылаться на элементы в другом пространстве имен, не указывая полное имя. Она эквивалентна директиве `using` в C# или `imports` в [!INCLUDE[vb_current_short](../debugger/includes/vb_current_short_md.md)].

Общие сведения о написании текстовых шаблонов T4 см. в разделе [написание текстового шаблона T4](../modeling/writing-a-t4-text-template.md).

## <a name="using-the-import-directive"></a>Использование директивы Import

```
<#@ import namespace="namespace" #>
```

 В этом примере в коде шаблона можно пропустить явное пространство имен для членов группы System.IO:

```
<#@ import namespace="System.IO" #>
<#
   string fileContent = File.ReadAllText("C:\x.txt"); // System.IO.File
#>
The file contains: <#=  fileContent #>
```

## <a name="standard-imports"></a>Стандартные импорты
 Следующее пространство имен импортируется автоматически, поэтому для него не нужно создавать директиву импорта:

- `System`

  Кроме того, при использовании пользовательской директивы процессор директив может импортировать некоторые пространства имен автоматически.

  Например, при создании шаблонов для доменного языка (DSL) не требуется создавать директивы импорта для следующих пространств имен:

- `Microsoft.VisualStudio.Modeling`

- Пространство имен DSL

## <a name="see-also"></a>См. также

- [Директива Assembly T4](../modeling/t4-assembly-directive.md)
