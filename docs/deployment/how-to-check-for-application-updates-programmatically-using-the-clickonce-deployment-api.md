---
title: Автоматическое обновление приложений с помощью API развертывания ClickOnce
description: Узнайте, как написать код в ClickOnce, использующий класс Аппликатиондеплоймент для проверки наличия обновлений на основе события, например запроса пользователя.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, updates
- application updates
ms.assetid: 1a886310-67c8-44e5-a382-c2f0454f887d
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: db82151b7fd4dbe894cecf8fbf5f5b64cb2f5919
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/02/2021
ms.locfileid: "106213944"
---
# <a name="how-to-check-for-application-updates-programmatically-using-the-clickonce-deployment-api"></a>Практическое руководство. Проверка обновлений для приложения программным способом с помощью развертывания API ClickOnce
Технология ClickOnce предоставляет два способа обновления приложения после его развертывания. В первом методе можно настроить развертывание ClickOnce для автоматической проверки обновлений через определенные промежутки времени. Во втором методе можно написать код, использующий <xref:System.Deployment.Application.ApplicationDeployment> класс для проверки наличия обновлений на основе события, например запроса пользователя.

 В следующих процедурах показан код для выполнения программного обновления, а также описывается настройка развертывания ClickOnce для включения программных проверок обновлений.

 Чтобы обновить приложение ClickOnce программным способом, необходимо указать расположение для обновлений. Иногда это называется поставщиком развертывания. Дополнительные сведения об установке этого свойства см. в разделе [Выбор стратегии обновления ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md).

> [!NOTE]
> Вы также можете использовать описанный ниже метод, чтобы развернуть приложение из одного расположения, но обновить его с другого. Дополнительные сведения см. [в разделе инструкции. Указание альтернативного расположения для обновлений развертывания](../deployment/how-to-specify-an-alternate-location-for-deployment-updates.md).

### <a name="to-check-for-updates-programmatically"></a>Программная проверка обновлений

1. Создайте новое приложение Windows Forms с помощью предпочтительной командной строки или визуальных средств.

2. Создайте любую кнопку, пункт меню или другой элемент пользовательского интерфейса, который пользователи должны выбрать для проверки наличия обновлений. В обработчике событий этого элемента вызовите следующий метод, чтобы проверить наличие обновлений и установить их.

    :::code language="csharp" source="../snippets/csharp/VS_Snippets_Winforms/ClickOnceAPI/CS/Form1.cs" id="Snippet6":::
    :::code language="cpp" source="../snippets/cpp/VS_Snippets_Winforms/ClickOnceAPI/cpp/form1.cpp" id="Snippet6":::
    :::code language="vb" source="../snippets/visualbasic/VS_Snippets_Winforms/ClickOnceAPI/VB/Form1.vb" id="Snippet6":::

3. Скомпилируйте приложение.

### <a name="use-mageexe-to-deploy-an-application-that-checks-for-updates-programmatically"></a>Использование Mage.exe для развертывания приложения, которое программно проверяет на наличие обновлений

- Следуйте инструкциям по развертыванию приложения с помощью Mage.exe, как описано в [разделе Пошаговое руководство. Развертывание приложения ClickOnce вручную](../deployment/walkthrough-manually-deploying-a-clickonce-application.md). При вызове Mage.exe для создания манифеста развертывания обязательно используйте параметр командной строки `providerUrl` и укажите URL-адрес, по которому ClickOnce должен проверять наличие обновлений. Если приложение будет обновляться с `http://www.adatum.com/MyApp` , например, вызов для создания манифеста развертывания может выглядеть следующим образом:

    ```cmd
    mage -New Deployment -ToFile WindowsFormsApp1.application -Name "My App 1.0" -Version 1.0.0.0 -AppManifest 1.0.0.0\MyApp.manifest -providerUrl http://www.adatum.com/MyApp/MyApp.application
    ```

### <a name="using-mageuiexe-to-deploy-an-application-that-checks-for-updates-programmatically"></a>Использование MageUI.exe для развертывания приложения, которое программно проверяет на наличие обновлений

- Следуйте инструкциям по развертыванию приложения с помощью Mage.exe, как описано в [разделе Пошаговое руководство. Развертывание приложения ClickOnce вручную](../deployment/walkthrough-manually-deploying-a-clickonce-application.md). На вкладке **Параметры развертывания** задайте для поля **начальное расположение** значение манифест приложения ClickOnce, которое должно проверять наличие обновлений. На вкладке **Параметры обновления** снимите флажок **это приложение должно проверять наличие обновлений** .

## <a name="net-framework-security"></a>Безопасность .NET Framework
 Приложение должно иметь разрешения полного доверия для использования программного обновления.

## <a name="see-also"></a>См. также раздел
- [Как указать альтернативное расположение для обновлений развертывания](../deployment/how-to-specify-an-alternate-location-for-deployment-updates.md)
- [Выбор стратегии обновления ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md)
- [Публикация приложений ClickOnce](../deployment/publishing-clickonce-applications.md)