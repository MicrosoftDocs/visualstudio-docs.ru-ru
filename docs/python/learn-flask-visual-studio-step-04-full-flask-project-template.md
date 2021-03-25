---
title: 'Руководство по Flask в Visual Studio, шаг 4: шаблоны веб-проекта'
titleSuffix: ''
description: Пошаговое руководство по основам Flask в контексте проектов Visual Studio с описанием функций, предоставляемых в шаблонах веб-проекта Flask и веб-проекта Flask/Jade.
ms.date: 01/07/2019
ms.topic: tutorial
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 7926a7983e43545ad47e8bc975f051821c108c18
ms.sourcegitcommit: f1dff6c4532c43b0444aa12ea57e90bb7dba6fba
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/23/2021
ms.locfileid: "104806008"
---
# <a name="step-4-use-the-full-flask-web-project-template"></a>Шаг 4. Использование полного шаблона веб-проекта Flask

**Предыдущий шаг: [Обработка статических файлов, добавление страниц и использование наследования шаблонов](learn-flask-visual-studio-step-03-serve-static-files-add-pages.md)**

Теперь, когда вы ознакомились с основами Flask, создав в Visual Studio приложение на основе шаблона для пустого проекта приложения Flask, вам будет легче создать более полное приложение с помощью шаблона "Веб-проект Flask".

На этом этапе вы сделаете следующее:

> [!div class="checklist"]
> - создадите более полное веб-приложение Flask с помощью шаблона "Веб-проект Flask" и изучите структуру проекта (шаг 4.1);
> - узнаете, какие представления и шаблоны страниц создаются при использовании шаблона проекта, в котором содержится три страницы, наследованные от шаблона базовой страницы, и используются статические библиотеки JavaScript, такие как jQuery и Bootstrap (ша 4.2);
> - узнаете, как реализуется маршрутизация URL-адресов, предоставляемая шаблоном (шаг 4.3).

Эта статья также относится к шаблону "Веб-проект Flask/Jade", который создает приложение, идентичное приложению "Веб-проект Flask", с помощью модуля шаблонов Jade вместо Jinja. Дополнительные сведения представлены в конце этой статьи.

## <a name="step-4-1-create-a-project-from-the-template"></a>Шаг 4.1. Создание проекта на основе шаблона

1. В Visual Studio перейдите к **обозревателю решений**, щелкните правой кнопкой мыши решение **LearningFlask**, созданное ранее в рамках этого руководства, и выберите **Добавить** > **Новый проект**. (Если же вы хотите использовать новое решение, вместо этого выберите **Файл** > **Создать** > **Проект**.)

1. В диалоговом окне создания проекта найдите и выберите шаблон **Веб-проект Flask**, присвойте проекту имя FlaskWeb и нажмите кнопку **ОК**.

1. Так как шаблон также включает файл *requirements.txt*, в Visual Studio запрашивается расположение для установки этих зависимостей. Выберите параметр **Install into a virtual environment** (Установка в виртуальном окружении) и в диалоговом окне **Добавление виртуального окружения** выберите **Создать**, чтобы принять значения по умолчанию.

1. Когда Visual Studio завершит настройку виртуального окружения, назначьте проект **FlaskWeb** в качестве проекта по умолчанию для решения Visual Studio. Для этого в **обозревателе решений** щелкните правой кнопкой мыши имя проекта и выберите пункт **Назначить запускаемым проектом**. Запускаемый проект, выделенный полужирным шрифтом, выполняется при запуске отладчика.

    ![Обозреватель решений с выбранным в качестве запускаемого проектом FlaskWeb](media/flask/step04-second-project-in-solution-set-as-startup-project.png)

1. Выберите **Отладка** > **Начать отладку** (**F5**) или нажмите кнопку **Веб-сервер** на панели инструментов, чтобы запустить сервер:

    ![Кнопка панели инструментов запуска веб-сервера в Visual Studio](media/flask/run-web-server-toolbar-button.png)

