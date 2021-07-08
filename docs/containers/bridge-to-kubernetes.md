---
title: Учебник. Подключение компьютеров разработки к Bridge to Kubernetes
ms.technology: vs-azure
ms.date: 03/24/2021
ms.topic: tutorial
description: Узнайте, как использовать функцию Bridge to Kubernetes в Visual Studio для подключения компьютера разработчика к кластеру Kubernetes.
keywords: Bridge to Kubernetes, Azure Dev Spaces, Dev Spaces, Docker, Kubernetes, Azure, контейнеры
monikerRange: '>=vs-2019'
ms.author: ghogen
author: ghogen
manager: jmartens
ms.openlocfilehash: b8d6c98d2e2146ad57871b74cd2d522ed2b04259
ms.sourcegitcommit: 0499d813d5c24052c970ca15373d556a69507250
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/29/2021
ms.locfileid: "113046122"
---
# <a name="tutorial-use-bridge-to-kubernetes-to-connect-your-clusters-and-your-development-computers"></a>Учебник. Использование Bridge to Kubernetes для подключения кластеров к компьютерам разработки

В этом учебнике вы узнаете, как использовать функцию Bridge to Kubernetes для перенаправления трафика между кластером Kubernetes и кодом, выполняемом на компьютере разработки. 

В нем также приводится скрипт для развертывания большого примера приложения с несколькими микрослужбами в кластере Kubernetes.

Дополнительные сведения о Bridge to Kubernetes см. в статье [как работает Bridge to Kubernetes](overview-bridge-to-kubernetes.md).

## <a name="prerequisites"></a>Предварительные требования

- Кластер Kubernetes.
- [Visual Studio 2019][visual-studio] версии 16.7 (предварительная версия 4) или более поздней версии в Windows 10.
- [Установленное расширение Bridge to Kubernetes][btk-extension].

## <a name="about-the-data"></a>О данных

