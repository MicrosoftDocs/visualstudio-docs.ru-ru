---
title: Поддержка автоматизации для страниц параметров | Документация Майкрософт
description: Узнайте, как сделать страницы параметров настраиваемых инструментов в пакетах VSPackage доступными для модели автоматизации Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Tools Options pages [Visual Studio SDK], automation support
- automation [Visual Studio SDK], creating Tools Options pages
ms.assetid: 0b25b82c-7432-4e0a-9e84-350269ba8260
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: b587af698cf7f044c02baab1a8207be1457d6cfd
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105086226"
---
# <a name="automation-support-for-options-pages"></a>Поддержка автоматизации для страниц параметров
Пакеты VSPackage могут предоставлять диалоговые окна настраиваемых **параметров** в меню **Сервис** (**Сервис параметры** страницы) в [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] и предоставлять их для модели автоматизации.

## <a name="tools-options-pages"></a>Сервис Параметры - страницы
 Для создания страницы **параметров средств** пакет VSPackage должен предоставить реализацию пользовательского элемента управления, возвращаемую в среду, с помощью реализации <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> метода VSPackage. (Или для управляемого кода — <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> метод.)

 Это необязательно, но настоятельно рекомендуется, чтобы разрешить доступ к этой новой странице через модель автоматизации. Для этого выполните следующие шаги.

1. Расширьте <xref:EnvDTE._DTE.Properties%2A> объект с помощью реализации объекта, производного от IDispatch.

2. Возврат реализации <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> метода (или для управляемого кода <xref:Microsoft.VisualStudio.Shell.Package.GetAutomationObject%2A> метода) в объект, производный от IDispatch.

3. Когда потребитель автоматизации вызывает <xref:EnvDTE._DTE.Properties%2A> метод на странице настраиваемого свойства **параметра** , среда использует <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> метод для получения реализации автоматизации страницы настраиваемых **средств** .

4. Затем объект автоматизации VSPackage используется для предоставления каждого <xref:EnvDTE.Property> возвращаемого объекта <xref:EnvDTE._DTE.Properties%2A> .

   Пример реализации настраиваемой страницы **параметров средств** см. в разделе [VSSDK Samples](https://github.com/Microsoft/VSSDK-Extensibility-Samples).

## <a name="see-also"></a>См. также
- [Предоставление доступа к объектам проекта](../../extensibility/internals/exposing-project-objects.md)
