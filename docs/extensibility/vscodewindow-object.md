---
title: Объект Вскодевиндов | Документация Майкрософт
description: Сведения о окнах кода, которые являются специализированными окнами документов, которые могут содержать одно или несколько текстовых представлений, обычно это объект Встекствиев.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- VSCodeWindow
helpviewer_keywords:
- views [Visual Studio SDK], VSCodeWindow object
- VsCodeWindow object
ms.assetid: cf5fe926-e784-4098-bc01-cac49c7c55c6
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 77839bf80f30de3177f647795ffb89aa3e103d58
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105062425"
---
# <a name="vscodewindow-object"></a>Объект Вскодевиндов
Окно кода — это специализированное окно документа, которое может содержать одно или несколько текстовых представлений, обычно это <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView> объект.

 В архитектуре окно кода — это окно документа, которое находится в рамке окна. Функционально окно кода — это просто окно документа с дополнительными функциями. В режиме многодокументного интерфейса (MDI) окно кода является дочерним фреймом MDI. Дополнительные сведения см. [в разделе Настройка окон кода с помощью API прежних версий](/previous-versions/visualstudio/visual-studio-2015/extensibility/customizing-code-windows-by-using-the-legacy-api?preserve-view=true&view=vs-2015).

 В следующей таблице содержатся интерфейсы в <xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow> объекте.

|Метод|Описание|
|------------|-----------------|
|<xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>|Предоставляет универсальный механизм доступа для определения службы, которая идентифицируется глобальным уникальным идентификатором (GUID).|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>|Представляет дочерний интерфейс многодокументного интерфейса (MDI), содержащий одно или несколько представлений кода.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>|Заполняет рамку окна.|

## <a name="see-also"></a>См. также
- <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>
- [Изменение фигур](https://www.microsoft.com/download/details.aspx?id=55984)