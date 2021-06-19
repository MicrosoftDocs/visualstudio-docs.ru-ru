---
title: Создание текстового шаблона из текстового шаблона
description: Содержит сведения о создании текстового шаблона из другого текстового шаблона с помощью escape-последовательностей.
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, generating templates from templates
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.custom: SEO-VS-2020
ms.workload:
- multiple
ms.openlocfilehash: 9347e32a72e7f590f8f513c4b47a4b7aae699f27
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2021
ms.locfileid: "112387181"
---
# <a name="how-to-generate-templates-from-templates-by-using-escape-sequences"></a>Практическое руководство. Создание шаблонов из шаблонов с помощью escape-последовательностей
Можно создать текстовый шаблон, который создает другой текстовый шаблон в качестве выходного текста. Для этого необходимо использовать escape-последовательности для отделения тегов текстовых шаблонов. Если вы не используете escape-последовательности, созданный текстовый шаблон будет иметь предварительно определенное значение. Дополнительные сведения об использовании escape-последовательностей в текстовых шаблонах см. [в разделе использование escape-последовательностей в текстовых шаблонах](../modeling/using-escape-sequences-in-text-templates.md).

### <a name="to-generate-a-text-template-from-within-a-text-template"></a>Создание текстового шаблона из текстового шаблона

- Используйте обратную косую черту ( \\ ) в качестве escape-символа для создания необходимых тегов разметки в текстовом шаблоне для директив, инструкций, выражений и функций класса в отдельном файле текстового шаблона.

    ```
    \<#@ directive \#>
    \<# statement \#>
    \<#= expression \#>
    \<#+ classfeature \#>
    ```

## <a name="example"></a>Пример
 В следующем примере escape-символы используются для создания текстового шаблона из текстового шаблона. `output`Директива устанавливает тип файла назначения в тип файла текстового шаблона (. TT).

```csharp
\<#@ output extension=".tt" \#>
\<#@ assembly name="System.Xml.dll" \#>
\<#@ import namespace="System.Xml" \#>
\<#
XmlDocument xDoc = new XmlDocument();
//System.Diagnostics.Debugger.Break();
    xDoc.Load(@"E:\CSharp\Overview.xml");
    XmlAttributeCollection attributes = xDoc.Attributes;
    if (attributes != null)
    {
       foreach (XmlAttribute attr in attributes)
       {\#>
           \<#= attr.Name \#>
       \<#}
     }
\#>
```

 Созданный текстовый вывод является текстовым шаблоном.

```
<#@ output extension=".tt" #>
<#@ assembly name="System.Xml.dll" #>
<#@ import namespace="System.Xml" #>
<#
XmlDocument xDoc = new XmlDocument();
//System.Diagnostics.Debugger.Break();
    xDoc.Load(@"E:\CSharp\Overview.xml");
    XmlAttributeCollection attributes = xDoc.Attributes;
    if (attributes != null)
    {
       foreach (XmlAttribute attr in attributes)
       {#>
           <#= attr.Name #>
       <#}
     }
#>
```
