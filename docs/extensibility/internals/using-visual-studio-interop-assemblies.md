---
title: Использование сборок взаимодействия Visual Studio | Документация Майкрософт
description: Узнайте, как сборки взаимодействия Visual Studio позволяют управляемым приложениям получать доступ к COM-интерфейсам, обеспечивающим расширяемость Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio, interop assemblies
- interop assemblies, Visual Studio
- managed VSPackages, interop assemblies
ms.assetid: 1043eb95-4f0d-4861-be21-2a25395b3b3c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: fc5f1a01c406f2457eaaa6a58e214f06fbd31127
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/02/2021
ms.locfileid: "106213658"
---
# <a name="using-visual-studio-interop-assemblies"></a>Использование сборок взаимодействия Visual Studio
Сборки взаимодействия Visual Studio позволяют управляемым приложениям получать доступ к COM-интерфейсам, обеспечивающим расширяемость Visual Studio. Существуют некоторые различия между прямыми интерфейсами COM и их версиями взаимодействия. Например, значения HRESULT обычно представлены в виде значений типа int и должны обрабатываться так же, как исключения, а параметры (особенно исходящие параметры) обрабатываются по-разному.

## <a name="handling-hresults-returned-to-managed-code-from-com"></a>Обработка значений HRESULT, возвращаемых в управляемый код из COM
 При вызове COM-интерфейса из управляемого кода проверьте значение HRESULT и при необходимости создайте исключение. Класс <xref:Microsoft.VisualStudio.ErrorHandler> содержит метод <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A>, который создает исключение COM в зависимости от переданного ему значения HRESULT.

 По умолчанию метод <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A> создает исключение каждый раз, когда ему передается значение HRESULT меньше нуля. В случаях, когда такие значения HRESULT являются допустимыми и исключения создавать не нужно, в <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A> следует передать дополнительные значения HRESULT после их проверки. Если проверяемые значения HRESULT совпадают со значениями HRESULT, явно переданными в <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A>, исключение не создается.

> [!NOTE]
> <xref:Microsoft.VisualStudio.VSConstants>Класс содержит константы для распространенных значений HRESULT, например, и <xref:Microsoft.VisualStudio.VSConstants.S_OK> <xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL> , и [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] HRESULT, например, <xref:Microsoft.VisualStudio.VSConstants.VS_E_INCOMPATIBLEDOCDATA> и <xref:Microsoft.VisualStudio.VSConstants.VS_E_UNSUPPORTEDFORMAT> . <xref:Microsoft.VisualStudio.VSConstants> также предоставляет методы <xref:Microsoft.VisualStudio.ErrorHandler.Succeeded%2A> и <xref:Microsoft.VisualStudio.ErrorHandler.Failed%2A>, которые соответствуют макросам SUCCEEDED и FAILED в COM.

 Например, рассмотрим приведенный ниже вызов функции, в котором <xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL> является допустимым возвращаемым значением, но любое другое значение HRESULT меньше нуля представляет ошибку.

 :::code language="vb" source="../../snippets/visualbasic/VS_Snippets_VSSDK/vssdkhresultinformation/vb/vssdkhresultinformationpackage.vb" id="Snippet1":::
 :::code language="csharp" source="../../snippets/csharp/VS_Snippets_VSSDK/vssdkhresultinformation/cs/vssdkhresultinformationpackage.cs" id="Snippet1":::

 Если имеется несколько допустимых возвращаемых значений, дополнительные значения HRESULT можно просто добавить в список в вызове <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A>.

 :::code language="vb" source="../../snippets/visualbasic/VS_Snippets_VSSDK/vssdkhresultinformation/vb/vssdkhresultinformationpackage.vb" id="Snippet2":::
 :::code language="csharp" source="../../snippets/csharp/VS_Snippets_VSSDK/vssdkhresultinformation/cs/vssdkhresultinformationpackage.cs" id="Snippet2":::

