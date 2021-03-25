---
title: 'Руководство по Flask в Visual Studio, шаг 5: шаблон проекта опросов'
titleSuffix: ''
description: Пошаговое руководство по основам Flask в контексте проектов Visual Studio с описанием функций шаблонов "Веб-проект опроса Flask" и "Веб-проект опроса Flask/Jade".
ms.date: 01/07/2019
ms.topic: tutorial
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.custom: seodec18
monikerRange: vs-2017
ms.workload:
- python
- data-science
ms.openlocfilehash: fd67e527ccf62de17dc15a5415f573c9622a51e9
ms.sourcegitcommit: f1dff6c4532c43b0444aa12ea57e90bb7dba6fba
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/23/2021
ms.locfileid: "104805982"
---
# <a name="step-5-use-the-polls-flask-web-project-template"></a>Шаг 5. Использование шаблона веб-проекта опроса Flask

**Предыдущий шаг: [Использование полного шаблона веб-проекта Flask](learn-flask-visual-studio-step-04-full-flask-project-template.md)**

Ознакомившись с шаблоном "Веб-проект Flask" Visual Studio, вы можете рассмотреть третий шаблон Flask, "Веб-проект опроса Flask", который создается на базе того же кода.

На этом шаге вы научитесь делать следующее.

> [!div class="checklist"]
> - Создание проекта на основе шаблона и инициализация базы данных (шаг 5.1)
> - Ознакомление с моделями данных (шаг 5.2)
> - Общие сведения о резервных хранилищах данных (шаг 5.3)
> - Общие сведения о представлениях сведений об опросе и результатах опроса (шаг 5.4)

