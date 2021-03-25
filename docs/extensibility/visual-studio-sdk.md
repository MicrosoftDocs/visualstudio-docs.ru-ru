---
title: Пакет SDK для Visual Studio | Документация Майкрософт
description: Пакет SDK для Visual Studio позволяет расширять функции или добавлять новые функции в Visual Studio. Узнайте о некоторых способах расширения Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- VSSDK.v90.StartPage
helpviewer_keywords:
- Visual Studio SDK
- VS SDK (see Visual Studio SDK)
- Visual Studio, SDK
ms.assetid: 1f7c348a-114c-4243-b392-3531e9c9c6fd
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 91411ec183e6c51abd825af1080c4330ca46fc90
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105062529"
---
# <a name="visual-studio-sdk"></a>SDK для Visual Studio
Пакет SDK для Visual Studio помогает расширить возможности Visual Studio или интегрировать новые функции в Visual Studio. Вы можете распространять расширения для других пользователей, а также для Visual Studio Marketplace. Ниже перечислены некоторые из способов расширения Visual Studio:

- Добавление команд, кнопок, меню и других элементов пользовательского интерфейса в интегрированную среду разработки

- Добавление окон инструментов для новых функциональных возможностей

- Расширение IntelliSense для данного языка или обеспечение IntelliSense для новых языков программирования

- Используйте лампочки, чтобы предоставить подсказки и предложения, помогающие разработчикам писать более подходящий код.

- Включить поддержку для нового языка

- Добавление пользовательского типа проекта

- Достигайте миллионов разработчиков с помощью Visual Studio Marketplace

  Если вы ранее не записали расширение Visual Studio, то получите дополнительные сведения об этих функциях и [Начните разработку расширений Visual Studio](../extensibility/starting-to-develop-visual-studio-extensions.md).

## <a name="install-the-visual-studio-sdk"></a>Установка пакета SDK для Visual Studio
 Пакет SDK для Visual Studio является дополнительным компонентом в программе установки Visual Studio. Пакет SDK для VS можно установить и позже. Дополнительные сведения см. [в статье Установка пакета SDK для Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="whats-new-in-the-visual-studio-sdk"></a>Новые возможности пакета SDK для Visual Studio
 В пакете SDK для Visual Studio есть некоторые новые функции, такие как предупреждение о синхронно загружаемых расширениях и формат VSIX v3, а также критические изменения, которые могут потребовать обновления расширения. Дополнительные сведения см. в статьях [новые возможности пакета SDK для Visual studio 2019](../extensibility/whats-new-visual-studio-2019-sdk.md) и [новые возможности пакета SDK для Visual Studio 2017](../extensibility/what-s-new-in-the-visual-studio-2017-sdk.md).

## <a name="visual-studio-user-experience-guidelines"></a>Рекомендации по работе с пользователем Visual Studio
 Получите советы по проектированию пользовательского интерфейса для расширения в [руководстве пользователя Visual Studio](../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md).

 Вы также можете узнать, как сделать расширение более удобным на устройствах с высоким разрешением и с помощью [проблем с адресом dpi](../extensibility/addressing-dpi-issues2.md) .

 Воспользуйтесь [службой образов и каталогом](../extensibility/image-service-and-catalog.md) , чтобы получить превосходные возможности управления образами и поддержки высокого DPI.

## <a name="find-and-install-existing-visual-studio-extensions"></a>Поиск и установка существующих расширений Visual Studio
 Расширения Visual Studio можно найти в диалоговом окне **расширения и обновления** в меню **Сервис** . Дополнительные сведения см. в статье [Поиск и использование расширений Visual Studio](../ide/finding-and-using-visual-studio-extensions.md). Расширения можно также найти в [Visual Studio Marketplace](https://marketplace.visualstudio.com/)

## <a name="visual-studio-sdk-reference"></a>Справочник по Visual Studio SDK
 Справочник по API пакета SDK для Visual Studio можно найти в [справочнике по Visual Studio SDK](../extensibility/visual-studio-sdk-reference.md).

## <a name="visual-studio-sdk-samples"></a>Примеры пакета SDK для Visual Studio
 Примеры Open Source для расширений VS SDK можно найти на сайте GitHub в [примерах Visual Studio](https://github.com/Microsoft/VSSDK-Extensibility-Samples). Этот репозиторий GitHub содержит примеры, иллюстрирующие различные Расширяемые функции в Visual Studio.

## <a name="other-visual-studio-sdk-resources"></a>Другие ресурсы пакета SDK для Visual Studio
 Если у вас есть вопросы о VSSDK или хотите поделиться опытом разработки расширений, вы можете использовать [форум по расширению Visual Studio](https://social.msdn.microsoft.com/Forums/vstudio/home?forum=vsx) или [екстендвс gitter чатрум](https://gitter.im/Microsoft/extendvs).

 Дополнительные сведения см. в [блоге Аркана по VSX](/archive/blogs/vsx/) и в нескольких блогах, написанных специалистами MVP корпорации Майкрософт:

- [Избранные расширения Visual Studio](https://scottdorman.blog/2014/10/05/favorite-visual-studio-extensions/)

- [Расширяемость Visual Studio](http://www.visualstudioextensibility.com/overview/vs/)

- [Расширение Visual Studio](https://blog.slaks.net/2013-10-18/extending-visual-studio-part-1-getting-started/)

## <a name="see-also"></a>См. также

- [Создание расширения с помощью команды меню](../extensibility/creating-an-extension-with-a-menu-command.md)
- [Руководство. Миграция проектов расширяемости в Visual Studio 2017](../extensibility/how-to-migrate-extensibility-projects-to-visual-studio-2017.md)
- [Часто задаваемые вопросы: преобразование надстроек в расширения VSPackage](/previous-versions/visualstudio/visual-studio-2015/extensibility/faq-converting-add-ins-to-vspackage-extensions?preserve-view=true&view=vs-2015)
- [Управление несколькими потоками в управляемом коде](../extensibility/managing-multiple-threads-in-managed-code.md)
- [Расширение меню и команд](../extensibility/extending-menus-and-commands.md)
- [Добавление команд в панели инструментов](../extensibility/adding-commands-to-toolbars.md)
- [Расширение и настройка окон инструментов](../extensibility/extending-and-customizing-tool-windows.md)
- [Расширения редактора и языковой службы](../extensibility/editor-and-language-service-extensions.md)
- [Расширение проектов](../extensibility/extending-projects.md)
- [Расширение параметров пользователя и параметров](../extensibility/extending-user-settings-and-options.md)
- [Создание пользовательских шаблонов проектов и элементов](../extensibility/creating-custom-project-and-item-templates.md)
- [Расширение свойств и окна свойств](../extensibility/extending-properties-and-the-property-window.md)
- [Расширение других частей Visual Studio](../extensibility/extending-other-parts-of-visual-studio.md)
- [Использование и предоставление служб](../extensibility/using-and-providing-services.md)
- [Управление пакетами VSPackage](../extensibility/managing-vspackages.md)
- [Изолированная оболочка Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/isolated-shell/)
- [Поставка расширений Visual Studio](../extensibility/shipping-visual-studio-extensions.md)
- [Компоненты пакета SDK для Visual Studio](../extensibility/internals/inside-the-visual-studio-sdk.md)
- [Поддержка пакета SDK для Visual Studio](../extensibility/support-for-the-visual-studio-sdk.md)
- [Справочник по Visual Studio SDK](../extensibility/visual-studio-sdk-reference.md)