## <a name="returning-hresults-to-com-from-managed-code"></a>Возврат значений HRESULT в COM из управляемого кода
 Если исключений не возникает, управляемый код возвращает <xref:Microsoft.VisualStudio.VSConstants.S_OK> в вызвавшую его функцию COM. COM-взаимодействие поддерживает общие исключения, которые являются строго типизированными в управляемом коде. Например, метод, принимающий недопустимый аргумент `null`, вызывает исключение <xref:System.ArgumentNullException>.

 Если вы не знаете, какое именно исключение следует создать, но знаете, какое значение HRESULT нужно вернуть в COM, вы можете использовать метод <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A> для создания соответствующего исключения. Такой подход работает и в случае с нестандартными ошибками, например <xref:Microsoft.VisualStudio.VSConstants.VS_E_INCOMPATIBLEDOCDATA>. Метод <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A> пытается сопоставить переданное ему значение HRESULT со строго типизированным исключением. Если это ему не удается, он создает универсальное исключение COM. Конечным результатом является то, что значение HRESULT, которое вы передали в <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A> из управляемого кода, возвращается в вызвавшую этот код функцию COM.

> [!NOTE]
> Исключения снижают производительность и предназначены для указания на аномальные состояния программы. Часто наступающие условия следует обрабатывать внутри программы без создания исключений.

## <a name="iunknown-parameters-passed-as-type-void"></a>Параметры IUnknown передаются как тип void * *
 Найдите параметры [out], которые определены как тип `void **` в COM-интерфейсе, но определены как `[``iid_is``]` в [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] прототипе метода сборки взаимодействия.

 Иногда COM-интерфейс создает `IUnknown` объект, а COM-интерфейс передает его как тип `void **` . Эти интерфейсы особенно важны, поскольку если переменная определена как [out] в IDL, то `IUnknown` объект подсчитывается по ссылке с помощью `AddRef` метода. Если объект не обрабатывается должным образом, происходит утечка памяти.

> [!NOTE]
> `IUnknown`Объект, созданный COM-интерфейсом и возвращаемый в переменной [out], вызывает утечку памяти, если она не была явно освобождена.

 Управляемые методы, обрабатывающие такие объекты, должны обрабатываться <xref:System.IntPtr> как указатель на `IUnknown` объект и вызывать <xref:System.Runtime.InteropServices.Marshal.GetObjectForIUnknown%2A> метод для получения объекта. Затем вызывающий объект должен привести возвращаемое значение к любому подходящему типу. Если объект больше не нужен, вызовите метод, <xref:System.Runtime.InteropServices.Marshal.Release%2A> чтобы освободить его.

 Ниже приведен пример вызова <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.QueryViewInterface%2A> метода и `IUnknown` правильной обработки объекта:

```
MyClass myclass;
Object object;
IntPtr pObj;
Guid iid = Typeof(MyClass).Guid;
int hr = windowFrame.QueryViewInterface(ref iid, out pObj);
if (NativeMethods.Succeeded(hr))
{
    try
    {
        object = Marshal.GetObjectForIUnknown(pObj);
        myclass = object;
    }
    finally
    {
        Marshal.Release(pObj);
    }
}
else
{
    // error calling QueryViewInterface
}
```

> [!NOTE]
> Для передачи `IUnknown` указателей объектов в качестве типа известны следующие методы <xref:System.IntPtr> . Обработайте их, как описано в этом разделе.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A>

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory.InitializeForOwner%2A>

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetNestedHierarchy%2A>

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.CreateProject%2A>

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.QueryViewInterface%2A>

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2.get_CfgType%2A>