Visual Studio также предоставляет шаблон "Веб-проект опроса Flask/Jade", который выводит идентичное приложение, однако использует расширение Jade для модуля шаблонов Jinja. Дополнительные сведения см. в разделе [Шаг 4. Использование шаблона "Веб-проект Flask/Jade"](learn-flask-visual-studio-step-04-full-flask-project-template.md#the-flaskjade-web-project-template).

## <a name="step-5-1-create-the-project"></a>Шаг 5.1. Создание проекта

1. В Visual Studio перейдите к **обозревателю решений**, щелкните правой кнопкой мыши решение **LearningFlask**, созданное ранее в рамках этого руководства, и выберите **Добавить** > **Новый проект**. (Если же вы хотите использовать новое решение, вместо этого выберите **Файл** > **Создать** > **Проект**.)

1. В диалоговом окне создания проекта найдите и выберите шаблон **Веб-проект опроса Flask**, вызовите проект FlaskPolls и нажмите кнопку **ОК**.

1. Как и другие шаблоны проектов в Visual Studio, шаблон "Веб-проект опроса Flask" содержит файл *requirements.txt*, и Visual Studio запрашивает, куда установить эти зависимости. Выберите параметр **Install into a virtual environment** (Установка в виртуальном окружении) и в диалоговом окне **Добавление виртуального окружения** выберите **Создать**, чтобы принять значения по умолчанию. (Для этого шаблона требуется платформа Flask, а также пакеты azure-storage и pymongo. Для шаблона "Веб-проект опроса Flask/Jade" также требуется пакет pyjade.)

1. Для проекта **FlaskPolls** установите значение по умолчанию для решения Visual Studio, щелкнув правой кнопкой мыши этот проект в **обозревателе решений** и выбрав пункт **Назначить запускаемым проектом**. Запускаемый проект, выделенный полужирным шрифтом, выполняется при запуске отладчика.

1. Выберите **Отладка** > **Начать отладку** (**F5**) или нажмите кнопку **Веб-сервер** на панели инструментов, чтобы запустить сервер:

    ![Кнопка панели инструментов запуска веб-сервера в Visual Studio](media/django/run-web-server-toolbar-button.png)

1. Приложение, созданное с помощью шаблона, содержит три страницы — домашнюю страницу, вкладки "О программе" и "Контактные сведения", перемещаться по которым можно с использованием верхней панели навигации. Выделите пару минут на просмотр различных частей приложения (страницы "О программе" и "Контактные сведения" очень похожи на страницу "Веб-проект Flask" и не будут обсуждаться в дальнейшем).

    ![Вид полного приложения "Веб-проект опроса Flask"](media/flask/step06-full-app-view.png)

1. На домашней странице кнопка **Create Sample Polls** (Создать пример опроса) инициализирует хранилище данных приложения с тремя разными опросами, как описано на странице *models/samples.json*. По умолчанию приложение использует базу данных в памяти (как показано на странице "О программе"), которая сбрасывается при каждом перезапуске приложения. Приложение также содержит код для работы со службой хранилища Azure и MongoDB, как описано далее в этой статье.

1. После инициализации хранилищ данных вы можете голосовать в разных опросах, как показано на домашней странице (панель навигации и нижний колонтитул не показаны для удобства):

    ![Вид приложения опроса после инициализации хранилища данных](media/flask/step06-polls-initialized.png)

1. При выборе опроса отображаются его конкретные варианты:

    ![Интерфейс голосования для опроса](media/flask/step06-polls-voting-interface.png)

1. Как только вы проголосуете, приложение выведет страницу результатов и позволит вам проголосовать еще раз:

    ![Представление результатов после голосования](media/flask/step06-polls-results.png)

1. Вы можете оставить приложение запущенным и пройти следующие разделы.

    Чтобы остановить работу приложения и [зафиксировать изменения в системе управления исходным кодом](learn-flask-visual-studio-step-02-create-app.md#commit-to-source-control), сначала откройте страницу **Изменения** в **Team Explorer**, щелкните правой кнопкой мыши папку виртуального окружения (возможно, **env**) и выберите **Игнорировать эти локальные элементы**.

### <a name="examine-the-project-contents"></a>Анализ содержимого проекта

Как было отмечено ранее, с большей частью содержимого проекта, созданного на основе шаблона "Веб-проект опроса Flask" (и шаблона "Веб-проект опроса Flask/Jade"), вы должны быть знакомы, если изучили другие шаблоны проектов Visual Studio. В дополнительных шагах этой статьи приведены более значительные изменения и дополнения, а именно модели данных и дополнительные представления.

## <a name="step-5-2-understand-the-data-models"></a>Шаг 5.2. Ознакомление с моделями данных

Модели данных для приложения — это классы Python с именами Poll и Choice, которые определены в *models/\_\_init\_\_.py*. Класс Poll представляет вопрос, для которого коллекция экземпляров Choice представляет доступные ответы. Кроме того, Poll поддерживает общее число голосов (для любого варианта) и метод для вычисления статистических данных, которые используются для создания представлений:

```python
class Poll(object):
    """A poll object for use in the application views and repository."""
    def __init__(self, key=u'', text=u''):
        """Initializes the poll."""
        self.key = key
        self.text = text
        self.choices = []
        self.total_votes = None

    def calculate_stats(self):
        """Calculates some statistics for use in the application views."""
        total = 0
        for choice in self.choices:
            total += choice.votes
        for choice in self.choices:
            choice.votes_percentage = choice.votes / float(total) * 100 \
                if total > 0 else 0
        self.total_votes = total

class Choice(object):
    """A poll choice object for use in the application views and repository."""
    def __init__(self, key=u'', text=u'', votes=0):
        """Initializes the poll choice."""
        self.key = key
        self.text = text
        self.votes = votes
        self.votes_percentage = None
```

Эти модели данных представляют собой универсальные абстракции, позволяющие представлениям приложения работать с разными типами резервных хранилищ данных, которые описаны в следующем шаге.

## <a name="step-5-3-understand-the-backing-data-stores"></a>Шаг 5.3. Общие сведения о резервных хранилищах данных

Приложение, созданное с помощью шаблона "Веб-проект опроса Flask", может работать с хранилищем данных в памяти, в хранилище таблиц Azure или базе данных MongoDB.

Механизм хранения данных реализуется следующим образом.

1. Тип репозитория указывается с помощью переменной среды `REPOSITORY_NAME`, для которой можно задать значение memory, azuretablestore или mongodb. Фрагмент кода в *settings.py* извлекает имя, используя значение memory по умолчанию. Если вы хотите изменить резервное хранилище, необходимо задать переменную среды и перезапустить приложение.

    ```python
    from os import environ
    REPOSITORY_NAME = environ.get('REPOSITORY_NAME', 'memory')
    ```

1. Затем код *settings.py* инициализирует объект `REPOSITORY_SETTINGS`. Чтобы использовать хранилище таблиц Azure или MongoDB, необходимо сначала инициализировать эти хранилища данных в другом месте, а затем задать необходимые переменные среды, указывающие приложению, как подключаться к хранилищу:

    ```python
    if REPOSITORY_NAME == 'azuretablestorage':
        REPOSITORY_SETTINGS = {
            'STORAGE_NAME': environ.get('STORAGE_NAME', ''),
            'STORAGE_KEY': environ.get('STORAGE_KEY', ''),
            'STORAGE_TABLE_POLL': environ.get('STORAGE_TABLE_POLL', 'polls'),
            'STORAGE_TABLE_CHOICE': environ.get('STORAGE_TABLE_CHOICE', 'choices'),
        }
    elif REPOSITORY_NAME == 'mongodb':
        REPOSITORY_SETTINGS = {
            'MONGODB_HOST': environ.get('MONGODB_HOST', None),
            'MONGODB_DATABASE': environ.get('MONGODB_DATABASE', 'polls'),
            'MONGODB_COLLECTION': environ.get('MONGODB_COLLECTION', 'polls'),
        }
    elif REPOSITORY_NAME == 'memory':
        REPOSITORY_SETTINGS = {}
    else:
        raise ValueError('Unknown repository.')
    ```

1. В файле *views.py* приложение вызывает фабричный метод для инициализации объекта `Repository`, используя имя и параметры хранилища данных:

    ```python
    from FlaskPolls.models import PollNotFound
    from FlaskPolls.models.factory import create_repository
    from FlaskPolls.settings import REPOSITORY_NAME, REPOSITORY_SETTINGS

    repository = create_repository(REPOSITORY_NAME, REPOSITORY_SETTINGS)
    ```

1. Метод `factory.create_repository` находится в файле *models\factory.py*, который просто импортирует соответствующий модуль репозитория, а затем создает экземпляр `Repository`:

    ```python
    def create_repository(name, settings):
        """Creates a repository from its name and settings. The settings
        is a dictionary where the keys are different for every type of repository.
        See each repository for details on the required settings."""
        if name == 'azuretablestorage':
            from .azuretablestorage import Repository
        elif name == 'mongodb':
            from .mongodb import Repository
        elif name == 'memory':
            from .memory import Repository
        else:
            raise ValueError('Unknown repository.')

        return Repository(settings)
    ```

1. Реализации класса `Repository`, предназначенные для каждого хранилища данных, можно найти в *models\azuretablestorage.py*, *models\mongodb.py* и *models\memory.py*. Реализация хранилища Azure использует пакет azure-storage; реализация MongoDB использует пакет pymongo. Как указано в шаге 5–1, оба пакета входят в файл *requirements.txt* шаблона проекта. Ознакомление с этими сведениями мы предлагаем выполнить как самостоятельное упражнение.

Иными словами, класс `Repository` абстрагирует конкретные сведения о хранилище данных, а приложение использует переменные среды во время выполнения для выбора и настройки одной из трех реализаций.

Ниже приведена процедура добавления поддержки другого хранилища данных, помимо трех хранилищ, предоставляемых шаблоном проекта.

1. Скопируйте *memory.py* в новый файл, чтобы получить базовый интерфейс для класса `Repository`.
1. Измените реализацию класса в соответствии с выбранным хранилищем данных.
1. Измените *factory.py* для добавления нового варианта `elif`, который распознает имя добавленного хранилища данных и импортирует соответствующий модуль.
1. Измените файл *settings.py* для распознавания другого имени в переменной среды `REPOSITORY_NAME` и инициализируйте `REPOSITORY_SETTINGS` соответствующим образом.

### <a name="seed-the-data-store-from-samplesjson"></a>Заполнение хранилища данных значениями из samples.json

Изначально любое выбранное хранилище данных не содержит опросы, поэтому на домашней странице приложения отображается сообщение **No polls available** (Нет доступных опросов) вместе с кнопкой **Create Sample Polls** (Создать пример опроса). Тем не менее после нажатия кнопки представление изменяется для отображения доступных опросов. Это переключение происходит благодаря условным тегам в *templates\index.html* (некоторые пустые строки опущены для удобства):

```html
{% extends "layout.html" %}
{% block content %}
<h2>{{title}}.</h2>

{% if polls %}
<table class="table table-hover">
    <tbody>
        {% for poll in polls %}
        <tr>
            <td>
                <a href="/poll/{{poll.key}}">{{poll.text}}</a>
            </td>
        </tr>
        {% endfor %}
    </tbody>
</table>
{% else %}
<p>No polls available.</p>
<br />
<form action="/seed" method="post">
    <button class="btn btn-primary" type="submit">Create Sample Polls</button>
</form>
{% endif %}
{% endblock %}
```

Переменная `polls` в шаблоне получена при вызове `repository.get_polls`, который возвращает значение nothing до завершения инициализации хранилища данных.

При нажатии кнопки **Создать пример опроса** выполняется переход к URL-адресу /seed. Обработчик для этого маршрута определен в *views.py*:

```python
@app.route('/seed', methods=['POST'])
def seed():
    """Seeds the database with sample polls."""
    repository.add_sample_polls()
    return redirect('/')
```

Вызов `repository.add_sample_polls()` завершается в одной из конкретных реализаций `Repository` для выбранного хранилища данных. Каждая реализация вызывает метод `_load_samples_json` (в *models\_\_init\_\_.py*) для загрузки файла *models\samples.json* в память, а затем выполняет итерацию по данным для создания необходимых объектов `Poll` и `Choice` в хранилище данных.

После завершения этого процесса инструкция `redirect('/')` в методе `seed` возвращается на домашнюю страницу. Так как `repository.get_polls` теперь возвращает объект данных, условные теги в *templates\index.html* отображают таблицу, содержащую опросы.

### <a name="question-how-does-one-add-new-polls-to-the-app"></a>Вопрос. Как добавить новый опрос в приложение?

Ответ. Приложение, предоставленное с помощью этого шаблона проекта, не поддерживает добавление или редактирование опросов. Для создания новых данных инициализации можно изменить *models\samples.json*, однако это приведет к сбросу хранилища данных. Чтобы реализовать возможности редактирования, необходимо расширить интерфейс класса `Repository` с помощью методов для создания необходимых экземпляров `Choice` и `Poll`, а затем на дополнительных страницах реализовать пользовательский интерфейс, использующий эти методы.

## <a name="step-5-4-understand-the-poll-detail-and-results-views"></a>Шаг 5.4. Общие сведения о представлениях сведений об опросе и результатах опроса

Большинство представлений, созданных с использованием шаблона "Веб-проект опроса Flask" и "Веб-проект опроса Flask/Jade", такие как представления для страниц "О программе" и "Контактные сведения", похожи на представления, созданные с использованием шаблона "Веб-проект Flask" (или "Веб-проект Flask/Jade"), с которым вы работали ранее в этом руководстве. В предыдущем разделе вы также узнали, как реализуется домашняя страница для отображения кнопки инициализации или списка опросов.

Нам остается только рассмотреть представления голосования (сведений) и результатов отдельного опроса.

При выборе опроса на домашней странице приложение переходит к URL-адресу /poll/\<key\>, где *key* — это уникальный идентификатор опроса. В файле *views.py* можно видеть, что функция `details` назначается для обработки маршрутизации URL-адресов для метода GET и запросов. Кроме того, мы видим, что использование `<key>` в маршруте URL-адреса определяет сопоставление любого подобного маршрута с той же функцией и приводит к формированию аргумента в функции с тем же именем:

```python
@app.route('/poll/<key>', methods=['GET', 'POST'])
def details(key):
    """Renders the poll details page."""
    error_message = ''
    if request.method == 'POST':
        try:
            choice_key = request.form['choice']
            repository.increment_vote(key, choice_key)
            return redirect('/results/{0}'.format(key))
        except KeyError:
            error_message = 'Please make a selection.'

    return render_template(
        'details.html',
        title='Poll',
        year=datetime.now().year,
        poll=repository.get_poll(key),
        error_message=error_message,
    )
```

Чтобы отобразить опрос (запросы GET), эта функция просто вызывает *templates\details.html*, который выполняет итерацию по массиву `choices` опроса, создавая переключатель для каждого элемента.

```html
{% extends "layout.html" %}

{% block content %}

<h2>{{poll.text}}</h2>
<br />

{% if error_message %}
<p class="text-danger">{{error_message}}</p>
{% endif %}

<form action="/poll/{{poll.key}}" method="post">
    {% for choice in poll.choices %}
    <div class="radio">
        <label>
            <input type="radio" name="choice" id="choice{{choice.key}}" value="{{choice.key}}" />
            {{ choice.text }}
        </label>
    </div>
    {% endfor %}
    <br />
    <button class="btn btn-primary" type="submit">Vote</button>
</form>

{% endblock %}
```

Поскольку кнопка **Vote** (Голосовать) имеет `type="submit"`, при ее нажатии создается запрос POST к тому же URL-адресу, который снова направляется к функции `details`. На этот раз, тем не менее, она извлекает вариант из данных формы и перенаправляет его в /results/\<choice\>.

Затем URL-адрес /results/\<key\> направляется в функцию `results` во *views.py*, которая вызывает метод `calculate_stats` опроса, а также использует *templates\results.html* для подготовки к просмотру:

```python
@app.route('/results/<key>')
def results(key):
    """Renders the results page."""
    poll = repository.get_poll(key)
    poll.calculate_stats()
    return render_template(
        'results.html',
        title='Results',
        year=datetime.now().year,
        poll=poll,
    )
```

Шаблон *results.html*, в свою очередь, просто перебирает варианты выбора опроса и формирует индикатор хода выполнения для каждого:

```html
{% extends "layout.html" %}

{% block content %}

<h2>{{poll.text}}</h2>
<br />

{% for choice in poll.choices %}
<div class="row">
    <div class="col-sm-5">{{choice.text}}</div>
    <div class="col-sm-5">
        <div class="progress">
            <div class="progress-bar" role="progressbar" aria-valuenow="{{choice.votes}}" aria-valuemin="0" aria-valuemax="{{poll.total_votes}}" style="width: {{choice.votes_percentage}}%;">
                {{choice.votes}}
            </div>
        </div>
    </div>
</div>
{% endfor %}

<br />
<a class="btn btn-primary" href="/poll/{{poll.key}}">Vote again?</a>

{% endblock %}
```

## <a name="next-steps"></a>Дальнейшие действия

> [!Note]
> Если вы зафиксировали свое решение Visual Studio с системой управления исходным кодом в ходе работы с этим руководством, настало время сделать другую фиксацию. Ваше решение должно соответствовать исходному коду руководства на сайте GitHub: [Microsoft/python-sample-vs-learning-flask](https://github.com/Microsoft/python-sample-vs-learning-flask).

Вы узнали все о шаблонах "Пустой веб-проект Flask", "Веб-проект Flask[/Jade]" и "Веб-проект опроса Flask[/Jade]" в Visual Studio. Вы получили представление об основах Flask, таких как использование представлений, шаблонов и маршрутизации, и узнали, как использовать резервные хранилища данных. Теперь вы можете приступить к созданию собственного веб-приложения с любыми необходимыми представлениями и моделями.

Запуск веб-приложения на компьютере разработчика — это лишь один шаг, чтобы сделать приложение доступным для клиентов. Следующие шаги могут включать приведенные ниже задачи:

- Развертывание веб-приложения на рабочий сервер, например в службу приложений Azure. См. статью [Публикация в "Службе приложений Azure"](publishing-python-web-applications-to-azure-from-visual-studio.md).

- Добавьте реализацию репозитория, использующую другое хранилище данных промышленного уровня, например PostgreSQL, MySQL и SQL Server (все они могут размещаться на платформе Azure). Вы можете также использовать [пакет SDK Azure для Python](/azure/python/), чтобы работать со службами хранилища Azure, такими как таблицы и большие двоичные объекты, а также с Cosmos DB.

- Настройте конвейер непрерывной интеграции или непрерывного развертывания в таких службах, как Azure DevOps. В дополнение к работе с системой управления исходным кодом (в Azure Repos, GitHub или в другом месте), можно настроить проект Azure DevOps для автоматического выполнения модульных тестов в качестве необходимого условия для выпуска, а также настроить конвейер для развертывания на промежуточный сервер для дополнительных тестов перед развертыванием в рабочей среде. Кроме того, Azure DevOps интегрируется с решениями мониторинга, такими как App Insights, и закрывает весь цикл гибкими средствами планирования. Дополнительные сведения см. в статье [Создание конвейера CI/CD для Python с помощью Azure DevOps Projects](/azure/devops-project/azure-devops-project-python?view=vsts&preserve-view=true) и в общей [документации по Azure DevOps](/azure/devops/?view=vsts&preserve-view=true).
