---
title: Пользовательские параметры | Документация Майкрософт
description: Узнайте, как создавать настраиваемые параметры, управляющие работой мастера после запуска мастера, изменяя VSZ-файл.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- wizards, custom parameters
- custom parameters
ms.assetid: ba5c364b-66e6-47ea-9760-a0b70de8f0a0
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 3e5d8d9bf78f06dd55a88a2fbd47749224be3949
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105091101"
---
# <a name="custom-parameters"></a>Настраиваемые параметры
Пользовательские параметры управляют работой мастера после запуска мастера. Связанный *VSZ* -файл предоставляет массив определяемых пользователем параметров, которые упаковываются интегрированной средой разработки (IDE) и передаются мастеру как массив строк при запуске мастера. Затем мастер анализирует массив строк и использует эти сведения для управления фактической работой мастера. Таким образом, мастер может настроить функциональные возможности в зависимости от содержимого файла *VSZ* .

 Параметры контекста, с другой стороны, определяют состояние проекта при запуске мастера. Дополнительные сведения см. в разделе [Параметры контекста](../../extensibility/internals/context-parameters.md).

 Ниже приведен пример файла *VSZ* с пользовательскими параметрами.

```
VSWIZARD 8.0
Wizard=VsWizard.VsWizard_Engine
Param="WIZARD_NAME = Sample Wizard"
Param="WIZARD_UI = FALSE"
Param="RELATIVE_PATH = VSWizards\Classwiz\ATL"
Param="PREPROCESS_FUNCTION = CanAddATLSupport"
Param="PROJECT_TYPE = CSPROJ"
```

 Автор файла *VSZ* добавляет значения параметров. Когда пользователь выбирает **Новый проект** или **добавляет новый элемент** в меню **файл** или щелкает правой кнопкой мыши проект в **Обозреватель решений**, интегрированная среда разработки собирает эти значения в массив строк. Затем интегрированная среда разработки вызывает <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.AddItem%2A> метод проекта с <xref:Microsoft.VisualStudio.Shell.Interop.VSADDITEMOPERATION> установленным флагом, и проект вызывает <xref:EnvDTE.IVsExtensibility.RunWizardFile%2A> метод, отвечающий за запуск мастера и возврат результата.

 Мастер отвечает за синтаксический анализ массива строк и правильное взаимодействие со строками. Таким образом, реализуя пользовательские параметры, можно создать один мастер, выполняющий различные функции. Другими словами, один мастер может иметь три разных *VSZ* -файла. Каждый файл передает различные наборы пользовательских параметров для управления поведением мастера в различных ситуациях.

 Дополнительные сведения см. в разделе [Мастер (VSZ-файл)](../../extensibility/internals/wizard-dot-vsz-file.md).

## <a name="see-also"></a>См. также
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3>
- [Контекстные параметры](../../extensibility/internals/context-parameters.md)
- [Мастеры](../../extensibility/internals/wizards.md)
- [Файл мастера (VSZ)](../../extensibility/internals/wizard-dot-vsz-file.md)
