---
title: Подготовка к отладке приложений Windows Forms | Документация Майкрософт
description: Выполните действия для подготовки к отладке приложений Windows Forms, созданных с помощью шаблона проекта Windows Forms в Visual Studio.
ms.custom: SEO-VS-2020, seodec18
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging Windows applications
- Windows applications, debugging
- debugging [Visual Studio], Windows applications
- debugging [C#], Windows applications
- debugging [Visual Basic], Windows applications
ms.assetid: 7092ee7f-8378-4def-aef8-1695bd97cf14
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: a59e454238bf362aec20916c6d1f6ed2e4ff187f
ms.sourcegitcommit: 5654b7a57a9af111a6f29239212d76086bc745c9
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/03/2021
ms.locfileid: "101684149"
---
# <a name="debugging-preparation-windows-forms-applications"></a>Подготовка к отладке: Приложения Windows Forms

Шаблон проекта приложения Windows Forms создает приложение Windows Forms. Отладка приложений такого типа в [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] не вызывает никаких затруднений. Сведения о создании проекта этого типа см. в статье [Создание приложения Windows Forms на C# в Visual Studio](../ide/create-csharp-winform-visual-studio.md).

 При создании проекта Windows Forms из шаблона проекта, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] автоматически создает требуемые параметры для отладки и выпуска. При необходимости эти параметры можно изменить. Эти параметры могут быть изменены в диалоговом окне **\<project name> Страницы свойств** (**Мой проект** в Visual Basic).

 Дополнительные сведения см. в статье [Рекомендуемые параметры свойств](../debugger/managed-debugging-recommended-property-settings.md).

 В следующей таблице приведены дополнительные параметры, рекомендуемые к использованию.

### <a name="configuration-properties-in-debug-tab"></a>"Свойства конфигурации" во вкладке "Отладка"

|**Имя свойства**|**Параметр**|
|-----------------------|-----------------|
|**Действие при запуске**|— Установите **Запуск проекта** в большинстве случаев. Установите **Запуск внешней программы**, если требуется запускать другой исполняемый файл при запуске отладки (обычно для отладки DLL).|

 Можно выполнять отладку приложений Windows Forms из [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] или путем присоединения к уже запущенному приложению. См. сведения о [присоединении к выполняемым процессам](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).

### <a name="to-debug-a-c-f-or-visual-basic-windows-forms-application"></a>Выполнение отладки приложения Windows Forms на C#, F# или Visual Basic

1. Откройте проект в [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].

2. Создайте точки останова, если требуется.

    Поскольку приложения Windows Forms управляются событиями, точки останова появятся в коде обработчиков событий, или в методах, вызываемых ими. Типичные события, в которые стоит помещать точки останова:

   1. события, связанные с элементом управления, такие как Click, Enter, и т.д.;

   2. события, связанные с запуском приложений и завершением работы, такие как Load, Activated и т. д.;

   3. события, связанные с фокусом и проверками.

      Подробнее см. в разделе [Создание обработчиков событий в Windows Forms](/dotnet/framework/winforms/creating-event-handlers-in-windows-forms).

3. В меню **Отладка** выберите команду **Запуск**.

4. Отладка с использованием конкретных методик описывается в статье [Первое знакомство с отладчиком](../debugger/debugger-feature-tour.md).

## <a name="see-also"></a>См. также
- [Отладка управляемого кода](../debugger/debugging-managed-code.md)
- [Типы проектов C#, F# и Visual Basic](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)
- [Практическое руководство. Настройка конфигураций отладки и выпуска](../debugger/how-to-set-debug-and-release-configurations.md)
- [Параметры проекта для конфигураций отладки C#](../debugger/project-settings-for-csharp-debug-configurations.md)
- [Параметры проекта для конфигурации отладки Visual Basic](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)
- [Подключение к выполняющимся процессам](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)
- [Windows Forms](/dotnet/framework/winforms/index)