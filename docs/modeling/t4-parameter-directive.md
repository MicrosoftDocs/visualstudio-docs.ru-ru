---
title: Директива Parameter T4
description: Изучите, что в Visual Studio директива parameter объявляет свойства в коде шаблона, которые инициализируются из значений, переданных из внешнего контекста.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 8ef80179d43996669b9d883fd2ca9163208d18d7
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2021
ms.locfileid: "112386102"
---
# <a name="t4-parameter-directive"></a>Директива Parameter T4

В текстовом шаблоне Visual Studio `parameter` директива объявляет свойства в коде шаблона, которые инициализируются из значений, переданных из внешнего контекста. Эти значения можно задать при написании кода, вызывающего преобразование текста.

## <a name="using-the-parameter-directive"></a>Использование директивы Parameter

```
<#@ parameter type="Full.TypeName" name="ParameterName" #>
```

 `parameter`Директива объявляет свойства в коде шаблона, которые инициализируются из значений, переданных из внешнего контекста. Эти значения можно задать при написании кода, вызывающего преобразование текста. Значения могут передаваться либо в `Session` словаре, либо в <xref:System.Runtime.Remoting.Messaging.CallContext> .

 Можно объявлять параметры любого типа, поддерживающего удаленное взаимодействие. То есть тип должен быть объявлен с <xref:System.SerializableAttribute> или должен быть производным от <xref:System.MarshalByRefObject> . Это позволяет передавать значения параметров в домен приложения, в котором обрабатывается шаблон.

 Например, можно написать текстовый шаблон со следующим содержимым:

```
<#@ template language="C#" #>

<#@ parameter type="System.Int32" name="TimesToRepeat" #>

<# for (int i = 0; i < TimesToRepeat; i++) { #>
Line <#= i #>
<# } #>
```

## <a name="passing-parameter-values-to-a-template"></a>Передача значений параметров в шаблон
 При написании расширения Visual Studio, такого как команда меню или обработчик событий, можно обработать шаблон с помощью службы текстовых шаблонов:

```csharp
// Get a service provider - how you do this depends on the context:
IServiceProvider serviceProvider = dte; // or dslDiagram.Store, for example
// Get the text template service:
ITextTemplating t4 = serviceProvider.GetService(typeof(STextTemplating)) as ITextTemplating;
ITextTemplatingSessionHost host = t4 as ITextTemplatingSessionHost;
// Create a Session in which to pass parameters:
host.Session = host.CreateSession();
// Add parameter values to the Session:
session["TimesToRepeat"] = 5;
// Process a text template:
string result = t4.ProcessTemplate("MyTemplateFile.t4",
  System.IO.File.ReadAllText("MyTemplateFile.t4"));
```

## <a name="passing-values-in-the-call-context"></a>Передача значений в контексте вызова
 Можно также передавать значения в виде логических данных в <xref:System.Runtime.Remoting.Messaging.CallContext> .

 В следующем примере значения передаются с помощью обоих методов:

```csharp
ITextTemplating t4 = this.Store.GetService(typeof(STextTemplating)) as ITextTemplating;
ITextTemplatingSessionHost host = t4 as ITextTemplatingSessionHost;
host.Session = host.CreateSession();
// Pass a value in Session:
host.Session["p1"] = 32;
// Pass another value in CallContext:
System.Runtime.Remoting.Messaging.CallContext.LogicalSetData("p2", "test");

// Process a small template inline:
string result = t4.ProcessTemplate("",
   "<#@parameter type=\"System.Int32\" name=\"p1\"#>"
 + "<#@parameter type=\"System.String\" name=\"p2\"#>"
 + "Test <#=p1#> <#=p2#>");

// Result value is:
//     Test 32 test
```

## <a name="passing-values-to-a-run-time-preprocessed-text-template"></a>Передача значений в шаблон текста Run-Time (предварительно обработанный)
 Обычно не требуется использовать `<#@parameter#>` директиву с текстовыми шаблонами времени выполнения (предварительно обработанными). Вместо этого можно определить дополнительный конструктор или устанавливаемое свойство для созданного кода, через который вы передаете значения параметров. Дополнительные сведения см. в статье [Создание текста во время выполнения с помощью текстовых шаблонов T4](../modeling/run-time-text-generation-with-t4-text-templates.md).

 Однако если вы хотите использовать `<#@parameter>` в шаблоне времени выполнения, можно передать ему значения с помощью словаря сеанса. Например, предположим, что вы создали файл как предварительно обработанный шаблон с именем `PreTextTemplate1` . Вы можете вызвать шаблон в программе, используя следующий код.

```csharp
PreTextTemplate1 t = new PreTextTemplate1();
t.Session = new Microsoft.VisualStudio.TextTemplating.TextTemplatingSession();
t.Session["TimesToRepeat"] = 5;
// Add other parameter values to t.Session here.
t.Initialize(); // Must call this to transfer values.
string resultText = t.TransformText();
```

## <a name="obtaining-arguments-from-texttemplateexe"></a>Получение аргументов из TextTemplate.exe

> [!IMPORTANT]
> `parameter`Директива не извлекает значения, заданные в `-a` параметре `TextTransform.exe` программы. Чтобы получить эти значения, установите `hostSpecific="true"` в `template` директиве и используйте `this.Host.ResolveParameterValue("","","argName")` .
