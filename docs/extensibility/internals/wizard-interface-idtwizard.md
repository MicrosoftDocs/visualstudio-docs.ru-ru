---
title: Интерфейс мастера (Идтвизард) | Документация Майкрософт
description: Интегрированная среда разработки использует интерфейс Идтвизард для взаимодействия с мастерами. Мастера должны реализовать этот интерфейс для установки в интегрированной среде разработки.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDTWizard interface
- wizards, interface
ms.assetid: 09618d9d-d115-45b6-bccc-de328994b39c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 930996de7fa5366463ec2d60f7cf96d941f6c243
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/25/2021
ms.locfileid: "112898621"
---
# <a name="wizard-interface-idtwizard"></a>Интерфейс мастера (IDTWizard)
Интегрированная среда разработки (IDE) использует <xref:EnvDTE.IDTWizard> интерфейс для взаимодействия с мастерами. Мастера должны реализовать этот интерфейс для установки в интегрированной среде разработки.

 <xref:EnvDTE.IDTWizard.Execute%2A>Метод является единственным методом, связанным с <xref:EnvDTE.IDTWizard> интерфейсом. Мастера реализуют этот метод, и интегрированная среда разработки вызывает метод для интерфейса. В следующем примере показана сигнатура метода.

```
/* IDTWizard Method */
STDMETHOD(Execute)(THIS_
   /* [in] */ IDispatch *Application,
   /* [in] */ long hwndOwner,
   /* [in] */ SAFEARRAY * *ContextParams,
   /* [in] */ SAFEARRAY * *CustomParams,
   /* [out] [in] */ wizardResult *RetVal
   );
```

 Механизм запуска аналогичен для мастеров " **Новый проект** " и " **Добавление новых элементов** ". Для запуска можно вызвать <xref:EnvDTE.IDTWizard> интерфейс, определенный в дтеинтернал. h. Единственное различие — это набор контекстных и пользовательских параметров, которые передаются в интерфейс при вызове интерфейса.

 Ниже приведена информация о <xref:EnvDTE.IDTWizard> интерфейсе, который мастер должен реализовать для работы в [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] интегрированной среде разработки. Интегрированная среда разработки вызывает <xref:EnvDTE.IDTWizard.Execute%2A> метод в мастере, передавая ему следующее:

- Объект DTE

     Объект DTE является корнем модели автоматизации.

- Маркер для диалогового окна окна, как показано в сегменте кода `hwndOwner ([in] long)` .

     Мастер использует его `hwndOwner` в качестве родительского для диалогового окна мастера.

- Контекстные параметры передаются в интерфейс как Variant для SAFEARRAY, как показано в сегменте кода `[in] SAFEARRAY (VARIANT)* ContextParams` .

     Параметры контекста содержат массив значений, относящихся к типу запуска мастера и текущему состоянию проекта. Интегрированная среда разработки передает параметры контекста в мастер. Дополнительные сведения см. в разделе [Параметры контекста](../../extensibility/internals/context-parameters.md).

- Пользовательские параметры, передаваемые интерфейсу как Variant для SAFEARRAY, как показано в сегменте кода `[in] SAFEARRAY (VARIANT)* CustomParams` .

     Пользовательские параметры содержат массив определяемых пользователем параметров. VSZ-файл передает в интегрированную среду разработки пользовательские параметры. Значения определяются `Param=` инструкциями. Дополнительные сведения см. в разделе [пользовательские параметры](../../extensibility/internals/custom-parameters.md).

- Возвращаемые значения для интерфейса

    ```
    wizardResultSuccess = -1,
    wizardResultFailure = 0
    wizardResultCancel = 1
    wizardResultBackout = 2
    ```

## <a name="see-also"></a>См. также
- [Параметры контекста](../../extensibility/internals/context-parameters.md)
- [Пользовательские параметры](../../extensibility/internals/custom-parameters.md)
- [Мастеры](../../extensibility/internals/wizards.md)
- [Файл мастера (VSZ-файл)](../../extensibility/internals/wizard-dot-vsz-file.md)
