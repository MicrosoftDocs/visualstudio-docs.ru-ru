---
title: Создание страниц параметров | Документация Майкрософт
description: Узнайте, как создать страницу параметров в меню "Сервис" в Visual Studio, реализовав класс DialogPage из управляемой платформы пакетов.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- managed package framework, creating Tools Options pages
- Tools Options pages [Visual Studio SDK], creating using managed package framework
ms.assetid: 1bf11fec-dece-4943-8053-6de1483c43eb
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: f7b1b8b92f978739bfa4e540013347e216781cd4
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/02/2021
ms.locfileid: "106217246"
---
# <a name="create-options-pages"></a>Создание страниц параметров
В [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] платформе управляемых пакетов классы, производные от <xref:Microsoft.VisualStudio.Shell.DialogPage> расширения [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] интегрированной среды разработки, добавляют страницы **параметров** в меню **Сервис** .

 Объект, реализующий заданную страницу **параметров инструментов** , связан с определенными пакетами VSPackage <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> объектом.

 Поскольку среда создает экземпляр объекта, реализующий определенную страницу **параметров средств** , когда эта конкретная страница отображается в интегрированной среде разработки:

- Страница **параметров инструментов** должна быть реализована для собственного объекта, а не для объекта, реализующего VSPackage.

- Объект не может реализовывать несколько страниц **параметров инструментов** .

## <a name="register-as-a-tools-options-page-provider"></a>Регистрация в качестве поставщика страницы параметров инструментов
 Конфигурация пользователя VSPackage, поддерживающая пользовательские настройки на страницах **параметров инструментов** , указывает объекты, предоставляющие эти страницы **параметров инструментов** , применяя к реализации экземпляры, <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> примененные к этой конфигурации <xref:Microsoft.VisualStudio.Shell.Package> .

 Должен существовать один экземпляр <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> для каждого <xref:Microsoft.VisualStudio.Shell.DialogPage> производного типа, который реализует страницу **параметров инструментов** .

 Каждый экземпляр <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> использует тип, который реализует страницу **параметров средств** , строки, содержащие категорию и подкатегорию, используемые для указания страницы **параметров инструментов** , а также сведения о ресурсах для регистрации типа в виде страницы **параметров инструментов** .

## <a name="persist-tools-options-page-state"></a>Сохранить состояние страницы параметров инструментов
 Если реализация страницы **параметров инструментов** была зарегистрирована с включенной поддержкой автоматизации, интегрированная среда разработки сохраняет состояние страницы вместе со всеми другими страницами **параметров средств** .

 Пакет VSPackage может управлять собственным сохранением с помощью <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> . Следует использовать только один или другой метод сохраняемости.

## <a name="implement-dialogpage-class"></a>Реализация класса DialogPage
 Объект, предоставляющий реализацию VSPackage <xref:Microsoft.VisualStudio.Shell.DialogPage> производного типа, может использовать преимущества следующих наследуемых функций:

- Окно пользовательского интерфейса по умолчанию.

- Механизм сохраняемости по умолчанию доступен либо при <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> применении к классу, либо если для <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute.SupportsProfiles%2A> свойства задано значение `true` <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> , применяемое к классу.

- Поддержка автоматизации.

  Минимальное требование для объекта, реализующего страницу **параметров инструментов** с помощью <xref:Microsoft.VisualStudio.Shell.DialogPage> , — это добавление открытых свойств.

  Если класс правильно зарегистрирован в качестве поставщика страницы **параметров средств** , то его открытые свойства доступны в разделе **Параметры** меню **Сервис** в форме сетки свойств.

  Все эти функции по умолчанию можно переопределить. Например, для создания более сложного пользовательского интерфейса требуется только переопределение реализации по умолчанию <xref:Microsoft.VisualStudio.Shell.DialogPage.Window%2A> .

## <a name="example"></a>Пример
 Ниже приведена простая реализация "Hello World" страницы параметров. Добавление следующего кода в проект по умолчанию, созданный с помощью шаблона пакета Visual Studio, с выбранным параметром **команды меню** будет адекватно продемонстрировать функциональность страницы параметров.

### <a name="description"></a>Описание
 Следующий класс определяет минимальную страницу параметров "Hello World". При открытии пользователь может задать `HelloWorld` свойство public в сетке свойств.

### <a name="code"></a>Код
:::code language="csharp" source="../../snippets/csharp/VS_Snippets_VSSDK/ui_usersettings_toolsoptionpages/cs/class1.cs" id="Snippet11":::
:::code language="vb" source="../../snippets/visualbasic/VS_Snippets_VSSDK/ui_usersettings_toolsoptionpages/vb/class1.vb" id="Snippet11":::

### <a name="description"></a>Описание
 Применение следующего атрибута к классу Package делает страницу параметров доступной при загрузке пакета. Числа — это произвольные идентификаторы ресурсов для категории и страницы, а логическое значение в конце указывает, поддерживает ли страница автоматизацию.

### <a name="code"></a>Код
:::code language="csharp" source="../../snippets/csharp/VS_Snippets_VSSDK/ui_usersettings_toolsoptionpages/cs/uiusersettingstoolsoptionspagespackage.cs" id="Snippet07":::
:::code language="vb" source="../../snippets/visualbasic/VS_Snippets_VSSDK/ui_usersettings_toolsoptionpages/vb/uiusersettingstoolsoptionspagespackage.vb" id="Snippet07":::

### <a name="description"></a>Описание
 Следующий обработчик событий отображает результат в зависимости от значения свойства, заданного на странице Параметры. <xref:Microsoft.VisualStudio.Shell.Package.GetDialogPage%2A>Для доступа к свойствам, предоставляемым страницей, в нем используется метод с результатом явного приведения к типу настраиваемой страницы параметров.

 В случае проекта, созданного шаблоном пакета, вызовите эту функцию из функции, `MenuItemCallback` чтобы присоединить ее к команде по умолчанию, добавленной в меню **Сервис** .

### <a name="code"></a>Код
:::code language="csharp" source="../../snippets/csharp/VS_Snippets_VSSDK/ui_usersettings_toolsoptionpages/cs/uiusersettingstoolsoptionspagespackage.cs" id="Snippet08":::
:::code language="vb" source="../../snippets/visualbasic/VS_Snippets_VSSDK/ui_usersettings_toolsoptionpages/vb/uiusersettingstoolsoptionspagespackage.vb" id="Snippet08":::

## <a name="see-also"></a>См. также раздел
- [Расширение параметров пользователя и параметров](../../extensibility/extending-user-settings-and-options.md)
- [Поддержка автоматизации для страниц параметров](../../extensibility/internals/automation-support-for-options-pages.md)
