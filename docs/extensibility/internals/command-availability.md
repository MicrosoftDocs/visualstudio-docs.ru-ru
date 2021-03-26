---
title: Доступность команды | Документация Майкрософт
description: Узнайте, какие команды доступны в Visual Studio, используя контекст команды, который изменяется в зависимости от текущего проекта, текущего редактора и других факторов.
ms.custom: SEO-VS-2020
ms.date: 03/22/2018
ms.topic: conceptual
helpviewer_keywords:
- commands, context
- menu items, visibility contexts
ms.assetid: c74e3ccf-d771-48c8-a2f9-df323b166784
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 738e326c0e6300520d66d64fda4bb5040f231c75
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105074747"
---
# <a name="command-availability"></a>Доступность команды

Контекст Visual Studio определяет доступные команды. Контекст может изменяться в зависимости от текущего проекта, текущего редактора, загруженных пакетов VSPackage и других аспектов интегрированной среды разработки (IDE).

## <a name="command-contexts"></a>Контексты команд

Наиболее распространены следующие контексты команд:

- IDE: команды, предоставляемые интегрированной средой разработки, доступны всегда.

- VSPackage: пакеты VSPackage могут определять, когда следует отображать или скрывать команды.

- Проект: команды проекта отображаются только для текущего выбранного проекта.

- Редактор: только один редактор может быть активным за раз. Доступны команды из активного редактора. Редактор тесно работает с языковой службой. Языковая служба должна обработать свои команды в контексте связанного редактора.

- Тип файла: редактор может загружать более одного типа файлов. Доступные команды могут изменяться в зависимости от типа файла.

- Активное окно: в последнем активном окне документа задается контекст пользовательского интерфейса для привязок к ключам. Однако окно инструментов с таблицей привязки к ключам, похожее на внутренний веб-браузер, может также установить контекст пользовательского интерфейса. Для окон документов с несколькими вкладками, таких как редактор HTML, каждая вкладка имеет свой идентификатор GUID контекста команды. После регистрации окно инструментов всегда доступно в меню **вид** .

- Контекст пользовательского интерфейса: контекста пользовательского интерфейса определяются значениями <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT> класса, например <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionBuilding_guid> при сборке решения или <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.Debugging_guid> при активном отладчике. Несколько контекстов пользовательского интерфейса могут быть активными одновременно.

## <a name="define-custom-context-guids"></a>Определение пользовательских идентификаторов GUID контекста

Если соответствующий идентификатор GUID контекста команды еще не определен, можно определить его в VSPackage, а затем запрограммировать его как активный или неактивный, чтобы управлять видимостью команд:

1. Зарегистрируйте идентификаторы GUID контекста, вызвав <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.GetCmdUIContextCookie%2A> метод.

2. Получите состояние GUID контекста, вызвав <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.IsCmdUIContextActive%2A> метод.

3. Включите или отключите контекстные GUID контекста, вызвав <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.SetCmdUIContext%2A> метод.

> [!CAUTION]
> Убедитесь, что VSPackage не влияет на существующие идентификаторы GUID контекста, так как от них могут зависеть другие пакеты VSPackage.

## <a name="see-also"></a>См. также

- [Объекты контекста выделения](../../extensibility/internals/selection-context-objects.md)
- [Как пакеты VSPackage добавляют элементы пользовательского интерфейса](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
