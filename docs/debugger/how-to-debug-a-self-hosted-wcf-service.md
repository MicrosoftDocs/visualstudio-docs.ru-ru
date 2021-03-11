---
title: Отладка резидентной службы WCF | Документация Майкрософт
description: Сведения том, как выполнять отладку локальной службы WCF. Самый простой способ — настроить Visual Studio для запуска клиента и сервера, но это не всегда возможно.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging, WCF
- WCF, self-hosted service
- WCF, debugging
ms.assetid: 288922be-ba3f-411e-af50-bba39c9529cc
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 3cd11966347cd90576eb78a59f6c7eb96cc697ef
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102155085"
---
# <a name="how-to-debug-a-self-hosted-wcf-service"></a>Практическое руководство. отладку резидентной службы WCF
*Резидентная служба* является службой WCF, которая не запускается внутри IIS, узла службы WCF или сервера разработки [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]. Самый легкий путь отладки резидентной WCF — это настройка [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] для запуска клиента и сервера при выборе пункта **Начать отладку** в меню **Отладка**.

 Если служба WCF является резидентной внутри или является процессом, который не может быть запущен таким же образом, как служба NT, использовать этот метод нельзя. Вместо этого можно выполнить одно из следующих действий:

- Вручную присоединить отладчик к главному процессу. Дополнительные сведения см. в статье [Присоединение к выполняемым процессам](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).

     Или...

- Начать отладку клиента, а затем сделать шаг с заходом в вызов службы. Для этого необходимо включить отладку в файле app.config file. Дополнительные сведения см. в разделе [Ограничения по отладке WCF](../debugger/limitations-on-wcf-debugging.md).

### <a name="to-start-both-client-and-host-from-visual-studio"></a>Запуск клиента и процесса размещения из Visual Studio

1. Создайте решение [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], содержащее проекты клиента и сервера.

2. Настройте решение для запуска клиентских и серверных процессов при выборе **Пуск** в меню **Отладка**.

   1. В **обозревателе решений** щелкните правой кнопкой мыши имя решения.

   2. Щелкните **Установка запускаемых проектов**.

   3. В диалоговом окне **Свойства решения \<name>** выберите **Несколько запускаемых проектов**.

   4. В сетке **Несколько запускаемых проектов** на строке, соответствующей серверному проекту, щелкните **Действие** и выберите **Пуск**.

   5. На строке, соответствующей клиентскому проекту, щелкните **Действие** и выберите **Пуск**.

   6. Нажмите кнопку **ОК**.

## <a name="see-also"></a>См. также
- [Отладка служб WCF](../debugger/debugging-wcf-services.md)
- [Ограничения на отладку WCF](../debugger/limitations-on-wcf-debugging.md)
- [Практическое руководство. Пошаговая отладка служб WCF](../debugger/how-to-step-into-wcf-services.md)
