---
title: Преобразование класса в абстрактный
description: Узнайте, как сделать класс абстрактным после написания абстрактного метода.
ms.date: 11/03/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jmartens
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: ac3d6b9cef8d20d85049da830dfb830321faab75
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/02/2021
ms.locfileid: "106214542"
---
# <a name="make-class-abstract"></a>Преобразование класса в абстрактный

Область применения этого рефакторинга:

- C#

- Visual Basic

**Что?** Рефакторинг "Преобразование класса в абстрактный".

**Когда?** Написание абстрактного метода в классе, который не является абстрактным.

**Зачем?**  Наличие исправления кода, позволяющего преобразовать класс в абстрактный после написания абстрактного метода, позволит сэкономить время.

## <a name="how-to"></a>Практические советы

1. Поместите курсор в абстрактный метод.

2. Нажмите клавиши **CTRL**+ **.** чтобы открыть меню **Быстрые действия и рефакторинг**.

3. Выберите **Make class "abstract"** (Сделать класс абстрактным).

    ![Преобразование класса в абстрактный](media/make-class-abstract.png)

## <a name="see-also"></a>См. также раздел

- [Рефакторинг](../refactoring-in-visual-studio.md)