Этот учебник использует Bridge to Kubernetes для разработки версии микрослужбы простого приложения TODO в любом кластере Kubernetes. Этот [образец приложения TODO App][todo-app-github] с использованием Visual Studio был адаптирован из кода, предоставленного [TodoMVC](http://todomvc.com). 

 Эти шаги должны быть применимы к любому кластеру Kubernetes. Так что если у вас уже есть свое приложение в кластере Kubernetes, вы можете выполнить описанные ниже инструкции, используя имена собственных служб.

Пример приложения TODO состоит из внешнего интерфейса и серверной части, обеспечивающей постоянное хранилище. В этом расширенном примере добавлен компонент статистики и приложение разбито на несколько микрослужб, а именно:

- внешний интерфейс вызывает database-api для сохранения и обновления элементов TODO;
- служба database-api использует базу данных Mongo для сохранения элементов TODO;
- внешний интерфейс записывает события добавления, завершения и удаления в очередь RabbitMQ;
- рабочая роль статистики получает события из очереди RabbitMQ и обновляет кэш Redis;
- API-интерфейс статистики предоставляет кэшированную статистику для отображения во внешнем интерфейсе.

В целом это расширенное приложение TODO состоит из шести взаимосвязанных компонентов.


## <a name="check-the-cluster"></a>Проверка кластера

Откройте командную строку и убедитесь, что средство `kubectl` установлено в пути, кластер, который вы хотите использовать, доступен и готов, и задайте контекст для этого кластера.

```cmd
kubectl cluster-info
kubectl config use-context {context-name}
```

где {context-name} — это имя контекста для кластера, который вы хотите использовать для примера todo-app.

## <a name="deploy-the-application"></a>Развертывание приложения

Клонируйте [репозиторий mindaro](https://github.com/Microsoft/mindaro) и откройте командное окно с текущей рабочей папкой в *samples/todo-app*.

Создайте пространство имен для примера.

```cmd
kubectl create namespace todo-app
```

Затем примените манифест развертывания:

```cmd
kubectl apply -n todo-app -f deployment.yaml
```

Это простое развертывание, которое предоставляет внешний интерфейс с помощью службы типа `LoadBalancer`. Подождите, пока все модули pod будут запущены и внешний IP-адрес службы `frontend` станет доступным.

Если вы выполняете тестирование с помощью MiniKube, для разрешения внешнего IP-адреса вам нужно будет использовать `minikube tunnel`. Если вы используете AKS или другой облачный поставщик Kubernetes, внешний IP-адрес назначается автоматически. Используйте приведенную ниже команду, чтобы отследить службу `frontend` и дождаться, пока она запустится.

```output
kubectl get service -n todo-app frontend --watch

NAME       TYPE           CLUSTER-IP    EXTERNAL-IP     PORT(S)        AGE
frontend   LoadBalancer   10.0.245.78   20.73.226.228   80:31910/TCP   6m26s
```

Перейдите к приложению, используя внешний IP-адрес и локальный порт (первое число в столбце PORT(S)).

```
http://{external-ip}:{local-port}
```

Протестируйте запущенное приложение в браузере. Обратите внимание, что по мере добавления, завершения и удаления элементов TODO на странице статистики появляются ожидаемые метрики.

## <a name="connect-to-your-cluster-and-debug-a-service"></a>Подключение к кластеру и отладка службы

Откройте *samples\todo-app\database-api\database-api.csproj* в Visual Studio. В проекте в раскрывающемся списке параметров запуска выберите **Bridge to Kubernetes**, как показано ниже.

![Выбор параметра Bridge to Kubernetes](media/bridge-to-kubernetes/choose-bridge-to-kubernetes.png)

Нажмите кнопку запуска рядом с пунктом *Bridge to Kubernetes*. В диалоговом окне **Создание профиля для Bridge to Kubernetes** выполните указанные ниже действия.

- Выберите имя кластера.
- Выберите *todo-app* для вашего пространства имен.
- Выберите *database-api* для службы, которую необходимо перенаправить.
- Выберите тот же URL-адрес, который вы использовали ранее для запуска браузера, http://{external-ip}:{local-port}.

![Выбор кластера Bridge to Kubernetes](media/bridge-to-kubernetes/configure-bridge-debugging.png)

Выберите, следует ли использовать изолированный режим, в котором ваши изменения не будут влиять на других пользователей, использующих кластер. Режим изоляции реализуется путем маршрутизации ваших запросов к вашей копии каждой затронутой службы. При этом остальной трафик маршрутизируется в обычном режиме. Дополнительные сведения об этом см. в статье [Как работает Bridge to Kubernetes][btk-overview-routing].

Нажмите кнопку **ОК**. Весь трафик в кластере Kubernetes перенаправляется для службы *database-api* в версию вашего приложения, запущенного на компьютере разработки. Функция Bridge to Kubernetes также направляет весь исходящий трафик из приложения обратно в кластер Kubernetes.

> [!NOTE]
> Вам будет предложено предоставить *EndpointManager* повышенные привилегии для изменения файла hosts.

Когда в строке состояния указывается, что установлено подключение к службе `database-api`, это означает, что компьютер разработки подключен.

![Компьютер разработки подключен](media/bridge-to-kubernetes/development-computer-connected.png)

> [!NOTE]
> В дальнейшем при запуске диалоговое окно **Создание профиля для Bridge to Kubernetes** выводиться не будет. Параметры можно изменить в области **Отладка** в свойствах проекта.

После подключения компьютера разработки трафик заменяемой службы начинает перенаправляться на него.

> [!NOTE]
> Чтобы изменить профиль отладки позже, например, если вам потребуется протестировать его с другой службой Kubernetes, выберите **Отладка** > **Debug Properties** (Свойства отладки) и нажмите кнопку **Изменить**.

## <a name="set-a-break-point"></a>Установка точки останова

Откройте MongoHelper.cs и щелкните где-нибудь в строке 68 метода CreateTask, чтобы поместить туда курсор. Задайте точку останова, нажав клавишу *F9* или выбрав пункт меню **Отладка** > **Переключить точку останова**.

Перейдите к примеру приложения, открыв общедоступный URL-адрес (внешний IP-адрес службы интерфейса). Чтобы возобновить работу службы, нажмите клавишу **F5** или выберите пункт меню **Отладка** > **Продолжить**.

Удалите точку останова, поместив курсор на строку с точкой останова и нажав клавишу **F9**.

> [!NOTE]
> По умолчанию при остановке задачи отладки компьютер разработки отключается от кластера Kubernetes. Это поведение можно изменить, изменив значение параметра **Отключиться после отладки** на `false` в разделе **Средства отладки Kubernetes** диалогового окна **Инструменты** > **Параметры**. После изменения этого параметра компьютер разработки будет оставаться подключенным при остановке и запуске отладки. Чтобы отключить компьютер разработки от кластера, нажмите кнопку **Отключиться** на панели инструментов.
>
>![Снимок экрана: параметры отладки Kubernetes](media/bridge-to-kubernetes/kubernetes-debugging-options.png)

## <a name="additional-configuration"></a>Дополнительная настройка

Bridge to Kubernetes может обрабатывать трафик маршрутизации и выполнять репликацию переменных среды без дополнительной настройки. Если необходимо скачать файлы, подключенные к контейнеру в кластере Kubernetes, например файл ConfigMap, можно создать `KubernetesLocalProcessConfig.yaml` для скачивания этих файлов на компьютер разработки. Дополнительные сведения см. в статье об [использовании KubernetesLocalProcessConfig.yaml для дополнительной настройки Bridge to Kubernetes][kubernetesLocalProcessConfig-yaml].

## <a name="using-logging-and-diagnostics"></a>Использование ведения журналов и диагностики

Журналы диагностики находятся в подкаталоге `Bridge to Kubernetes` в каталоге *TEMP* на компьютере разработки.

## <a name="next-steps"></a>Следующие шаги

Узнайте, как работает Bridge to Kubernetes.

> [!div class="nextstepaction"]
> [Как работает Bridge to Kubernetes](overview-bridge-to-kubernetes.md)

[todo-app-github]: https://github.com/Microsoft/mindaro
[supported-regions]: https://azure.microsoft.com/global-infrastructure/services/?products=kubernetes-service
[troubleshooting]: /azure/dev-spaces/troubleshooting#fail-to-restore-original-configuration-of-deployment-on-cluster
[visual-studio]: https://www.visualstudio.com/vs/
[btk-extension]: https://marketplace.visualstudio.com/items?itemName=ms-azuretools.mindaro
[kubernetesLocalProcessConfig-yaml]: configure-bridge-to-kubernetes.md
[btk-overview-routing]: overview-bridge-to-kubernetes.md#using-routing-capabilities-for-developing-in-isolation
