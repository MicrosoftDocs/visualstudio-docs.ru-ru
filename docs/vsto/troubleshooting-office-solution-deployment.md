---
title: Устранение неполадок развертывания решений Office
description: Узнайте, как можно решать распространенные проблемы, которые могут возникнуть при развертывании решений Office.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: troubleshooting
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ClickOnce deployment [Office development in Visual Studio], troubleshooting
- Office development in Visual Studio, troubleshooting
- deploying applications [Office development in Visual Studio], troubleshooting
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 59b5e36eb02ff2c8db9e2e206a4040757e130716
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99968844"
---
# <a name="troubleshoot-office-solution-deployment"></a>Устранение неполадок развертывания решений Office
  В этом разделе содержатся сведения об устранении неполадок, которые могут возникнуть при развертывании решений Office.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

## <a name="troubleshoot-office-solutions-by-using-the-event-viewer"></a>Устранение неполадок решений Office с помощью средства просмотра событий
 Вы можете использовать средство просмотра событий в Windows для просмотра сообщений об ошибках, записанных средой выполнения [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] при установке или удалении решений Office. С помощью этих сообщений из журнала событий можно разрешать проблемы развертывания и установки. Дополнительные сведения см. в статье [ведение журнала событий для решений Office](../vsto/event-logging-for-office-solutions.md).

## <a name="change-the-assembly-name-causes-conflicts"></a>Изменение имени сборки вызывает конфликты
 Если изменить значение **имени сборки** на странице **приложение** **конструктора проектов** после развертывания решения, средства публикации будут изменять пакет установки, чтобы он имел один *Setup.exe* файл и два манифеста развертывания. При развертывании двух файлов манифеста могут возникнуть следующие обстоятельства.

- Если конечный пользователь установит обе версии, приложение будет загружать обе надстройки VSTO.

- Если надстройка VSTO была установлена до изменения имени сборки, конечный пользователь никогда не будет получать обновления.

  Чтобы избежать этих условий, не изменяйте значение **имени сборки** решения после развертывания решения.

## <a name="check-for-updates-takes-a-long-time"></a>Проверка наличия обновлений занимает много времени
 Visual Studio 2010 Tools для Office Runtime предоставляет запись реестра, которую администраторы могут использовать для задания значения времени ожидания загрузки манифестов и решения.

#### <a name="to-set-the-time-out-value"></a>Установка значения времени ожидания.

1. В реестре перейдите в следующий раздел:

     **HKEY_CURRENT_USER\Software\Microsoft\VSTA**

2. В подразделе **AddInTimeout** задайте значение времени ожидания в миллисекундах.

     Если подраздел **AddInTimeout** не существует, создайте его как DWORD.

## <a name="cant-update-or-publish-to-a-network-file-share"></a>Не удается обновить или опубликовать в сетевой общей папке
 Решения Office, находясь в общей сетевой папке, могут отображать ошибочное сообщение во время обновления, если во время публикации обновления файл *Setup.exe* решения заблокирован в процессе. Сообщение может говорить следующее: "Не удается добавить ’setup.exe’ на веб-сайт. Файл ’setup.exe’ уже существует на этом веб-сайте".

 Чтобы предотвратить блокировку файла, можно сделать этот файловый ресурс доступным конечным пользователям только для чтения. Однако если в этом файловом ресурсе имеются документы, они также становятся доступными конечным пользователям только для чтения.

## <a name="prerequisites-for-microsoft-office-arent-installed"></a>Предварительные требования для Microsoft Office не установлены
 Вы можете добавить .NET Framework, [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]и основные сборки взаимодействия Office в пакет установки в качестве необходимых компонентов, развертываемых вместе с решением Office. Сведения об установке основных сборок взаимодействия см. в статьях [Настройка компьютера для разработки решений Office](../vsto/configuring-a-computer-to-develop-office-solutions.md) и [Установка основных сборок взаимодействия Office](../vsto/how-to-install-office-primary-interop-assemblies.md).

## <a name="publish-using-localhost-can-cause-installation-problems"></a>Публикация с использованием localhost может привести к проблемам установки
 При использовании в `http://localhost` качестве расположения для публикации или установки решений на уровне документа **Мастер публикации** не преобразует строку в реальное имя компьютера. В таком случае необходимо установить решение на компьютере разработки. Чтобы развернутые решения могли использовать службы IIS на компьютере разработки, вместо localhost указывайте полное имя для всех расположений HTTP, HTTPS и FTP.

## <a name="cached-assemblies-are-loaded-instead-of-updated-assemblies"></a>Вместо обновленных сборок загружаются кэшированные сборки
 Fusion, загрузчик сборок .NET Framework, загружает кэшированную копию сборок, если выходной путь проекта указывает на сетевой файловый ресурс, сборка подписана строгим именем и версия сборки настройки не изменена. При обновлении сборки, которая удовлетворяет этим условиям, обновление не будет отображаться при следующем запуске проекта, поскольку будет загружена кэшированная копия.

 Вы можете настроить Visual Studio так, чтобы Fusion загружал сборки при каждом запуске проекта.

### <a name="to-download-assemblies-instead-of-loading-cached-copies"></a>Загрузка сборок вместо загрузки кэшированных копий

1. В меню последовательно выберите **Проект**, _ProjectName_**Свойства**.

2. На странице **Приложения** выберите **Сведения о сборке**.

3. Задайте для номера редакции (третье поле) **версии сборки** подстановочный знак ( \* ). Например, "1,0. *".  Затем нажмите кнопку **ОК** .

   После изменения версии сборки вы можете продолжить подписывать сборку строгим именем, и Fusion будет загружать последнюю версию настройки.

 [!NOTE]
