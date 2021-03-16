---
title: Создание переопределений методов Equals и GetHashCode C#
description: Узнайте, как использовать меню "Быстрые действия и рефакторинг" для создания методов Equals и GetHashCode.
ms.custom: SEO-VS-2020
ms.date: 03/08/2021
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: 6a9d0ea6f6cb0aedc4fa13a8014b1a8bd66ccca0
ms.sourcegitcommit: 6ed6ae5a1693607dce57923a78d01eea3d88b29a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/09/2021
ms.locfileid: "102514968"
---
# <a name="generate-equals-and-gethashcode-method-overrides-in-visual-studio"></a>Создание переопределений для методов Equals и GetHashCode в Visual Studio

Область применения этого формирования кода:

- C#

**Что?** Эта возможность позволяет создавать методы **Equals** и **GetHashCode**.

**Когда?** Создавайте эти переопределения, если у вас есть тип, который нужно сравнить по одному или нескольким полям, а не по расположению объектов в памяти.

**Зачем?**

- При реализации типа значения рекомендуется переопределить метод **Equals**. При этом обеспечивается повышенная производительность по сравнению с реализацией метода Equals по умолчанию для ValueType.

- При реализации ссылочного типа рекомендуется переопределить метод **Equals**, если ваш тип выглядит как базовый, например Point, String, BigNumber и т. д.

- Переопределите метод **GetHashCode**, чтобы тип правильно работал в хэш-таблице. Дополнительные сведения см. в руководстве по [операторам равенства](/dotnet/standard/design-guidelines/equality-operators).

## <a name="how-to"></a>Практические советы

1. Поместите курсор в любую позицию на строке объявления типа.

    ```csharp
    public class ImaginaryNumber
    {
        public double RealNumber { get; set; }
        public double ImaginaryUnit { get; set; }
    }
    ```

   Теперь код должен выглядеть как на следующем снимке экрана:

   ![Снимок экрана: выделенный код, в котором применяется созданный метод](media/overrides-highlight-cs.png)

   > [!TIP]
   > Не выбирайте имя типа двойным щелчком, иначе параметр меню будет недоступен. Просто установите курсор в любую позицию на строке.

1. Далее выберите одно из следующих действий:

   - Нажмите клавиши **CTRL**+ **.** чтобы открыть меню **Быстрые действия и рефакторинг**.

   - Щелкните правой кнопкой мыши и выберите меню **Быстрые действия и рефакторинг**.

   - Нажмите кнопку ![Снимок экрана: значок отвертки "Быстрые действия" в Visual Studio](../media/screwdriver-icon.png) , которая отображается в левом поле.

1. Выберите **Создать Equals(object)** или **Создать Equals и GetHashCode** в раскрывающемся меню.

   ![Снимок экрана: раскрывающееся меню "Создание переопределений"](media/overrides-preview-cs.png)

1. В диалоговом окне **Выбрать члены** выберите члены, для которых хотите создать методы:

    ![Диалоговое окно создания переопределений](media/overrides-dialog-cs.png)

    > [!TIP]
    > В этом диалоговом окне также можно создавать операторы, используя флажок в нижней части окна.

   Методы `Equals` и `GetHashCode` создаются с реализациями по умолчанию, как показано в следующем коде:

    ```csharp
   public class ImaginaryNumber : IEquatable<ImaginaryNumber>
    {
        public double RealNumber { get; set; }
        public double ImaginaryUnit { get; set; }

        public override bool Equals(object obj)
        {
            return Equals(obj as ImaginaryNumber);
        }

        public bool Equals(ImaginaryNumber other)
        {
            return other != null &&
                   RealNumber == other.RealNumber &&
                   ImaginaryUnit == other.ImaginaryUnit;
        }

        public override int GetHashCode()
        {
            return HashCode.Combine(RealNumber, ImaginaryUnit);
        }
    }
    ```

   Теперь код должен выглядеть как на следующем снимке экрана:

   ![Снимок экрана: результат созданного метода](media/overrides-result-cs.png)

## <a name="see-also"></a>См. также

- [Создание кода](../code-generation-in-visual-studio.md)
- [Просмотр изменений](../../ide/preview-changes.md)
