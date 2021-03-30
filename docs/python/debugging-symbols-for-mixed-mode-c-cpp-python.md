---
title: Символы для смешанного режима отладки Python и C++
description: Узнайте о возможностях загрузки символов для отладки Python и отладки в смешанном режиме C++ в Visual Studio.
ms.date: 11/12/2018
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.workload:
- python
- data-science
ms.openlocfilehash: d6820b9d94e8b4849c646c16075614aed17a4dd3
ms.sourcegitcommit: 20f546a0b13b56e7b0da21abab291d42a5ba5928
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/23/2021
ms.locfileid: "104884139"
---
# <a name="install-debugging-symbols-for-python-interpreters"></a>Установка отладочных символов для интерпретаторов Python

Чтобы предоставить полные возможности отладки, [отладчику смешанного режима Python](debugging-mixed-mode-c-cpp-python-in-visual-studio.md) в Visual Studio нужны отладочные символы для интерпретатора Python, который используется для анализа множества внутренних структур данных. Для *python27.dll*, например, соответствующим файлом символов является *python27.pdb*; для *python36.dll* файлом символов является *python36.pdb*. Каждая версия интерпретатора также поддерживает файлы символов для различных модулей.

В Visual Studio 2017 и более поздних версий интерпретаторы Python 3 и Anaconda 3 автоматически устанавливают соответствующие символы, которые Visual Studio находит автоматически. Для Visual Studio 2015 и более ранних версий или при использовании других интерпретаторов нужно отдельно скачать символы и указать их в Visual Studio, выбрав **Сервис** > **Параметры** и перейдя на вкладку **Отладка** > **Символы**. Эти действия описаны в разделах ниже.

Visual Studio может вывести запрос на использование символов (обычно при запуске сеанса отладки в смешанном режиме). В этом случае отображается диалоговое окно с двумя вариантами выбора:

- **Открыть диалоговое окно параметров** — открывает вкладку **Отладка** > **Символы** в диалоговом окне **Параметры**.
- **Скачать символы для моего интерпретатора** — открывает эту страницу документации. В этом случае выберите **Сервис** > **Параметры** и перейдите на вкладку **Отладка** > **Символы**, чтобы продолжить.

    ![Запрос на добавление символов в отладчике смешанного режима](media/mixed-mode-debugging-symbols-required.png)

## <a name="download-symbols"></a>Скачать символы

- Python 3.5 и более поздние версии: получите отладочные символы с помощью установщика Python. Выберите **Выборочная установка**, затем нажмите кнопку **Далее** и перейдите к разделу **Дополнительные параметры**. Здесь установите флажки **Загрузить отладочные символы** и **Загрузить двоичные файлы отладки**.

    ![Добавление отладочных символов в установщике Python 3.x](media/mixed-mode-debugging-symbols-installer35.png)

    Файлы символов (*PDB*) будут находиться в корневой папке установки (файлы символов для отдельных модулей находятся в папке *DLLs*). Поэтому Visual Studio находит их автоматически, и никакие дополнительные действия не требуются.

