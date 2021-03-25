---
title: Поля и интерфейсы окна свойств | Документация Майкрософт
description: Сведения о выборе, который определяет, какие сведения отображаются в окно свойств на основе окна, имеющего фокус в интегрированной среде разработки Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Properties window, fields and interfaces
ms.assetid: 0328f0e5-2380-4a7a-a872-b547cb775050
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 9f445d31fe995321ad6ec334a5b6eb93570b8875
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105061034"
---
# <a name="properties-window-fields-and-interfaces"></a>Properties Window Fields and Interfaces
Модель выбора позволяет определить, какие сведения отображаются в окне **Свойства** , на основе окна, имеющего фокус в интегрированной среде разработки. Для каждого окна и объекта в выбранном окне может быть отправлен объект контекста выбора в глобальный контекст выбора. Среда обновляет глобальный контекст выделения значениями из рамки окна, когда это окно находится в фокусе. При изменении фокуса, поэтому выполняет контекст выбора.

## <a name="tracking-selection-in-the-ide"></a>Отслеживание выбора в интегрированной среде разработки
 Для фрейма окна или сайта, принадлежащего интегрированной среде разработки, имеется служба с именем <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection> . В следующих шагах показано, как изменение в выделении, вызванное пользовательским изменением фокуса на другое открытое окно или выбором другого элемента проекта в **Обозреватель решений**, реализуется для изменения содержимого, отображаемого в окне « **свойства** ».

1. Объект, созданный пакетом VSPackage, который набирается в выбранном окне, вызывает метод <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A> <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection> <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection> .

2. Контейнер выбора, предоставленный выбранным окном, создает собственный <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> объект. При изменении выбора пакет VSPackage вызывает <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> для уведомления всех прослушивателей в среде, включая окно **свойства** , для изменения. Он также предоставляет доступ к сведениям о иерархии и элементе, связанным с новым выбором.

3. Вызов <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> и передача. выбранные элементы иерархии в `VSHPROPID_BrowseObject` параметре заполняют <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> объект.

4. Для __VSHPROPID возвращается объект, производный от [интерфейса IDispatch](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch) [. VSHPROPID_BrowseObject](<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_BrowseObject>) для запрошенного элемента, и среда заключает его в оболочку <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> (см. следующий шаг). Если вызов завершается неудачей, среда выполняет второй вызов `IVsHierarchy::GetProperty` , передавая ему контейнер выбора [__VSHPROPID. VSHPROPID_SelContainer](<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_SelContainer>) , что элемент или элементы иерархии являются предоставленными.

    Проект VSPackage не создается <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> , поскольку предоставляемый средой пакет VSPackage, реализующий его (например, **Обозреватель решений**) <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> от его имени.

