---
title: Обозреватель схемы XML
description: Узнайте о функциях обозревателя XML-схем, интегрированного с Visual Studio, и редактора XML.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 2fc39e98-b194-456b-a452-cfafb0a52d66
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: c4b16c1baa039a2f1e812d35e7a4994ffc0d5e5c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99874890"
---
# <a name="xml-schema-explorer"></a>Обозреватель схемы XML

**Обозреватель XML-схем** интегрирован с Microsoft Visual Studio, а редактор XML позволяет работать со схемами языка определения схемы XML (XSD). При открытии файла XML-схемы в **обозревателе XML-схем** появляется узел **Набор схем**. Все включенные, импортированные или переопределенные схемы для конечного файла, а также любые файлы, которые указаны через инструкцию `include` или `import`, также появляются в **обозревателе XML-схемы**.

**Обозреватель XML-схем** позволяет:

- Получить быстрый обзор набора схем

- Просматривать и совершать переходы по дереву.

- Выполнять поиск ключевого слова и определенной схемы. Дополнительные сведения см. в статье [Поиск набора схем](../xml-tools/searching-the-schema-set.md).

- Добавлять результаты поиска в представление графика или представление модели содержимого.

- Сортировать дерево по порядку документа, типу или имени. Дополнительные сведения см. в статье [Сортировка, фильтрация и группирование](../xml-tools/sorting-filtering-and-grouping-xml-schema-explorer.md).

- Открыть редактор XML и перейти к местоположению кода в XSD-файле. Дополнительные сведения см. в статье [об интеграции с редактором XML](../xml-tools/integration-with-xml-editor.md).

- Создать XML-образцы для глобальных элементов.

**Обозреватель XML-схем** представляет иерархический вид схемы в виде дерева. **Обозреватель XML-схем** также производит поиск, фильтрацию, навигацию и сортировку. Для получения доступа к **обозревателю XML-схем**, необходимо выполнить следующее:

- Если вы находитесь в [начальном представлении](../xml-tools/start-view.md), щелкните ссылку **Обозреватель XML-схем**.

- Если вы находитесь в [представлении графика](../xml-tools/graph-view.md) или [представлении модели содержимого](../xml-tools/content-model-view.md) и имеете узлы в рабочей области, воспользуйтесь контекстным меню (щелкните правой кнопкой мыши), чтобы выбрать **обозреватель XML-схем**.

- Можно также выбрать **обозреватель XML-схем** в меню **Вид**.

- Получить доступ к **обозревателю XML-схем** можно посредством *VB*-файла, содержащего XML-литерал Visual Basic, связанный с *XSD*-файлом. Для просмотра набора схем в **обозревателе XML-схем** щелкните правой кнопкой мыши узел XML в XML-литерале или импорте пространства имен XML и выберите команду **Show in Schema Explorer** (Показать в обозревателе схем). Дополнительные сведения см. в статье [Интеграция XML-литералов с обозревателем XML-схем](../xml-tools/integration-of-xml-literals-with-xml-schema-explorer.md).

## <a name="tree-view"></a>Вид дерева
В **обозревателе XML-схем** отображаются сведения о прекомпилированном наборе схем в виде дерева. Структура дерева организована следующим образом.

- На верхнем уровне - узел набора схем.

- Второй уровень содержит пространства имен.

- Третий уровень содержит файлы.

- Четвертый уровень содержит глобальные узлы. Сюда могут входить элементы, группы, сложные типы, простые типы, атрибуты, группы атрибутов и инструкции `include`, `import`, `redefine`.

Ниже приведен пример структуры дерева:

![Обозреватель схемы XML](../xml-tools/media/xmlschemaexplorer.gif)

## <a name="selection-and-activation"></a>Выделение и активация
Чтобы выделить и выбрать узел, щелкните один раз обозреватель схем.

Для активации узла щелкните узел дважды или нажмите клавишу **ВВОД** при выбранном узле.

- Активация узла открывает файл, в котором определен данный узел (если файл еще не открыт), и выбирает узел из файла.

- Активация узла файла открывает выбранный файл (если файл еще не открыт) и выделяет узел `<schema>`.

- Активация SchemaSet или узла пространства имен не выполняет никаких действий

## <a name="drag-and-drop-nodes"></a>Перетаскивание узлов
Глобальные узлы, узлы файлов и узлы пространства имен можно перетаскивать в представление конструктора XSD. Если в данный момент открыто [начальное представление](../xml-tools/start-view.md), то при перетаскивании на него узла откроется [представление графика](../xml-tools/graph-view.md). Если в данный момент открыто [представление модели содержимого](../xml-tools/content-model-view.md) или представление графика, представление не изменится, если перетащить на него узел.

При перетаскивании файлов в представление все глобальные узлы в файле добавляются в [рабочую область конструктора XSD](../xml-tools/xml-schema-designer-workspace.md). Сброс пространств имен на представление добавит все глобальные узлы пространства имен в рабочую область. Рабочая область совместно используется всеми представлениями.

 Нельзя перетаскивать локальные узлы или импортируемые пространства имен.

## <a name="see-also"></a>См. также

- [Практическое руководство. Добавление узлов в рабочую область из обозревателя схем XML](../xml-tools/how-to-add-nodes-to-the-workspace-from-the-xml-schema-explorer.md)