> Начиная с Visual Studio 2017 при попытке использовать подстановочные знаки в версии сборки возникнет ошибка сборки.  Это обусловлено тем, что подстановочные карты в версии сборки нарушают детерминированную функцию MSBuild. Вам будет предложено либо удалить подстановочные знаки из версии сборки, либо отключить определитель.  Дополнительные сведения о детерминированной функции см. в разделе [Общие свойства проекта MSBuild](../msbuild/common-msbuild-project-properties.md) и [Настройка сборки](../msbuild/customize-your-build.md) .

## <a name="installation-fails-when-the-uri-has-characters-that-arent-us-ascii"></a>Установка завершается сбоем, если в URI есть символы, не являющиеся US-ASCII
 При публикации решения Office в расположении HTTP, HTTPS и FTP путь не может содержать какие-либо символы Юникода, не входящие в набор US-ASCII. Такие символы могут привести к непредсказуемому поведению программы установки. Используйте для пути установки только символы US-ASCII.

## <a name="prompt-to-manually-uninstall-appears-when-you-publish-and-install-a-solution-on-the-development-computer"></a>Запрос на удаление вручную появляется при публикации и установке решения на компьютере разработчика
 При сборке решения Office версия сборки регистрируется автоматически. Если ранее вы опубликовали и установили то же решение на свой компьютер разработки, то после следующей сборки, перестроения или публикации решения среда выполнения [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] обнаруживает, что путь установки для опубликованной версии и версия сборки отличаются. Появляется сообщение об ошибке "Не удается установить настройку, поскольку уже установлена другая версия, обновление которой из этой папки невозможно". Разделы реестра обновляются при каждом перестроении решения. Таким образом, необходимо удалить предыдущую версию перед публикацией, отладкой или запуском новой версии.

 Чтобы предотвратить появление этого сообщения, создайте другую учетную запись пользователя на компьютере разработки для тестирования развертывания. Вы также можете удалить версию из списка программ, установленных на компьютере, перед следующей публикацией, отладкой или перестроением решения.

## <a name="uncaught-exception-or-method-not-found-error-when-you-install-a-solution"></a>При установке решения возникла ошибка "неперехваченное исключение" или "метод не найден"
 При установке решений Office путем открытия манифеста развертывания ( *VSTO* -файла), приложения Office, документа или книги сообщения об ошибках могут отображаться в следующих случаях.

- Метод не найден.

- MissingMethodException.

- Неперехваченное исключение.

  Чтобы предотвратить эти сообщения об ошибках, устанавливайте решение путем запуска программы установки.

  При установке решения без запуска программы установки установщик не проверяет и не устанавливает необходимые компоненты. Программа установки проверяет наличие соответствующих версий необходимых компонентов и устанавливает их по мере необходимости.

## <a name="manifest-registry-keys-for-add-ins-change-after-an-installshield-limited-edition-project-is-built"></a>Разделы реестра манифеста для надстроек изменяются после сборки проекта InstallShield Limited Edition
 Раздел реестра манифеста, который является частью программы установки надстройки VSTO, иногда изменяется с *VSTO* на *. dll. manifest* при сборке проекта InstallShield Limited Edition.

 Чтобы обойти эту проблему, создайте проект InstallShield Limited Edition в другом решении или используйте CompanyName.AddinName в качестве значения раздела реестра, содержащего имя надстройки VSTO.

## <a name="the-clickonce-installer-for-your-office-solution-doesnt-install-the-primary-interop-assemblies"></a>Установщик ClickOnce для решения Office не устанавливает основные сборки взаимодействия
 При запуске программы установки, созданной ClickOnce для решения Office, установщик для основных сборок взаимодействия Office запускается только в том случае, если никакие основные сборки взаимодействия еще не установлены.

 Если программа установки не устанавливает сборки PIA правильно, установите их вручную, запустив файл установщика с именем *o2007pia.msi* из каталога установки.

## <a name="reinstall-office-solutions-causes-an-argument-out-of-range-exception"></a>Переустановка решений Office приводит к исключению аргумента вне диапазона
 При повторной установке решения Office может возникать исключение <xref:System.ArgumentOutOfRangeException> со следующим сообщением об ошибке: "Заданный аргумент находится вне диапазона допустимых значений".

 Такая ситуация возникает, если регистр URL-адреса для местоположения установки отличается. Например, эта ошибка появляется, если вы установили решение Office впервые, `http://fabrikam.com/ExcelSolution.vsto` а затем использовали `http://fabrikam.com/excelsolution.vsto` второй раз.

 Чтобы предотвратить появление этого сообщения, используйте один и тот же регистр при установке решения Office.

## <a name="cant-install-a-clickonce-solution-by-opening-the-deployment-manifest-from-the-web"></a>Не удается установить решение ClickOnce, открыв манифест развертывания из Интернета
 Пользователи могут установить решение Office путем открытия манифеста развертывания из Интернета. Однако некоторые установки службы IIS (IIS) блокируют расширение имени файла *VSTO* . Необходимо определить тип MIME в службах IIS, прежде чем использовать его для развертывания решения Office.

 Сведения о том, как определить тип MIME в IIS 7, см. в разделе [Добавление типа MIME (IIS7)](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc725608(v=ws.10)).

 Установите **.vsto** в качестве расширения и **application/x-ms-vsto** в качестве типа MIME.

## <a name="see-also"></a>См. также раздел

- [Устранение неполадок развертываний ClickOnce](../deployment/troubleshooting-clickonce-deployments.md)
- [Развертывание решения Office](../vsto/deploying-an-office-solution.md)
- [Устранение неполадок в Visual Studio](/troubleshoot/visualstudio/welcome-visual-studio/)