---
title: Упрощение выражения LINQ
description: Такой рефакторинг используется для удаления ненужных вызовов к Enumerable для метода Where.
ms.date: 08/12/2020
ms.topic: reference
author: m-redding
ms.author: midumont
manager: jmartens
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 20a3524d786b1f03fc3e221d1b257892d9439a0b
ms.sourcegitcommit: 8590cf6b3351e82827fd21159beefef0c02bf162
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/08/2021
ms.locfileid: "102466171"
---
# <a name="simplify-linq-expression"></a>Упрощение выражения LINQ

Область применения этого рефакторинга:

- C#

**Что?** Экземпляры выполнения рефакторинга `SomeEnumerableType.Where(<LambdaExpression>).Single()` в `SomeEnumerable.Single(<LambdaExpression>)` для `Enumerable.Single()`, а также следующие методы Enumerable: `SingleOrDefault()`, `Last()`, `LastOrDefault()`, `Any()`, `Count()`, `First()` и `FirstOrDefault()`.

**Когда?**  Все экземпляры, в которых метод вызывает `Single()`, `SingleOrDefault()` и т. д., не имеют аргументов, и перед ними указывается выражение `Where()`. Входные данные для выражения `Where()` не могут быть построены в виде дерева выражения.

**Зачем?** Удаление ненужного вызова Enumerable для метода `.Where()` повышает производительность и удобочитаемость.

## <a name="how-to"></a>Практическое руководство

1. Поместите курсор в экземпляр `SomeEnumerableType.Where(<LambdaExpression>).Single()` в Visual Studio.
2. Нажмите клавиши **CTRL**+ **.** чтобы открыть меню **Быстрые действия и рефакторинг**.
3. Выберите **Упростить выражение LINQ**

   ![Преобразование typeof в nameof](media/simplify-linq-expression.png)

## <a name="see-also"></a>См. также

- [Рефакторинг](../refactoring-in-visual-studio.md)
