---
title: Предоставление событий в пакете SDK для Visual Studio | Документация Майкрософт
description: Сведения о методах и записях реестра Visual Studio, которые предоставляют события для проектов и элементов проектов.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- events [Visual Studio], exposing
- automation [Visual Studio SDK], exposing events
ms.assetid: 70bbc258-c221-44f8-b0d7-94087d83b8fe
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 019efb11d7a31af875425888a1f70423bca76ca9
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105069807"
---
# <a name="expose-events-in-the-visual-studio-sdk"></a>Предоставление событий в пакете SDK для Visual Studio
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] позволяет выполнять исходные события с помощью автоматизации. Рекомендуется использовать исходные события для проектов и элементов проектов.

 События извлекаются потребителями службы автоматизации из <xref:EnvDTE.DTEClass.Events%2A> объекта или <xref:EnvDTE.DTEClass.GetObject%2A> (например, `GetObject("EventObjectName")` ). Среда вызывает `IDispatch::Invoke` , используя `DISPATCH_METHOD` `DISPATCH_PROPERTYGET` флаги или для возврата события.

 В следующем процессе объясняется, как возвращаются события, относящиеся к пакету VSPackage.

1. Среда запустится.

2. Он считывает из реестра все имена значений в ключах **Automation**, **аутоматионевентс** и **AutomationProperties** всех пакетов VSPackage и сохраняет эти имена в таблице.

3. Потребитель автоматизации вызывает в этом примере `DTE.Events.AutomationProjectsEvents` или `DTE.Events.AutomationProjectItemsEvents` .

4. Среда находит строковый параметр в таблице и загружает соответствующий пакет VSPackage.

5. Среда вызывает <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> метод, используя имя, переданное в вызове; в этом примере — `AutomationProjectsEvents` или `AutomationProjectItemsEvents` .

6. VSPackage создает корневой объект с такими методами, как `get_AutomationProjectsEvents` и, `get_AutomationProjectItemEvents` а затем возвращает указатель IDispatch на объект.

7. Среда вызывает соответствующий метод на основе имени, переданного в вызов службы автоматизации.

8. `get_`Метод создает другой объект события на основе IDispatch, который реализует `IConnectionPointContainer` интерфейс и `IConnectionPoint` интерфейс и возвращает `IDispatchpointer` объект объекту.

   Чтобы предоставить событие с помощью службы автоматизации, необходимо ответить на него <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> и просмотреть строки, добавленные в реестр. В примере "базовый проект" строки — *бскпрожектсевентс* и *бскпрожектитемсевентс*.

## <a name="registry-entries-from-the-basic-project-sample"></a>Записи реестра из примера "базовый проект"
 В этом разделе показано, куда добавить в реестр значения событий автоматизации.

 **[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0\Packages\\<пкггуид \> \аутоматионевентс]**

 **Аутоматионпрожектевентс** = возвращает `AutomationProjectEvents` объект.

 **Аутоматионпрожектитемевентс** = возвращает `AutomationProjectItemsEvents` объект.

|Имя|Type|Диапазон|Описание|
|----------|----------|-----------|-----------------|
|По умолчанию (@)|REG_SZ|Не используется|Не используется. Для документации можно использовать поле данных.|
|*аутоматионпрожектсевентс*|REG_SZ|Имя объекта события.|Уместно только имя ключа. Для документации можно использовать поле данных.<br /><br /> Этот пример взят из примера "базовый проект".|
|*аутоматионпрожектитемевентс*|REG_SZ|Имя объекта события|Уместно только имя ключа. Для документации можно использовать поле данных.<br /><br /> Этот пример взят из примера "базовый проект".|

 Когда потребитель автоматизации запрашивает какие-либо объекты событий, создайте корневой объект, который содержит методы для любого события, которое поддерживает пакет VSPackage. Среда вызывает соответствующий `get_` метод для этого объекта. Например, если `DTE.Events.AutomationProjectsEvents` вызывается, `get_AutomationProjectsEvents` вызывается метод для корневого объекта.

 ![События проекта Visual Studio](../../extensibility/internals/media/projectevents.gif "прожектевентс") Модель автоматизации для событий

 Класс `CProjectEventsContainer` представляет исходный объект для *бскпрожектсевентс* и `CProjectItemsEventsContainer` представляет исходный объект для *бскпрожектитемсевентс*.

 В большинстве случаев необходимо вернуть новый объект для каждого запроса события, так как большинство объектов событий принимает объект фильтра. При срабатывании события проверьте этот фильтр, чтобы убедиться, что обработчик событий вызывается.

 *Аутоматионевентс. h* и *аутоматионевентс. cpp* содержат объявления и реализации классов, приведенных в следующей таблице.

|Класс|Описание|
|-----------|-----------------|
|`CAutomationEvents`|Реализует корневой объект события, полученный из `DTE.Events` объекта.|
|`CProjectsEventsContainer` и `CProjectItemsEventsContainer`|Реализуйте объекты источника событий, которые инициируют соответствующие события.|

 В следующем примере кода показано, как реагировать на запрос объекта события.

```cpp
STDMETHODIMP CVsPackage::GetAutomationObject(
    /* [in]  */ LPCOLESTR       pszPropName,
    /* [out] */ IDispatch **    ppIDispatch)
{
    ExpectedPtrRet(ppIDispatch);
    *ppIDispatch = NULL;

    if (_wcsicmp(pszPropName, g_wszAutomationProjects) == 0)
        //Is the requested name our Projects object?
    {
        return GetAutomationProjects(ppIDispatch);
        // Gets our Projects object.
    }
    else if (_wcsicmp(pszPropName, g_wszAutomationProjectsEvents) == 0)
        //Is the requested name our ProjectsEvents object?
    {
        return CAutomationEvents::GetAutomationEvents(ppIDispatch);
          // Gets our ProjectEvents object.
    }
    else if (_wcsicmp(pszPropName, g_wszAutomationProjectItemsEvents) == 0)  //Is the requested name our ProjectsItemsEvents object?
    {
        return CAutomationEvents::GetAutomationEvents(ppIDispatch);
          // Gets our ProjectItemsEvents object.
    }
    return E_INVALIDARG;
}
```

 В приведенном выше коде `g_wszAutomationProjects` — это имя коллекции проектов (*фигпрожектс*), `g_wszAutomationProjectsEvents` (*фигпрожектсевентс*) и `g_wszAutomationProjectItemsEvents` (*фигпрожектитемевентс*) — это имена событий проекта и элементов проекта, источником которых является реализация VSPackage.

 Объекты событий извлекаются из одного центрального расположения — `DTE.Events` объекта. Таким образом, все объекты событий группируются, так что конечному пользователю не придется просматривать всю объектную модель, чтобы найти определенное событие. Это также позволяет предоставлять конкретные объекты VSPackage, вместо того чтобы реализовывать собственный код для системных событий. Однако для конечного пользователя, который должен найти событие для вашего `ProjectItem` интерфейса, не сразу же ясно, откуда извлекается этот объект события.

## <a name="see-also"></a>См. также
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A>
