---
title: Расширение свойств | Документация Майкрософт
description: Узнайте о интерфейсах, которые необходимо реализовать, и вызовите, чтобы расширить список свойств в окно свойств Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Properties window, providing support
ms.assetid: 68e2cbd4-861c-453f-8c9f-4ab6afc80e67
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 3b1006f74cd2de03b4fe74e090d7ffcd1c921e5d
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105069651"
---
# <a name="extend-properties"></a>Расширение свойств
Окно [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] **свойства** — это обозреватель универсальных свойств для компонентов COM и com+, поддерживающий все [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] продукты. Окно **Свойства** работает со `ITypeInfo` сведениями о типе и метаданными com+ для перечисления свойств времени разработки для выбранного объекта в любом другом окне интегрированной среды разработки (IDE).

 Окно **Свойства** , которое можно открыть, нажав клавишу **F4** на клавиатуре или выбрав **окно "свойства** " в меню " **вид** ", используется для просмотра и изменения свойств, не зависящих от конфигурации, а также для событий выбранных объектов во время разработки. Зависящие от конфигурации свойства, связанные с решениями и проектами, отображаются на [страницах свойств](../../extensibility/internals/property-pages.md). Для получения дополнительных сведений об [управлении параметрами конфигурации](../../extensibility/internals/managing-configuration-options.md).

 ![Обзор окно свойств](../../extensibility/internals/media/vspropertieswindow.png "вспропертиесвиндов") окно свойств

 В этом разделе содержатся подробные сведения, относящиеся к отдельным областям окна **свойств** и интерфейсам, которые необходимо реализовать, и вызвать для заполнения окна.

## <a name="in-this-section"></a>Содержание раздела
- [Обзор окно свойств](../../extensibility/internals/properties-window-overview.md)

 Описывает назначение окна « **Свойства** » относительно окна инструментов и окна документа.

- [Политика шаблона и окно свойств](../../extensibility/internals/template-policy-and-the-properties-window.md)

 Описывает, как проект содержится в проекте корпоративного шаблона и как этот проект корпоративного шаблона может применить политику.

- [окно свойств поля и интерфейсы](../../extensibility/internals/properties-window-fields-and-interfaces.md)

 Описывает базис для выбора, который определяет, какие сведения отображаются в окне " **Свойства** ".

- [Список объектов окно свойств](../../extensibility/internals/properties-window-object-list.md)

 Описывает назначение списка объектов окна **свойств** , описывающее, как, когда другой объект из этого списка активирует вызов, среда сообщает о том, что был выбран новый объект.

- [окно свойств кнопки](../../extensibility/internals/properties-window-buttons.md)

 Объясняет назначение четырех кнопок по умолчанию, отображаемых на панели инструментов окна **свойств** .

- [Сетка "Отображение свойств"](../../extensibility/internals/properties-display-grid.md)

 Объясняет, где поля имен свойств и значений свойств находятся в сетке.

## <a name="related-sections"></a>Связанные разделы
- [Типы проектов](../../extensibility/internals/project-types.md)

 Обсуждаются проекты в качестве стандартных блоков [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] интегрированной среды разработки.

- [Компиляция и сборка](../../ide/compiling-and-building-in-visual-studio.md)

 Описывает, как можно использовать [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] платформу для непрерывного тестирования и отладки приложений при их создании.

- [IDispatch](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch)

 Описывает `IDispatch` интерфейс, который был впервые разработан для поддержки автоматизации, предоставляя механизм с поздним связыванием для доступа к сведениям о методах и свойствах объекта и получения сведений о них.

- [Управление параметрами приложения (.NET)](../../ide/managing-application-settings-dotnet.md)

 Содержит общие сведения о параметрах приложений, которые позволяют настроить приложение таким образом, чтобы значения свойств хранились во внешнем файле конфигурации, а не в скомпилированном коде приложения.

- [Проекты и решения](../../ide/solutions-and-projects-in-visual-studio.md)

 Объясняется [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] эффективность управления такими элементами, как ссылки, подключения к данным, папки и файлы, необходимые для разработки с помощью решений и проектов.

- [Расширение других частей Visual Studio](../../extensibility/extending-other-parts-of-visual-studio.md)

 Объясняется использование служб [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] для создания элементов пользовательского интерфейса, соответствующих остальным частям [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].
