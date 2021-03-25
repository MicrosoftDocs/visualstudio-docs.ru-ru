---
title: Сведения о параметре в устаревшем языке Service1 | Документация Майкрософт
description: Узнайте, как реализовать подсказку о параметрах IntelliSense, которая предоставляет пользователям указания в устаревшей языковой службе.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services, method tips
- method tips
- language services, parameter info tooltip
- IVsMethodData interface
- Parameter Info (IntelliSense)
ms.assetid: f367295e-45b6-45d2-9ec8-77481743beef
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 4dade924ef89be22161c598ba0ae64084c0697ea
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105061151"
---
# <a name="parameter-info-in-a-legacy-language-service-1"></a>Сведения о параметрах в устаревшей языковой службе 1
Подсказка о параметрах IntelliSense предоставляет пользователям подсказки о том, где они находятся в языковой конструкции.

 Устаревшие языковые службы реализуются как часть VSPackage, но более новым способом реализации функций языковой службы является использование расширений MEF. Дополнительные сведения см. в разделе [расширение редактора и языковых служб](../../extensibility/extending-the-editor-and-language-services.md).

> [!NOTE]
> Рекомендуется как можно скорее начать использовать новый API редактора. Это улучшит производительность языковой службы и позволит использовать новые функции редактора.

## <a name="how-parameter-info-tooltips-work"></a>Как работают всплывающие подсказки о параметрах
 При вводе инструкции в редакторе VSPackage отображает небольшое окно подсказки, содержащее определение вводимой инструкции. Например, если ввести оператор Microsoft Foundation Classes (MFC) `pMainFrame ->UpdateWindow` и нажать клавишу открывающей скобки, чтобы начать вывод списка параметров, появится подсказка метода, отображающая определение `UpdateWindow` метода.

 Подсказки сведений о параметрах обычно используются вместе с завершением операторов. Они наиболее полезны для языков с параметрами или другими отформатированными сведениями после имени метода или ключевого слова.

 Подсказки сведений о параметрах инициируются языковой службой посредством перехвата команд. Для перехвата пользовательских символов объект языковой службы должен реализовать <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> интерфейс и передать ему указатель на <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> реализацию, вызвав <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> метод в <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> интерфейсе. Фильтр команд перехватывает команды, введенные в окно кода. Отслеживайте сведения о командах, чтобы выяснить, когда следует отображать сведения о параметрах пользователю. Вы можете использовать один и тот же фильтр команд для завершения операторов, маркеров ошибок и т. д.

 При вводе ключевого слова, для которого языковая служба может предоставлять указания, служба языка создает <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow> объект и вызывает <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateTipWindow%2A> метод в <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> интерфейсе, чтобы уведомить интегрированную среду разработки о необходимости отобразить указание. Создайте <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow> объект с помощью `VSLocalCreateInstance` и укажите компонентный класс `CLSID_VsMethodTipWindow` . `VsLocalCreateInstance` — Это функция, определенная в файле заголовка всдок. h, который вызывает `QueryService` для локального реестра и вызывает `CreateInstance` объект для `CLSID_VsMethodTipWindow` .

## <a name="providing-a-method-tip"></a>Предоставление подсказки метода
 Чтобы предоставить подсказку метода, вызовите <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow.SetMethodData%2A> метод в <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow> интерфейсе, передав ему свою реализацию <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData> интерфейса.

 При <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData> вызове класса его методы вызываются в следующем порядке:

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetContextStream%2A>

     Возвращает расположение и длину соответствующих данных в текущем текстовом буфере. Это указывает интегрированной среде разработки не скрывать эти данные с помощью окна подсказки.

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetCurMethod%2A>

     Возвращает номер метода (Отсчитываемый от нуля индекс), который должен отображаться изначально. Например, если вы возвращаете ноль, то изначально представляется первый перегруженный метод.

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetOverloadCount%2A>

     Возвращает количество перегруженных методов, которые применимы в текущем контексте. Если для этого метода возвращается значение больше 1, то в текстовом представлении отображаются стрелки вверх и вниз. Если щелкнуть стрелку вниз, среда IDE вызывает <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.NextMethod%2A> метод. Если щелкнуть стрелку вверх, интегрированная среда разработки вызовет <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.PrevMethod%2A> метод.

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetMethodText%2A>

     Текст подсказки сведений о параметре создается во время нескольких вызовов <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetMethodText%2A> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetParameterText%2A> методов и.

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetParameterCount%2A>

     Возвращает число параметров, отображаемых в методе.

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetParameterText%2A>

     Если возвращается номер метода, соответствующий перегрузке, которую требуется отобразить, вызывается этот метод, после чего вызывается <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.UpdateView%2A> метод.

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.UpdateView%2A>

     Информирует языковую службу о необходимости обновления редактора при отображении подсказки метода. В <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.UpdateView%2A> методе вызовите следующую команду:

    ```
    <pTxWin> ->UpdateTipWindow(<pTip>, UTW_CONTENTCHANGED | UTW_CONTEXTCHANGED).
    ```

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A>

     При <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A> закрытии окна подсказки метода вы получаете вызов метода.
