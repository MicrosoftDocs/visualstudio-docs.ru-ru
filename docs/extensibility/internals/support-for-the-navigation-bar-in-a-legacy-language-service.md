---
title: Поддержка панели навигации в языковой службе прежних версий
description: Узнайте, как поддерживать панель навигации в языковой службе прежних версий. В панели навигации в представлении редактора отображаются типы и элементы в файле.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Navigation bar, supporting in language services [managed package framework]
- language services [managed package framework], Navigation bar
ms.assetid: 2d301ee6-4523-4b82-aedb-be43f352978e
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: e75103d008e65c6d2060d598e442499f38a0e322
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105080662"
---
# <a name="support-for-the-navigation-bar-in-a-legacy-language-service"></a>Поддержка панели навигации в языковой службе прежних версий
В панели навигации в верхней части представления редактора отображаются типы и элементы в файле. Типы отображаются в левом раскрывающемся списке, и элементы отображаются в правом раскрывающемся списке. Когда пользователь выбирает тип, курсор помещается в первую строку типа. Когда пользователь выбирает элемент, курсор помещается в определение элемента. Раскрывающиеся списки обновляются в соответствии с текущим положением курсора.

## <a name="displaying-and-updating-the-navigation-bar"></a>Отображение и обновление панели навигации
 Для поддержки панели навигации необходимо создать класс, производный от <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> класса, и реализовать <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> метод. Когда языковая служба получает окно кода, базовый <xref:Microsoft.VisualStudio.Package.LanguageService> класс создает экземпляр <xref:Microsoft.VisualStudio.Package.CodeWindowManager> , который содержит <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> объект, представляющий окно кода. <xref:Microsoft.VisualStudio.Package.CodeWindowManager>Затем объекту присваивается новый <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> объект. <xref:Microsoft.VisualStudio.Package.LanguageService.CreateDropDownHelper%2A>Метод получает <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> объект. Если вы возвращаете экземпляр <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> класса, компонент <xref:Microsoft.VisualStudio.Package.CodeWindowManager> вызывает <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> метод для заполнения внутренних списков и передает <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> объект в [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] раскрывающийся список. Диспетчер раскрывающихся панелей, в свою очередь, вызывает метод для <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.SetDropdownBar%2A> <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> объекта, чтобы установить <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBar> объект, содержащий две раскрывающиеся полосы.

 При перемещении курсора <xref:Microsoft.VisualStudio.Package.LanguageService.OnIdle%2A> метод вызывает <xref:Microsoft.VisualStudio.Package.LanguageService.OnCaretMoved%2A> метод. Базовый <xref:Microsoft.VisualStudio.Package.LanguageService.OnCaretMoved%2A> метод вызывает <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> метод в <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> классе для обновления состояния панели навигации. В этот метод передается набор <xref:Microsoft.VisualStudio.Package.DropDownMember> объектов. Каждый объект представляет запись в раскрывающемся списке.

## <a name="the-contents-of-the-navigation-bar"></a>Содержимое панели навигации
 Панель навигации обычно содержит список типов и список элементов. Список типов включает все типы, доступные в текущем исходном файле. Имена типов включают полные сведения о пространстве имен. Ниже приведен пример кода C# с двумя типами:

```csharp
namespace TestLanguagePackage
{
    public class TestLanguageService
    {
        internal struct Token
        {
            int tokenID;
        }
        private Tokens[] tokens;
        private string serviceName;
    }
}
```

 В списке Тип отобразятся `TestLanguagePackage.TestLanguageService` и `TestLanguagePackage.TestLanguageService.Tokens` .

 В списке члены отображаются доступные члены типа, выбранного в списке типы. Используя приведенный выше пример кода, если `TestLanguagePackage.TestLanguageService` является выбранным типом, список Members будет содержать закрытые члены `tokens` и `serviceName` . Внутренняя структура `Token` не отображается.

 Можно реализовать список членов, чтобы сделать имя элемента полужирным при помещении курсора внутрь него. Элементы также могут отображаться серым цветом, что указывает на то, что они находятся за пределами области, в которой находится курсор.

