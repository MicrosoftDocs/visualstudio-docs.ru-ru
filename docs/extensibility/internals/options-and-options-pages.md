---
title: Страницы параметров и параметров | Документация Майкрософт
description: Сведения о поддержке страниц параметров, которые позволяют изменять значения параметров, определяющих состояние пакета VSPackage.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Tools Options pages [Visual Studio SDK], managed package framework support
- managed package framework, Tools Options pages support
- support, Tools Options pages
- Tools Options pages [Visual Studio SDK], layouts
- Tools Options pages [Visual Studio SDK], attributes
ms.assetid: e6c0e636-5ec3-450e-b395-fc4bb9d75918
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 32bcb32c4fc80a5806c9007c3119a2ba3de62427
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/02/2021
ms.locfileid: "106214516"
---
# <a name="options-and-options-pages"></a>Параметры и страницы параметров
При выборе пункта **Параметры** в меню **Сервис** открывается диалоговое окно **Параметры** . Параметры в этом диалоговом окне в совокупности называются страницами параметров. Элемент управления "дерево" в области навигации включает категории "Параметры", и каждая категория содержит страницы параметров. При выборе страницы ее параметры отображаются на правой панели. Эти страницы позволяют изменить значения параметров, определяющих состояние VSPackage.

## <a name="support-for-options-pages"></a>Поддержка страниц параметров
 <xref:Microsoft.VisualStudio.Shell.Package>Класс обеспечивает поддержку для создания параметров страницы и категории параметров. <xref:Microsoft.VisualStudio.Shell.DialogPage>Класс реализует страницу параметров.

 Реализация по умолчанию <xref:Microsoft.VisualStudio.Shell.DialogPage> предлагает своим открытым свойствам пользователя в универсальной сетке свойств. Это поведение можно настроить, переопределив различные методы на странице, чтобы создать страницу настраиваемых параметров, имеющую собственный пользовательский интерфейс. Дополнительные сведения см. в разделе [Создание страницы параметров](../../extensibility/creating-an-options-page.md).

 <xref:Microsoft.VisualStudio.Shell.DialogPage>Класс реализует <xref:Microsoft.VisualStudio.Shell.IProfileManager> , который обеспечивает сохраняемость для страниц параметров, а также для параметров пользователя. Реализации по умолчанию <xref:Microsoft.VisualStudio.Shell.IProfileManager.LoadSettingsFromStorage%2A> <xref:Microsoft.VisualStudio.Shell.IProfileManager.SaveSettingsToStorage%2A> методов и сохраняют изменения свойств в пользовательском разделе реестра, если это свойство можно преобразовать в строку и из нее.

## <a name="options-page-registry-path"></a>Путь к реестру страницы параметров
 По умолчанию путь реестра для свойств, управляемых страницей параметров, определяется сочетанием <xref:Microsoft.VisualStudio.Shell.Package.UserRegistryRoot%2A> , словом DialogPage и именем типа для класса страницы Options. Например, класс страницы Options можно определить следующим образом.

 :::code language="csharp" source="../../snippets/csharp/VS_Snippets_VSSDK/vssdksupportforoptionspages/cs/vssdksupportforoptionspagespackage.cs" id="Snippet1":::
 :::code language="vb" source="../../snippets/visualbasic/VS_Snippets_VSSDK/vssdksupportforoptionspages/vb/vssdksupportforoptionspagespackage.vb" id="Snippet1":::

 Если <xref:Microsoft.VisualStudio.Shell.Package.UserRegistryRoot%2A> HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0Exp, то пары имя-значение и значения свойства являются подразделами HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0Exp\DialogPage\Company.OptionsPage.OptionsPageGeneral.

 Путь реестра страницы параметров определяется путем объединения <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A> , слова, тулсоптионспажес, а также категории и имени страницы параметров. Например, если на странице «настраиваемые параметры» есть страница «Категория», страницы «Мои параметры» и <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A> HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp, то на странице «Параметры» содержится раздел реестра HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\ToolsOptionsPages\My Option Pages\Custom.

## <a name="toolsoptions-page-attributes-and-layout"></a>Атрибуты и макет страницы "Сервис/Параметры"
 <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute>Атрибут определяет группировку страниц настраиваемых параметров по категориям в дереве переходов диалогового окна " **Параметры** ". <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute>Атрибут связывает страницу параметров с пакетом VSPackage, предоставляющим интерфейс. Рассмотрим следующий фрагмент кода:

