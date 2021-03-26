---
title: Флаги Command-Line компилятора VSCT | Документация Майкрософт
description: Компилятор Командная таблица Visual Studio предоставляет параметры командной строки для обеспечения успешной компиляции vsct-файлов.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT files, compiling
- command-table file compilation (VSCT files)
ms.assetid: 9dc6c33f-e6cf-4cf2-9b05-e8f7bfac1cfb
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 20c078d65af6224c65c2c574471b046deaf0cc92
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105069300"
---
# <a name="vsct-compiler-command-line-flags"></a>Флаги командной строки компилятора VSCT
Компилятор Командная таблица Visual Studio (VSCT) предоставляет параметры командной строки для обеспечения успешной компиляции VSCT-файлов.

## <a name="command-line-parameters"></a>Параметры командной строки
 Чтобы просмотреть базовую справку VSCT из [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] **командного** окна, перейдите к папке \висуалстудиоинтегратион\тулс\бин\ *путь установки пакета SDK для Visual Studio* и введите:

```
vsct /?
```

 Возвращаемые данные:

```
Microsoft (R) Visual Studio (R) Command Table Compiler Version 3.00.2000

Syntax: vsct <infile> [<outfile>] [-S[symbols file]] [-D<preprocessor-define>]*
[-I<include-path>]* [-L<language>] [-E[C|H|N]:<name>]

  -D    Specify any additional preprocessor defines
  -I    Indicate what additional include paths to send to the preprocessor
  -L    Specify the language to use when selecting strings
  -E    Emit C# objects in the specified namespace for command items,
        followed by [L|F|H|N]:<value>
        F = Name of the file to emit (used if -EL is provided)
        L = Name of a language providing a CodeDOM provider
        N = namespace (required if -EL is provided)
        H = C++ header
  -c    Clean build skipping dependency checks
  -v    Verbose output
```

> [!NOTE]
> Символы-(тире) и/(косая черта) являются допустимой нотацией для указания параметров командной строки.

 Ниже приведены допустимые флаги и их значения.

|Параметр|Описание|
|------------|-----------------|
|-d|Укажите любые дополнительные определенные символы.|
|-I|Укажите дополнительные пути включения, которые следует использовать при разрешении ссылок на файлы.|
|-l|Укажите <xref:System.Globalization.CultureInfo> имя языка и региональных параметров, например "en-US".|
|-E|Выдавать объекты C# в указанном пространстве имен для командных элементов, за которыми следует [C&#124;H&#124;N]:*filename*, где C = C#, H = заголовок C++, N = Namespace. Пространство имен является обязательным для C#.|
|-v|Подробный вывод.|

 Параметр-L указывает компилятору выбрать группу строк, чтобы создать файл binary. CTO, соответствующий заданному <xref:System.Globalization.CultureInfo> имени языка и региональных параметров. Указанное имя языка и региональных параметров должно соответствовать атрибуту Language одного или нескольких [элементов strings](../../extensibility/strings-element.md) в vsct файле. Если у элемента строк нет атрибута языка, он наследуется от содержащего его [элемента коммандтабле](../../extensibility/commandtable-element.md).

 Файл. vsct может содержать несколько строковых элементов, и у каждого из них может быть другой атрибут языка. Глобализация достигается за счет многократного запуска компилятора VSCT и изменения параметра-L для каждого имени языка и региональных параметров.

 Если имя языка и региональных параметров, заданное параметром-L, не соответствует атрибуту Language любого элемента Strings, компилятор будет пытаться сопоставить язык, а не регион. Например, если не удается найти "en-US", компилятор попытается использовать "en". В этом случае будет выполнена попытка использовать текущий язык и региональные параметры операционной системы. Это приведет к компиляции первого найденного элемента Strings.

 Параметр-E можно использовать для выдачи заголовочного файла в стиле C, содержащего символы, используемые в командной таблице, или для создания файла C#, содержащего объекты для символов команды.

 Переключатели-D и-I имеют синтаксис флагов препроцессора Cl.exe C с одинаковыми именами. Для расширения XML- \<Defined> тестов в атрибутах используются определения-D с форматом X = Y `Condition` . -I включает пути, используемые для разрешения \<Include> \<Extern> и \<Bitmap> ссылок на файлы. Дополнительные сведения см. в [справочнике по XML-схеме VSCT](../../extensibility/vsct-xml-schema-reference.md).

 Компилятор VSCT также может декомпилировать ранее созданный двоичный файл. Для этого укажите двоичный файл для \<infile> .   Если двоичный файл был создан компилятором VSCT, его символы уже внедрены и будут выдавать выходные данные с символами в \<Symbols> разделе выходных данных. Если двоичный файл был создан компилятором CTC, выходные данные будут содержать фактические идентификаторы GUID и идентификаторы. Если файл *. ctsym, созданный текущими версиями Ctc.exe, находится в той же папке, что и входной двоичный файл, то символы будут загружены из этого файла и использованы для вывода.

## <a name="see-also"></a>См. также
- [Файлы таблицы команд Visual Studio (VSCT-файлы)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
- [Справочник по схемам XML VSCT](../../extensibility/vsct-xml-schema-reference.md)
- [Как добавить элементы пользовательского интерфейса с помощью пакетов VSPackage](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
