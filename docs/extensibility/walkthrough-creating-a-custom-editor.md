---
title: Пошаговое руководство. Создание настраиваемого редактора | Документация Майкрософт
description: Узнайте, как с помощью этого пошагового руководства шаблон проекта VSPackage может создать простой пользовательский редактор в C++.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- editors [Visual Studio SDK], custom - create
ms.assetid: d090abb6-d99f-4083-a3db-cd16bf81ce7d
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 79adcf719091619fe4c4eb62b1fe89ba3da388f5
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105062022"
---
# <a name="walkthrough-create-a-custom-editor"></a>Пошаговое руководство. Создание пользовательского редактора
Шаблон проекта VSPackage может создавать простой пользовательский редактор в C++. Шаблон проекта VSPackage больше не поддерживает проекты C# и Visual Basic. Дополнительные сведения см. в разделе [пакет SDK для Visual Studio](../extensibility/visual-studio-sdk.md).

## <a name="prerequisites"></a>Предварительные требования
 Для выполнения этого пошагового руководства необходимо установить пакет SDK для Visual Studio. Дополнительные сведения см. [в статье Установка пакета SDK для Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="the-visual-studio-package-project-template"></a>Шаблон проекта пакета Visual Studio
 Шаблон проекта пакета Visual Studio можно найти в диалоговом окне **Новый проект** в папке **расширяемость C++** .

### <a name="to-create-a-vspackage-using-the-visual-studio-package-template"></a>Создание VSPackage с помощью шаблона пакета Visual Studio

1. Создайте проект с помощью шаблона пакета Visual Studio.

2. Выберите параметр **Пользовательский редактор** и нажмите кнопку **Далее**. Откроется страница **Параметры редактора** .

3. Введите имя редактора в поле **имя редактора** . Введите расширение файла, которое необходимо связать с редактором, в поле **расширение файла** . Редактор доступен для файлов с этим расширением. Расширение файла регистрируется только для Visual Studio, а не для Windows. Введите имя файла по умолчанию для новых документов, созданных с помощью редактора, в поле **Default File Name (имя файла по умолчанию** ).

4. Нажмите кнопку **Готово** , чтобы создать VSPackage в указанной папке.

### <a name="to-test-your-custom-editor"></a>Тестирование пользовательского редактора

1. В меню **файл** наведите указатель мыши на пункт **создать** и выберите **файл**.

2. В области **Установленные шаблоны** диалогового окна **новый файл** выберите шаблон файла, а затем зарегистрированный тип файла.

3. Нажмите кнопку **Открыть** , чтобы просмотреть и изменить документ.

     Редактор поддерживает операции копирования и вставки, поиска и замены, а также операций открытия и загрузки.

## <a name="see-also"></a>См. также
- [VSPackages](../extensibility/internals/vspackages.md)