## <a name="optional-out-parameters"></a>Необязательные параметры [out]
 Найдите параметры, которые определены как тип данных [out] ( `int` , `object` и т. д.) в com-интерфейсе, но они определены как массивы одного типа данных в [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] прототипе метода сборки взаимодействия.

 Некоторые COM-интерфейсы, такие как <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgs%2A> , обрабатывают [out] как необязательные. Если объект не является обязательным, эти COM-интерфейсы возвращают `null` указатель в качестве значения этого параметра вместо создания объекта [out]. Это сделано намеренно. Для этих интерфейсов `null` указатели предполагаются как часть правильного поведения VSPackage, и ошибка не возвращается.

 Так как среда CLR не позволяет использовать значение параметра [out] `null` , часть спроектированного поведения этих интерфейсов не будет напрямую доступна в управляемом коде. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Методы сборки взаимодействия для затронутых интерфейсов обдействуются по этой причине, определяя соответствующие параметры в виде массивов, так как среда CLR допускает передачу `null` массивов.

 Управляемые реализации этих методов должны `null` поставлять массив в параметр, когда ничего не возвращается. В противном случае создайте одноэлементный массив правильного типа и вставьте возвращаемое значение в массив.

 Управляемые методы, получающие сведения из интерфейсов с необязательными параметрами [out], получают параметр в виде массива. Просто изучите значение первого элемента массива. Если это не так `null` , то следует считать первый элемент, как если бы он был исходным параметром.

## <a name="passing-constants-in-pointer-parameters"></a>Передача констант в параметрах указателя
 Найдите параметры, которые определены как указатели [in] в COM-интерфейсе, но они определены как <xref:System.IntPtr> тип в [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] прототипе метода сборки взаимодействия.

 Аналогичная проблема возникает, когда COM-интерфейс передает специальное значение, например 0,-1 или-2, вместо указателя на объект. В отличие от [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] , среда CLR не позволяет приводить константы в качестве объектов. Вместо этого в [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] сборке взаимодействия определяется параметр в виде <xref:System.IntPtr> типа.

 Управляемые реализации этих методов должны использовать преимущества того факта, что у <xref:System.IntPtr> класса есть `int` и `void *` конструкторы, и, чтобы создать <xref:System.IntPtr> объект из объекта или целочисленной константы, в зависимости от ситуации.

 Управляемые методы, получающие <xref:System.IntPtr> параметры этого типа, должны использовать <xref:System.IntPtr> Операторы преобразования типов для обработки результатов. Сначала преобразуйте <xref:System.IntPtr> в `int` и проверьте его на соответствие константам с соответствующими целочисленными значениями. Если значения не совпадают, преобразуйте их в объект требуемого типа и продолжайте.

 Примеры см. в статьях <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> и <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenSpecificEditor%2A> .

## <a name="ole-return-values-passed-as-out-parameters"></a>Возвращаемые значения OLE, переданные как параметры [out]
 Ищите методы, которые имеют `retval` возвращаемое значение в COM-интерфейсе, но имеют `int` возвращаемое значение и дополнительный параметр массива [out] в [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] прототипе метода сборки взаимодействия. Должно быть ясно, что для этих методов требуется специальная обработка, поскольку [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] прототипы методов сборки взаимодействия имеют еще один параметр, чем методы COM-интерфейса.

 Многие COM-интерфейсы, которые работают с действиями OLE, отправляют сведения о состоянии OLE обратно в вызывающую программу, хранящуюся в `retval` возвращаемом значении интерфейса. Вместо использования возвращаемого значения соответствующие [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] методы сборки взаимодействия отправляют информацию обратно вызывающей программе, хранящейся в параметре массива [out].

 Управляемые реализации этих методов должны создавать одноэлементный массив того же типа, что и параметр [out], и размещать его в параметре. Значение элемента массива должно совпадать с соответствующим COM-элементом `retval` .

 Управляемые методы, вызывающие интерфейсы этого типа, должны извлечь первый элемент из массива [out]. Этот элемент можно рассматривать как `retval` возвращаемое значение из соответствующего COM-интерфейса.

## <a name="see-also"></a>См. также
- [Взаимодействие с неуправляемым кодом](/dotnet/framework/interop/index)