1. Приложение, созданное с помощью шаблона, содержит три страницы — домашнюю страницу, а также страницы со сведениями и контактными данными. Вы можете перемещаться между ними, используя панель навигации. Выделите пару минут, чтобы просмотреть части приложения. Чтобы пройти аутентификацию в приложении с помощью команды **Вход**, используйте учетные данные суперпользователя, созданные ранее.

    ![Полное представление приложения веб-проекта Flask в браузере](media/flask/step04-full-app-desktop-view.png)

1. Приложение, созданное с помощью шаблона "Веб-проект Flask", использует созданный на основе начальной загрузки адаптивный макет, учитывающий форм-факторы мобильных устройств. Чтобы увидеть, как работает адаптивность, уменьшите размер окна браузера так, чтобы содержимое отображалось по вертикали, а панель навигации была в виде значка меню.

    ![Мобильное (уменьшенное) представление приложения веб-проекта Flask](media/flask/step04-full-app-mobile-view.png)

1. Вы можете оставить приложение запущенным и пройти следующие разделы.

    Чтобы остановить работу приложения и [зафиксировать изменения в системе управления исходным кодом](learn-flask-visual-studio-step-02-create-app.md#commit-to-source-control), сначала откройте страницу **Изменения** в **Team Explorer**, щелкните правой кнопкой мыши папку виртуального окружения (возможно, **env**) и выберите **Игнорировать эти локальные элементы**.

### <a name="examine-what-the-template-creates"></a>Просмотр элементов, созданных с помощью шаблона

Шаблон "Веб-проект Flask" создает структуру, показанную ниже. Содержимое очень похоже на то, которое мы создали на предыдущих шагах. Различие заключается в том, что шаблон "Веб-проект Flask" содержит больше структур в папке *static*, так как он включает jQuery и начальную загрузку, обеспечивая адаптивность. Шаблон также добавляет страницу контактных данных. В целом, если вы выполнили предыдущую процедуру в этом учебнике, все компоненты шаблона должны быть вам знакомы.

- Файлы в корневом каталоге проекта:
  - *runserver.py* — скрипт для запуска приложения на сервере разработки;
  - *requirements.txt* — файл, который содержит зависимость от Flask 0.x.
- Папка *FlaskWeb* содержит все файлы приложения:
  - *\_\_init.py\_\_* помечает код приложения как модуль Python, создает объект Flask и импортирует представления приложения.
  - *views.py* содержит код для отображения страниц.
  - Папка *static* содержит вложенные папки с именами *content* (CSS-файлы), *fonts* (файлы шрифтов) и *scripts* (файлы JavaScript).
  - Папка *templates* содержит базовый шаблон *layout.html* вместе с *about.html*, *contact.html* и *index.html* для отдельных страниц, каждая из которых расширяет *layout.html*.

### <a name="question-is-it-possible-to-share-a-virtual-environment-between-visual-studio-projects"></a>Вопрос. Можно ли предоставлять проектам Visual Studio общий доступ к виртуальному окружению?

Ответ. Да, но при этом учитывайте, что, вероятно, со временем для разных проектов будут использоваться разные пакеты. Таким образом, в общем виртуальном окружении будут содержаться все пакеты для всех проектов, в которых используется окружение.

Чтобы все равно использовать существующее виртуальное окружение, сделайте следующее:

1. Когда в Visual Studio будет предложено установить зависимости, выберите вариант **Я установлю их самостоятельно**.
1. В **обозревателе решений** щелкните правой кнопкой мыши узел **Окружения Python** и выберите **Добавить существующее виртуальное окружение**.
1. Перейдите к папке виртуального окружения и выберите ее. Затем нажмите кнопку **ОК**.

## <a name="step-4-2-understand-the-views-and-page-templates-created-by-the-project-template"></a>Шаг 4.2. Сведения о представлениях и шаблонах страниц, созданных с использованием шаблона проекта

При запуске проекта вы увидите, что приложение содержит три представления: домашняя страница, а также страницы со сведениями и контактными данными. Код этих представлений хранится в папке *FlaskWeb/views.py*. Каждая функция представления просто вызывает `flask.render_template` с путем к шаблону и переменный список аргументов для значений, присваиваемых шаблону. Например, страница "О программе" обрабатывается функцией `about` (декоратор которой обеспечивает маршрутизацию URL-адресов):

```python
@app.route('/about')
def about():
    """Renders the about page."""
    return render_template(
        'about.html',
        title='About',
        year=datetime.now().year,
        message='Your application description page.'
    )
```

Функции `home` и `contact` практически идентичны, имеют аналогичные декораторы и немного разные аргументы.

Шаблоны расположены в папке *templates* приложения. Файл базового шаблона (*layout.html*) является самым большим. В нем содержатся ссылки на все необходимые статические файлы (JavaScript и CSS), определяется блок content, переопределяемый другими страницами, и предоставляется еще один блок с именем scripts. Эти области показаны в следующем фрагменте файла *layout.html*:

```html
<!DOCTYPE html>
<html>
<head>
    <meta charset="utf-8" />

    <!-- Define a viewport for Bootstrap's responsive rendering -->
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>{{ title }} - My Flask Application</title>

    <link rel="stylesheet" type="text/css" href="/static/content/bootstrap.min.css" />
    <link rel="stylesheet" type="text/css" href="/static/content/site.css" />
    <script src="/static/scripts/modernizr-2.6.2.js"></script>
</head>

<body>
    <!-- Navbar omitted -->

    <div class="container body-content">
        <!-- "content" block that pages are expected to override -->
        {% block content %}{% endblock %}
        <hr />
        <footer>
            <p>&copy; {{ year }} - My Flask Application</p>
        </footer>
    </div>

    <!-- Additional scripts; use the "scripts" block to add page-specific scripts.  -->
    <script src="/static/scripts/jquery-1.10.2.js"></script>
    <script src="/static/scripts/bootstrap.js"></script>
    <script src="/static/scripts/respond.js"></script>
    {% block scripts %}{% endblock %}

</body>
</html>
```

Каждый шаблон отдельной страницы (*about.html*, *contact.html* и *index.html*) дополняет основной шаблон *layout.html*. *about.html* — это самый простой шаблон, в котором отображаются теги `{% extends %}` и `{% block content %}`.

```html
{% extends "app/layout.html" %}

{% block content %}

<h2>{{ title }}.</h2>
<h3>{{ message }}</h3>

<p>Use this area to provide additional information.</p>

{% endblock %}
```

Шаблоны *index.html* и *contact.html* имеют такую же структуру, но предоставляют больше содержимого в блоке content.

## <a name="the-flaskjade-web-project-template"></a>Использование шаблона "Веб-проект Flask/Jade"

Как уже отмечалось в начале этой статьи, Visual Studio предоставляет шаблон "Веб-проект Flask/Jade", который создает приложение, визуально идентичное результату шаблона "Веб-проект Flask". Основное различие заключается в использовании модуля шаблонов Jade, который является расширением Jinja, реализующим те же принципы с помощью более краткого кода. В частности, Jade использует ключевые слова, а не теги, заключенные в разделители {% %}, и позволяет ссылаться на стили CSS и HTML-элементы с помощью ключевых слов.

Чтобы можно было включить Jade, шаблон проекта должен включать пакет pyjade в файле *requirements.txt*.

Файл *\_\_init\_\_.py* приложения содержит строку для

```python
app.jinja_env.add_extension('pyjade.ext.jinja.PyJadeExtension')
```

В папке *templates* вы видите файлы *JADE* вместо шаблонов *HTML*, и представления в *views.py* ссылаются на эти файлы в вызовах к `flask.render_template`. В противном случае код представлений будет тем же.

Открыв один из файлов *JADE*, можно увидеть более короткое выражение шаблона. Например, вот содержимое *templates/layout.jade*, созданное с помощью шаблона "Веб-проект Flask/Jade":

```jade
doctype html
html
  head
    meta(charset='utf-8')
    meta(name='viewport', content='width=device-width, initial-scale=1.0')
    title #{title} - My Flask/Jade Application
    link(rel='stylesheet', type='text/css', href='/static/content/bootstrap.min.css')
    link(rel='stylesheet', type='text/css', href='/static/content/site.css')
    script(src='/static/scripts/modernizr-2.6.2.js')
  body
    .navbar.navbar-inverse.navbar-fixed-top
      .container
        .navbar-header
          button.navbar-toggle(type='button', data-toggle='collapse', data-target='.navbar-collapse')
            span.icon-bar
            span.icon-bar
            span.icon-bar
          a.navbar-brand(href='/') Application name
        .navbar-collapse.collapse
          ul.nav.navbar-nav
            li
              a(href='/') Home
            li
              a(href='/about') About
            li
              a(href='/contact') Contact
    .container.body-content
      block content
      hr
      footer
        p &copy; #{year} - My Flask/Jade Application

    script(src='/static/scripts/jquery-1.10.2.js')
    script(src='/static/scripts/bootstrap.js')
    script(src='/static/scripts/respond.js')

    block scripts
```

А вот содержимое *templates/about.jade*, демонстрирующее использование `#{ <name>}` в качестве заполнителей:

```jade
extends layout

block content
  h2 #{title}.
  h3 #{message}
  p Use this area to provide additional information.
```

Вы можете поэкспериментировать с синтаксисами Jinja и Jade, чтобы понять, какой из них вам лучше подходит.

## <a name="next-steps"></a>Дальнейшие действия

::: moniker range="vs-2017"
- [Шаблон веб-проекта опроса Flask](learn-flask-visual-studio-step-05-polls-flask-web-project-template.md)
::: moniker-end

::: moniker range=">=vs-2019"
> [!Note]
> Если вы зафиксировали свое решение Visual Studio с системой управления исходным кодом в ходе работы с этим руководством, настало время сделать другую фиксацию. Ваше решение должно соответствовать исходному коду руководства на сайте GitHub: [Microsoft/python-sample-vs-learning-flask](https://github.com/Microsoft/python-sample-vs-learning-flask).

Вы узнали все о шаблонах "Пустой веб-проект Flask", "Веб-проект Flask[/Jade]" и "Веб-проект опроса Flask[/Jade]" в Visual Studio. Вы получили представление об основах Flask, таких как использование представлений, шаблонов и маршрутизации, и узнали, как использовать резервные хранилища данных. Теперь вы можете приступить к созданию собственного веб-приложения с любыми необходимыми представлениями и моделями.

Запуск веб-приложения на компьютере разработчика — это лишь один шаг, чтобы сделать приложение доступным для клиентов. Следующие шаги могут включать приведенные ниже задачи:

- Развертывание веб-приложения на рабочий сервер, например в службу приложений Azure. См. статью [Публикация в "Службе приложений Azure"](publishing-python-web-applications-to-azure-from-visual-studio.md).

- Добавьте реализацию репозитория, использующую другое хранилище данных промышленного уровня, например PostgreSQL, MySQL и SQL Server (все они могут размещаться на платформе Azure). Вы можете также использовать [пакет SDK Azure для Python](/azure/python/), чтобы работать со службами хранилища Azure, такими как таблицы и большие двоичные объекты, а также с Cosmos DB.

- Настройте конвейер непрерывной интеграции или непрерывного развертывания в таких службах, как Azure DevOps. В дополнение к работе с системой управления исходным кодом (в Azure Repos, GitHub или в другом месте), можно настроить проект Azure DevOps для автоматического выполнения модульных тестов в качестве необходимого условия для выпуска, а также настроить конвейер для развертывания на промежуточный сервер для дополнительных тестов перед развертыванием в рабочей среде. Кроме того, Azure DevOps интегрируется с решениями мониторинга, такими как App Insights, и закрывает весь цикл гибкими средствами планирования. Дополнительные сведения см. в статье [Создание конвейера CI/CD для Python с помощью Azure DevOps Projects](/azure/devops-project/azure-devops-project-python?view=vsts&preserve-view=true) и в общей [документации по Azure DevOps](/azure/devops/?view=vsts&preserve-view=true).
::: moniker-end

## <a name="go-deeper"></a>Дополнительные подробности

- [Написание первого приложения Flask. Часть 4 — формы и универсальные представления](https://docs.djangoproject.com/en/2.0/intro/tutorial04/) (docs.djangoproject.com)
- [Jade на GitHub (документация)](https://github.com/liuliqiang/pyjade) (github.com)
- Исходный код, используемый в руководстве, на сайте GitHub: [Microsoft/python-sample-vs-learning-flask](https://github.com/Microsoft/python-sample-vs-learning-flask)
