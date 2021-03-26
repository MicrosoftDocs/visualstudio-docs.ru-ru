---
title: Реализация генераторов Single-File | Документация Майкрософт
description: Узнайте, как использовать настраиваемое средство, реализующее интерфейс Ивссинглефилеженератор, для расширения Visual Basic и систем проектов Visual C# в Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- custom tools, implementing
- projects [Visual Studio SDK], extensibility
- projects [Visual Studio SDK], managed custom tools
ms.assetid: fe9ef6b6-4690-4c2c-872c-301c980d17fe
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: a46ebce9a554c90e23f9ce5f29680fc3ef86b337
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105085836"
---
# <a name="implementing-single-file-generators"></a>Реализация генераторов одного файла
Пользовательское средство, которое иногда называют генератором одиночных файлов, может использоваться для расширения [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] системы проектов и в [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . Пользовательский инструмент — это COM-компонент, реализующий <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator> интерфейс. С помощью этого интерфейса пользовательское средство преобразует один входной файл в отдельный выходной файл. Результатом преобразования может быть исходный код или любые другие полезные выходные данные. Два примера пользовательских файлов кода — это код, создаваемый в ответ на изменения в визуальном конструкторе и файлах, созданных с помощью языка описания веб-служб (WSDL).

 При загрузке пользовательского инструмента или сохранении входного файла система проекта вызывает <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.Generate%2A> метод и передает ссылку на <xref:Microsoft.VisualStudio.Shell.Interop.IVsGeneratorProgress> интерфейс обратного вызова, при котором средство может сообщить пользователю о ходе выполнения.

 Выходной файл, формируемый настраиваемым инструментом, добавляется в проект с зависимостью от входного файла. Система проекта автоматически определяет имя выходного файла на основе строки, возвращаемой реализацией пользовательского инструмента <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.DefaultExtension%2A> .

 Пользовательский инструмент должен реализовывать <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator> интерфейс. При необходимости пользовательские инструменты поддерживают <xref:Microsoft.VisualStudio.OLE.Interop.IObjectWithSite> интерфейс для получения сведений из источников, отличных от входного файла. В любом случае, прежде чем использовать пользовательский инструмент, необходимо зарегистрировать его в системе или в [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] локальном реестре. Дополнительные сведения о регистрации пользовательских средств см. в разделе [Регистрация генераторов одного файла](../../extensibility/internals/registering-single-file-generators.md).

## <a name="see-also"></a>См. также
- [Предоставление типов конструкторам визуальных элементов](../../extensibility/internals/exposing-types-to-visual-designers.md)
