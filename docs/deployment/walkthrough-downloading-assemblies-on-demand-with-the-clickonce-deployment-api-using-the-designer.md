---
title: Загрузка сборок по запросу с помощью конструктора (API ClickOnce)
description: Узнайте, как пометить определенные сборки в приложении ClickOnce как необязательные с помощью конструктора и скачать их, когда они необходимы для среды CLR.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- assemblies, downloading [ClickOnce]
- Windows applications, ClickOnce deployments
- ClickOnce deployment, on-demand download
- on-demand assemblies, ClickOnce
ms.assetid: 59a0dd5f-1cab-4f2f-b780-0ab7399905d5
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 7bb30b26e859708d295a31bd45b310897e4bcaac
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/02/2021
ms.locfileid: "106216999"
---
# <a name="walkthrough-download-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer"></a>Пошаговое руководство. Загрузка сборок по запросу с помощью API развертывания ClickOnce в конструкторе
По умолчанию все сборки, включенные в приложение [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] , загружаются при первом его запуске. Однако некоторые части приложения могут быть нужны лишь небольшому числу пользователей. В этом случае рекомендуется скачивать сборку только при создании одного из ее типов. В следующем примере показано, как пометить определенные сборки в приложении как "необязательные" и скачивать их с помощью классов в пространстве имен <xref:System.Deployment.Application> , когда среда CLR нуждается в них.

> [!NOTE]
> Для выполнения данной процедуры приложение должно выполняться с полным доверием.

