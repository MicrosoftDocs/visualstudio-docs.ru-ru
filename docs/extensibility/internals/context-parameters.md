---
title: Параметры контекста | Документация Майкрософт
description: Сведения о параметрах контекста в интегрированной среде разработки (IDE) Visual Studio, которые определяют состояние проекта при добавлении или реализации мастера.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- wizards, context parameters
- context parameters
ms.assetid: 1a062dcb-8a8f-40dd-bea9-3d10f9448966
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 14d60aa31fb586651ea6e2b00a8f8038bfaa42b9
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105057082"
---
# <a name="context-parameters"></a>Контекстные параметры
В [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] интегрированной среде разработки (IDE) можно добавлять мастера в диалоговые окна **Новый проект**, **Добавить новый элемент** или **Добавить подпроект** . Добавленные мастера можно найти в меню **файл** или щелкнув правой кнопкой мыши проект в **Обозреватель решений**. Интегрированная среда разработки передает параметры контекста в реализацию мастера. Параметры контекста определяют состояние проекта, когда интегрированная среда разработки вызывает мастер.

 Интегрированная среда разработки запускает мастера, устанавливая <xref:Microsoft.VisualStudio.Shell.Interop.VSADDITEMOPERATION> флаг в вызове метода для проекта в интегрированной среде разработки <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.AddItem%2A> . Если этот параметр задан, проект должен вызывать `IVsExtensibility::RunWizardFile` выполнение метода с помощью зарегистрированного имени мастера или GUID и других параметров контекста, которые среда IDE передает в нее.

## <a name="context-parameters-for-new-project"></a>Параметры контекста для нового проекта

| Параметр | Описание |
|-------------------------| - |
| `WizardType` | Зарегистрированный тип мастера ( <xref:EnvDTE.Constants.vsWizardNewProject> ) или GUID, указывающий тип мастера. В [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] реализации для мастера используется идентификатор GUID {0F90E1D0-4999-11D1-b6d1-00A0C90F2744}. |
| `ProjectName` | Строка, которая является уникальным [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] именем проекта. |
| `LocalDirectory` | Локальное расположение рабочих файлов проекта. |
| `InstallationDirectory` | Путь к каталогу для [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] установки. |
| `FExclusive` | Логический флаг, указывающий, что проект должен закрыть открытые решения. |
| `SolutionName` | Имя файла решения без части каталога или расширения *SLN* . Имя файла *suo* также создается с помощью `SolutionName` . Если этот аргумент не является пустой строкой, мастер использует <xref:EnvDTE._Solution.Create%2A> перед добавлением проекта с <xref:EnvDTE._Solution.AddFromTemplate%2A> . Если это имя является пустой строкой, используйте <xref:EnvDTE._Solution.AddFromTemplate%2A> без вызова <xref:EnvDTE._Solution.Create%2A> . |
| `Silent` | Логическое значение, указывающее, должен ли мастер выполняться автоматически, как если бы было нажато кнопку **Готово** ( `TRUE` ). |

## <a name="context-parameters-for-add-new-item"></a>Параметры контекста для добавления нового элемента

| Параметр | Описание |
|-------------------------| - |
| `WizardType` | Зарегистрированный тип мастера ( <xref:EnvDTE.Constants.vsWizardAddItem> ) или GUID, указывающий тип мастера. В [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] реализации для мастера используется идентификатор GUID {0F90E1D1-4999-11D1-b6d1-00A0C90F2744}. |
| `ProjectName` | Строка, которая является уникальным [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] именем проекта. |
| `ProjectItems` | Локальное расположение, содержащее рабочие файлы проекта. |
| `ItemName` | Имя добавляемого элемента. Это имя является либо именем файла по умолчанию, либо именем файла, которое пользователь вводит в диалоговом окне **Добавление элементов** . Имя основано на флагах, заданных в файле *VSDir* . Имя может иметь значение null. |
| `InstallationDirectory` | Путь к каталогу для [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] установки. |
| `Silent` | Логическое значение, указывающее, должен ли мастер выполняться автоматически, как если бы было нажато кнопку **Готово** ( `TRUE` ). |

## <a name="context-parameters-for-add-sub-project"></a>Параметры контекста для добавления подпроекта

| Параметр | Описание |
|-------------------------| - |
| `WizardType` | Зарегистрированный тип мастера ( <xref:EnvDTE.Constants.vsWizardAddSubProject> ) или GUID, указывающий тип мастера. В [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] реализации для мастера используется идентификатор GUID {0F90E1D2-4999-11D1-b6d1-00A0C90F2744}. |
| `ProjectName` | Строка, которая является уникальным [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] именем проекта. |
| `ProjectItems` | Указатель на `ProjectItems` коллекцию, в которой работает мастер. Этот указатель передается мастеру на основе выбора иерархии проекта. Пользователь обычно выбирает папку, в которую следует поместить элемент, а затем вызывает диалоговое окно **Добавление элемента** проекта. |
| `LocalDirectory` | Локальное расположение рабочих файлов проекта. |
| `ItemName` | Имя добавляемого элемента. Это имя является либо именем файла по умолчанию, либо именем файла, которое пользователь вводит в диалоговом окне **Добавление элементов** . Имя основано на флагах, заданных в файле *VSDir* . Имя может иметь значение null. |
| `InstallationDirectory` | Путь к каталогу [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] установки. |
| `Silent` | Логическое значение, указывающее, должен ли мастер выполняться автоматически, как если бы было нажато кнопку **Готово** ( `TRUE` ). |

## <a name="see-also"></a>См. также
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject2>
- [Настраиваемые параметры](../../extensibility/internals/custom-parameters.md)
- [Мастеры](../../extensibility/internals/wizards.md)
- [Файл мастера (VSZ)](../../extensibility/internals/wizard-dot-vsz-file.md)
- [Параметры контекста для запуска мастеров](/previous-versions/tz690efs(v=vs.140))