:::code language="csharp" source="../../snippets/csharp/VS_Snippets_VSSDK/vssdksupportforoptionspages/cs/vssdksupportforoptionspagespackage.cs" id="Snippet2":::
:::code language="vb" source="../../snippets/visualbasic/VS_Snippets_VSSDK/vssdksupportforoptionspages/vb/vssdksupportforoptionspagespackage.vb" id="Snippet2":::

 Это объявляет, что MyPackage предоставляет две страницы параметров: Оптионспажеженерал и Оптионспажекустом. В диалоговом окне **Параметры** обе страницы параметров отображаются в категории **Мои страницы** параметров как **Общие** и **Настраиваемые** соответственно.

## <a name="option-attributes-and-layout"></a>Атрибуты и макет параметров
 Пользовательский интерфейс, предоставляемый страницей, определяет внешний вид параметров на странице настраиваемых параметров. Макет, метки и описание параметров на странице универсальные параметры определяются следующими атрибутами.

- <xref:System.ComponentModel.CategoryAttribute> Определяет категорию параметра.

- <xref:System.ComponentModel.DisplayNameAttribute> Определяет отображаемое имя параметра.

- <xref:System.ComponentModel.DescriptionAttribute> Определяет описание параметра.

  > [!NOTE]
  > Эквивалентные атрибуты, Сркатегори, Локдисплайнаме и Срдескриптион, используют строковые ресурсы для локализации и определяются в [примере управляемого проекта](/azure/devops/integrate/index).

  Рассмотрим следующий фрагмент кода:

  :::code language="csharp" source="../../snippets/csharp/VS_Snippets_VSSDK/vssdksupportforoptionspages/cs/optionspagecustom.cs" id="Snippet3":::
  :::code language="vb" source="../../snippets/visualbasic/VS_Snippets_VSSDK/vssdksupportforoptionspages/vb/optionspagegeneral.vb" id="Snippet3":::

  Параметр Оптионинтежер отображается на странице Параметры в виде **целочисленного параметра** в категории **Мои параметры** . Если этот параметр выбран, в поле Описание отображается **параметр Description (мое целое число**).

## <a name="accessing-options-pages-from-another-vspackage"></a>Доступ к страницам параметров из другого пакета VSPackage
 Пакет VSPackage, на котором размещается страница параметров и управляет им, может быть программно доступен из другого пакета VSPackage с помощью модели автоматизации. Например, в следующем коде пакет VSPackage регистрируется как размещенная страница параметров.

 :::code language="csharp" source="../../snippets/csharp/VS_Snippets_VSSDK/vssdksupportforoptionspages/cs/vssdksupportforoptionspagespackage.cs" id="Snippet4":::
 :::code language="vb" source="../../snippets/visualbasic/VS_Snippets_VSSDK/vssdksupportforoptionspages/vb/vssdksupportforoptionspagespackage.vb" id="Snippet4":::

 Следующий фрагмент кода получает значение Оптионинтежер из Мйоптионпаже:

 :::code language="csharp" source="../../snippets/csharp/VS_Snippets_VSSDK/vssdksupportforoptionspages/cs/vssdksupportforoptionspagespackage.cs" id="Snippet5":::
 :::code language="vb" source="../../snippets/visualbasic/VS_Snippets_VSSDK/vssdksupportforoptionspages/vb/vssdksupportforoptionspagespackage.vb" id="Snippet5":::

 Когда <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> атрибут регистрирует страницу параметров, эта страница регистрируется в ключе AutomationProperties, если `SupportsAutomation` аргумент атрибута имеет значение `true` . Автоматизация проверяет эту запись реестра, чтобы найти соответствующий пакет VSPackage, а затем автоматизирует доступ к свойству на странице "размещенные параметры", в данном случае на странице "Сетка".

 Путь реестра для свойства службы автоматизации определяется путем объединения <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A> , слова, AutomationProperties, а также категории и имени страницы параметров. Например, если на странице «Параметры» имеется категория «моя Категория», имя страницы «Моя сетка» и <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A> HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp, то свойство автоматизации содержит раздел реестра HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\AutomationProperties\My Category\My Grid Page.

> [!NOTE]
> Каноническое имя, страница Category.My Grid, является значением подраздела имени этого раздела.