> [!NOTE]
> Отображаемые диалоговые окна и команды меню могут отличаться от описанных в справке в зависимости от текущих параметров или выпуска. Чтобы изменить параметры, выберите в меню **Сервис** пункт **Импорт и экспорт параметров** . Дополнительные сведения см. в разделе [Сброс параметров](../ide/environment-settings.md#reset-settings).

## <a name="create-the-projects"></a>Создание проектов

### <a name="to-create-a-project-that-uses-an-on-demand-assembly-with-visual-studio"></a>Создание проекта, использующего сборку по запросу с помощью Visual Studio

1. Создайте проект Windows Forms в [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. В меню **Файл** выберите пункт **Добавить**, затем щелкните **Создание проекта**. Выберите проект **Библиотека классов** в диалоговом окне и назовите его `ClickOnceLibrary`.

   > [!NOTE]
   > В Visual Basic мы рекомендуем изменить свойства проекта, чтобы сменить корневое пространство имен для этого проекта на `Microsoft.Samples.ClickOnceOnDemand` или то, которое подходит вам. Для простоты два проекта в этом пошаговом руководстве находятся в одном пространстве имен.

2. Определите класс `DynamicClass` с одним свойством `Message`.

    :::code language="vb" source="../snippets/visualbasic/VS_Snippets_Winforms/ClickOnceLibrary/VB/Class1.vb" id="Snippet1":::
    :::code language="csharp" source="../snippets/csharp/VS_Snippets_Winforms/ClickOnceLibrary/CS/Class1.cs" id="Snippet1":::

3. Выберите проект Windows Forms в **обозревателе решений**. Добавьте ссылку на сборку <xref:System.Deployment.Application> и ссылку на проект `ClickOnceLibrary` .

   > [!NOTE]
   > В Visual Basic мы рекомендуем изменить свойства проекта, чтобы сменить корневое пространство имен для этого проекта на `Microsoft.Samples.ClickOnceOnDemand` или то, которое подходит вам. Для простоты два проекта в этом пошаговом руководстве находятся в одном пространстве имен.

4. Щелкните форму правой кнопкой мыши, выберите **Просмотреть код** и добавьте следующие ссылки на форму.

    :::code language="csharp" source="../snippets/csharp/VS_Snippets_Winforms/ClickOnceOnDemand/CS/Form1.cs" id="Snippet1":::
    :::code language="vb" source="../snippets/visualbasic/VS_Snippets_Winforms/ClickOnceOnDemand/VB/Form1.vb" id="Snippet1":::

5. Добавьте следующий код для скачивания этой сборки по запросу. Этот код показывает, как сопоставить набор сборок с именем группы с помощью универсального класса <xref:System.Collections.DictionaryBase.Dictionary%2A> . Поскольку в этом пошаговом руководстве мы скачиваем только одну сборку, в нашей группе присутствует только одна сборка. В реальном приложении рекомендуется скачать сразу все сборки, связанные с одной функцией в приложении. Таблица сопоставлений позволяет легко сделать это, связав все библиотеки DLL, относящиеся к некоторому компоненту, с именем группы скачивания.

    :::code language="csharp" source="../snippets/csharp/VS_Snippets_Winforms/ClickOnceOnDemand/CS/Form1.cs" id="Snippet2":::
    :::code language="vb" source="../snippets/visualbasic/VS_Snippets_Winforms/ClickOnceOnDemand/VB/Form1.vb" id="Snippet2":::

6. В меню **Вид** выберите пункт **Область элементов**. Перетащите <xref:System.Windows.Forms.Button> с **панели элементов** в форму. Дважды нажмите кнопку и добавьте приведенный ниже код в обработчик событий <xref:System.Windows.Forms.Control.Click> .

    :::code language="csharp" source="../snippets/csharp/VS_Snippets_Winforms/ClickOnceOnDemand/CS/Form1.cs" id="Snippet3":::
    :::code language="vb" source="../snippets/visualbasic/VS_Snippets_Winforms/ClickOnceOnDemand/VB/Form1.vb" id="Snippet3":::

## <a name="mark-assemblies-as-optional"></a>Пометить сборки как необязательные

### <a name="to-mark-assemblies-as-optional-in-your-clickonce-application-by-using-visual-studio"></a>Пометка сборок как необязательных в приложении ClickOnce с помощью Visual Studio

1. Щелкните правой кнопкой мыши проект Windows Forms в **обозревателе решений** и выберите пункт **Свойства**. Перейдите на вкладку **Публикация** .

2. Нажмите кнопку **Файлы приложения** .

3. Найдите описание для *ClickOnceLibrary.dll*. Задайте в раскрывающемся списке **Состояние публикации** значение **Включить**.

4. Разверните раскрывающийся список **Группа** и выберите **Создать**. Введите имя `ClickOnceLibrary` в качестве имени новой группы.

5. Продолжайте публикацию приложения, как описано в статье [как опубликовать приложение ClickOnce с помощью мастера публикации](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md).

### <a name="to-mark-assemblies-as-optional-in-your-clickonce-application-by-using-manifest-generation-and-editing-tool--graphical-client-mageuiexe"></a>Пометка сборок как необязательных в приложении ClickOnce с помощью Инструмента создания и изменения манифестов с графическим клиентом (MageUI.exe)

1. Создайте [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] манифесты, как описано в разделе [Пошаговое руководство. Развертывание приложения ClickOnce вручную](../deployment/walkthrough-manually-deploying-a-clickonce-application.md).

2. Перед закрытием MageUI.exe выберите вкладку, содержащую манифест приложения развертывания и откройте на ней вкладку **Файлы** .

3. Найдите ClickOnceLibrary.dll в списке файлов приложения и задайте в столбце **Тип файла** значение **Нет**. Для столбца **Группа** введите значение `ClickOnceLibrary.dll`.

## <a name="test-the-new-assembly"></a>Тестирование новой сборки

Тестирование сборки по запросу:

1. Запустите приложение, развернутое с использованием [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].

2. Когда появится основная форма, нажмите <xref:System.Windows.Forms.Button>. В окне сообщения вы должны видеть строку "Hello, World!"

## <a name="see-also"></a>См. также раздел

- <xref:System.Deployment.Application.ApplicationDeployment>