## <a name="enabling-support-for-the-navigation-bar"></a>Включение поддержки для панели навигации
 Чтобы включить поддержку для панели навигации, необходимо задать `ShowDropdownBarOption` <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> для параметра атрибута значение `true` . Этот параметр задает свойство <xref:Microsoft.VisualStudio.Package.LanguagePreferences.ShowNavigationBar%2A>. Для поддержки панели навигации необходимо реализовать <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> объект в <xref:Microsoft.VisualStudio.Package.LanguageService.CreateDropDownHelper%2A> методе <xref:Microsoft.VisualStudio.Package.LanguageService> класса.

 В реализации <xref:Microsoft.VisualStudio.Package.LanguageService.CreateDropDownHelper%2A> метода, если <xref:Microsoft.VisualStudio.Package.LanguagePreferences.ShowNavigationBar%2A> свойство имеет значение `true` , можно вернуть <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> объект. Если объект не возвращается, панель навигации не отображается.

 Параметр для отображения панели навигации может быть установлен пользователем, поэтому этот элемент управления можно сбросить, пока открыто представление редактора. Пользователь должен закрыть и снова открыть окно редактора перед изменением.

## <a name="implementing-support-for-the-navigation-bar"></a>Реализация поддержки для панели навигации
 <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A>Метод принимает два списка (по одному для каждого раскрывающегося списка) и два значения, представляющие текущее выделение в каждом списке. Можно обновить списки и значения выбора, в этом случае <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> метод должен вернуться, `true` чтобы показать, что списки были изменены.

 По мере изменения выбора в раскрывающемся списке Типы список членов должен быть обновлен в соответствии с новым типом. Ниже перечислены элементы, отображаемые в списке члены.

- Список элементов для текущего типа.

- Все элементы, доступные в исходном файле, но со всеми элементами, не входящими в текущий тип, отображаются серым цветом. Пользователь по-прежнему может выбирать серые члены, чтобы их можно было использовать для быстрой навигации, но цвет указывает, что они не являются частью выбранного типа.

  Реализация <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> метода обычно выполняет следующие действия:

1. Возвращает список текущих объявлений для исходного файла.

     Существует несколько способов заполнения списков. Одним из подходов является создание пользовательского метода для версии <xref:Microsoft.VisualStudio.Package.LanguageService> класса, который вызывает <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> метод с пользовательской причиной синтаксического анализа, возвращающей список всех объявлений. Другим подходом может быть вызов <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> метода непосредственно из <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> метода с пользовательской причиной синтаксического анализа. Третьим подходом может быть кэширование объявлений в <xref:Microsoft.VisualStudio.Package.AuthoringScope> классе, возвращенном последней операцией полного анализа в классе, <xref:Microsoft.VisualStudio.Package.LanguageService> и их извлечение из <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> метода.

2. Заполните или обновите список типов.

     Содержимое списка типов может обновляться, когда источник изменился или если выбрано изменение стиля текста для типов, основанных на текущей позиции курсора. Обратите внимание, что эта позицией передается в <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> метод.

3. Определите тип для выбора в списке Типы на основе текущей позиции курсора.

     Можно выполнить поиск в объявлениях, полученных на шаге 1, чтобы найти тип, включающий текущую точку курсора, а затем выполнить поиск по списку типы для этого типа, чтобы определить его индекс в списке типы.

4. Заполнение или обновление списка элементов на основе выбранного типа.

     Список члены отражает, что в данный момент отображается в раскрывающемся списке **элементы** . Содержимое списка членов может потребоваться обновить, если источник изменился или если отображаются только элементы выбранного типа, а выбранный тип изменился. Если выбрано отображение всех элементов в исходном файле, необходимо обновить стиль текста каждого элемента в списке, если текущий выбранный тип изменился.

5. Определение элемента для выбора в списке элементов на основе текущей позиции курсора.

     Выполните поиск по объявлениям, полученным на шаге 1, для элемента, который содержит текущую точку курсора, а затем найдите этот элемент в списке члены, чтобы определить его индекс в списке элементов.

6. Возвращает, `true` Если в списки или выбранные элементы в списке были внесены какие либо изменения.
