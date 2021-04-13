---
title: Программа улучшения качества программного обеспечения
description: Узнайте, как управлять параметрами конфиденциальности в Visual Studio.
ms.date: 05/21/2018
ms.topic: conceptual
author: PoulChapman
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 6c7f425d87ba6316c3a3cab66f2b342b4c1141f4
ms.sourcegitcommit: 5c0e20fc6005bc1f8ca38f4122378c4ac21ba89a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/01/2021
ms.locfileid: "106110601"
---
# <a name="visual-studio-customer-experience-improvement-program"></a>Программа улучшения качества программного обеспечения Visual Studio

Программа улучшения качества программного обеспечения Visual Studio (VSCEIP) помогает Майкрософт совершенствовать Visual Studio. Эта программа [собирает сведения об ошибках](../ide/diagnostic-data-collection.md), компьютерном оборудовании и использовании Visual Studio, не прерывая работу пользователей на компьютере. Собранные сведения помогают корпорации Майкрософт понять, какие функции нуждаются в улучшении. В этом документе описано, как принять участие в программе VSCEIP или отказаться. Явный отказ предполагает отказ от **необязательного** сбора диагностических данных. Чтобы обеспечить безопасность, актуальность и производительность Visual Studio, **требуется** сбор некоторых диагностических данных. На этот процесс сбора ваш явный отказ от VSCEIP не повлияет.

[!INCLUDE [gdpr-hybrid-note](../misc/includes/gdpr-hybrid-note.md)]
> [!NOTE]
> Параметры согласия или запрета использования телеметрии VSCEIP не применяются к параметру "Сообщить о проблеме" в Visual Studio. При отправке отчетов о проблемах журналы собираются и отправляются в корпорацию Майкрософт только при предоставлении разрешения нажатием кнопки "Отправить". Если вы заинтересованы в управлении журналами перед отправкой путем нажатия кнопки "Сообщить о проблеме", дополнительные сведения см. в статье о [конфиденциальности данных отзывов](./developer-community-privacy.md).

## <a name="opt-in-or-out"></a>Управления участием в программе

Программа VSCEIP включена по умолчанию. Вы можете отключить ее или включить снова следующим образом:

1. В Visual Studio выберите **Справка** > **Отправить отзыв**, а затем выберите **Параметры**.

   Откроется диалоговое окно **Программа улучшения Visual Studio**.

1. Чтобы отказаться от участия, выберите **Я не хочу участвовать** и нажмите **ОК**. Чтобы согласиться на участие, выберите **Я хочу участвовать** и нажмите **ОК**.

   ![Диалоговое окно "Программа улучшения Visual Studio"](media/experience-improvement-program.png)

### <a name="registry-settings"></a>Параметры регистрации

Если вы устанавливаете [Build Tools для Visual Studio](https://visualstudio.microsoft.com/downloads/#build-tools-for-visual-studio-2017), обновите реестр, чтобы настроить VSCEIP. Корпоративные клиенты могут создать групповую политику на основе реестра, в которой будет включено или отключено участие в программе VSCEIP.

Ниже приведены соответствующие разделы и параметры реестра:

::: moniker range="vs-2017"

- В 64-разрядной операционной системе: ключ = **HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\VSCommon\15.0\SQM**
- В 32-разрядной операционной системе: ключ = **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VSCommon\15.0\SQM**
- Если включена групповая политика: ключ = **HKEY_LOCAL_MACHINE\Software\Policies\Microsoft\VisualStudio\SQM**

::: moniker-end

::: moniker range=">=vs-2019"

- В 64-разрядной операционной системе: ключ = **HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\VSCommon\16.0\SQM**
- В 32-разрядной операционной системе: ключ = **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VSCommon\16.0\SQM**
- Если включена групповая политика: ключ = **HKEY_LOCAL_MACHINE\Software\Policies\Microsoft\VisualStudio\SQM**

::: moniker-end

Запись = **OptIn**

Значение — (DWORD)

- **0** — отказаться (отключить VSCEIP)
- **1** — согласиться (включить VSCEIP)

> [!CAUTION]
> Неправильное изменение реестра может серьезно повредить систему. Перед внесением изменений следует сделать резервную копию всех ценных данных на компьютере. В случае возникновения неполадок после внесения изменений вручную можно использовать параметр запуска **Загрузка последней удачной конфигурации**.

Для получения информации о собранных, обработанных или переданных VSCEIP сведениях см. [Заявление о конфиденциальности Майкрософт](https://privacy.microsoft.com/privacystatement).

## <a name="see-also"></a>См. также раздел

* [Диагностическая информация, собираемая Visual Studio](diagnostic-data-collection.md)
* [Параметры обратной связи Visual Studio](../ide/feedback-options.md)
* [Как сообщить о проблеме с Visual Studio 2017](../ide/how-to-report-a-problem-with-visual-studio.md)
* [Сообщество разработчиков Visual Studio](https://aka.ms/feedback/suggest?space=8)
* [Заявление о конфиденциальности Майкрософт](https://privacy.microsoft.com/privacystatement)
