---
title: Сведения о среде выполнения системы управления версиями | Документация Майкрософт
description: Сведения о добавлении проекта в систему управления версиями, когда пользователь добавляет файл в проект в системе управления версиями или через контроллер автоматизации.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], runtime details
ms.assetid: 1acd30e0-f98c-4bde-b9cd-4076845887df
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 4a25a9c29c828e1d5e70d143ccd3582dc4ec6f48
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105064219"
---
# <a name="source-control-runtime-details"></a>Сведения о среде выполнения системы управления версиями
Проект добавляется в систему управления версиями, когда пользователь добавляет файл в проект в систему управления версиями или через контроллер автоматизации, например мастер. Проект не указывает на себя, что он находится в системе управления версиями; Она поддерживает систему управления версиями, но ее необходимо добавить в нее вручную.

## <a name="registering-with-a-source-control-package"></a>Регистрация в пакете системы управления версиями
 При добавлении файла проекта в систему управления версиями среда вызывает <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2.SetSccLocation%2A> для предоставления четырех непрозрачных строк, используемых в качестве файлов cookie системой управления версиями. Храните эти строки в файле проекта. Эти строки должны передаваться в заглушку системы управления версиями (компонент Visual Studio, Управляющий пакетами управления версиями) при запуске типа проекта путем вызова <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2.RegisterSccProject%2A> . Это, в свою очередь, загружает соответствующий пакет системы управления версиями и перенаправляет вызов его реализации `IVsSccManager2::RegisterSccProject` .

## <a name="see-also"></a>См. также
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2.RegisterSccProject%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2.SetSccLocation%2A>
- [Поддержка системы управления версиями](../../extensibility/internals/supporting-source-control.md)
