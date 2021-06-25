---
title: Константы IDE | Документация Майкрософт
description: Класс Всконстантс предоставляет константы, характерные для интегрированной среды разработки и ранее определенные только в файлах заголовков.
ms.custom: SEO-VS-2020
ms.date: 03/22/2018
ms.topic: reference
helpviewer_keywords:
- IDE, errors
- logical views
- errors [Visual Studio], IDE
- UI context constants
- constants, Visual Studio IDE
- IDE, constants
- physical views
ms.assetid: 5030e70a-241d-474a-ba8c-e3b1cf947ff0
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 802de0fd29d909320040667f972de422595bdd4f
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/25/2021
ms.locfileid: "112904972"
---
# <a name="ide-constants"></a>Константы IDE

<xref:Microsoft.VisualStudio.VSConstants>Класс предоставляет константы, характерные для интегрированной среды разработки (IDE) и ранее определенные только в файлах заголовков.

## <a name="logical-and-physical-views"></a>Логические и физические представления

|Значение|Описание|
|-----------|-----------------|
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.Code_guid>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97>`cmdidOpenWith`обработчики должны передать это значение <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> методу, чтобы получить диалоговое окно " **Открыть с помощью** ", в данном случае в случае возможных представлений кода.|
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.Debugging_guid>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97>`cmdidOpenWith`обработчики передают это значение в <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> метод, чтобы получить диалоговое окно **Открыть с помощью** , в этом случае заполнено возможными <xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.Debugging_guid> представлениями отладки, которые сопоставляются с тем же представлением, что и <xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.Code_guid> .|
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.Designer_guid>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97>`cmdidOpenWith`обработчики передают это значение <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> методу, чтобы получить диалоговое окно **Открыть с помощью** , в данном случае для просмотра представлений конструктора **форм** .|
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.Primary_guid>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97>`cmdidOpenWith`обработчики передают это значение в <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> метод, чтобы получить диалоговое окно **Открыть с помощью** , в данном случае представление по умолчанию (первичное) для фабрики редактора.|
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.TextView_guid>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97>`cmdidOpenWith`обработчики передают это значение <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> методу, чтобы получить диалоговое окно **Открыть с помощью** для представления документа или текстового редактора данных.|
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.UserChooseView_guid>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97>`cmdidOpenWith`обработчики передают это значение <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> методу, который предлагает пользователю выбрать, какое пользовательское представление использовать.|

## <a name="editor-factory-flags"></a>Флаги фабрики редактора

