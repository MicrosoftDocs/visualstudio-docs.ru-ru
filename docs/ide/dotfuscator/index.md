---
title: Dotfuscator Community
ms.date: 03/28/2019
ms.devlang: dotnet
ms.topic: overview
keywords: Dotfuscator, Dotfuscator CE, Dotfuscator Community, PreEmptive, PreEmptive Solutions, PreEmptive Protection, protection, community edition, obfuscation, .NET, free, Visual Studio 2019, Visual Studio 2017, Visual Studio
helpviewer_keywords:
- PreEmptive Protection Dotfuscator
- Dotfuscator Community Edition
- Dotfuscator CE
- Dotfuscator Community
- Dotfuscator
- obfuscation
- protection
description: Узнайте, как защитить свои приложения .NET с помощью бесплатной копии средства Dotfuscator Community, включенного в Visual Studio 2017.
ms.assetid: d9550502-0a82-49a6-b005-2caa791fbe02
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.openlocfilehash: 75437af41cec6fd770af9dfcdb399ed51543b7ff
ms.sourcegitcommit: 5fb4a67a8208707e79dc09601e8db70b16ba7192
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/17/2021
ms.locfileid: "112308224"
---
# <a name="dotfuscator-community"></a>Dotfuscator Community

***PreEmptive Protection - Dotfuscator*** — это решение для комплексной защиты приложений .NET, которое легко встраивается в жизненный цикл разработки безопасного программного обеспечения.
Используйте его, чтобы обеспечить усиленную безопасность и настроить очистку рабочего стола, мобильных устройств, сервера и встроенных приложений. Так вы сможете защитить коммерческие тайны и другую интеллектуальную собственность от пиратства, подделки, изменения данных и несанкционированной отладки.
Решение Dotfuscator выполняется на скомпилированных сборках. Вам не нужно писать дополнительный код или иметь доступ к исходному коду.

![PreEmptive Protection — Dotfuscator](media/header.svg)

## <a name="why-protection-matters"></a>Почему важна защита

**Защищать интеллектуальную собственность** очень важно.
Код вашего приложения содержит сведения о проектировании и реализации, которые могут считаться интеллектуальной собственностью.
Однако приложения, создаваемые на платформе .NET Framework, [содержат большой объем метаданных и промежуточного высокоуровневого кода][assemblies], поэтому их можно легко изучать и декомпилировать с помощью множества бесплатных автоматизированных средств.
Прервав и остановив такую декомпиляцию, вы сможет предотвратить несанкционированное раскрытие интеллектуальной собственности, а также продемонстрировать, что ваш код содержит коммерческую тайну.
Решение Dotfuscator позволяет [маскировать][obfuscation] ваши сборки .NET (выполнять их обфускацию), чтобы затруднить их изучение. При этом оно сохраняет исходное поведение приложений.

Также важно **обеспечить целостность приложения**.
Помимо декомпиляции, злоумышленники могут попытаться скопировать ваше приложение (компьютерное пиратство), изменить его поведение во время выполнения или манипулировать его данными.
Dotfuscator позволяет внедрить в приложение возможность [обнаруживать и реагировать на неавторизованное использование][checks]: незаконное изменение данных, отладку третьими лицами, запуск на рутованных устройствах и другие случаи.

Дополнительные сведения о том, как Dotfuscator встраивается в жизненный цикл разработки защищенных приложений (SDL), см. на странице [SDL App Protection][sdl-protection] (Защита приложений в рамках цикла SDL) в разделе решений компании PreEmptive.

## <a name="about-dotfuscator-community"></a>О Dotfuscator Community

Ваша копия Microsoft Visual Studio включает копию ***PreEmptive Protection — Dotfuscator Community***, доступную для бесплатного личного использования.
(Эта бесплатная версия ранее называлась Dotfuscator Community Edition или Dotfuscator CE.) Инструкции по установке версии Dotfuscator Community, прилагаемой к Visual Studio, см. на [странице по установке][install].

Dotfuscator Community предлагает разработчикам, архитекторам и тест-инженерам набор служб для [обеспечения и усиления защиты программного обеспечения][software-protection].
Примеры [обфускации .NET][obfuscation] и других функций [защиты приложений][app-protection], входящих в Dotfuscator Community:

* *[Переименование][renaming]* идентификаторов затрудняет изучение и декомпиляцию скомпилированных сборок.
* *[Защита от незаконного изменения][tamper]* позволяет обнаруживать выполнение незаконно измененных приложений и завершать незаконные сеансы либо принимать какие-то меры.
* *[Защита от отладки][debug]* позволяет обнаруживать в работающем приложении подключенный отладчик и завершать сеансы отладки либо принимать необходимые меры.
* *[Защита на рутованных устройствах][root]* позволяет обнаруживать запуск приложения на рутованном устройстве с Android и завершать сеансы на таких устройствах либо принимать какие-то меры.
* *[Проверки срока действия][shelflife]* позволяют закодировать дату "окончания срока службы" и завершать сеансы приложений, срок действия которых истек.

Подробные сведения об этих возможностях и о том, как встроить их в вашу стратегию защиты приложений, см. на [странице по возможностям][capabilities].

Dotfuscator Community предоставляет настроенную систему базовой защиты.
А зарегистрированные пользователи Dotfuscator Community и пользователи ***PreEmptive Protection — Dotfuscator Professional***, ведущего решения по [обфускации .NET][net-obfuscator] в мире, получают еще больше функций для защиты своих приложений.
Сведения о расширении Dotfuscator см. на [странице по обновлениям][upgrades].

## <a name="getting-started"></a>Начало работы

::: moniker range=">=vs-2019"

Чтобы начать использовать Dotfuscator Community в рамках Visual Studio, введите `dotfuscator` на **панели поиска** (CTRL+Q).

* Если вы уже установили Dotfuscator Community, в **поле поиска** под заголовком *Menus* (Меню) будет отображаться параметр, с помощью которого можно запустить Dotfuscator Community. Дополнительные сведения см. на [странице с инструкциями по началу работы в полном руководстве пользователя Dotfuscator Community][get-started].
* Если вы не установили Dotfuscator Community, в **поле поиска** вместо этого под заголовком *Individual Components* (Отдельные компоненты) будет отображаться параметр **Install PreEmptive Protection - Dotfuscator** (Установить PreEmptive Protection — Dotfuscator). Дополнительные сведения см. на [странице по установке][install].

::: moniker-end

::: moniker range="vs-2017"

Чтобы начать использовать Dotfuscator Community в рамках Visual Studio, введите `dotfuscator` на **панели быстрого запуска** (CTRL+Q).

* Если вы установили Dotfuscator Community, при **быстром запуске** вы увидите *меню* для открытия пользовательского интерфейса Dotfuscator Community. Дополнительные сведения см. на [странице с инструкциями по началу работы в полном руководстве пользователя Dotfuscator Community][get-started].
* Если вы не установили Dotfuscator Community еще не установлено, при **быстром запуске** вам будет предложено выполнить *установку*. Дополнительные сведения см. на [странице по установке][install].

::: moniker-end

Вы также можете скачать **последнюю версию** Dotfuscator Community на [странице загрузок Dotfuscator сайта preemptive.com][download].

## <a name="full-documentation"></a>Полная документация

На этой странице и в ее разделах приведен общий обзор возможностей Dotfuscator Community, а также [инструкции по установке этого инструмента][install].

Подробные инструкции по его использованию, в том числе [как приступить к работе с пользовательским интерфейсом Dotfuscator Community][get-started], см. в [полном руководстве пользователя Dotfuscator Community на сайте preemptive.com][full].

<!-- Copyright © 2019 PreEmptive Solutions, LLC -->

[assemblies]:  /dotnet/standard/assembly-format
[software-protection]:  https://www.preemptive.com/software-protection
[obfuscation]:  https://www.preemptive.com/obfuscation
[app-protection]:  https://www.preemptive.com/application-protection
[sdl-protection]:  https://www.preemptive.com/solutions/SDL-App-Protection
[net-obfuscator]:  https://www.preemptive.com/products/dotfuscator/overview
[download]:  https://www.preemptive.com/products/dotfuscator/downloads

[install]:  install.md
[capabilities]:  capabilities.md
[upgrades]:  upgrades.md

[get-started]:  https://www.preemptive.com/dotfuscator/ce/docs/help/gui_getstarted.html

[renaming]:  https://www.preemptive.com/dotfuscator/ce/docs/help/obfuscation_renaming.html

[checks]:  https://www.preemptive.com/dotfuscator/ce/docs/help/checks_overview.html
[tamper]:  https://www.preemptive.com/dotfuscator/ce/docs/help/checks_tamper.html
[debug]:  https://www.preemptive.com/dotfuscator/ce/docs/help/checks_debug.html
[root]: https://www.preemptive.com/dotfuscator/ce/docs/help/checks_root.html
[shelflife]:  https://www.preemptive.com/dotfuscator/ce/docs/help/checks_shelflife.html

[full]:  https://www.preemptive.com/dotfuscator/ce/docs/help/index.html
