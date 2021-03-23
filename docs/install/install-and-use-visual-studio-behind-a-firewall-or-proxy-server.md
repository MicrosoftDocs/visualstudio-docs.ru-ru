---
title: Установка и использование в среде, защищенной брандмауэром или прокси-сервером
description: Узнайте, какие URL-адреса доменов, порты и протоколы может потребоваться внести в список разрешений или открыть, если в организации применяется брандмауэр или прокси-сервер.
ms.date: 06/17/2020
ms.custom: seodec18
ms.topic: conceptual
helpviewer_keywords:
- network installation, Visual Studio
- administrator guide, Visual Studio
- installing Visual Studio, administrator guide
- list of domains, locations, URLs
ms.assetid: ''
author: ornellaalt
ms.author: ornella
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 44af5c5a00e1ca26eb545b0973090486f6d320ea
ms.sourcegitcommit: 99b66b0f4ced46ead0b2506a103f974f40cc0076
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/12/2021
ms.locfileid: "103295708"
---
# <a name="install-and-use-visual-studio-and-azure-services-behind-a-firewall-or-proxy-server"></a>Установка и использование Visual Studio и служб Azure, расположенных за брандмауэром или прокси-сервером

Если вы или ваша организация используете средства обеспечения безопасности, например брандмауэр или прокси-сервер, значит есть URL-адреса доменов, которые нужно добавить в список разрешений, а также порты и протоколы, которые нужно открыть, чтобы обеспечить оптимальные установку и использование Visual Studio и служб Azure.