|Значение|Описание|
|-----------|-----------------|
|[CEF. клонефиле](<xref:Microsoft.VisualStudio.VSConstants.CEF#Microsoft_VisualStudio_VSConstants_CEF_CloneFile>)|Устаревший флаг в сочетании с побитовым параметром в качестве первого параметра <xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A> метода.|
|[CEF. опенаснев](<xref:Microsoft.VisualStudio.VSConstants.CEF#Microsoft_VisualStudio_VSConstants_CEF_OpenAsNew>)|Сочетание побитового в качестве первого параметра <xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A> метода, указывает, что Фабрика редактора должна выполнять необходимые исправления.|
|[CEF. OpenFile](<xref:Microsoft.VisualStudio.VSConstants.CEF#Microsoft_VisualStudio_VSConstants_CEF_OpenFile>)|В сочетании с побитовым параметром в качестве первого параметра <xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A> метода этот флаг является взаимоисключающим для [CEF. Клонефиле](<xref:Microsoft.VisualStudio.VSConstants.CEF#Microsoft_VisualStudio_VSConstants_CEF_CloneFile>).|
|[CEF. Удаля](<xref:Microsoft.VisualStudio.VSConstants.CEF#Microsoft_VisualStudio_VSConstants_CEF_Silent>)|Сочетание побитового в качестве первого параметра <xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A> метода означает, что Фабрика редактора должна создать редактор без отображения пользовательского интерфейса.|

## <a name="visual-studio-errors"></a>Ошибки Visual Studio

|Значение|Описание|
|-----------|-----------------|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_BUSY>|Константа, возвращаемая интерфейсами для асинхронного поведения, если объект, который в данный момент находится в состоянии, уже занят|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_INCOMPATIBLEDOCDATA>|Ошибка HRESULT, относящаяся к Visual Studio для "несовместимых данных документа".|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_PACKAGENOTLOADED>|Ошибка HRESULT, относящаяся к Visual Studio и указывающая «пакет не загружен».|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_PROJECTALREADYEXISTS>|Ошибка HRESULT, относящаяся к Visual Studio и указывающая, что "проект уже существует".|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_PROJECTMIGRATIONFAILED>|Ошибка HRESULT, относящаяся к Visual Studio и показывающая "Сбой конфигурации проекта".|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_PROJECTNOTLOADED>|Ошибка HRESULT, относящаяся к Visual Studio и показывающая, что "проект не загружен".|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_SOLUTIONALREADYOPEN>|Ошибка HRESULT, относящаяся к Visual Studio и показывающая, что решение уже открыто.|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_SOLUTIONNOTOPEN>|Ошибка HRESULT, относящаяся к Visual Studio и показывающая, что решение не открыто.|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_SPECIFYING_OUTPUT_UNSUPPORTED>|Возвращается интерфейсами сборки, которые имеют параметры для указания массива из <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutput> интерфейса, но реализация может применить метод только ко всем выходам.|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_UNSUPPORTEDFORMAT>|<xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A>Метод возвращает это значение, если документ имеет формат, который не может быть открыт в редакторе.|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_WIZARDBACKBUTTONPRESS>|Значение HRESULT, указывающее, что пользователь нажал кнопку "назад" в мастере Visual Studio.|

## <a name="visual-studio-constants"></a>Константы Visual Studio

|Значение|Описание|
|-----------|-----------------|
|<xref:Microsoft.VisualStudio.VSConstants.VS_S_PROJECTFORWARDED>|Ошибка HRESULT, относящаяся к Visual Studio и показывающая "проект перенаправлен".|
|<xref:Microsoft.VisualStudio.VSConstants.VS_S_TBXMARKER>|Константа, относящаяся к Visual Studio для маркера панели элементов.|
|<xref:Microsoft.VisualStudio.VSConstants.VSM_ENTERMODAL>|Константа, относящаяся к Visual Studio для вещания сообщения уведомления с помощью <xref:Microsoft.VisualStudio.Shell.Interop.IVsBroadcastMessageEvents.OnBroadcastMessage%2A> метода, который указывает начало модальности.|
|<xref:Microsoft.VisualStudio.VSConstants.VSM_EXITMODAL>|Константа, относящаяся к Visual Studio для вещания сообщения уведомления с помощью <xref:Microsoft.VisualStudio.Shell.Interop.IVsBroadcastMessageEvents.OnBroadcastMessage%2A> метода, который указывает на окончание модальности.|
|<xref:Microsoft.VisualStudio.VSConstants.VSM_TOOLBARMETRICSCHANGE>|Константа, относящаяся к Visual Studio для вещания сообщения уведомления через <xref:Microsoft.VisualStudio.Shell.Interop.IVsBroadcastMessageEvents.OnBroadcastMessage%2A> метод, указывающий, что метрики панели команд изменились.|
|<xref:Microsoft.VisualStudio.VSConstants.VSCOOKIE_NIL>|Константа, относящаяся к Visual Studio, указывающая, что файл cookie не был задан.|
|[ВСИТЕМИД. Указатель](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID#Microsoft_VisualStudio_VSConstants_VSITEMID_Nil>)|Идентификатор элемента Visual Studio, который представляет отсутствие элемента проекта. Это значение используется, если текущий выбор отсутствует.|
|[ВСИТЕМИД. Корневой](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID#Microsoft_VisualStudio_VSConstants_VSITEMID_Root>)|Идентификатор элемента Visual Studio, представляющий корень иерархии проекта и используемый для идентификации всей иерархии, в отличие от одного элемента.|
|[ВСИТЕМИД. Выбор](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID#Microsoft_VisualStudio_VSConstants_VSITEMID_Selection>)|Идентификатор элемента Visual Studio, представляющий выбранный в данный момент элемент или элементы, которые могут включать корень иерархии.|

## <a name="ivsselectionevents"></a>ивсселектионевентс
 Описывает, какой компонент интегрированной среды разработки был только что выбран, в <xref:Microsoft.VisualStudio.Shell.Interop.IVsSelectionEvents.OnElementValueChanged%2A> вызове, например.

|Константа|Значение|
|--------------|-----------|
|[SelectionElement.DocУментфраме](<xref:Microsoft.VisualStudio.VSConstants.SelectionElement#Microsoft_VisualStudio_VSConstants_SelectionElement_DocumentFrame>)|0x2|
|[Селектионелемент. Пропертибровсерсид](<xref:Microsoft.VisualStudio.VSConstants.SelectionElement#Microsoft_VisualStudio_VSConstants_SelectionElement_PropertyBrowserSID>)|0x4|
|[Селектионелемент. Стартуппрожект](<xref:Microsoft.VisualStudio.VSConstants.SelectionElement#Microsoft_VisualStudio_VSConstants_SelectionElement_StartupProject>)|0x3|
|[Селектионелемент. UndoManager](<xref:Microsoft.VisualStudio.VSConstants.SelectionElement#Microsoft_VisualStudio_VSConstants_SelectionElement_UndoManager>)|0x0|
|[Селектионелемент. UserContext](<xref:Microsoft.VisualStudio.VSConstants.SelectionElement#Microsoft_VisualStudio_VSConstants_SelectionElement_UserContext>)|0x5|
|[Селектионелемент. WindowFrame](<xref:Microsoft.VisualStudio.VSConstants.SelectionElement#Microsoft_VisualStudio_VSConstants_SelectionElement_WindowFrame>)|0x1|

## <a name="vsselelemid"></a>всселелемид
 Константы, используемые для обозначения нового состояния выбора.

|Константа|Значение|
|--------------|-----------|
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|2|
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|7|
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|4|
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|6|
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|3|
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|0|
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|5|
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|1|

## <a name="component-selector-dialog-constants"></a>Константы диалогового окна выбора компонентов

|Константа|Значение|
|--------------|-----------|
|<xref:Microsoft.VisualStudio.VSConstants.CPDN_SELCHANGED>|WM_USER + 1280|
|<xref:Microsoft.VisualStudio.VSConstants.CPDN_SELDBLCLICK>|WM_USER + 1281|
|<xref:Microsoft.VisualStudio.VSConstants.CPPM_CLEARSELECTION>|WM_USER + 1290|
|<xref:Microsoft.VisualStudio.VSConstants.CPPM_GETSELECTION>|WM_USER + 1287|
|<xref:Microsoft.VisualStudio.VSConstants.CPPM_INITIALIZELIST>|WM_USER + 1285|
|<xref:Microsoft.VisualStudio.VSConstants.CPPM_INITIALIZETAB>|WM_USER + 1288|
|<xref:Microsoft.VisualStudio.VSConstants.CPPM_QUERYCANSELECT>|WM_USER + 1286|
|<xref:Microsoft.VisualStudio.VSConstants.CPPM_SETMULTISELECT>|WM_USER + 1289|

## <a name="see-also"></a>См. также

- [Команды, определяемые интегрированной средой разработки для расширения систем проектов](../extensibility/internals/ide-defined-commands-for-extending-project-systems.md)