5. Среда вызывает методы <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> для получения объектов, основанных на `IDispatch` интерфейсе, для заполнения окна **свойств** .

   При изменении значения в окне **свойств** пакеты VSPackage реализуют `IVsTrackSelectionEx::OnElementValueChangeEx` и `IVsTrackSelectionEx::OnSelectionChangeEx` сообщают об изменении значения элемента. Затем среда вызывает <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> или <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> , чтобы информация, отображаемая в окне **свойств** , была синхронизирована со значениями свойств. Дополнительные сведения см. [в разделе Обновление значений свойств в окне "Свойства"](#updating-property-values-in-the-properties-window).

   Помимо выбора другого элемента проекта в **Обозреватель решений** для вывода свойств, относящихся к этому элементу, можно также выбрать другой объект в форме или окне документа с помощью раскрывающегося списка, доступного в окне « **свойства** ». Дополнительные сведения см. в разделе [список объектов окна свойств](../../extensibility/internals/properties-window-object-list.md).

   Можно изменить способ отображения сведений в сетке окна **свойств** в алфавитном порядке по категориям, а также, если это возможно, открыть страницу свойств для выбранного объекта, нажав соответствующие кнопки в окне « **свойства** ». Дополнительные сведения см. в разделе [кнопки окна свойств](../../extensibility/internals/properties-window-buttons.md) и [страницы свойств](../../extensibility/internals/property-pages.md).

   Наконец, в нижней части окна **Свойства** также содержится описание поля, выбранного в сетке окна **свойства** . Дополнительные сведения см. [в разделе Получение описаний полей из окна "Свойства"](#getting-field-descriptions-from-the-properties-window).

## <a name="updating-property-values-in-the-properties-window"></a><a name="updating-property-values-in-the-properties-window"></a> Обновление значений свойств в окне "Свойства"
Существует два способа поддерживать синхронизацию окна **Свойства** с изменениями значения свойства. Первый способ — вызывать интерфейс <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell>, который предоставляет доступ к базовым функциям окон, включая создание окон инструментов и документов, предоставляемых средой, и доступ к ним. Следующие шаги описывают этот процесс синхронизации.

### <a name="updating-property-values-using-ivsuishell"></a>Обновление значений свойств с помощью IVsUIShell

#### <a name="to-update-property-values-using-the-ivsuishell-interface"></a>Обновление значений свойств с помощью интерфейса IVsUIShell

1. Вызывайте <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> (через службу <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>) каждый раз, когда пакетам VSPackage, проектам или редакторам необходимо создать или перечислить окна инструментов или документов.

2. Реализуйте <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.RefreshPropertyBrowser%2A> , чтобы обеспечить синхронизацию окна **свойств** с изменениями свойств для проекта (или любого другого выбранного объекта, просматриваемого окном **свойств** ) без реализации <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> и срабатывания <xref:Microsoft.VisualStudio.OLE.Interop.IPropertyNotifySink.OnChanged%2A> событий.

3. Реализуйте методы <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy><xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.AdviseHierarchyEvents%2A> и <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.UnadviseHierarchyEvents%2A> соответственно для установки и отключения уведомлений клиента о событиях иерархии, не требуя от иерархии реализации <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer>.

### <a name="updating-property-values-using-iconnection"></a>Обновление значений свойств с помощью IConnection
 Второй способ поддерживать синхронизацию окна **Свойства** с изменениями значений свойств — реализовать `IConnection` в доступном для подключения объекте, чтобы указать наличие исходящих интерфейсов. Если требуется локализовать имя свойства, создайте производный объект из <xref:System.ComponentModel.ICustomTypeDescriptor>. Реализация <xref:System.ComponentModel.ICustomTypeDescriptor> может изменять возвращаемые дескрипторы свойств и имя свойства. Чтобы локализовать описание, создайте атрибут, который является производным от <xref:System.ComponentModel.DescriptionAttribute>, и переопределите свойство Description.

#### <a name="considerations-in-implementing-the-iconnection-interface"></a>Рекомендации по реализации интерфейса IConnection

1. `IConnection` предоставляет доступ к подобъекту перечислителя с интерфейсом <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnectionPoints>. Он также предоставляет доступ для всех подобъектов точки соединения, каждый из которых реализует интерфейс <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint>.

2. Любой объект обзора отвечает за реализацию события <xref:Microsoft.VisualStudio.OLE.Interop.IPropertyNotifySink>. Окно **Свойства** будет содержать рекомендацию события, заданного через `IConnection`.

3. Точка подключения определяет, сколько подключений (одно или несколько) разрешено в его реализации <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.Advise%2A>. Точка подключения, которая разрешает только один интерфейс, может возвращать <xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL> из метода <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.EnumConnections%2A>.

4. Клиент может вызвать интерфейс `IConnection` для получения доступа к подобъекту перечислителя с интерфейсом <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnectionPoints>. Интерфейс <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnectionPoints> затем можно вызвать для перечисления точек подключения для каждого исходящего идентификатора интерфейса (IID).

5. `IConnection` также можно вызывать для получения доступа к подобъектам точки подключения с интерфейсом <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> для каждого исходящего IID. Через <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> интерфейс клиент запускает или завершает цикл рекомендаций с подключаемым объектом и собственной синхронизацией клиента. Клиент также может вызвать <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> интерфейс для получения объекта перечислителя с <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnections> интерфейсом для перечисления известных им соединений.

## <a name="getting-field-descriptions-from-the-properties-window"></a><a name="getting-field-descriptions-from-the-properties-window"></a> Получение описаний полей из окна «Свойства»
В нижней части окна **Свойства** в области описания отображаются сведения, относящиеся к выбранному полю свойства. Эта функция включена по умолчанию. Если необходимо скрыть поле описания, правой кнопкой мыши щелкните окно **Свойства** и выберите пункт **Описание**. При этом также снимается флажок рядом с заголовком **Описание** в окне меню. Чтобы отобразить поле повторно, выполните те же действия для включения пункта **Описание** .

 Сведения в поле "Описание" поступают из <xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo>. Каждый метод, интерфейс, компонентный класс и т. д. может иметь нелокализованный атрибут `helpstring` в библиотеке типов. Окно **Свойства** извлекает строку из <xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo.GetDocumentation%2A> .

### <a name="to-specify-localized-help-strings"></a>Указание локализованных строк справки

1. Добавьте атрибут `helpstringdll` в инструкцию библиотеки в библиотеке типов (`typelib`).

   > [!NOTE]
   > Этот шаг является необязательным, если библиотека типов находится в файле библиотеки (OLB-файле).

2. Укажите атрибуты `helpstringcontext` для строк. Можно также указать атрибуты `helpstring` .

    Они отличаются от атрибутов `helpfile` и `helpcontext` , которые содержатся в реальных разделах справки в формате CHM.

   Чтобы получить сведения о описании, отображаемые для выделенного имени свойства, в окне **свойств** вызывается <xref:System.Runtime.InteropServices.ComTypes.ITypeInfo2.GetDocumentation2%2A> выбранное свойство, в котором указывается требуемый `lcid` атрибут для выходной строки. На внутреннем уровне <xref:System.Runtime.InteropServices.ComTypes.ITypeInfo2> находит DLL-файл, указанный в атрибуте `helpstringdll`, и вызывает в этом файле метод `DLLGetDocumentation` с заданным контекстом и атрибутом `lcid`.

   Подпись и реализация метода `DLLGetDocumentation` выглядят следующим образом.

```cpp
STDAPI DLLGetDocumentation
(
   ITypeLib * /* ptlib */,
   ITypeInfo * /* ptinfo */,
   LCID /* lcid */,
   DWORD dwCtx,
   BSTR * pbstrHelpString
);
```

 Функция `DLLGetDocumentation` должна быть функцией экспорта, определенной в DEF-файле библиотеки DLL.

 На внутреннем уровне создается OLB-файл, который на самом деле является библиотекой DLL. Эта библиотека DLL содержит один ресурс — файл библиотеки типов (TLB-файл) — и одну экспортированную функцию — `DLLGetDocumentation`.

 Что касается OLB-файлов, атрибут `helpstringdll` является необязательным, так как это тот же файл, содержащий сам TLB-файл.

 Таким образом, чтобы строки отображались в области **Описание** , нужно по меньшей мере указать атрибут `helpstring` в библиотеке типов. Если эти строки требуется локализовать, необходимо указать необязательный атрибут `helpstringdll` и обязательный атрибут `helpstringcontext` , а затем реализовать `DLLGetDocumentation`.

 При получении локализованных сведений с помощью атрибута `helpstringcontext` idl и `DLLGetDocumentation`реализовывать дополнительные интерфейсы не нужно.

 Другим способом получения локализованного имени и описания свойства является реализация метода <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.GetLocalizedPropertyInfo%2A>. Дополнительные сведения, относящиеся к реализации этого метода, см. в статье [Properties Window Fields and Interfaces](../../extensibility/internals/properties-window-fields-and-interfaces.md).

## <a name="see-also"></a>См. также

- [Расширение свойств](../../extensibility/internals/extending-properties.md)
