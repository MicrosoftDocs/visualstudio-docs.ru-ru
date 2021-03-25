---
title: Устранение неполадок регистрации пакета RegPkg | Документация Майкрософт
description: Используйте эти сведения для устранения неполадок с регистрацией пакетов RegPkg в Visual Studio. Используйте версию RegPkg, подходящую для вашего пакета.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: troubleshooting
helpviewer_keywords:
- RegPkg
ms.assetid: f33f822f-697a-4bad-9c10-554b4c8f6246
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 48e3699b095ed7b9d0e72cf7b09ad02e26ac5a51
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105090763"
---
# <a name="troubleshooting-regpkg-package-registration"></a>Устранение неполадок регистрации пакета RegPkg
> [!NOTE]
> Для регистрации пакетов в Visual Studio предпочтительным способом является использование файлов pkgdef. Это позволяет развертывать расширения без доступа к системному реестру. Файлы pkgdef создаются с помощью [служебной программы CreatePkgDef](../../extensibility/internals/createpkgdef-utility.md).

 Чтобы зарегистрировать пакет с помощью RegPkg в [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , необходимо использовать версию regpkg, подходящую для вашего пакета.

## <a name="regpkg-versions-related-to-package-versions"></a>Версии RegPkg, связанные с версиями пакетов
 Существует две версии RegPkg. Одна версия включена в [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . Используйте эту версию для регистрации пакетов, созданных с помощью одной из следующих сборок:

1. Microsoft.VisualStudioShell.9.0.dll

2. Microsoft.VisualStudioShell.10.0.dll

3. Microsoft.VisualStudioShell.11.0.dll

   Он не может зарегистрировать пакеты, созданные с помощью предыдущей Microsoft.VisualStudio.Shell.dll сборки.

   Более ранняя версия RegPkg может регистрировать пакеты, созданные с помощью сборки Microsoft.VisualStudio.Shell.dll. Однако он не может зарегистрировать пакеты, созданные с помощью более поздних версий этой сборки.

## <a name="see-also"></a>См. также
- [VSPackages](../../extensibility/internals/vspackages.md)
- [Устранение неполадок в Visual Studio](/troubleshoot/visualstudio/welcome-visual-studio/)
