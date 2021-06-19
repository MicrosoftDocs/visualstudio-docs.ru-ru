---
title: Директива T4 CleanUpBehavior
description: Сведения об директиве Клеанупбехавиор и об удалении appDomain после обработки текстового шаблона.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 078b688c238bea47e4ab38b3302708bf5e5189cf
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2021
ms.locfileid: "112386349"
---
# <a name="t4-cleanupbehavior-directive"></a>Директива T4 CleanUpBehavior

Для удаления appDomain после обработки текстового шаблона добавьте следующую строку:

```
<#@ CleanupBehavior processor="T4VSHost" CleanupAfterProcessingtemplate="true" #>
```

Текстовые шаблоны обрабатываются в appDomain, который отличается от хост-процесса. В большинстве случаев после обработки одного текстового шаблона appDomain снова используется для обработки следующего шаблона. Но если указан атрибут CleanupBehavior, appDomain удаляется и следующий шаблон обрабатывается в новом appDomain.

Это замедляет обработку текста, но может быть полезно для гарантированного удаления ресурсов.

Эта директива работает только в узле Visual Studio.
