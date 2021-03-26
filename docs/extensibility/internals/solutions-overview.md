---
title: Обзор решений
description: Узнайте о внутренних компонентах решения, для разработчиков расширений, которые хотят работать с решениями в расширениях Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- solutions, about solutions
ms.assetid: 3b21e3a1-170a-4485-941e-6b04b7b27886
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 914f1744accc10eb55cfb0b321a04560c27bca05
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105069378"
---
# <a name="solutions-overview"></a>Обзор решений

Решение — это группа из одного или нескольких проектов, совместно работающих с созданием приложения. Сведения о проекте и состоянии, относящиеся к решению, хранятся в двух разных файлах решений. [Файл решения (SLN)](solution-dot-sln-file.md) основан на тексте и может размещаться под управлением исходного кода и совместно использоваться пользователями. [Файл параметров пользователя решения (. suo)](solution-user-options-dot-suo-file.md) является двоичным. В результате файл. suo не может быть помещен в систему управления исходным кодом и содержит сведения, относящиеся к пользователю.

Любой пакет VSPackage может выполнять запись в любой тип файла решения. Из-за особенностей этих файлов для записи в них можно использовать два разных интерфейса. <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps>Интерфейс записывает текстовую информацию в файл. sln, и <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts> интерфейс записывает двоичные потоки в файл. suo.

> [!NOTE]
> Проекту не обязательно явно записывать запись в файл решения; среда обрабатывает этот проект. Таким образом, если вы не хотите добавлять дополнительное содержимое специально для файла решения, вам не нужно регистрировать пакет VSPackage таким образом.

Каждый пакет VSPackage, поддерживающий сохраняемость решения, использует три интерфейса — <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence> интерфейс, который реализуется средой и вызывается пакетом VSPackage, а также `IVsPersistSolutionProps` и `IVsPersistSolutionOpts` , которые реализуются пакетом VSPackage. `IVsPersistSolutionOpts`Интерфейс должен быть реализован только в том случае, если частная информация должна быть записана пакетом VSPackage в suo-файл.

При открытии решения выполняется следующий процесс.

1. Среда считывает решение.

2. Если среда находит, то `CLSID` загружает соответствующий пакет VSPackage.

3. Если загружен пакет VSPackage, среда вызывает интерфейс для `QueryInterface` интерфейса <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage> , который необходим для пакета VSPackage.

   - При чтении из файла. sln среда вызывает метод `QueryInterface` для `IVsPersistSolutionProps` .

   - При чтении из файла SUO среда вызывает метод `QueryInterface` для `IVsPersistSolutionOpts` .

   Конкретные сведения об использовании этих файлов можно найти в [решении (. SLN) файл](../../extensibility/internals/solution-dot-sln-file.md) и [пользовательские параметры решения (. Файл SUO)](../../extensibility/internals/solution-user-options-dot-suo-file.md).

> [!NOTE]
> Если вы хотите создать новую конфигурацию решения, состоящую из двух конфигураций проектов и исключая треть из сборки, необходимо использовать пользовательский интерфейс страниц свойств или автоматизацию. Нельзя изменить конфигурации диспетчера сборки решения и их свойства напрямую, но можно управлять диспетчером сборки решения с помощью `SolutionBuild` класса из dte в модели автоматизации. Дополнительные сведения о настройке решений см. в разделе [Конфигурация решения](../../extensibility/internals/solution-configuration.md).

## <a name="see-also"></a>См. также

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence>