* **[Установка Visual Studio](#install-visual-studio)** . Таблицы в этом разделе содержат URL-адреса доменов, которые нужно добавить в список разрешений, чтобы получить доступ ко всем необходимым компонентам и рабочим нагрузкам.

* **[Использование Visual Studio и служб Azure](#use-visual-studio-and-azure-services)** . Таблица в этом разделе содержит URL-адреса доменов, которые нужно добавить в список разрешений, а также порты и протоколы, которые нужно открыть, чтобы получить доступ ко всем необходимым компонентам и службам.

> [!NOTE]
> Эта статья относится к Visual Studio в Windows, однако некоторые сведения также применимы к [установке Visual Studio для Mac](/visualstudio/mac/install-behind-a-firewall-or-proxy-server) за брандмауэром или прокси-сервером.

## <a name="install-visual-studio"></a>Установка Visual Studio

### <a name="urls-to-add-to-an-allow-list"></a>URL-адреса, добавляемые в список разрешений

С учетом того, что Visual Studio Installer скачивает файлы из различных доменов и их серверов загрузки, ниже приведены URL-адреса доменов, которые нужно добавить в список разрешений как доверенные с помощью пользовательского интерфейса или скриптов развертывания.

#### <a name="microsoft-domains"></a>Домены Майкрософт

| Домен | Цель |
| - | - |
| go.microsoft.com | Настройка разрешения URL-адресов |
| aka.ms | Настройка разрешения URL-адресов |
| download.visualstudio.microsoft.com | Настройка расположения для скачивания пакетов |
| download.microsoft.com | Настройка расположения для скачивания пакетов |
| download.visualstudio.com | Настройка расположения для скачивания пакетов |
| dl.xamarin.com | Настройка расположения для скачивания пакетов |
| xamarin-downloads.azureedge.net | Расположение списка скачивания пакетов SDK для Android |
| marketplace.visualstudio.com | Расположение для скачивания расширений Visual Studio |
| \*.gallerycdn.vsassets.io  | Расположение для скачивания расширений Visual Studio |
| visualstudio.microsoft.com | Расположение документации |
| docs.microsoft.com | Расположение документации |
| msdn.microsoft.com | Расположение документации |
| www\.microsoft.com | Расположение документации |
| \*.windows.net | Расположение входа |
| \*.microsoftonline.com | Расположение входа |
| \*.live.com | Расположение входа |
| | |

#### <a name="non-microsoft-domains"></a>Сторонние домены

| Домен | Устанавливает эти рабочие нагрузки |
| - | - |
| archive.apache.org | Разработка мобильных приложений с помощью JavaScript (Cordova) |
| cocos2d-x.org | Разработка игр с помощью C++ (Cocos) |
| download.epicgames.com | Разработка игр с помощью C++ (Unreal Engine) |
| download.oracle.com | Разработка мобильных приложений с помощью JavaScript (пакет SDK для Java) <br /><br />Разработка мобильных приложений с помощью .NET (пакет SDK для Java) |
| download.unity3d.com | Разработка игр с помощью Unity (Unity) |
| netstorage.unity3d.com | Разработка игр с помощью Unity (Unity) |
| dl.google.com | Разработка мобильных приложений с помощью JavaScript (пакеты SDK и NDK для Android, эмулятор) <br /><br />Разработка мобильных приложений с помощью .NET (пакеты SDK и NDK для Android, эмулятор) |
| www\.incredibuild.com | Разработка игр с помощью C++ (IncrediBuild) |
| incredibuildvs2017i.azureedge.net | Разработка игр с помощью C++ (IncrediBuild) |
| www\.python.org | Разработка с помощью Python (Python) <br /><br />Приложения для обработки и анализа данных и аналитические приложения (Python) |
| developerservices2.apple.com | Подготовка Xamarin.iOS |
| developer.apple.com | Подготовка Xamarin.iOS |
| appstoreconnect.apple.com | Подготовка Xamarin.iOS |
| idmsa.apple.com | Подготовка Xamarin.iOS |
| akamized.net | Сеть доставки содержимого (Akamai Technologies) |
| | |

## <a name="use-visual-studio-and-azure-services"></a>Использование Visual Studio и служб Azure

### <a name="urls-to-add-to-an-allow-list-and-ports-and-protocols-to-open"></a>URL-адреса для добавления в список разрешений, а также порты и протоколы для открытия

Ниже приведены URL-адреса доменов, которые нужно добавить в список разрешений, а также порты и протоколы, которые нужно открыть, чтобы обеспечить доступ ко всем необходимым компонентам при использовании Visual Studio или служб Azure, расположенных за брандмауэром или прокси-сервером.

| Служба или сценарий | Конечная точка DNS | Протокол<br/>/Порт | Описание |
| - | - | -: | - | - |
| URL-адрес<br>разрешение | go.microsoft.com<br><br>aka.ms | | Используется для сокращения URL-адресов, которые затем разрешаются в длинные URL-адреса |
| Начальная страница | vsstartpage.blob.core.windows.net | 443 | Используется для отображения новостей для разработчиков на начальной странице (только Visual Studio 2017) |
| Целевая<br> Уведомление <br>Служба | targetednotifications-tm.trafficmanager.net <br><br>www.research.net | 443<br><br>443 | Используется для фильтрации глобального списка уведомлений, чтобы сделать его применимым только к определенным типам компьютеров и сценариев использования |
| Расширение <br>для расширения | marketplace.visualstudio.com<br><br>&#42;.windows.net <br>&#42;.microsoftonline.com <br>&#42;.live.com | 443 | Используется для уведомления о доступном обновлении для установленного расширения <br><br> Используется как расположение для входа |
| Интеграция <br>Интеграция | az861674.vo.msecnd.net | 443<br> | Используется для настройки новых проектов и отправки данных об использовании в зарегистрированную учетную запись Application Insights |
| Code Lens | codelensprodscus1su0.app.<br>codelens.visualstudio.com | 443 | Используется для предоставления сведений в редакторе, например времени последнего обновления файла, временной шкалы изменений, связанных с изменениями рабочими элементами, данных о авторе и т. д. |
| Экспериментальный <br>экспериментальной функции | visualstudio-devdiv-c2s.msedge.net | 80 | Используется для активации новых экспериментальных функций или измененных функций |
| Значок идентификатора <br>(имя пользователя и аватар)<br>и <br>перемещения | app.vssps.visualstudio.com <br><br>app.vsspsext.visualstudio.com<br><br>app.vssps.visualstudio.com<br><br> ns-sb2-prod-ch1-002.cloudapp.net <br><br>az700632.vo.msecnd.net<br><br>api.vstsusers.visualstudio.com/profiles/* | 443 | Используется для отображения имени пользователя и аватара в среде IDE <br><br> Используется для перемещения изменений параметров с одного компьютера на другой |
| Настройки удаленной системы | az700632.vo.msecnd.net | 443 | Используется для отключения расширений, которые могут вызывать проблемы в работе Visual Studio |
| Средства Windows | developer.microsoft.com <br><br>dev.windows.com  <br><br>appdev.microsoft.com | https/443 | Применяется для сценариев использования магазина приложений Windows |
| Поддержка <br>Обнаружение <br><br>Поддержка <br>Определение<br><br>Поддержка <br>схемы JSON для <br>ресурсов Azure | json.schemastore.org <br>schemastoreorg.azurewebsites.net<br><br>json-schema.org<br><br>schema.management.azure.com | http/80<br>https/443<br><br>http/80<br><br>https/443 | Используется для обнаружения и скачивания схем JSON, которые можно применять при изменении документов JSON <br><br>Используется для получения схемы проверки метаданных для JSON<br><br>Используется, чтобы получить текущую схему для шаблонов развертывания Azure Resource Manager |
| Обнаружение <br>обнаружение | Skimdb.npmjs.com <br><br>Registry.npmjs.org <br><br>Api.npms.io | https/443<br><br>http/80 и<br> https/443<br>https/443 | Требуется для поиска пакетов NPM и используется для установки клиентского пакета скриптов в веб-проектах |
| Значки<br> значки<br><br>Значки <br>search | Bower.io <br><br>bowercache.azurewebsites.net <br>go.microsoft.com <br>Registry.bower.io | http/80<br><br>https/443<br>http/80<br>https/443 | Предоставляет значок по умолчанию для пакета Bower  <br><br>Позволяет выполнять поиск пакетов Bower |
| NuGet<br><br>Пакет NuGet<br> обнаружение | api.nuget.org <br>www.nuget.org <br>nuget.org <br>azuresearch-usnc.nuget.org <br>azuresearch-ussc.nuget.org <br>licenses.nuget.org <br>nuget.cdn.azure.cn <br>azuresearch-ea.nuget.org <br>azuresearch-sea.nuget.org <br><br>crl3.digicert.com <br>crl4.digicert.com <br>ocsp.digicert.com <br>cacerts.digicert.com | https/443<br><br>http/80 и<br>https/443<br> | Используется для проверки подписанных пакетов NuGet.<br><br>Требуется для поиска пакетов NuGet и их версий |
| Сведения о репозитории GitHub | api.github.com | https/443 | Требуется для получения дополнительных сведений о пакетах Bower |
| Веб-анализаторы кода | Eslint.org<br><br>www.Bing.com <br><br>www.coffeelint.org | http/80 | |
| Создание проекта<br>шаблонов обозревателя<br>обнаружение <br><br>Создание проекта <br>в обозревателе<br> Cookiecutter | api.github.com <br>raw.githubusercontent.com <br>go.microsoft.com<br><br>pypi.org <br> pypi.python.org | https/443<br> | Используется для обнаружения шаблонов в Интернете из рекомендуемого нами веб-канала и репозиториев GitHub <br><br>Используется для создания проекта из шаблона Cookiecutter, для которого требуется один раз по требованию установить пакет Python для Cookiecutter из индекса пакета Python (PyPI) |
| Управление <br>обнаружение<br><br>Управление <br>управление<br><br>Оператор new <br>Python <br> проект <br>шаблоны | pypi.org<br> <br>pypi.python.org <br>bootstrap.pypa.io<br><br>go.microsoft.com | https/443 | Позволяет выполнять поиск пакетов PIP<br><br>Используется для автоматической установки пакета PIP, если он отсутствует <br><br>Используется для разрешения следующих новых шаблонов проектов Python в URL-адреса шаблонов Cookiecutter:<br> — проект классификатора;<br>— проект кластеризации; <br> — проект регрессии; <br> — PyGame с использованием PyKinect; <br> — проект Pyvot. |
| Служба <br>надстройка <br> манифеста <br>Проверка <br>Служба | verificationservice.osi.office.net | https/443 | Используется для проверки манифестов веб-надстроек Office |
| Веб-надстройки для SharePoint и <br>Office Add-ins | sharepoint.com<br> microsoft.com/microsoft-365<br> microsoftonline.com <br> outlook.com | https/443 | Используется для публикации и тестирования надстроек SharePoint и Office в SharePoint Online и Microsoft 365 |
| Узел службы <br>тестирования<br> Узел | | http/12292 | Правило брандмауэра, которое создается автоматически для тестирования надстроек SharePoint с помощью рабочих процессов |
| Автоматически собранные <br>статистические данные о надежности <br>и другие <br>программы улучшения качества <br>программного обеспечения (CEIP)<br> для пакета Azure SDK и <br>инструментов SQL <br><br> | vortex.data.microsoft.com<br> <br>dc.services.visualstudio.com | https/443 | Используется для отправки статистических данных о надежности (данных об аварийном завершении или отсутствии отклика) от пользователя в корпорацию Майкрософт. Фактические дампы аварийного завершения или отсутствия отклика по-прежнему будут отправляться, даже если включены Отчеты об ошибках Windows. Не будут отправляться только статистические данные. <br>Используется, чтобы выявить анонимное использование расширения пакета SDK для Azure Tools и средств SQL в Visual Studio |
| Visual Studio <br> программного обеспечения <br>Visual Studio <br><br>PerfWatson.exe | vortex.data.microsoft.com<br>dc.services.visualstudio.com<br>visualstudio-devdiv-c2s.msedge.net<br>az667904.vo.msecnd.net <br>scus-breeziest-in.cloudapp.net<br> | https/443 | Используется для сбора данных об анонимном использовании и журналов ошибок <br><br>Используется для отслеживания проблем блокировки пользовательского интерфейса |
| Создание и<br>администрирование <br>ресурсов Azure | management.azure.com <br>management.core.windows.net | https/443 | Используется для создания Веб-сайтов Azure и других ресурсов для поддержки публикаций веб-приложений, Функций Azure или веб-заданий |
| Рекомендации по <br>проверкам и расширениям <br>обновленного инструментария для веб-публикации | marketplace.visualstudio.com | https/443 | Используется для проверки доступности обновленного инструментария для публикации. Если эта конечная точка отключена, потенциально рекомендуемое расширение для веб-публикации может не отображаться |
| Сведения об обновленной <br>конечной точке для создания ресурсов Azure | \*.blob.core.windows.net | https/443 | Применяется для обновления конечных точек, используемых при создании ресурсов Azure для определенных служб Azure. Если эта конечная точка отключена, будут использоваться расположения последней скачанной или встроенной конечной точки |
| Удаленная отладка и <br>удаленное профилирование <br>Веб-сайтов Azure | &#42;.cloudapp.net <br> &#42;.azurewebsites.net | 4022 | Используется для присоединения удаленного отладчика к Веб-сайтам Azure. Если эта конечная точка отключена, подключение удаленного отладчика к Веб-сайтам Azure будет невозможным |
| Active Directory <br>Graph | graph.windows.net | https/443 | Используется для подготовки новых приложений Azure Active Directory. Также используется поставщиком подключенной службы MSGraph Microsoft 365 |
| Проверка <br>обновлений CLI <br>службы "Функции Azure" | functionscdn.azureedge.net | https/443 | Используется для проверки наличия обновленных версий CLI службы "Функции Azure". Если эта конечная точка отключена, будет использоваться кэшированная копия CLI (или копия, передаваемая компонентом "Функции Azure") |
| Cordova | npmjs.org<br>gradle.org | http/80 и<br/>https/443 | HTTP используется для скачивания Gradle во время сборки. HTTPS используется для включения подключаемых модулей Cordova в проекты |
| Cloud Explorer | 1. &#60;Конечная точка кластера&#62; <br>Service Fabric. <br>2. &#60;Конечная точка управления&#62;<br>Cloud Explorer общего назначения. <br>3. &#60;Конечная точка Graph&#62;<br>Cloud Explorer общего назначения.<br>4. &#60;Конечная точка учетной записи хранения&#62;:<br>узлы хранилища. <br>5. &#60;URL-адреса портала Azure&#62;:<br>Cloud Explorer общего назначения. <br>6. &#60;Конечные точки хранилища ключей&#62;: <br>узлы виртуальной машины Azure Resource Manager.<br>7. &#60;Общедоступный IP-адрес кластера&#62;:<br>удаленная отладка и трассировка ETW Service Fabric. | <br>1.https/19080<br>2. https/443<br>3. https/443<br>4. https/443<br>5. https/443<br>6. https/443<br>7.tcp/dynamic | 1. Пример: test12.eastus.cloudapp.com.<br>2. Позволяет извлекать данные о подписках и ресурсах, а также управлять ресурсами Azure.<br>3. Позволяет извлекать данные о подписках Azure Stack<br>4. Позволяет управлять ресурсами службы хранения (пример: mystorageaccount.blob.core.windows.net).<br>5. Пункт контекстного меню "Открыть на портале" (позволяет открыть элемент ресурса на портале Azure)<br>6.  Позволяет создавать и использовать хранилища ключей для отладки виртуальной машины (пример: myvault.vault.azure.net) <br><br>7. Динамически выделяет блок портов с учетом числа узлов в кластере и доступных портов. <br><br>Блок портов выполняет три попытки получения узлов минимум с 10 портами.<br><br>При трассировке потоковой передачи выполняется попытка получить блок портов, начиная с 810. Если какой-либо из этих блоков портов уже используется, выполняется попытка получить следующий блок и т. д. (Если подсистема балансировки нагрузки пуста, скорее всего, будут использоваться порты, начиная с 810.) <br><br>Точно так же для отладки резервируется четыре блока портов: <br>— connectorPort: 30398, <br>— forwarderPort: 31398, <br>— forwarderPortx86: 31399,<br>— fileUploadPort: 32398<br> |
| Облачные службы | 1. RDP<br><br>2. core.windows.net <br><br>3. management.azure.com<br> management.core.windows.net <br><br>4. &#42;.blob.core.windows.net <br>&#42;.queue.core.windows.net<br>&#42;.table.core.windows.net <br><br>5. portal.azure.com <br><br>6. &#60;пользовательская облачная служба&#62;.cloudapp.net <br> &#60;пользовательская виртуальная машина&#62;.&#60;region&#62;.azure.com | 1. rdp/3389 <br><br> 2. https/443 <br><br> 3. https/443 <br><br> 4. https/443 <br><br> 5. https/443 <br><br>6. tcp. <br>a) 30398 <br>b) 30400 <br>c) 31398 <br>d) 31400 <br>e) 32398 <br>f) 32400 | 1.  Удаленный рабочий стол для виртуальной машины облачных служб <br><br> 2.  Компонент учетной записи хранения для диагностики закрытой конфигурации <br><br> 3.  порталу Azure <br><br> 4. Обозреватель сервера — служба хранилища Azure. &#42; — это имя пользовательской учетной записи хранения  <br><br> 5.  Ссылки для открытия портала. &#47; скачивания сертификата подписки &#47; публикации файла настроек <br><br>6. а) Локальный порт соединителя для удаленной отладки облачной службы и виртуальной машины<br> 6. б) Общий порт соединителя для удаленной отладки облачной службы и виртуальной машины <br> 6. в) Локальный порт сервера пересылки для удаленной отладки облачной службы и виртуальной машины <br> 6. г) Общий порт сервера пересылки для удаленной отладки облачной службы и виртуальной машины  <br> 6. д) Локальный порт средства загрузки файлов для удаленной отладки облачной службы и виртуальной машины <br> 6. е) Общий порт средства загрузки файлов для удаленной отладки облачной службы и виртуальной машины |
| Service Fabric. | 1. <br>docs.Microsoft.com<br>aka.ms <br>go.microsoft.com <br><br>2. <br>vssftools.blob.core.windows.net <br>Vault.azure.com <br>Portal.azure.com <br><br> 3. &#42; vault.azure.net<br><br> 4. <br>app.vsaex.visualstudio.com<br>&#42; .vsspsext.visualstudio.com<br>clouds.vsrm.visualstudio.com <br>clouds.visualstudio.com<br>app.vssps.visualstudio.com <br>&#42; .visualstudio.com | https/443 | 1. Документация <br><br> 2. Функция создания кластера <br><br>3. Символ &#42; обозначает имя хранилища ключей Azure (пример: test11220180112110108.vault.azure.net)  <br><br>  4. Символ &#42; обозначает динамическую конечную точку (пример: vsspsextprodch1su1.vsspsext.visualstudio.com) |
| Снимок <br>Отладчик | 1. go.microsoft.com <br>2. management.azure.com <br> 3. &#42;.azurewebsites.net <br> 4. &#42;.scm.azurewebsites.net<br>5. api.nuget.org/v3/index.json <br>6.  Удаленная служба / IP-адреса серверов / полное доменное имя | 1. https/443 <br>2. https/443  <br>3. http/80 <br>4. https/443 <br>5. https/443 <br>6.  Concord/<br> 4022 (в зависимости от версии Visual Studio) | 1. Запрос JSON-файла для размера SKU службы приложений <br>2. Различные вызовы Azure RM <br>3. Вызов первоначальной загрузки сайта  <br>4. Целевая конечная точка клиента службы консоли Kudu для службы приложений <br>5. Запрос версии расширения сайта, опубликованного на nuget.org <br>6.  [Удаленная отладка](../debugger/remote-debugging.md) |
| Azure Stream Analytics <br><br>HDInsight | Management.azure.com | https/443 | Используется для просмотра, отправки, выполнения и администрирования заданий ASA <br><br> Используется для просмотра кластеров HDI, а также для отправки, диагностики и отладки заданий HDI |
| Azure Data Lake | &#42;.azuredatalakestore.net <br>&#42;.azuredatalakeanalytics.net | https/443 | Используется для компиляции, отправки, просмотра, диагностики и отладки заданий. Также используется для просмотра файлов ADLS, а также отправки и скачивания файлов |
| Служба упаковки | [account].visualstudio.com <br/> [учетная_запись].\*.visualstudio.com <br/> \*.blob.core.windows.net <br/> registry.npmjs.org </br> nodejs.org <br/> dist.nuget.org <br/> nuget.org | https/443 | Файлы \*.npmjs.org, \*.nuget.org и \*.nodejs.org требуются только в некоторых сценариях задач построения (например, для установщиков инструментов NuGet или Node), а также если вы планируете использовать в своих веб-каналах общедоступный восходящий источник. Три других домена являются обязательными для работы с основными функциями службы упаковки. |
| Azure DevOps Services | \*.vsassets.io <br/> static2.sharepointonline.com <br/> dev.azure.com | | Используется для подключения с помощью Azure DevOps Services |
| Служебная шина Azure | \*.servicebus.windows.net. | ampq/5671 и 5672, </br> sbmp/9350-9354, </br> http/80, </br> https/443 | Используется для создания очередей, очередей-распределителей и подписок. </br> Также используется для отправки сообщений в очереди и очереди-распределители служебной шины и получения сообщений оттуда. |
| Azure Cosmos DB | \*.documents.azure.com | https/443 | Используется для вызова основных API-интерфейсов базы данных документов. |
| Сообщество разработчиков | sendvsfeedback2.azurewebsites.net/api | https/443 | Используется для вызова API средства обратной связи сообщества разработчиков (мои вопросы, поиск, голосование, комментарий, отправка, загрузка, возобновление). |
| Intellicode | \*.intellicode.vsengsaas.visualstudio.com | https/443 | Используется для вызова API Intellicode |
| Live Share | \*.liveshare.vsengsaas.visualstudio.com| https/443 | Используется для вызова API Live Share |
| GitHub Codespaces | \*.online.visualstudio.com | https/443 | Используется для вызова интерфейсов API GitHub Codespaces |
| Автоматическое получение типа JavaScript | registry.npmjs.org | https/443 | Используется для установки определений типов TypeScript в целях предоставления IntelliSense для популярных библиотек JavaScript |
| Служба лицензирования подписок Visual Studio | app.vssps.visualstudio.com/apis/<br/>Licensing/ClientRights | https/443 | Лицензирование для активации через Интернет |
| Отладчик | 1. <br>vsdebugger.blob.core.windows.net <br>vsdebugger.azureedge.net <br><br>2. <br>download.visualstudio.com/\*/<br/>onecore.msvsmon.\*.zip<br><br> 3. referencesource.microsoft.com/symbols <br><br> 4. <br>symbols.nuget.org/download/symbols<br><br> 5. visualstudio.com<br><br>6. msdl.microsoft.com/download/symbols | https/443 | 1. <br>Используется для скачивания битов отладчика для отладки .NET Core в Unix/macOS через SSH <br><br>2. <br>Используется для скачивания битов отладчика для удаленной отладки контейнера Windows Docker<br><br> 3. Используется для пошагового выполнения исходного кода .NET Framework <br><br> 4. <br>(Если пользователь соглашается) Используется для скачивания символов, опубликованных на сервере символов nuget.org<br><br> 5. (Если пользователь соглашается) Используется для скачивания символов и двоичных файлов Майкрософт, может также потребоваться для отладки управляемого кода в дампах |
| GitHub Codespaces| \*.online.visualstudio.com | https/443 | Используется для вызова интерфейсов API GitHub Codespaces |
| Публикация приложения Xamarin Android | \*.googleapis.com <br/> play.google.com <br/>accounts.google.com | https/443 | Используется для взаимодействия со службой Google Play Маркет для публикации и отправки приложений Xamarin Android непосредственно из Visual Studio. |
| Служба поиска Visual Studio | data-ai.microsoft.com/search | https/443 | Используется для предоставления службы поиска Visual Studio с поддержкой искусственного интеллекта в поле поиска `Ctrl+Q` |
| Реестр контейнеров Azure | *.azurecr.io | https/443 | Доступ к реестрам контейнеров, размещенным в Azure, для настройки конвейеров CICD |
| | | | |

## <a name="troubleshoot-network-related-errors"></a>Устранение ошибок сети

Иногда вы можете столкнуться с ошибками сети или прокси-сервера, которые возникают при установке или использовании решения Visual Studio, расположенного за брандмауэром или прокси-сервером. Дополнительные сведения об обработке сообщений об ошибках см. а руководстве по [исправлению ошибок сети при установке или использовании Visual Studio](troubleshooting-network-related-errors-in-visual-studio.md).

## <a name="get-support"></a>Техническая поддержка

Доступен [**чат по вопросам установки**](https://visualstudio.microsoft.com/vs/support/#talktous), где можно получить поддержку при проблемах с установкой (только на английском языке).

Ниже приведены несколько дополнительных вариантов:

* Вы можете сообщить о проблемах с продуктом, используя средство [Сообщить о проблеме](../ide/how-to-report-a-problem-with-visual-studio.md). Оно доступно как в Visual Studio Installer, так и в IDE Visual Studio.
* Вы можете предлагать новые функции, просматривать описания проблем и искать решения в [сообществе разработчиков Visual Studio](https://aka.ms/feedback/suggest?space=8).
* Вы также можете связаться с нами и другими разработчиками Visual Studio, используя свою учетную запись [GitHub](https://github.com/) в [обсуждении Visual Studio в сообществе Gitter](https://gitter.im/Microsoft/VisualStudio).

## <a name="see-also"></a>См. также

* [Требования к подключению для Live Share](/visualstudio/liveshare/reference/connectivity/)
* [Создание сетевой установки Visual Studio](create-a-network-installation-of-visual-studio.md)
* [Исправление ошибок сети при установке или использовании Visual Studio](troubleshooting-network-related-errors-in-visual-studio.md)
* [Руководство администратора Visual Studio](visual-studio-administrator-guide.md)
* [Установка в среде, защищенной брандмауэром или прокси-сервером (Visual Studio для Mac)](/visualstudio/mac/install-behind-a-firewall-or-proxy-server)
