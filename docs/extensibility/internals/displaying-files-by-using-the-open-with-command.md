---
title: Отображение файлов при помощи команды "Открыть с помощью" | Документация Майкрософт
description: Сведения о том, как проект может вызвать команду Open с в интегрированной среде разработки (IDE) Visual Studio для отображения файлов.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project types, supporting Open With command
- Open With command
- persistence, supporting Open With command
ms.assetid: 53794bc3-1b73-4d40-954e-cfade1abddcf
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: e45e2c601873641b5ac79c54fd6709eb3f45f95d
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105069820"
---
# <a name="display-files-by-using-the-open-with-command"></a>Отображение файлов при помощи команды "Открыть с помощью"
Проект может попросить интегрированной среды разработки отобразить диалоговое окно " **Открыть с помощью** ". Этот запрос предлагает пользователю открыть файл с выбранными стандартными редакторами. Этот процесс описан в следующих шагах.

1. Проект вызывает <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> , указывая значение `OSE_UseOpenWithDialog` для `OSEOpenDocEditor` параметра.

2. На основе расширения имени файла документа интегрированная среда разработки определяет, какие редакторы, перечисленные в реестре, могут открыть указанный документ и отобразить эти сведения в диалоговом окне **Открыть с помощью** .

    > [!NOTE]
    > Проекты, имеющие встроенный редактор, который должен быть добавлен в диалоговое окно « **Открыть с помощью** », должны зарегистрировать фабрику редактора для каждого такого редактора. Встроенные редакторы работают только вместе с определенным типом проекта, который применяется в реализации <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> метода. Интегрированная среда разработки имеет встроенную фабрику редактора для основного текстового редактора и двоичного редактора. Интегрированная среда разработки также создает экземпляр фабрики редактора от имени каждой зарегистрированной ассоциации файлов Windows. Примером такого файла является Microsoft Word.

3. Как только пользователь выбирает элемент в диалоговом окне **Открыть с помощью** , интегрированная среда разработки открывает документ путем вызова <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> метода. Дополнительные сведения см. [в разделе как открыть стандартные редакторы](../../extensibility/how-to-open-standard-editors.md).

## <a name="see-also"></a>См. также
- [Открытие и сохранение элементов проекта](../../extensibility/internals/opening-and-saving-project-items.md)
- [Отображение файлов с помощью команды "открыть файл"](../../extensibility/internals/displaying-files-by-using-the-open-file-command.md)
- [Руководство. Открытие стандартных редакторов](../../extensibility/how-to-open-standard-editors.md)