- Python 3.4.x и более ранние версии: символы доступны в виде скачиваемых *ZIP*-файлов в [официальных дистрибутивах](#official-distributions) или в [Enthought Canopy](#enthought-canopy). После скачивания извлеките файлы в локальную папку, например в папку *Symbols* внутри папки Python.

    > [!Important]
    > Как в дополнительных сборках Python, так и в сборках 32- и 64-разрядных версий используются разные символы, поэтому нужно точно знать используемые версии. Чтобы проверить, какой интерпретатор используется, разверните в **обозревателе решений** *узел* **Окружения Python** в проекте и запишите имя среды. Затем перейдите в *окно* **Окружения Python** и запишите расположение установки. После этого откройте окно командной строки в этом расположении и запустите *python.exe*, чтобы отобразить точную версию и архитектуру — 32- или 64-разрядная.

- Если вы используете дистрибутив Python независимого производителя, например ActiveState Python, свяжитесь с авторами дистрибутива и попросите предоставить вам эти символы. WinPython поддерживает стандартный интерпретатор Python без малейших изменений, поэтому для него можно использовать символы из официального дистрибутива для соответствующего номера версии.

## <a name="point-visual-studio-to-the-symbols"></a>Указание Visual Studio на символы

Если вы загрузили символы отдельно, выполните следующие шаги, чтобы Visual Studio могла распознавать их. Если символы установлены с помощью Python 3.5 или более поздней версии установщика, Visual Studio находит их автоматически.

1. Выберите пункт меню **Сервис** > **Параметры**, а затем перейдите к разделу **Отладка** > **Символы**.

1. На панели инструментов нажмите кнопку **Добавить** (выделена ниже), укажите папку, где развернуты скачанные символы (там, где находится файл *python.pdb*, например *c:\python34\Symbols*, как показано ниже), а затем нажмите кнопку **ОК**.

    ![Параметры символов в отладчике смешанного режима](media/mixed-mode-debugging-symbols.png)

1. Во время сеанса отладки Visual Studio может также запросить расположение исходного файла для интерпретатора Python. Если вы скачали исходные файлы (например, на сайте [python.org/downloads/](https://www.python.org/downloads/)), их также можно указать.

> [!Note]
> Функции кэширования символов, отображаемые в диалоговом окне, используются для создания локального кэша символов, полученных из источника в Интернете. Эти функции не нужны для символов интерпретатора Python, так как они уже присутствуют локально. В любом случае см. раздел [Указание символов и исходных файлов в отладчике Visual Studio](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).

## <a name="official-distributions"></a>Официальные дистрибутивы

| Версия Python | Скачиваемые файлы |
| --- | --- |
| 3.5 и более поздние версии | Установите символы с помощью установщика Python. |
| 3.4.4 | [32-разрядная](https://www.python.org/ftp/python/3.4.4/python-3.4.4-pdb.zip) - [64-разрядная](https://www.python.org/ftp/python/3.4.4/python-3.4.4.amd64-pdb.zip) |
| 3.4.3 | [32-разрядная](https://www.python.org/ftp/python/3.4.3/python-3.4.3-pdb.zip) - [64-разрядная](https://www.python.org/ftp/python/3.4.3/python-3.4.3.amd64-pdb.zip) |
| 3.4.2 | [32-разрядная](https://www.python.org/ftp/python/3.4.2/python-3.4.2-pdb.zip) - [64-разрядная](https://www.python.org/ftp/python/3.4.2/python-3.4.2.amd64-pdb.zip) |
| 3.4.1 | [32-разрядная](https://www.python.org/ftp/python/3.4.1/python-3.4.1-pdb.zip) - [64-разрядная](https://www.python.org/ftp/python/3.4.1/python-3.4.1.amd64-pdb.zip) |
| 3.4.0 | [32-разрядная](https://www.python.org/ftp/python/3.4.0/python-3.4.0-pdb.zip) - [64-разрядная](https://www.python.org/ftp/python/3.4.0/python-3.4.0.amd64-pdb.zip) |
| 3.3.5 | [32-разрядная](https://www.python.org/ftp/python/3.3.5/python-3.3.5-pdb.zip) - [64-разрядная](https://www.python.org/ftp/python/3.3.5/python-3.3.5.amd64-pdb.zip) |
| 3.3.4 | [32-разрядная](https://www.python.org/ftp/python/3.3.4/python-3.3.4-pdb.zip) - [64-разрядная](https://www.python.org/ftp/python/3.3.4/python-3.3.4.amd64-pdb.zip) |
| 3.3.3 | [32-разрядная](https://www.python.org/ftp/python/3.3.3/python-3.3.3-pdb.zip) - [64-разрядная](https://www.python.org/ftp/python/3.3.3/python-3.3.3.amd64-pdb.zip) |
| 3.3.2 | [32-разрядная](https://www.python.org/ftp/python/3.3.2/python-3.3.2-pdb.zip) - [64-разрядная](https://www.python.org/ftp/python/3.3.2/python-3.3.2.amd64-pdb.zip) |
| 3.3.1 | [32-разрядная](https://www.python.org/ftp/python/3.3.1/python-3.3.1-pdb.zip) - [64-разрядная](https://www.python.org/ftp/python/3.3.1/python-3.3.1.amd64-pdb.zip) |
| 3.3.0 | [32-разрядная](https://www.python.org/ftp/python/3.3.0/python-3.3.0-pdb.zip) - [64-разрядная](https://www.python.org/ftp/python/3.3.0/python-3.3.0.amd64-pdb.zip) |
| 2.7.18 | [32-разрядная](https://www.python.org/ftp/python/2.7.18/python-2.7.18-pdb.zip) - [64-разрядная](https://www.python.org/ftp/python/2.7.18/python-2.7.18.amd64-pdb.zip) |
| 2.7.17 | [32-разрядная](https://www.python.org/ftp/python/2.7.17/python-2.7.17-pdb.zip) - [64-разрядная](https://www.python.org/ftp/python/2.7.17/python-2.7.17.amd64-pdb.zip) |
| 2.7.16 | [32-разрядная](https://www.python.org/ftp/python/2.7.16/python-2.7.16-pdb.zip) - [64-разрядная](https://www.python.org/ftp/python/2.7.16/python-2.7.16.amd64-pdb.zip) |
| 2.7.15 | [32-разрядная](https://www.python.org/ftp/python/2.7.15/python-2.7.15-pdb.zip) - [64-разрядная](https://www.python.org/ftp/python/2.7.15/python-2.7.15.amd64-pdb.zip) |
| 2.7.14 | [32-разрядная](https://www.python.org/ftp/python/2.7.14/python-2.7.14-pdb.zip) - [64-разрядная](https://www.python.org/ftp/python/2.7.14/python-2.7.14.amd64-pdb.zip) |
| 2.7.13 | [32-разрядная](https://www.python.org/ftp/python/2.7.13/python-2.7.13-pdb.zip) - [64-разрядная](https://www.python.org/ftp/python/2.7.13/python-2.7.13.amd64-pdb.zip) |
| 2.7.12 | [32-разрядная](https://www.python.org/ftp/python/2.7.12/python-2.7.12-pdb.zip) - [64-разрядная](https://www.python.org/ftp/python/2.7.12/python-2.7.12.amd64-pdb.zip) |
| 2.7.11 | [32-разрядная](https://www.python.org/ftp/python/2.7.11/python-2.7.11-pdb.zip) - [64-разрядная](https://www.python.org/ftp/python/2.7.11/python-2.7.11.amd64-pdb.zip) |
| 2.7.10 | [32-разрядная](https://www.python.org/ftp/python/2.7.10/python-2.7.10-pdb.zip) - [64-разрядная](https://www.python.org/ftp/python/2.7.10/python-2.7.10.amd64-pdb.zip) |
| 2.7.9 | [32-разрядная](https://www.python.org/ftp/python/2.7.9/python-2.7.9-pdb.zip) - [64-разрядная](https://www.python.org/ftp/python/2.7.9/python-2.7.9.amd64-pdb.zip) |
| 2.7.8 | [32-разрядная](https://www.python.org/ftp/python/2.7.8/python-2.7.8-pdb.zip) - [64-разрядная](https://www.python.org/ftp/python/2.7.8/python-2.7.8.amd64-pdb.zip) |
| 2.7.7 | [32-разрядная](https://www.python.org/ftp/python/2.7.7/python-2.7.7-pdb.zip) - [64-разрядная](https://www.python.org/ftp/python/2.7.7/python-2.7.7.amd64-pdb.zip) |
| 2.7.6 | [32-разрядная](https://www.python.org/ftp/python/2.7.6/python-2.7.6-pdb.zip) - [64-разрядная](https://www.python.org/ftp/python/2.7.6/python-2.7.6.amd64-pdb.zip) |
| 2.7.5 | [32-разрядная](https://www.python.org/ftp/python/2.7.5/python-2.7.5-pdb.zip) - [64-разрядная](https://www.python.org/ftp/python/2.7.5/python-2.7.5.amd64-pdb.zip) |
| 2.7.4 | [32-разрядная](https://www.python.org/ftp/python/2.7.4/python-2.7.4-pdb.zip) - [64-разрядная](https://www.python.org/ftp/python/2.7.4/python-2.7.4.amd64-pdb.zip) |
| 2.7.3 | [32-разрядная](https://www.python.org/ftp/python/2.7.3/python-2.7.3-pdb.zip) - [64-разрядная](https://www.python.org/ftp/python/2.7.3/python-2.7.3.amd64-pdb.zip) |
| 2.7.2 | [32-разрядная](https://www.python.org/ftp/python/2.7.2/python-2.7.2-pdb.zip) - [64-разрядная](https://www.python.org/ftp/python/2.7.2/python-2.7.2.amd64-pdb.zip) |
| 2.7.1 | [32-разрядная](https://www.python.org/ftp/python/2.7.1/python-2.7.1-pdb.zip) - [64-разрядная](https://www.python.org/ftp/python/2.7.1/python-2.7.1.amd64-pdb.zip) |

## <a name="enthought-canopy"></a>Enthought Canopy

Enthought Canopy предоставляет символы для своих двоичных файлов начиная с версии 1.2. Они автоматически устанавливаются вместе с дистрибутивом, но папку, в которой они размещены, нужно вручную добавить в путь к символам, как описано выше. В обычных установках Canopy для отдельных пользователей эти символы находятся в папке *%UserProfile%\AppData\Local\Enthought\Canopy\User\Scripts* для 64-разрядной версии и *%UserProfile%\AppData\Local\Enthought\Canopy32\User\Scripts* для 32-разрядной версии.

В установках Enthought Canopy 1.1 и более ранних версий, а также в дистрибутивах Enthought Python (EPD) символы для интерпретатора не предоставляются, а значит вы не сможете применить для них отладку в смешанном режиме.
