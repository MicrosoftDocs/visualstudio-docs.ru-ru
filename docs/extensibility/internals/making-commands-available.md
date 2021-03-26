---
title: Как сделать команды доступными | Документация Майкрософт
description: Узнайте, как управлять доступностью команд, добавленных в интегрированную среду разработки Visual Studio в пакеты VSPackage, с помощью отложенной загрузки, контекста и видимости.
ms.custom: SEO-VS-2020
ms.date: 03/22/2018
ms.topic: conceptual
helpviewer_keywords:
- menus [Visual Studio SDK], commands
- best practices, menu and toolbar commands
- toolbars [Visual Studio], best practices
- menu commands, best practices
ms.assetid: 3ffc4312-c6db-4759-a946-a4bb85f4a17a
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 29f5e5c634c1bf360409e35c87684282a26e8a07
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105095216"
---
# <a name="making-commands-available"></a>Доступность команд

При добавлении нескольких пакетов VSPackage в Visual Studio пользовательский интерфейс может стать оверкровдед с командами. Чтобы сократить эту проблему, можно запрограммировать пакет следующим образом.

- Запрограммировать пакет так, чтобы он загружался только в том случае, если он требуется пользователю.

- Запрограммировать пакет таким образом, чтобы его команды отображались только в том случае, если они могут потребоваться в контексте текущего состояния интегрированной среды разработки (IDE).

## <a name="delayed-loading"></a>Отложенная загрузка

Типичный способ включения отложенной загрузки заключается в проектировании VSPackage, чтобы команды отображались в пользовательском интерфейсе, но сам пакет не загружается, пока пользователь не щелкнет одну из команд. Для этого в vsct файле создайте команды без флагов команд.

В следующем примере показано определение команды меню из vsct-файла. Это команда, создаваемая шаблоном пакета Visual Studio при выборе **команды меню** в шаблоне.

```xml
<Button guid="guidTopLevelMenuCmdSet" id="cmdidTestCommand" priority="0x0100" type="Button">
  <Parent guid="guidTopLevelMenuCmdSet" id="MyMenuGroup" />
  <Icon guid="guidImages" id="bmpPic1" />
  <Strings>
    <CommandName>cmdidTestCommand</CommandName>
    <ButtonText>Test Command</ButtonText>
  </Strings>
</Button>
```

В примере, если родительская группа ( `MyMenuGroup` ) является дочерней по отношению к меню верхнего уровня, например меню **Сервис** , команда будет видна в этом меню, но пакет, выполняющий команду, не будет загружаться до тех пор, пока команда не нажата пользователем. Однако при программировании команды для реализации <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> интерфейса можно включить загрузку пакета при первом развертывании меню, содержащего команду.

Обратите внимание, что отложенная загрузка может также улучшить производительность при запуске.

## <a name="current-context-and-the-visibility-of-commands"></a>Текущий контекст и видимость команд

Команды VSPackage можно программировать как видимые или скрытые в зависимости от текущего состояния данных VSPackage или действий, которые в настоящее время являются актуальными. Пакет VSPackage можно использовать для установки состояния команд, обычно с помощью реализации <xref:EnvDTE.IDTCommandTarget.QueryStatus%2A> метода из <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> интерфейса, но для этого необходимо загрузить VSPackage, прежде чем он сможет выполнить код. Вместо этого рекомендуется включить интегрированную среду разработки для управления видимостью команд без загрузки пакета. Для этого в файле vsct Свяжите команды с одним или несколькими специальными контекстами пользовательского интерфейса. Эти контексты пользовательского интерфейса идентифицируются с помощью идентификатора GUID, известного как *идентификатор GUID контекста команды*.

[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] отслеживает изменения, вызванные действиями пользователя, такими как загрузка проекта или переход от правки к сборке. При возникновении изменений внешний вид интегрированной среды разработки автоматически изменяется. В следующей таблице показано четыре основных контекста изменений интегрированной среды разработки, которые [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] мониторы.

| Тип контекста | Описание |
|-------------------------| - |
| Тип активного проекта | Для большинства типов проектов это `GUID` значение совпадает с идентификатором GUID пакета VSPackage, реализующего проект. Однако в [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] проектах в качестве значения используется тип проекта `GUID` . |
| Активное окно | Как правило, это последнее активное окно документа, которое устанавливает текущий контекст пользовательского интерфейса для привязок к клавишам. Однако это также может быть окно инструментов с таблицей привязки ключей, похожей на внутренний веб-браузер. Для окон документов с несколькими вкладками, таких как редактор HTML, каждая вкладка имеет другой контекст команды `GUID` . |
| Служба Active Language | Языковая служба, связанная с файлом, который в настоящий момент отображается в текстовом редакторе. |
| Активное окно инструментов | Окно инструментов, которое открыто и имеет фокус. |

