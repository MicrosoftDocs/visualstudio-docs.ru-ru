---
title: Задание фонового изображения схемы
description: Узнайте, что в пакете SDK визуализации и моделирования Visual Studio можно задать фоновое изображение для созданного конструктора с помощью пользовательского кода.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 9304117932b92408f12a23747253de66dfd767d1
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2021
ms.locfileid: "112385673"
---
# <a name="setting-a-background-image-on-a-diagram"></a>Задание фонового изображения схемы
В пакете SDK визуализации и моделирования Visual Studio можно задать фоновое изображение для созданного конструктора с помощью пользовательского кода.

## <a name="setting-the-background-image"></a>Настройка фонового изображения

#### <a name="to-set-a-background-image-for-a-generated-designer"></a>Установка фонового изображения для сгенерированного конструктора

1. Скопируйте файл изображения, который будет использоваться в качестве фона схемы, в каталог Dsl\Resources текущего проекта.

2. В **Обозреватель решений** щелкните правой кнопкой мыши папку дсл\ресаурцес, наведите указатель на пункт **Добавить** и выберите пункт **существующий элемент**.

3. В диалоговом окне **Добавление существующего элемента** перейдите к папке дсл\ресаурцес.

4. В списке **тип файлов** выберите **файлы изображений**.

5. Щелкните файл образа, скопированный в каталог, и нажмите кнопку **Добавить**.

6. Щелкните правой кнопкой мыши элемент DSL и выберите пункт **Свойства** , чтобы открыть свойства проекта DSL.

7. На вкладке **ресурсы** щелкните **этот проект не содержит файл ресурсов по умолчанию. Щелкните здесь, чтобы создать его.**

8. Добавьте файл изображения в файл ресурсов, перетащив изображение из **Обозреватель решений** в окно ресурсы.

9. Откройте меню "Файл" и выберите параметр для сохранения свойств проекта.

10. Убедитесь, что файл Dsl\Properties\Resources.resx существует и под ним есть файл Resources.Designer.cs.

11. Если Resources. Designer. CS отсутствует, щелкните файл Resources. resx в **Обозреватель решений**.

12. В окне **Свойства** присвойте свойству `Custom Tool` значение `ResXFileCodeGenerator`.

13. В **Обозреватель решений** щелкните правой кнопкой мыши проект DSL, наведите указатель на пункт **Добавить** и выберите пункт **создать папку**.

14. Присвойте папке имя **Custom**.

15. Щелкните правой кнопкой мыши пользовательскую папку, наведите указатель на пункт **Добавить** и выберите пункт **новый элемент**.

16. В диалоговом окне **Добавление нового элемента** в списке **шаблоны** щелкните **файл кода**.

17. В поле **имя** введите `BackgroundImage.cs` и нажмите кнопку **добавить**.

18. Скопируйте указанный ниже код в файл BackgroundImage.cs, изменив пространство имен, имя класса схемы и имя ресурса файла изображения.

     Замените "MyDiagramClass" на имя частичного класса схемы, определенное в файле Dsl\GeneratedCode\Diagrams.cs. Узнать правильное пространство имен можно также с помощью файла Dsl\GeneratedCode\Diagrams.cs.

    ```csharp
    using System;
    using Microsoft.VisualStudio.Modeling.Diagrams;

    // Fix the namespace:
    namespace Fabrikam.MyLanguage
    {
      // Fix the Diagram Class name - get it from GeneratedCode\Diagram.cs

      public partial class Language29Diagram
      {
        protected override void InitializeInstanceResources()
        {
          // Fix the Resources namespace and the Image resource name:
          ImageField backgroundField = new ImageField("background",
              Fabrikam.MyLanguage.Properties.Resources.MyPicture);

          backgroundField.DefaultFocusable = false;
          backgroundField.DefaultSelectable = false;
          backgroundField.DefaultVisibility = true;
          backgroundField.DefaultUnscaled = false;

          shapeFields.Add(backgroundField);

          backgroundField.AnchoringBehavior
            .SetTopAnchor(AnchoringBehavior.Edge.Top, 0.01);
          backgroundField.AnchoringBehavior
            .SetLeftAnchor(AnchoringBehavior.Edge.Left, 0.01);
          backgroundField.AnchoringBehavior
            .SetRightAnchor(AnchoringBehavior.Edge.Right, 0.01);
          backgroundField.AnchoringBehavior
            .SetBottomAnchor(AnchoringBehavior.Edge.Bottom, 0.01);

          base.InitializeInstanceResources();
        }
      }
    }
    ```

     Дополнительные сведения о настройке модели с помощью программного кода см. [в разделе Навигация и обновление модели в программном коде](../modeling/navigating-and-updating-a-model-in-program-code.md).

## <a name="see-also"></a>См. также

- [Определение фигур и соединителей](../modeling/defining-shapes-and-connectors.md)
- [Настройка полей с текстом и изображениями](../modeling/customizing-text-and-image-fields.md)
- [Перемещение по модели и обновление модели в коде программы](../modeling/navigating-and-updating-a-model-in-program-code.md)
- [Написание кода для настройки доменного языка](../modeling/writing-code-to-customise-a-domain-specific-language.md)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]
