---
title: Визуальная студия SDK Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- VSSDK.v90.StartPage
helpviewer_keywords:
- Visual Studio SDK
- VS SDK (see Visual Studio SDK)
- Visual Studio, SDK
ms.assetid: 1f7c348a-114c-4243-b392-3531e9c9c6fd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 56f772d7d27f11318cdeb0bf365373d5f7c1294b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80698078"
---
# <a name="visual-studio-sdk"></a>Пакет SDK для Visual Studio
Пакет SDK для Visual Studio помогает расширить возможности Visual Studio или интегрировать новые функции в Visual Studio. Вы можете распространять ваши расширения среди других пользователей, а также в Visual Studio Marketplace. Некоторые способы расширения Visual Studio:

- Добавление команд, кнопок, меню и других элементов пользовательского интерфейса в среду IDE.

- Добавление окон инструментов для новых функций.

- Расширение IntelliSense для данного языка или предоставление IntelliSense для новых языков программирования.

- Использование лампочек для подсказок и предложений, которые помогают разработчикам улучшить код.

- Добавление поддержки нового языка.

- Добавление настраиваемого типа проекта.

- Охват миллионов разработчиков в Visual Studio Marketplace.

  Если ранее вы не писали расширений Visual Studio, вы найдете дополнительные сведения об этих функциях в разделе [Приступая к разработке расширений Visual Studio](../extensibility/starting-to-develop-visual-studio-extensions.md).

## <a name="install-the-visual-studio-sdk"></a>Установка пакета SDK для Visual Studio
 Пакет SDK для Visual Studio является дополнительной функцией в установке Visual Studio. Вы можете установить пакет SDK для VS позже. Дополнительные сведения см. в разделе [Установка пакета SDK для Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="whats-new-in-the-visual-studio-2017-sdk"></a>Новые возможности пакета SDK для Visual Studio 2017
 Пакет SDK для Visual Studio имеет несколько новых функций, например, VSIX вер. 3, а также критические изменения, которые могут потребовать обновления расширения. Дополнительные сведения см. в разделе [Новые возможности пакета SDK для Visual Studio 2017](../extensibility/what-s-new-in-the-visual-studio-2017-sdk.md).

## <a name="visual-studio-user-experience-guidelines"></a>Рекомендации по взаимодействию с пользователями Visual Studio
 Получите советы по разработке пользовательского интерфейса для расширений в разделе [Рекомендации по взаимодействию с пользователями Visual Studio](../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md).

 Узнайте, как улучшить внешний вид расширения на устройствах с высоким DPI в разделе [Решение проблем с DPI](../extensibility/addressing-dpi-issues2.md).

 В разделе [Службы и каталог изображений](../extensibility/image-service-and-catalog.md) получите сведения о возможностях управления изображениями, поддержки высокого DPI и использования тем.

## <a name="find-and-install-existing-visual-studio-extensions"></a>Поиск и установка существующих расширений Visual Studio
 Расширения Visual Studio можно найти в диалоговом окне **Управление расширениями** в меню **Расширения**. Дополнительные сведения см. в разделе [Управление расширениями для Visual Studio](../ide/finding-and-using-visual-studio-extensions.md). Расширения также можно найти в [Visual Studio Marketplace](https://marketplace.visualstudio.com/).

## <a name="visual-studio-sdk-reference"></a>Справочник по пакету SDK для Visual Studio
 Справочник по API пакета SDK для Visual Studio можно найти в разделе [Справочник по пакету SDK для Visual Studio](../extensibility/visual-studio-sdk-reference.md).

## <a name="visual-studio-sdk-samples"></a>Примеры расширений Visual Studio
 Примеры расширений для Visual Studio с открытым исходным кодом можно найти на GitHub в [Visual Studio Samples.](https://github.com/Microsoft/VSSDK-Extensibility-Samples). Репозиторий GitHub содержит примеры, иллюстрирующие различные расширяемые функции Visual Studio.

## <a name="other-visual-studio-sdk-resources"></a>Другие ресурсы пакета SDK для Visual Studio
 Задать вопросы о пакете SDK для VS или поделиться опытом разработки расширений можно на форуме [Visual Studio Integrate](https://social.msdn.microsoft.com/Forums/vstudio/home?forum=vsx) или в чате [ExtendVS Gitter](https://gitter.im/Microsoft/extendvs).

 Дополнительную информацию можно найти в блоге [VSX Arcana](https://blogs.msdn.microsoft.com/vsx/) и ряде блогов, написанных специалистами Microsoft MVP:

- [Favorite Visual Studio Extensions](https://scottdorman.blog/2014/10/05/favorite-visual-studio-extensions/).

- [Visual Studio Extensibility](http://www.visualstudioextensibility.com/overview/vs/).

- [Extending Visual Studio 2013](https://blog.slaks.net/2013-10-18/extending-visual-studio-part-1-getting-started/).

## <a name="see-also"></a>См. также

- [Создание расширения с помощью команды меню](../extensibility/creating-an-extension-with-a-menu-command.md)
- [Практическое руководство: Перенос проектов расширяемости в Visual Studio 2017](../extensibility/how-to-migrate-extensibility-projects-to-visual-studio-2017.md)
- [Вопросы и ответы: Преобразование надстроек в расширения VSPackage](/visualstudio/extensibility/faq-converting-add-ins-to-vspackage-extensions?view=vs-2015)
- [Управление несколькими потоками в управляемом коде](../extensibility/managing-multiple-threads-in-managed-code.md)
- [Расширение меню и команд](../extensibility/extending-menus-and-commands.md)
- [Добавление команд на панели инструментов](../extensibility/adding-commands-to-toolbars.md)
- [Расширение и настройка окон инструментов](../extensibility/extending-and-customizing-tool-windows.md)
- [Расширения службы редактора и языковой службы](../extensibility/editor-and-language-service-extensions.md)
- [Расширение проектов](../extensibility/extending-projects.md)
- [Расширение настроек и параметров пользователя](../extensibility/extending-user-settings-and-options.md)
- [Создание настраиваемых шаблонов проектов и элементов](../extensibility/creating-custom-project-and-item-templates.md)
- [Расширение свойств и окна свойств](../extensibility/extending-properties-and-the-property-window.md)
- [Расширение других элементов Visual Studio](../extensibility/extending-other-parts-of-visual-studio.md)
- [Использование и предоставление служб](../extensibility/using-and-providing-services.md)
- [Управление пакетами VSPackage](../extensibility/managing-vspackages.md)
- [Изолированная оболочка Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/isolated-shell/)
- [Поставка расширений Visual Studio](../extensibility/shipping-visual-studio-extensions.md)
- [Компоненты пакета SDK для Visual Studio](../extensibility/internals/inside-the-visual-studio-sdk.md)
- [Поддержка пакета SDK для Visual Studio](../extensibility/support-for-the-visual-studio-sdk.md)
- [Справочник по пакету SDK для Visual Studio](../extensibility/visual-studio-sdk-reference.md)
