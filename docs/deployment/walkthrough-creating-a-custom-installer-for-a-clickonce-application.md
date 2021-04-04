---
title: Создание пользовательского установщика для приложения ClickOnce
description: Узнайте, как пользовательский установщик может автоматически устанавливать и обновлять приложение ClickOnce на основе EXE-файла.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, custom installer
- installer [ClickOnce], custom
- deploying applications [ClickOnce], custom installer
- InPlaceHostingManager [ClickOnce], custom installer
- custom installer [ClickOnce]
ms.assetid: fb222cc5-8aeb-4b94-8c49-b93e342f5f69
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: e7ae131026a94fa368d55bad1d8cd2164b6f960b
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/02/2021
ms.locfileid: "106216934"
---
# <a name="walkthrough-create-a-custom-installer-for-a-clickonce-application"></a>Пошаговое руководство. Создание пользовательского установщика для приложения ClickOnce
Любое приложение ClickOnce, основанное на *exe* -файле, может устанавливаться автоматически и обновляться с помощью пользовательского установщика. Пользовательский установщик может реализовать пользовательский интерфейс во время установки, включая пользовательские диалоговые окна для операций безопасности и обслуживания. Для выполнения операций установки пользовательский установщик использует <xref:System.Deployment.Application.InPlaceHostingManager> класс. В этом пошаговом руководстве показано, как создать пользовательский установщик, который автоматически устанавливает приложение ClickOnce.

## <a name="prerequisites"></a>Предварительные требования

### <a name="to-create-a-custom-clickonce-application-installer"></a>Создание пользовательского установщика приложения ClickOnce

1. В приложении ClickOnce добавьте ссылки на System. Deployment и System. Windows. Forms.

2. Добавьте в приложение новый класс и укажите любое имя. В этом пошаговом руководстве используется имя `MyInstaller`.

3. Добавьте следующие `Imports` `using` директивы или в начало нового класса.

    ```vb
    Imports System.Deployment.Application
    Imports System.Windows.Forms
    ```

    ```csharp
    using System.Deployment.Application;
    using System.Windows.Forms;
    ```

4. Добавьте в класс следующие методы.

     Эти методы вызывают <xref:System.Deployment.Application.InPlaceHostingManager> методы для загрузки манифеста развертывания, утверждения соответствующих разрешений, попросите пользователя установить разрешение на установку, а затем скачайте и установите приложение в кэш ClickOnce. Пользовательский установщик может указать, что приложение ClickOnce является предварительно доверенным, или может отложить принятие решения о доверии <xref:System.Deployment.Application.InPlaceHostingManager.AssertApplicationRequirements%2A> вызовом метода. Этот код предварительно доверяет приложению.

    > [!NOTE]
    > Разрешения, назначенные с помощью предварительного доверия, не могут превышать разрешения пользовательского кода установщика.

    :::code language="vb" source="../snippets/visualbasic/VS_Snippets_Winforms/System.Deployment.Application.InPlaceHostingManager/VB/Form1.vb" id="Snippet1":::
    :::code language="csharp" source="../snippets/csharp/VS_Snippets_Winforms/System.Deployment.Application.InPlaceHostingManager/CS/Form1.cs" id="Snippet1":::

5. Чтобы попытаться выполнить установку из кода, вызовите `InstallApplication` метод. Например, если вы `MyInstaller` назовете свой класс, вы можете вызвать метод `InstallApplication` следующим образом.

    ```vb
    Dim installer As New MyInstaller()
    installer.InstallApplication("\\myServer\myShare\myApp.application")
    MessageBox.Show("Installer object created.")
    ```

    ```csharp
    MyInstaller installer = new MyInstaller();
    installer.InstallApplication(@"\\myServer\myShare\myApp.application");
    MessageBox.Show("Installer object created.");
    ```

## <a name="next-steps"></a>Дальнейшие действия
 Приложение ClickOnce может также добавлять пользовательскую логику обновления, включая пользовательский интерфейс, отображаемый во время процесса обновления. Дополнительные сведения см. в разделе <xref:System.Deployment.Application.UpdateCheckInfo>. Приложение ClickOnce также может подавлять стандартную запись меню "Пуск", ярлык, а также запись "Установка и удаление программ" с помощью `<customUX>` элемента. Дополнительные сведения см. в разделе [ \<entryPoint> element](../deployment/entrypoint-element-clickonce-application.md) и <xref:System.Deployment.Application.DownloadApplicationCompletedEventArgs.ShortcutAppId%2A> .

## <a name="see-also"></a>См. также раздел
- [Манифест приложения ClickOnce](../deployment/clickonce-application-manifest.md)
- [Элемент \<entryPoint>](../deployment/entrypoint-element-clickonce-application.md)
