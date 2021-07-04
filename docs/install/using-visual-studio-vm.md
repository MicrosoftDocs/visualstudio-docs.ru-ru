---
title: Использование Visual Studio на виртуальной машине Azure
titleSuffix: ''
description: Узнайте, как использовать Visual Studio на виртуальной машине Azure.
ms.date: 11/17/2020
ms.custom: seodec18
ms.topic: conceptual
helpviewer_keywords:
- azure services
- virtual machine
- installation
- visual studio
author: j-martens
ms.author: jmartens
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 41247c13e8b35fd6e6cd26ac0ad0ea82f742fbb0
ms.sourcegitcommit: 5fb4a67a8208707e79dc09601e8db70b16ba7192
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/17/2021
ms.locfileid: "112306700"
---
# <a name="visual-studio-images-on-azure"></a>Образы Visual Studio в Azure

Запуск Visual Studio на предварительно настроенной виртуальной машине Azure — простой и быстрый способ получить "с нуля" готовую к работе среду разработки. Образы системы с различными конфигурациями Visual Studio доступны в [Azure Marketplace](https://azuremarketplace.microsoft.com/marketplace/apps/category/compute?filters=virtual-machine-images%3Bmicrosoft%3Bwindows&page=1&subcategories=application-infrastructure).

Впервые работаете с Azure? [Создайте бесплатную учетную запись Azure](https://azure.microsoft.com/free).

## <a name="what-configurations-and-versions-are-available"></a>Доступные конфигурации и версии

В Azure Marketplace можно найти образы самых последних основных версий: Visual Studio 2019, Visual Studio 2017 и Visual Studio 2015.  Для каждой выпущенной основной версии доступны изначально выпущенная версия для Интернета (RTW) и последние обновленные версии.  Для каждой из этих версий доступны выпуски Visual Studio Enterprise и Visual Studio Community.  Эти образы обновляются по крайней мере раз в месяц для включения последних обновлений Visual Studio и Windows.  Хотя имена образов не меняются, описание каждого образа содержит версию установленного продукта и дату выпуска образа.

| Версия выпуска                                                                                                                                                | Выпуски              | Версия продукта       |
|----------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------------------|-----------------------|
| [Visual Studio 2019. Последняя (версия 16.8)](https://azuremarketplace.microsoft.com/marketplace/apps/microsoftvisualstudio.visualstudio2019latest?tab=Overview) | Enterprise, Community | Версия 16.8.0        |
| [Visual Studio 2019. RTW](https://azuremarketplace.microsoft.com/marketplace/apps/microsoftvisualstudio.visualstudio2019?tab=Overview)                         | Предприятие            | Версия 16.0.20       |
| [Visual Studio 2017. Последняя версия (версия 15.9)](https://azuremarketplace.microsoft.com/marketplace/apps/microsoftvisualstudio.visualstudio?tab=Overview)           | Enterprise, Community | Версия 15.9.29       |
| [Visual Studio 2017. RTW](https://azuremarketplace.microsoft.com/marketplace/apps/microsoftvisualstudio.visualstudio?tab=Overview)                             | Enterprise, Community | Версия 15.0.28       |
| [Visual Studio 2015. Последняя версия (обновление 3)](https://azuremarketplace.microsoft.com/marketplace/apps/microsoftvisualstudio.visualstudio?tab=Overview)               | Enterprise, Community | Версия 14.0.25431.01 |

> [!NOTE]
> В соответствии с политикой обслуживания корпорации Майкрософт истек срок обслуживания изначально выпущенной версии (RTW) Visual Studio 2015. Visual Studio 2015 с обновлением 3 — единственная предлагаемая версия в линейке продуктов Visual Studio 2015.

Дополнительные сведения см. в разделе [Обслуживание продуктов Visual Studio и Team Foundation Server](/visualstudio/productinfo/vs-servicing-vs).

## <a name="what-features-are-installed"></a>Какие компоненты устанавливаются?

Каждый образ содержит рекомендуемый набор компонентов для данного выпуска Visual Studio. Как правило, установка включает в себя:

* все доступные рабочие нагрузки, включая рекомендуемые дополнительные компоненты для них;
* пакеты SDK для .NET 4.6.2 и .NET 4.7, пакеты нацеливания и средства для разработчиков;
* Visual F#
* расширение GitHub для Visual Studio;
* Инструменты LINQ to SQL.

Ниже приведен пример командной строки, с помощью которой мы устанавливаем Visual Studio при создании образов.

```shell
    vs_enterprise.exe --allWorkloads --includeRecommended --passive ^
       --add Microsoft.Net.Component.4.7.SDK ^
       --add Microsoft.Net.Component.4.7.TargetingPack ^
       --add Microsoft.Net.Component.4.6.2.SDK ^
       --add Microsoft.Net.Component.4.6.2.TargetingPack ^
       --add Microsoft.Net.ComponentGroup.4.7.DeveloperTools ^
       --add Microsoft.VisualStudio.Component.FSharp ^
       --add Component.GitHub.VisualStudio ^
       --add Microsoft.VisualStudio.Component.LinqToSql
```

Если образы не включают в себя требуемый компонент Visual Studio, сообщите об этом с помощью средства обратной связи (в правом верхнем углу страницы).

## <a name="what-size-vm-should-i-choose"></a>Какой размер виртуальной машины следует выбрать?

Azure предлагает широкий диапазон размеров виртуальных машин. Так как Visual Studio является мощным многопоточным приложением, вам нужен размер виртуальной машины, в которой предусмотрено по крайней мере два процессора и 7 ГБ памяти. Ниже приведены рекомендуемые размеры виртуальных машин для образов Visual Studio:

* Standard_D2_v3
* Standard_D2s_v3
* Standard_D4_v3
* Standard_D4s_v3
* Standard_D2_v2
* Standard_D2S_v2
* Standard_D3_v2

Дополнительные сведения о последних размерах виртуальных машин см. в статье [Размеры виртуальных машин Windows в Azure](/azure/virtual-machines/windows/sizes).

Благодаря Azure первый выбранный вариант всегда можно заново сбалансировать, изменив размер виртуальной машины. Можно подготовить новую виртуальную машину, размер которой лучше подходит для ваших задач, или изменить размер существующей виртуальной машины, выбрав другое базовое оборудование. Дополнительные сведения см. в статье [Изменение размера виртуальной машины Windows](/azure/virtual-machines/windows/resize-vm).

## <a name="after-the-vm-is-running-whats-next"></a>Что делать после запуска виртуальной машины?

Visual Studio реализует модель использования собственной лицензии в Azure. Как и при установке закрытого оборудования, одним из первых шагов является лицензирование установленного экземпляра Visual Studio. Чтобы разблокировать Visual Studio, выполните одно из следующих действий:

* выполните вход с учетной записью Майкрософт, связанной с подпиской Visual Studio;
* введите ключ продукта, полученный при покупке Visual Studio.

Дополнительные сведения см. в разделах [Выполните вход в Visual Studio](../ide/signing-in-to-visual-studio.md) и [Практическое руководство. Разблокирование Visual Studio](../ide/how-to-unlock-visual-studio.md).

## <a name="how-do-i-save-the-development-vm-for-future-or-team-use"></a>Как сохранить виртуальную машину разработки для использования в будущем или использования командой?

Разнообразие сред разработки очень велико, и создание более сложных сред требует реальных затрат. Независимо от конфигурации вашей среды, вы можете сохранить или записать настроенную виртуальную машину в качестве "базового образа" для использования в будущем или для использования другими членами вашей команды. Затем при загрузке новой виртуальной машины ее можно будет подготовить из базового образа, а не из образа Azure Marketplace.

Вкратце, используйте инструмент Sysprep и завершите работу запущенной виртуальной машины. Затем запишите *(рисунок 1)* ее как образ с помощью пользовательского интерфейса портала Azure. Azure сохранит файл с расширением `.vhd`, содержащий образ, в учетной записи хранения на ваш выбор. Затем новый образ появится в списке ресурсов подписки в виде ресурса "Образ".

![Запись образа через пользовательский интерфейс портала Azure](media/capture-vm.png)

*Рис. 1. Запись образа через пользовательский интерфейс портала Azure.*

Дополнительные сведения см. в статье [Создание управляемого образа универсальной виртуальной машины в Azure](/azure/virtual-machines/windows/capture-image-resource).

> [!IMPORTANT]
> Не забудьте подготовить виртуальную машину с помощью Sysprep. Если пропустить этот шаг, то Azure не удастся подготовить виртуальную машину из образа.

> [!NOTE]
> За хранение этих образов будет взиматься плата, но эти дополнительные затраты будут незначительными по сравнению с дополнительными затратами, необходимыми для повторной сборки виртуальной машины "с нуля" для каждого пользователя в группе, которому она нужна. Например, создание и хранение в течение месяца образа размером 127 ГБ, который может повторно использовать вся ваша команда, обойдется всего в несколько долларов. Однако эти затраты незначительны по сравнению с часами, затрачиваемыми каждым сотрудником на сборку и проверку правильно настроенной среды разработки, предназначенной для индивидуального использования.

Кроме того, для ваших задач разработки или технологий может понадобиться больший масштаб. Например, это могут быть разнообразные конфигурации разработки и конфигурации с несколькими виртуальными машинами. Вы можете использовать Azure DevTest Labs, чтобы создать _файлы инструкций_, автоматизирующие создание вашего "золотого образа", а также управлять политиками для работающих виртуальных машин вашей команды. Статья [Использование Azure DevTest Labs для разработчиков](/azure/devtest-lab/devtest-lab-developer-lab) — лучший источник дополнительных сведений о DevTest Labs.

## <a name="next-steps"></a>Дальнейшие действия

Теперь, когда вы знаете о предварительно настроенных образах Visual Studio, следующим шагом является создание виртуальной машины.

* [Создание виртуальной машины с помощью портала Azure](/azure/virtual-machines/windows/quick-create-portal)
* [Обзор виртуальных машин Windows](/azure/virtual-machines/windows/overview)
