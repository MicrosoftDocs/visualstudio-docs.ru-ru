---
title: Пример ImageOptimizer для обновления расширений Visual Studio
description: Выполните пример, чтобы узнать, как обновить расширение Visual Studio для работы с предварительной версией Visual Studio 2022.
ms.date: 06/08/2021
ms.topic: sample
author: leslierichardson95
ms.author: lerich
manager: jmartens
monikerRange: vs-2022
ms.workload:
- vssdk
ms.openlocfilehash: 12bbc159884c16ea89849e5c97a4b87292f7089d
ms.sourcegitcommit: 674d3fafa7c9e0cb0d1338027ef419a49c028c36
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/24/2021
ms.locfileid: "112602221"
---
# <a name="imageoptimizer---update-a-visual-studio-extension-step-by-step"></a>ImageOptimizer — пошаговое обновление расширения Visual Studio

[!INCLUDE [preview-note](../includes/preview-note.md)]

В этом руководстве будут показаны все действия, необходимые для добавления поддержки Visual Studio 2022 при сохранении поддержки Visual Studio 2019 с использованием расширения Image Optimizer в качестве примера.  
Это подробное руководство с ссылками на git commit в каждом шаге, но вы также можете посмотреть окончательный PR здесь: [https://github.com/madskristensen/ImageOptimizer/pull/46](https://github.com/madskristensen/ImageOptimizer/pull/46).

Кроме того, в конце этого руководства приводятся [дополнительные примеры](#other-samples).

## <a name="step-1---modernize-the-project"></a>Шаг 1. Модернизация проекта

См. [Модернизация проекта](update-visual-studio-extension.md#modernize-your-vsix-project).

[git commit e052465](https://github.com/madskristensen/ImageOptimizer/pull/46/commits/e052465f30e6bed37e6d76eac016047095e8e18b)

Сначала мы переносим VSIX и проект модульного теста в .NET 4.7.2 на странице свойств проектов:

   ![Перенос версии платформы](media/samples/framework-bump.png)

Image Optimizer ссылался на некоторые старые специальные пакеты 14.* и 15.*. Вместо этого мы установим [пакет NuGet `Microsoft.VisualStudio.Sdk`](https://www.nuget.org/packages/microsoft.visualstudio.sdk), который консолидирует все необходимые ссылки.

```Diff
-  <ItemGroup>
-    <PackageReference Include="Madskristensen.VisualStudio.SDK">
-      <Version>14.0.0-beta4</Version>
-    </PackageReference>
-    <PackageReference Include="Microsoft.VSSDK.BuildTools">
-      <Version>15.8.3247</Version>
-      <IncludeAssets>runtime; build; native; contentfiles; analyzers</IncludeAssets>
-      <PrivateAssets>all</PrivateAssets>
-    </PackageReference>
-  </ItemGroup>

+  <ItemGroup>
+    <PackageReference Include="Microsoft.VisualStudio.SDK">
+      <Version>16.9.31025.194</Version>
+    </PackageReference>
+  </ItemGroup>
```

Сборка проекта успешно выполнена, и мы получаем несколько предупреждений о потоках. Мы исправляем эти предупреждения, щелкая `ctrl` и `.` и используя IntelliSense, чтобы добавить недостающие строки переключения потоков.

## <a name="step-2---refactor-source-code-into-a-shared-project"></a>Шаг 2. Рефакторинг исходного кода в общий проект

См. [Общие проекты](update-visual-studio-extension.md#use-shared-projects-for-multi-targeting).

Для поддержки Visual Studio 2022 необходимо добавить новый общий проект, содержащий исходный код расширения, которое будет совместно использоваться в проектах VSIX Visual Studio 2019 и Visual Studio 2022.

1. Добавление нового общего проекта в решение

   [git commit abf249d](https://github.com/madskristensen/ImageOptimizer/pull/46/commits/abf249d5a4bed9010652f3f3fc4753c7c771c892)

   ![Добавление общего проекта](media/samples/add-shared-project.png)

1. Добавьте ссылку на общий проект в свой проект VSIX.

   [git commit e8e941e](https://github.com/madskristensen/ImageOptimizer/pull/46/commits/e8e941e5a5482cc15f5b9e7e4f1727f5cab5b12c)

   :::image type="content" source="media/update-visual-studio-extension/add-shared-project-reference.png" alt-text="Добавление ссылки на общий проект" lightbox="media/update-visual-studio-extension/add-shared-project-reference.png":::

1. Переместите в новый общий проект файлы исходного кода (CS, XAML, RESX) **за исключением** следующих:
    - `source.extension.vsixmanifest`
    - файлов метаданных расширения (значков, лицензий, заметок о выпуске и т. д.);
    - VSCT-файлов;
    - Связанные файлы
    - внешних инструментов или библиотек, которые необходимо включить в VSIX.

   [git commit f31f051](https://github.com/madskristensen/ImageOptimizer/pull/46/commits/f31f0515305623988f2c355ed3bf5952fc8f1d9e)

   ![Перемещение файлов в общий проект](media/samples/move-to-shared-project.png)

1. Теперь переместите все метаданные, VSCT-файлы, связанные файлы, внешние инструменты и библиотеки в общее расположение и снова добавьте их в качестве связанных элементов в проект VSIX. **Не** удаляйте `source.extension.vsixmanifest`.

   [git commit 73ba920 — перемещение файлов](https://github.com/madskristensen/ImageOptimizer/pull/46/commits/73ba920b7db0bdb7c4d66aa9bc932c268efd49cb)

   [git commit d5e36b2 — добавление внешних инструментов и библиотек](https://github.com/madskristensen/ImageOptimizer/pull/46/commits/d5e36b2d047290d38ffc977511510bc03e257f13)

   1. Для этого проекта необходимо переместить значок расширения, VSCT-файл и внешние инструменты в новую папку `ImageOptimizer\Resources`. Скопируйте их в эту общую папку и удалите из проекта VSIX.
   1. Снова добавьте их в качестве связанных элементов, и если какие-то элементы уже связаны, их можно оставить в том же виде (например, лицензию).
   1. Убедитесь, что действие сборки и другие свойства в добавленных связанных файлах заданы правильно, выбирая каждый файл и проверяя окно инструментов "Свойства". Для нашего проекта нам нужно было установить следующее:
       - задать для действия сборки `icon.png` значение `Content` и установить "Включить в VSIX" как `true`;
       - задать для действия сборки `ImageOptimizer.vsct` значение `VSCTComplile` и установить "Включить в VSIX" как `false`;
       - задать для всех действий сборки для файлов в `Resources\Tools` значение `Content` и установить "Включить в VSIX" как `true`.

           ![Добавление связанных файлов в проект VSIX](media/samples/add-linked-files.png)

       - Кроме того, `ImageOptimizer.cs` является зависимостью `ImageOptimizer.vsct`. Для этого нам нужно вручную добавить эту зависимость в CSPROJ-файл:

          ```diff  
          - <Content Include="..\SharedFiles\ImageOptimizer.vsct">
          -   <Link>ImageOptimizer.vsct</Link>
          - </Content>
          - <Compile Include="..\SharedFiles\ImageOptimizer.cs">
          -   <Link>ImageOptimizer.cs</Link>
          - </Compile>

          + <VSCTCompile Include="..\SharedFiles\ImageOptimizer.vsct">
          +   <ResourceName>Menus.ctmenu</ResourceName>
          +   <Generator>VsctGenerator</Generator>
          +   <LastGenOutput>..\SharedFiles\ImageOptimizer.cs</LastGenOutput>
          + </VSCTCompile>
          + <Compile Include="..\SharedFiles\ImageOptimizer.cs">
          +   <AutoGen>True</AutoGen>
          +   <DesignTime>True</DesignTime>
          +   <DependentUpon>..\SharedFiles\ImageOptimizer.vsct</DependentUpon>
          + </Compile>
          ```

       - Если окно инструментов "Свойства" не позволяет задать конкретное действие сборки, можно вручную изменить CSPROJ-файл, как делалось выше, и задать действие сборки как необходимо.

1. Выполните сборку проекта, чтобы проверить внесенные изменения и исправить все ошибки. Описание распространенных проблем см. в разделе [Вопросы и ответы](update-visual-studio-extension.md#q--a).

## <a name="step-3---add-a-visual-studio-2022-vsix-project"></a>Шаг 3. Добавление проекта VSIX Visual Studio 2022

См. раздел [Добавление целевого объекта Visual Studio 2022](update-visual-studio-extension.md#add-a-visual-studio-2022-target).

1. Добавьте новый проект VSIX в решение.
1. Удалите весь дополнительный исходный код в новом проекте, за исключением `source.extension.vsixmanifest.`

   ![Создание нового проекта VSIX](media/samples/visual-studio-2022-vsix-initial.png)

1. Добавьте ссылку в общий проект.

   [git commit dd49cb2](https://github.com/madskristensen/ImageOptimizer/pull/46/commits/dd49cb227b52c46206bf4be5c25790ac0377568d)

   :::image type="content" source="media/update-visual-studio-extension/add-shared-project-reference.png" alt-text="Добавление ссылки на общий проект" lightbox="media/update-visual-studio-extension/add-shared-project-reference.png":::

1. Добавьте связанные файлы из проекта VSIX Visual Studio 2019 и проверьте соответствие свойств "Действие сборки" и "Включить в VSIX". Также скопируйте файл `source.extension.vsixmanifest`, который позднее мы изменим для поддержки Visual Studio 2022.

   [git commit 98c43ee](https://github.com/madskristensen/ImageOptimizer/pull/46/commits/98c43ee6fbe912c38a1275542c44c65e11d7dbd9)

   ![Добавление связанных файлов в проект VSIX](media/samples/visual-studio-2022-add-linked-files.png)

1. Попытка сборки показывает, что отсутствует ссылка на `System.Windows.Forms`. Просто добавьте ее в проект Visual Studio 2022 и перестройте его.

   [git commit de71ccd](https://github.com/madskristensen/ImageOptimizer/pull/46/commits/de71ccd9baff703aa6679392ad41a2cfe7bd7d72)

   ```Diff
   + <Reference Include="System.Windows.Forms" />
   ```

1. Обновите ссылки на пакеты `Microsoft.VisualStudio.SDK` и `Microsoft.VSSDK.BuildTools`, указав версии Visual Studio 2022.

   [git commit d581fc3](https://github.com/madskristensen/ImageOptimizer/pull/46/commits/d581fc3c954974124dc7e31e5ecc85f78f7828ab)

   > [!NOTE]
   > Это последние версии, доступные на момент создания этого руководства. Рекомендуется использовать самые последние доступные версии.
   >
   > ```diff
   > -<PackageReference Include="Microsoft.VisualStudio.SDK" Version="16.0.206" />
   > +<PackageReference Include="Microsoft.VisualStudio.SDK" Version="17.0.0-preview-1-31216-1036" />
   > -<PackageReference Include="Microsoft.VSSDK.BuildTools" Version="16.10.32" />
   > +<PackageReference Include="Microsoft.VSSDK.BuildTools" Version="17.0.63-Visual Studio 2022-g3f11f5ab" />
   > ```

1. Измените файл `source.extension.vsixmanifest`, чтобы он указывал целевой объект Visual Studio 2022.

   [git commit 9d393c7](https://github.com/madskristensen/ImageOptimizer/pull/46/commits/9d393c708c04ac4af48d1eb9ce3da4470db5d5cc)
   1. Задайте тег `<InstallationTarget>`, чтобы в нем были указаны Visual Studio 2022 и полезные данные amd64:

      ```xml
      <InstallationTarget Id="Microsoft.VisualStudio.Community" Version="[17.0,18.0)">
          <ProductArchitecture>amd64</ProductArchitecture>
      </InstallationTarget>
      ```

   1. Измените Prerequisite, включив только Visual Studio 2022 и более поздние версии:

      ```Diff
      - <Prerequisite Id="Microsoft.VisualStudio.Component.CoreEditor" Version="[15.0,)" DisplayName="Visual Studio core editor" />
      + <Prerequisite Id="Microsoft.VisualStudio.Component.CoreEditor" Version="[17.0,)" DisplayName="Visual Studio core editor" />
      ```

Теперь все готово.

В результате сборка создает VSIX-файлы Visual Studio 2019 и Visual Studio 2022.

## <a name="other-samples"></a>Другие примеры

- [Инструменты ProPower](https://github.com/microsoft/VS-PPT/pull/244)
  - PeekF1
    - Позволяет просматривать в веб-браузере справочную информацию о выбранном классе или объекте.
  - FixMixedTabs
    - Сканирует документы и заменяет знаки табуляции пробелами и наоборот.

## <a name="next-steps"></a>Дальнейшие действия

Подготовьтесь к обновлению расширения, ознакомившись с этим [пошаговым руководством](update-visual-studio-extension.md).
