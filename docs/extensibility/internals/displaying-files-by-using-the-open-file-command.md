---
title: Отображение файлов с помощью команды "открыть файл" | Документация Майкрософт
description: Сведения о том, как интегрированная среда разработки (IDE) Visual Studio обрабатывает команды открыть файл в меню файл для отображения файлов.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project types, supporting Open File command
- Open File command
- persistence, supporting Open File command
ms.assetid: 4fff0576-b2f3-4f17-9769-930f926f273c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: b2617050ff26536df5a94d0cb51fe74d37a55725
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105061346"
---
# <a name="display-files-by-using-the-open-file-command"></a>Отображение файлов с помощью команды "открыть файл"
Следующие шаги описывают, как интегрированная среда разработки обрабатывает команду **Open File** , доступную в меню **файл** в среде [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . Эти шаги также описывают, как проекты должны отвечать на вызовы, происходящие из этой команды.

 Когда пользователь щелкает команду **Открыть файл** в меню **файл** и выбирает файл из диалогового окна **Открытие файла** , выполняется следующая процедура:

1. С помощью таблицы выполняющегося документа интегрированная среда разработки определяет, открыт ли файл в проекте.

    - Если файл открыт, интегрированная среда разработки перемещает окно.

    - Если файл не открыт, интегрированная среда разработки вызывает <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A> запрос к каждому проекту, чтобы определить, какой проект может открыть файл.

        > [!NOTE]
        > В реализации проекта <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A> Укажите значение приоритета, указывающее уровень, на котором проект открывает файл. Значения приоритета предоставляются в <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY> перечислении.

2. Каждый проект реагирует на уровень приоритета, который указывает важность, которую он накладывает на проект, чтобы открыть файл.

3. Интегрированная среда разработки использует следующие критерии, чтобы определить, какой проект открывает файл:

    - Проект, отвечающий с наивысшим приоритетом ( `DP_Intrinsic` ), открывает файл. Если несколько проектов отвечают этому приоритету, первый проект, который будет отвечать, открывает файл.

    - Если ни один проект не отвечает с наивысшим приоритетом ( `DP_Intrinsic` ), но все проекты отвечают с тем же самым низким приоритетом, активный проект открывает файл. Если проект не активен, первый проект для ответа открывает файл.

    - Если ни один из проектов не владеет файлом ( `DP_Unsupported` ), проект "Прочие файлы" открывает файл.

         Если создается экземпляр проекта прочих файлов, то проект всегда отвечает со значением `DP_CanAddAsExternal` . Это значение указывает, что проект может открыть файл. Этот проект используется для размещения открытых файлов, которые не входят в другие проекты. Список элементов в этом проекте не сохранен; Этот проект отображается в **Обозреватель решений** только в том случае, если он используется для открытия файла.

         Если проект "Прочие файлы" не указывает, что он может открыть файл, то экземпляр проекта не был создан. В этом случае интегрированная среда разработки создает экземпляр проекта прочих файлов и указывает проекту открыть файл.

4. Как только интегрированная среда разработки определит, какой проект открывает файл, он вызывает <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A> метод для этого проекта.

5. Затем проект имеет возможность открыть файл с помощью редактора конкретного проекта или стандартного редактора. Дополнительные сведения см. в статьях [как открывать редакторы для конкретного проекта](../../extensibility/how-to-open-project-specific-editors.md) и [как открывать стандартные редакторы](../../extensibility/how-to-open-standard-editors.md)соответственно.

## <a name="see-also"></a>См. также
- [Отображение файлов при помощи команды "Открыть с помощью"](../../extensibility/internals/displaying-files-by-using-the-open-with-command.md)
- [Открытие и сохранение элементов проекта](../../extensibility/internals/opening-and-saving-project-items.md)
- [Пошаговое руководство. открытие редакторов, зависящих от проекта](../../extensibility/how-to-open-project-specific-editors.md)
- [Руководство. Открытие стандартных редакторов](../../extensibility/how-to-open-standard-editors.md)