Пятая основная область контекста — это состояние интерфейса IDE. Контексты пользовательского интерфейса определяются с помощью активного контекста команды `GUID` , как показано ниже.

- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionBuilding_guid>

- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.Debugging_guid>

- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.Dragging_guid>

- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.FullScreenMode_guid>

- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.DesignMode_guid>

- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.NoSolution_guid>

- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionExists_guid>

- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.EmptySolution_guid>

- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionHasSingleProject_guid>

- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionHasMultipleProjects_guid>

- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.CodeWindow_guid>

Эти идентификаторы GUID помечены как активные или неактивные, в зависимости от текущего состояния интегрированной среды разработки. Несколько контекстов пользовательского интерфейса могут быть активными одновременно.

### <a name="hide-and-display-commands-based-on-context"></a>Скрытие и отображение команд в зависимости от контекста

Вы можете отобразить или скрыть команду пакета в интегрированной среде разработки, не загружая сам пакет. Для этого определите команду в файле vsct пакета с помощью `DefaultDisabled` `DefaultInvisible` `DynamicVisibility` флагов команд, и добавьте один или несколько элементов [висибилититем](../../extensibility/visibilityitem-element.md) в раздел [висибилитиконстраинтс](../../extensibility/visibilityconstraints-element.md) . Если указанный контекст команды `GUID` становится активным, команда отображается без загрузки пакета.

### <a name="custom-context-guids"></a>Идентификаторы GUID настраиваемого контекста

Если соответствующий идентификатор GUID контекста команды еще не определен, можно определить его в VSPackage, а затем запрограммировать его как активный или неактивный, чтобы управлять видимостью команд. Используйте <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> службу, чтобы:

- Зарегистрируйте идентификаторы GUID контекста (путем вызова <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.GetCmdUIContextCookie%2A> метода).

- Получение состояния контекста `GUID` (путем вызова <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.IsCmdUIContextActive%2A> метода).

- Включение `GUID` и отключение контекста (путем вызова <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.SetCmdUIContext%2A> метода).

    > [!CAUTION]
    > Убедитесь, что VSPackage не влияет на состояние существующего GUID контекста, так как от них могут зависеть другие пакеты VSPackage.

## <a name="example"></a>Пример

Следующий пример команды VSPackage демонстрирует динамическую видимость команды, которая управляется контекстами команд без загрузки VSPackage.

Команда должна быть включена и отображаться каждый раз, когда существует решение; Это значит, что каждый раз, когда активен один из следующих идентификаторов GUID контекста команды:

- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.EmptySolution_guid>

- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionHasMultipleProjects_guid>

- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionHasSingleProject_guid>

В этом примере обратите внимание, что каждый флаг команды является отдельным элементом [флага команды](../../extensibility/command-flag-element.md) .

```xml
<Button guid="guidDynamicVisibilityCmdSet" id="cmdidMyCommand"
        priority="0x0100" type="Button">
  <Parent guid="guidDynamicVisibilityCmdSet" id="MyMenuGroup" />
  <Icon guid="guidImages" id="bmpPic1" />
  <CommandFlag>DefaultDisabled</CommandFlag>
  <CommandFlag>DefaultInvisible</CommandFlag>
  <CommandFlag>DynamicVisibility</CommandFlag>
  <Strings>
    <CommandName>cmdidMyCommand</CommandName>
    <ButtonText>My Command name</ButtonText>
  </Strings>
</Button>
```

Также обратите внимание, что каждый контекст пользовательского интерфейса должен быть указан в отдельном `VisibilityItem` элементе, как показано ниже.

```xml
<VisibilityConstraints>
  <VisibilityItem guid="guidDynamicVisibilityCmdSet"
                  id="cmdidMyCommand" context="UICONTEXT_EmptySolution" />
  <VisibilityItem guid="guidDynamicVisibilityCmdSet"
                      id="cmdidMyCommand" context="UICONTEXT_SolutionHasSingleProject" />
  <VisibilityItem guid="guidDynamicVisibilityCmdSet"
                  id="cmdidMyCommand" context="UICONTEXT_SolutionHasMultipleProjects" />
</VisibilityConstraints>
```

## <a name="see-also"></a>См. также

- [Добавление команды на панель инструментов обозреватель решений](../../extensibility/adding-a-command-to-the-solution-explorer-toolbar.md)
- [Как добавить элементы пользовательского интерфейса с помощью пакетов VSPackage](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Маршрутизация команд в пакетах VSPackage](../../extensibility/internals/command-routing-in-vspackages.md)
- [Динамическое добавление элементов меню](../../extensibility/dynamically-adding-menu-items.md)
