---
title: Представления с одним и несколькими вкладками | Документация Майкрософт
description: Сведения о реализации многостраничных представлений в редакторах, таких как окна редактора кода и конструктор форм.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - single and multi-tab views
ms.assetid: e3611704-349f-4323-b03c-f2b0a445d781
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 7c23693b5ae622912695c139714c7e818ed0e868
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105056328"
---
# <a name="single-and-multi-tab-views"></a>Представления с одной и несколькими вкладками
Редактор может создавать различные типы представлений. Одним из примеров является окно редактора кода, другое — конструктор форм.

 Представление с несколькими вкладками — это представление с несколькими вкладками. Например, редактор HTML имеет две вкладки внизу: **проектирование** и **источник**, каждое логическое представление. В представлении конструктора отображается веб-страница, подготовленная к просмотру, а другая отображает код HTML, который состоит из веб-страницы.

## <a name="accessing-physical-views"></a>Доступ к физическим представлениям
 Физические представления ведущие объекты представления документов, каждый из которых представляет представление данных в буфере, например код или форма. Соответственно, каждый объект представления документа имеет физическое представление (идентифицируемое как строка физического представления) и обычно одно логическое представление.

 Однако в некоторых случаях физическое представление может иметь два или более логических представления. Некоторые примеры представляют собой редактор с разделенным окном с параллельными представлениями или конструктор форм с ГРАФИЧЕСКИм пользовательским представлением и представлением кода программной части.

 Чтобы предоставить редактору доступ ко всем доступным физическим представлениям, необходимо создать уникальную строку физического представления для каждого типа объекта представления документа, который может быть создан фабрикой редактора. Например, [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] Фабрика редактора может создавать объекты представления документов для окна кода и окна конструктора форм.

## <a name="creating-multi-tabbed-views"></a>Создание представлений с несколькими вкладками
 Хотя объект представления документов должен быть связан с физическим представлением через уникальную строку физического представления, можно поместить несколько вкладок в физическое представление, чтобы обеспечить возможность просмотра данных различными способами. В этой конфигурации с несколькими вкладками все вкладки связаны с одной и той же строкой физического представления, но каждой вкладке присваивается другой GUID логического представления.

 Чтобы создать представление для редактора с несколькими вкладками, реализуйте <xref:Microsoft.VisualStudio.Shell.Interop.IVsMultiViewDocumentView> интерфейс, а затем свяжите другое логическое представление GUID ( <xref:Microsoft.VisualStudio.Shell.Interop.LogicalViewID> ) с каждой создаваемой вкладкой.

 Редактор HTML Visual Studio — это пример редактора с представлением с несколькими вкладками. Он содержит вкладки **конструктора** и **исходного кода** . Чтобы сделать это, другое логическое представление связывается с каждой вкладкой, `LOGICALVIEWID_TextView` для вкладки « **Дизайн** » и `LOGICALVIEWID_Code` для вкладки « **источник** ».

 Указав соответствующее логическое представление, пакет VSPackage может получить доступ к представлению, соответствующему конкретной цели, таким как разработка формы, редактирование кода или Отладка кода. Однако одно из окон должно быть определено строкой NULL, и оно должно соответствовать первичному логическому представлению ( `LOGVIEWID_Primary` ).

 В следующей таблице перечислены доступные значения логического представления и их использование.

|ИДЕНТИФИКАТОР GUID ЛОГВИЕВИД|Рекомендуемое использование|
|--------------------|---------------------|
|`LOGVIEWID_Primary`|По умолчанию/первичное представление фабрики редактора.<br /><br /> Все фабрики редактора должны поддерживать это значение. В этом представлении в качестве строки физического представления должна использоваться строка NULL. Для этого значения должно быть задано по крайней мере одно логическое представление.|
|`LOGVIEWID_Debugging`|Представление отладки. Как правило, `LOGVIEWID_Debugging` сопоставляется с тем же представлением, что и `LOGVIEWID_Code` .|
|`LOGVIEWID_Code`|Представление, запускаемое командой " **Просмотреть код** ".|
|`LOGVIEWID_Designer`|Представление, запущенное командой **просмотра формы** .|
|`LOGVIEWID_TextView`|Представление текстового редактора. Это представление, которое возвращает <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> , с которого можно получить доступ <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> .|
|`LOGVIEWID_UserChooseView`|Предлагает пользователю выбрать представление для использования.|
|`LOGVIEWID_ProjectSpecificEditor`|Передается в диалоговом окне " **Открыть с помощью** " в<br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.OpenItem%2A><br /><br /> Когда пользователь выбирает запись "(редактор проекта по умолчанию)".|

 Хотя GUID логического представления являются расширяемыми, можно использовать только идентификаторы GUID логического представления, определенные в VSPackage.

 При завершении работы Visual Studio оставляет идентификатор GUID фабрики редактора и строк физического представления, связанных с окном документа, чтобы его можно было использовать для повторного открытия окон документов при повторном открытии решения. Только окна, открытые при закрытии решения, сохраняются в файле решения (SUO). Эти значения соответствуют `VSFPROPID_guidEditorType` `VSFPROPID_pszPhysicalView` значениям и, передаваемым в `propid` параметре <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> метода.

