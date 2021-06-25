---
title: Интерфейсы языковой службы прежних версий | Документация Майкрософт
description: Сведения о интерфейсах, доступных в пакете SDK для Visual Studio, которые предоставляют функции устаревшей языковой службы.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IVsLanguageInfo interface
- language services, objects
ms.assetid: 03b2d507-f463-417e-bc22-bdac68eeda52
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 75697e1d212b24b743fed62284b384985749fe7b
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/25/2021
ms.locfileid: "112898608"
---
# <a name="legacy-language-service-interfaces"></a>Интерфейсы языковой службы прежних версий
Для любого конкретного языка программирования в каждый момент времени может существовать только один экземпляр языковой службы. Однако одна языковая служба может обслуживать несколько редакторов.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] не связывает языковую службу с каким-либо конкретным редактором. Поэтому при запросе операции языковой службы необходимо выбрать соответствующий редактор в качестве параметра.

## <a name="common-interfaces-associated-with-language-services"></a>Общие интерфейсы, связанные с языковой службой
 Редактор получает языковую службу, вызывая <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A> для соответствующего пакета VSPackage. Идентификатор службы (SID), переданный в этом вызове, определяет запрашиваемую языковую службу.

 Интерфейсы основной языковой службы можно реализовать на любом числе отдельных классов. Однако распространенный подход заключается в реализации следующих интерфейсов в одном классе:

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo>

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems>

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageDebugInfo>

- Среда <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageBlock> (необязательно)

  <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo>Интерфейс должен быть реализован на всех языковых службах. Он предоставляет сведения о языковой службе, такие как локализованное название языка, расширения имен файлов, связанные со службой языка, и способ получения цветового выделения.

## <a name="additional-language-service-interfaces"></a>Дополнительные интерфейсы языковой службы
 Другие интерфейсы могут предоставляться в вашей языковой службе. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] запрашивает отдельный экземпляр этих интерфейсов для каждого экземпляра текстового буфера. Поэтому следует реализовать каждый из этих интерфейсов на своем собственном объекте. В следующей таблице показаны интерфейсы, для которых требуется один экземпляр для каждого экземпляра текстового буфера.

|Интерфейс|Описание|
|---------------|-----------------|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager>|Управляет оформлением окна кода, например раскрывающимся полосой. Этот интерфейс можно получить с помощью <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetCodeWindowManager%2A> метода. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager>По одному окну кода.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>|Замечает ключевые слова языка и разделители. Этот интерфейс можно получить с помощью <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> метода. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> вызывается во время рисования. Старайтесь не допустить интенсивного выполнения вычислительных операций в <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> или производительности.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData>|Предоставляет подсказки параметров IntelliSense. Когда языковая служба распознает символ, указывающий, что следует отображать данные метода, например открывающую скобку, он вызывает <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow.SetMethodData%2A> метод, чтобы уведомить текстовое представление о том, что языковая служба готова отобразить подсказку сведений о параметрах. Затем текстовое представление обращается обратно к языковой службе с помощью методов <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData> интерфейса, чтобы получить необходимую информацию для отображения подсказки.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet>|Обеспечивает завершение операторов IntelliSense. Когда языковая служба готова к отображению списка завершения, она вызывает <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> метод в текстовом представлении. Затем текстовое представление обращается обратно к языковой службе с помощью методов <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> объекта.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter>|Позволяет изменять текстовое представление с помощью обработчика команд. Класс, в котором реализуется <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter> интерфейс, должен также реализовать <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> интерфейс. Текстовое представление получает <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter> объект, запрашивая <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> объект, который передается в <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> метод. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter>Для каждого представления должен быть один объект.|
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|Перехватывает команды, которые пользователь вводит в окно кода. Отслеживайте выходные данные <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> реализации, чтобы предоставить пользовательские сведения о завершении и просмотреть изменения<br /><br /> Чтобы передать <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> объект в текстовое представление, вызовите <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> .|

## <a name="see-also"></a>См. также
- [Разработка языковой службы прежних версий](../../extensibility/internals/developing-a-legacy-language-service.md)
- [Контрольный список. Создание языковой службы прежних версий](../../extensibility/internals/checklist-creating-a-legacy-language-service.md)
