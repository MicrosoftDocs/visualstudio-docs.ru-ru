---
title: Неиспользуемые значения и параметры
description: Сведения о неиспользуемых назначениях, переменных и параметрах, а также о том, как они отображаются в редакторе кода в Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 02/15/2019
ms.topic: reference
author: kendrahavens
ms.author: kehavens
manager: jmartens
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: cd0b6e936f4478cb4b74a3f004e69d77dbad7fbc
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99960615"
---
# <a name="unused-value-assignments-variables-and-parameters"></a>Неиспользуемые назначения, переменные и параметры

Область применения этого рефакторинга:

- C#
- Visual Basic

**Что?** Скрывает неиспользуемые параметры и создает предупреждение для неиспользуемых значений выражения. Компилятор также выполняет анализ потока для поиска всех неиспользуемых присвоений значений. Неиспользуемые присвоения значений скрываются, и отображается лампочка с [быстрым действием](../quick-actions.md) для удаления избыточного присвоения. Для неиспользуемых переменных с неизвестными значениями отображается [быстрое действие](../quick-actions.md) с предложением использовать вместо этого [пустые переменные](/dotnet/csharp/discards). (Пустые переменные — это временные фиктивные переменные, которые намеренно не используются в коде приложения. Они позволяют уменьшить объем выделяемой памяти и сделать код более удобным для чтения.)

**Когда?** У вас есть присвоения значений, параметры и значения выражения, которые никогда не используются.

**Зачем?** Иногда бывает трудно заметить, что присвоение значения, переменная или параметр больше не используются. Если скрыть эти значения или выдать предупреждение, вы получите визуальную подсказку о том, какой код можно удалить.

## <a name="unused-expression-values-and-parameters-diagnostic"></a>Диагностика неиспользуемых значений и параметров выражения

1. Имеется присвоение значения, переменная или параметр, которые не используются.
2. Неиспользуемое присвоение значения или неиспользуемый параметр выделены неярким шрифтом. Неиспользуемое значение выражения вызывает предупреждение.

  ![Неиспользуемый параметр](media/unused-parameter.png)
  ![Неиспользуемое значение](media/unused-value.png)
  ![Неиспользуемое присвоение значения](media/unused-value-assignment.png)
  ![Неиспользуемая пустая переменная](media/unused-value-discard.png)

## <a name="see-also"></a>См. также раздел

- [Рефакторинг](../refactoring-in-visual-studio.md)
- [Советы для разработчиков .NET](../csharp-developer-productivity.md)