## <a name="example"></a>Пример
 В этом фрагменте показано <xref:Microsoft.VisualStudio.Shell.Interop.LogicalViewID.TextView> , как объект используется для доступа к представлению, реализующему `IVsCodeWindow` . В этом случае <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShellOpenDocument> служба используется для вызова <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenDocumentViaProject%2A> и запроса `LOGVIEWID_TextView` , который получает указатель на фрейм окна. Указатель на объект представления документа получается путем вызова метода <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> и указания значения `VSFPROPID_DocView` . Из объекта представления документов `QueryInterface` вызывается для `IVsCodeWindow` . В этом случае ожидание заключается в том, что возвращается текстовый редактор, поэтому объект представления документа, возвращаемый в <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> методе, является окном кода.

```cpp
HRESULT CFindTool::GotoFileLocation(const WCHAR * szFile, long iLine, long iStart, long iLen)
{
  HRESULT hr;
  if (NULL == szFile || !*szFile)
    return E_INVALIDARG;

  if (iLine == -1L)
    return S_FALSE;

  VSITEMID                  itemid;
  VARIANT                   var;
  RECT                      rc;
  IVsUIShellOpenDocument *  pOpenDoc    = NULL;
  IVsCodeWindow *           pCodeWin    = NULL;
  IVsTextView *             pTextView   = NULL;
  IVsUIHierarchy *          pHierarchy  = NULL;
  IVsWindowFrame *          pFrame      = NULL;
  IUnknown *                pUnk        = NULL;
  IVsHighlight *            pHighlight  = NULL;

  IfFailGo(CGlobalServiceProvider::HrQueryService(SID_SVsUIShellOpenDocument, IID_IVsUIShellOpenDocument, (void **)&pOpenDoc));
  IfFailGo(pOpenDoc->OpenDocumentViaProject(szFile, LOGVIEWID_TextView, NULL, &pHierarchy, &itemid, &pFrame));
  pFrame->Show();
  VariantInit(&var);
  IfFailGo(pFrame->GetProperty(VSFPROPID_DocView, &var));
  if (VT_UNKNOWN != var.vt) { hr = E_FAIL; goto Error; }
  pUnk = V_UNKNOWN(&var);
  if (NULL != pUnk)
  {
    IfFailGo(pUnk->QueryInterface(IID_IVsCodeWindow, (void **)&pCodeWin));
    if (SUCCEEDED(hr = pCodeWin->GetLastActiveView(&pTextView)) ||
        SUCCEEDED(hr = pCodeWin->GetPrimaryView(&pTextView)) )
    {
      pTextView->SetSelection(iLine, iStart, iLine, iStart + iLen);
      // uncover selection
      IfFailGo(pTextView->QueryInterface(IID_IVsHighlight, (void**)&pHighlight));
      IfFailGo(SUCCEEDED(pHighlight->GetHighlightRect(&rc)));
      UncoverSelectionRect(&rc);
    }
  }

Error:
  CLEARINTERFACE(pHighlight);
  CLEARINTERFACE(pTextView);
  CLEARINTERFACE(pCodeWin);
  CLEARINTERFACE(pUnk);
  CLEARINTERFACE(pFrame);
  CLEARINTERFACE(pOpenDoc);
  CLEARINTERFACE(pHierarchy);
  RedrawWindow(m_hwndResults, NULL, NULL, RDW_ERASE|RDW_FRAME|RDW_INVALIDATE|RDW_ALLCHILDREN);
  return hr;
}
```

## <a name="see-also"></a>См. также
- [Поддержка представления нескольких документов](../extensibility/supporting-multiple-document-views.md)
- [Практическое руководство. Вложение представлений в данные документа](../extensibility/how-to-attach-views-to-document-data.md)
- [Создание специализированных редакторов и конструкторов](../extensibility/creating-custom-editors-and-designers.md)
