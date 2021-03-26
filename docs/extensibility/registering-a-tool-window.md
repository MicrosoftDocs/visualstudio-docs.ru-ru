---
title: Регистрация окна инструментов | Документация Майкрософт
description: Узнайте, как зарегистрировать окна инструментов в Visual Studio с помощью атрибут providetoolwindowattribute и Провидетулвиндоввисибилитяттрибуте.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- tool windows, registering managed
- tool windows, registering
ms.assetid: 8c8c4a24-3da4-497b-9db2-0ddd7cfbfdd2
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 13c3035f089855f88d54ecc8b3c1e6434ac10e65
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105056588"
---
# <a name="register-a-tool-window"></a>Регистрация окна инструментов
Вы можете зарегистрировать окна инструментов с помощью <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowAttribute> и  <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowVisibilityAttribute> .

## <a name="example"></a>Пример

```csharp

[ProvideToolWindow(typeof(PersistedWindowPane), Style = MsVsShell.VsDockStyle.Tabbed, Window = "3ae79031-e1bc-11d0-8f78-00a0c9110057")]
[ProvideToolWindow(typeof(DynamicWindowPane), PositionX=250, PositionY=250, Width=160, Height=180, Transient=true)]
[ProvideToolWindowVisibility(typeof(DynamicWindowPane), /*UICONTEXT_SolutionExists*/"f1536ef8-92ec-443c-9ed7-fdadf150da82")]
[ProvideMenuResource(1000, 1)]
[PackageRegistration(UseManagedResourcesOnly = true)]
[Guid("01069CDD-95CE-4620-AC21-DDFF6C57F012")]
public class PackageToolWindow : Package
{
```

 В приведенном выше коде <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowAttribute> регистрирует `PersistedWindowPane` `DynamicWindowPane` окна инструментов и в Visual Studio. Окно сохраненного инструмента закреплено с **Обозреватель решений**, а динамическому окну дается начальное положение и размер по умолчанию. Динамическое окно становится временным, что означает, что он не создается при запуске. При этом записывается `DontForceCreate` значение `ToolWindows` ключа в системном реестре. Дополнительные сведения см. в разделе [Настройка экрана окна инструментов](/previous-versions/visualstudio/visual-studio-2015/extensibility/tool-window-display-configuration?preserve-view=true&view=vs-2015).