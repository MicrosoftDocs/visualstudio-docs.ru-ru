---
title: 'Контрольный список: создание языковой службы прежних версий | Документация Майкрософт'
description: Ознакомьтесь с основными действиями, которые необходимо выполнить, чтобы создать устаревшую языковую службу для редактора основных редакторов Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services
- language services, native code
ms.assetid: 8b73b341-a33a-4ab5-9390-178c9e563d2d
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 111e72714f4afd56b7b53e9cc48329ba6ce68162
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105074799"
---
# <a name="checklist-create-a-legacy-language-service"></a>Контрольный список: создание языковой службы прежних версий
В следующем контрольном списке перечислены основные шаги, которые необходимо выполнить, чтобы создать языковую службу для [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] базового редактора. Чтобы интегрировать языковую службу в [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , необходимо создать средство оценки выражений отладки. Дополнительные сведения см. в разделе [написание вычислительных выражений CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md) в [расширяемости отладчика Visual Studio](../../extensibility/debugger/visual-studio-debugger-extensibility.md).

## <a name="steps-to-create-a-language-service"></a>Действия по созданию языковой службы

1. Реализовать интерфейс <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>.

    - В VSPackage реализуйте <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> интерфейс для предоставления языковой службы.

    - Обеспечьте доступность языковой службы в интегрированной среде разработки (IDE) в вашей <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> реализации.

2. Реализуйте <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> интерфейс в основном классе языковой службы.

     <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo>Интерфейс является отправной точкой взаимодействия между основным редактором и языковой службой.

### <a name="optional-features"></a>Дополнительные функции
 Следующие функции являются необязательными и могут быть реализованы в любом порядке. Эти функции повышают функциональность языковой службы.

- Цветовая подсветка синтаксиса

  Реализовать интерфейс <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>. Ваша реализация этого интерфейса должна получить сведения о соответствующем цветовом средстве синтаксического анализа.

  <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A>Метод возвращает <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> интерфейс. Для каждого текстового буфера создается отдельный экземпляр тонирования, поэтому необходимо реализовать <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> интерфейс отдельно. Дополнительные сведения см. [в разделе цветовое выделение синтаксиса в языковой службе прежних версий](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md).

- Окно кода

  Реализуйте <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> интерфейс, чтобы разрешить языковой службе принимать уведомления при создании нового окна кода.

  <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetCodeWindowManager%2A>Метод возвращает <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> интерфейс. Языковая служба затем может добавить специальный пользовательский интерфейс в окно кода в <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager.AddAdornments%2A> . Языковая служба также может выполнять любую специальную обработку, например добавление фильтра представления текста в <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager.OnNewView%2A> .

- Фильтр представления текста

  Чтобы обеспечить завершение операторов IntelliSense в языковой службе, необходимо перехватить некоторые команды, которые в противном случае будут обработаны в текстовом представлении. Чтобы перехватить эти команды, выполните следующие действия.

  - Реализуйте <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> , чтобы участвовать в цепочке команд и управлять командами редактора.

  - Вызовите <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> метод и передайте <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> реализацию.

  - Вызовите <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.RemoveCommandFilter%2A> метод при отсоединении от представления, чтобы эти команды больше не передавались.

  Команды, которые необходимо обработать, зависят от предоставленных служб. Дополнительные сведения см. в разделе [важные команды для фильтров языковой службы](../../extensibility/internals/important-commands-for-language-service-filters.md).

  > [!NOTE]
  > <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter>Интерфейс должен быть реализован в том же объекте, что и <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> интерфейс.

- Завершение операторов

  Реализовать интерфейс <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet>.

  Поддерживает команду завершения операторов (то есть <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> ) и вызывают <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> метод в <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> интерфейсе, передавая <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> интерфейс. Дополнительные сведения см. [в разделе Завершение операторов в языковой службе прежних версий](../../extensibility/internals/statement-completion-in-a-legacy-language-service.md).

- Советы по методам

  Реализуйте <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData> интерфейс, чтобы предоставить данные для окна подсказки метода.

  Установите фильтр текстового представления для правильной обработки команд, чтобы узнать, когда следует отображать окно подсказки данных метода. Дополнительные сведения см. [в разделе сведения о параметрах в устаревшей языковой службе](../../extensibility/internals/parameter-info-in-a-legacy-language-service1.md).

- Маркеры ошибок

  Реализовать интерфейс <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient>.

  Создайте объекты маркера ошибок, реализующие <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> интерфейс, и вызовите <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.CreateLineMarker%2A> метод, передав <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> интерфейс объекта маркера ошибки.

  Обычно каждый маркер ошибки управляет элементом в окне Список задач.

- Элементы списка задач

  Реализуйте класс элемента задачи, предоставляющий <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskItem> интерфейс.

  Реализуйте класс поставщика задач, предоставляющий <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskProvider> интерфейс и <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskProvider2> интерфейс.

  Реализуйте класс перечислителя задач, предоставляющий <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumTaskItems> интерфейс.

  Зарегистрируйте поставщик задач в методе списка задач <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskList.RegisterTaskProvider%2A> .

  Получите <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskList> интерфейс, вызвав поставщик службы языковой службы с идентификатором GUID службы <xref:Microsoft.VisualStudio.Shell.Interop.SVsTaskList> .

  Создание объектов элементов задач и вызов <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskList.RefreshTasks%2A> метода в <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskList> интерфейсе при наличии новых или обновленных задач.

- Закомментировать элементы задачи

  Используйте <xref:Microsoft.VisualStudio.Shell.Interop.IVsCommentTaskInfo> интерфейс и <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumCommentTaskTokens> интерфейс для получения маркеров задачи комментария.

  Получите <xref:Microsoft.VisualStudio.Shell.Interop.IVsCommentTaskInfo> интерфейс от <xref:Microsoft.VisualStudio.Shell.Interop.SVsTaskList> службы.

  Получите <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumCommentTaskTokens> интерфейс из <xref:Microsoft.VisualStudio.Shell.Interop.IVsCommentTaskInfo.EnumTokens%2A> метода.

  Реализуйте <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskListEvents> интерфейс для прослушивания изменений в списке токенов.

- Структуризация

  Существует несколько вариантов поддержки структурирования. Например, можно поддерживать команду **Свернуть в определения** , предоставлять управляемые редактором области структуры или поддерживать регионы, управляемые клиентом. Дополнительные сведения см. в разделе [инструкции. Предоставление расширенной поддержки структурирования в языковой службе прежних версий](../../extensibility/internals/how-to-provide-expanded-outlining-support-in-a-legacy-language-service.md).

- Регистрация языковой службы

  Дополнительные сведения о регистрации языковой службы см. в статьях [Регистрация устаревшей языковой службы](../../extensibility/internals/registering-a-legacy-language-service2.md) и Управление пакетами [VSPackage](../../extensibility/managing-vspackages.md).

- Контекстно-зависимая справка

  Предоставьте контекст для редактора одним из следующих способов:

  - Предоставьте контекст для текстовых маркеров, реализовав <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerContextProvider> интерфейс.

  - Предоставьте весь контекст пользователя, реализовав <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageContextProvider> интерфейс.

## <a name="see-also"></a>См. также
- [Разработка языковой службы прежних версий](../../extensibility/internals/developing-a-legacy-language-service.md)
- [Написание вычислителя выражений CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
