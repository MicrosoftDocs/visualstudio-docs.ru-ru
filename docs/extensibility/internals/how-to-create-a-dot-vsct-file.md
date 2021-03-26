---
title: Как создать. Файл vsct | Документация Майкрософт
description: Узнайте, как вручную создать файл vsct, файл конфигурации таблицы команд Visual Studio на основе XML.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- VSCT files, creating
ms.assetid: b955f51c-f9f9-49c3-a8e4-63b6eb0e0341
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 7fe1d92a9117193a72f579a01f264f1a13be6b6e
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105056614"
---
# <a name="how-to-create-a-vsct-file"></a>Как создать vsct-файл

Существует несколько способов создания файла конфигурации таблицы команд Visual Studio (*vsct*) на основе XML.

- В [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] шаблоне пакета можно создать новый пакет VSPackage.

- Для создания файла из существующего *CTC* -файла можно использовать компилятор конфигурации таблицы команд на основе XML, *Vsct.exe*.

- *Vsct.exe* можно использовать для создания файла *vsct* из существующего *CTO* -файла.

- Новый *vsct* -файл можно создать вручную.

  В этой статье объясняется, как вручную создать новый *vsct* -файл.

### <a name="to-manually-create-a-new-vsct-file"></a>Создание нового vsct-файла вручную

1. Запустите среду [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].

2. В меню **Файл** укажите пункт **Создать**, а затем выберите пункт **Файл**.

3. В области **шаблоны** выберите **XML-файл** и нажмите кнопку **Открыть**.

4. В меню **вид** выберите пункт **свойства** , чтобы отобразить свойства XML-файла.

5. В окне **Свойства** нажмите кнопку **Обзор** в свойстве **схемы** .

6. В списке схем XSD выберите схему *vsct. xsd* . Если он отсутствует в списке, нажмите кнопку **Добавить** , а затем найдите файл на локальном диске. По завершении нажмите кнопку **ОК** .

7. В XML-файле введите *<коммандтабле* и нажмите клавишу **Tab**. Закройте тег, введя *>* .

    Это действие создает файл Basic *. vsct* .

8. Заполните элементы XML-файла, который требуется добавить, в соответствии со ссылкой на [XML-схему VSCT](../../extensibility/vsct-xml-schema-reference.md). Дополнительные сведения см. в разделе [Author. vsct Files](../../extensibility/internals/authoring-dot-vsct-files.md).

<a name="how-to-create-a-dot-vsct-file-from-an-existing-dot-ctc-file"></a>

## <a name="how-to-create-a-vsct-file-from-an-existing-ctc-file"></a>Как создать vsct-файл из существующего CTC-файла

Вы можете создать *VSCT* -файл на основе XML из существующего файла. *CTC* исходного кода. Таким образом можно воспользоваться новым форматом компилятора таблицы команд [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] на основе XML (VSCT).

### <a name="to-create-a-vsct-file-from-a-ctc-file"></a>Создание файла VSCT на основе файла CTC

1. Получите копию языка Perl.

2. Получите копию *ConvertCTCToVSCT.pl* сценария Perl, которая обычно находится в папке *\<Visual Studio SDK installation path> \висуалстудиоинтегратион\тулс\бин* .

3. Получите копию исходного файла *CTC* , который необходимо преобразовать.

4. Поместите файлы в один каталог.

5. В [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] окне командной строки перейдите в каталог.

6. Type

   ```
   perl.exe ConvertCTCtoVSCT.pl PkgCmd.ctc PkgCmd.vsct
   ```

    где *PkgCmd. CTC* — это имя файла *CTC* , а *PkgCmd. vsct* — имя создаваемого *vsct* -файла.

    Это действие создает новый исходный файл XML-команды *vsct* . Файл можно скомпилировать с помощью *Vsct.exe*, компилятора VSCT, как и любой другой файл *VSCT* .

   > [!NOTE]
   > Чтобы улучшить удобочитаемость файла *vsct* , можно переформатировать XML-комментарии.

<a name="how-to-create-a-dot-vsct-file-from-an-existing-dot-cto-file"></a>

## <a name="how-to-create-a-vsct-file-from-an-existing-cto-file"></a>Как создать vsct-файл из существующего CTO-файла

Можно создать XML-файл с *расширением vsct* на основе существующего файла binary *. CTO* . Это позволяет воспользоваться преимуществами нового формата компилятора таблицы команд. Этот процесс работает даже в том случае, если файл *. CTO* был скомпилирован из *CTC* -файла. Файл *. vsct* можно изменить и скомпилировать в другой файл CTO.

### <a name="to-create-a-vsct-file-from-a-cto-file"></a>Создание файла VSCT на основе файла CTO

1. Получение копий файла *CTO* и соответствующего *ctsym* файла.

2. Поместите файлы в тот же каталог, что и компилятор *vsct.exe* .

3. В командной строке Visual Studio перейдите в каталог, содержащий файлы *. CTO* и *. ctsym* .

4. Type

    ```
    vsct.exe <ctofilename>.cto <vsctfilename>.vsct -S<symfilename>.ctsym
    ```

     где \<ctofilename\> — имя *CTO* -файла, \<vsctfilename\> — имя создаваемого файла *vsct* , а \<symfilename\> — имя *ctsym* -файла.

     Этот процесс создает новый файл компилятора XML-команд *vsct* . Файл можно изменить и скомпилировать с помощью *vsct.exe*, компилятора vsct, как и любого другого файла *vsct* .

## <a name="compile-the-code"></a>Компиляция кода
 Простое добавление файла *vsct* в проект не приводит к его компиляции. Его необходимо включить в процесс сборки.

### <a name="to-add-a-vsct-file-to-project-compilation"></a>Добавление файла. vsct в компиляцию проекта

1. Откройте файл проекта в редакторе. Если проект загружен, его необходимо сначала выгрузить.

2. Добавьте [элемент ItemGroup](../../msbuild/itemgroup-element-msbuild.md) , содержащий `VSCTCompile` элемент, как показано в следующем примере.

    ```xml
    <ItemGroup>
      <VSCTCompile Include="TopLevelMenu.vsct">
        <ResourceName>Menus.ctmenu</ResourceName>
      </VSCTCompile>
    </ItemGroup>

    ```

     `ResourceName`Элемент всегда должен иметь значение `Menus.ctmenu` .

3. Если проект содержит *RESX* -файл, добавьте `EmbeddedResource` элемент, содержащий `MergeWithCTO` элемент, как показано в следующем примере:

    ```xml
    <EmbeddedResource Include="VSPackage.resx">
      <MergeWithCTO>true</MergeWithCTO>
      <ManifestResourceName>VSPackage</ManifestResourceName>
    </EmbeddedResource>

    ```

     Эта разметка должна идти внутри `ItemGroup` элемента, содержащего внедренные ресурсы.

4. Откройте файл пакета, который обычно называется *\<ProjectName\> Package. CS* или *\<ProjectName\> Package. vb*, в редакторе.

5. Добавьте `ProvideMenuResource` атрибут в класс Package, как показано в следующем примере.

    ```csharp
    [ProvideMenuResource("Menus.ctmenu", 1)]
    ```

     Первое значение параметра должно соответствовать значению `ResourceName` атрибута, определенного в файле проекта.

## <a name="see-also"></a>См. также
- [Файлы Author. vsct](../../extensibility/internals/authoring-dot-vsct-files.md)
- [Файлы таблицы команд Visual Studio (. vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
- [Справочник по XML-схеме VSCT](../../extensibility/vsct-xml-schema-reference.md)
