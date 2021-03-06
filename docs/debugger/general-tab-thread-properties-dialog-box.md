---
title: Вкладка "Общие", диалоговое окно "Свойства потока" | Документация Майкрософт
description: Просмотр сведений о потоке, таких как имя модуля, идентификаторы потока и процесса, состояние потока, причина ожидания и время ЦП, в диалоговом окне "Свойства потока".
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- threading [Visual Studio], thread properties
- thread properties
ms.assetid: 46b6c668-6786-456e-97dc-337bcac0d812
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 02ba7d14dad8e4755170ffca7853aa9cc6c85a19
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99870549"
---
# <a name="general-tab-thread-properties-dialog-box"></a>Вкладка "Общие" диалогового окна "Свойства потока"
Это диалоговое окно используется для получения дополнительных сведений о конкретном потоке. Чтобы отобразить это диалоговое окно, переместите фокус в окно [представления потоков](../debugger/threads-view.md) или откройте окно [представления сообщений](../debugger/messages-view.md) и разверните сообщение. Выберите любой узел потока в дереве, а затем в меню **Вид** выберите пункт **Свойства**.

 В диалоговом окне **Свойства потока** имеется одна область, вкладка **Общие**. Доступны следующие параметры.

|Ввод|Описание|
|-----------|-----------------|
|**Имя модуля**|Имя модуля.|
|**Идентификатор потока**|Уникальный идентификатор этого потока. Обратите внимание, что идентификаторы потоков повторно используемые, поэтому они определяют конкретный поток только в течение времени существования этого потока.|
|**Идентификатор процесса**|Уникальный идентификатор этого процесса. Идентификаторы процессов повторно используемые, поэтому они определяют процесс только в течение времени существования этого процесса. Тип объекта "Процесс" создается при запуске программы. Все потоки в процессе совместно используют одно и то же адресное пространство и имеют доступ к одним и тем же данным. Выберите данное значение, чтобы просмотреть свойства процесса с этим идентификатором.|
|**Состояние потока**|Текущее состояние потока. Выполняющийся поток использует процессор; резервный поток собирается использовать его. Готовый поток ожидает, когда можно начать использовать процессор, так как он не свободен. Поток в переходе ожидает ресурс для выполнения, например, ожидает, пока его стек выполнения будет загружен в память с диска. Ожидающему потоку не требуется процессор, так как он ожидает завершения периферийной операции или освобождения ресурса.|
|**Причина ожидания**|Это применимо только в том случае, если поток находится в состоянии ожидания. Пары событий используются для взаимодействия с защищенными подсистемами.|
|**Время ЦП**|Общее время ЦП, затраченное на этот процесс и его потоки. Равно сумме времени пользователя и привилегированного времени.|
|**Время пользователя**|Общее время, затраченное потоком на выполнение кода в пользовательском режиме. Приложения выполняются в пользовательском режиме, как и подсистемы, такие как диспетчер окон и графический модуль.|
|**Время работы в привилегированном режиме**|Общее время, затраченное потоком на выполнение кода в привилегированном режиме. При вызове системных служб Windows они часто выполняются в привилегированном режиме, который открывает для них доступ к закрытым системным данным. Такие данные защищены от доступа из потоков, выполняющихся в пользовательском режиме. Вызовы системы могут быть явными или неявными, как, например, при сбое страницы или возникновении прерывания.|
|**Затраченное время**|Общее время выполнения данного потока (в секундах).|
|**Текущий приоритет**|Текущий динамический приоритет данного потока. Потоки внутри процесса могут повышать и понижать собственный базовый приоритет относительно базового приоритета процесса.|
|**Базовый приоритет**|Текущий базовый приоритет данного потока.|
|**Начальный адрес**|Начальный виртуальный адрес для данного потока.|
|**ПК пользователя**|Пользовательский программный счетчик для потока.|
|**Переключения контекста**|Количество переключений из одного потока в другой. Переключения потоков могут выполняться внутри одного процесса или между процессами. Переключение потока может быть вызвано тем, что один поток запрашивает информацию у другого, или выгружением потока, когда поток с более высоким приоритетом становится готовым к запуску.|