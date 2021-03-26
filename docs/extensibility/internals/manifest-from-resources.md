---
title: Manifest from Resources | Документация Майкрософт
description: Узнайте, как использовать средство Manifest from Resources для добавления файлов PNG или XAML в файл имажеманифест для использования со службой изображений Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 0234109b-5dcb-4d9d-acb9-a63f8bd5699c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 42bd932b093ae805e8885bc9fc61324c3cadbe30
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105095177"
---
# <a name="manifest-from-resources"></a>Manifest from Resources
Средство Manifest from Resources — это консольное приложение, которое принимает список ресурсов изображений (PNG или XAML) и создает файл. имажеманифест, который позволяет использовать эти образы в службе образов Visual Studio. Кроме того, это средство можно использовать для добавления изображений в существующий имажеманифест. Это средство удобно использовать для добавления точек на дюйм и поддержки изображений в расширение Visual Studio. Созданный имажеманифест-файл должен быть включен в и развернут как часть расширения Visual Studio (VSIX).

## <a name="how-to-use-the-tool"></a>Использование средства
 **Синтаксис**

 Манифестфромресаурцес/ресаурцес: \<Dir1> ; \<Img1> /assembly: \<AssemblyName>\<Optional Args>

 **Аргументы**

|**Имя коммутатора**|**Примечания**|**Обязательный или необязательный**|
|-|-|-|
|/ресаурцес|Разделенный точками с запятой список образов или каталогов. Этот список всегда должен содержать полный список изображений, которые будут находиться в манифесте. Если задан только частичный список, то записи, не включенные в журнал, будут потеряны.<br /><br /> Если данный файл ресурсов является полосой изображения, средство разделит его на отдельные изображения перед добавлением каждого из них в манифест.<br /><br /> Если изображение является PNG-файлом, мы рекомендуем отформатировать его следующим образом, чтобы инструмент мог заполнить нужные атрибуты изображения: \<Name> . \<Width> . \<Height> . файле.|Обязательно|
|/Assembly|Имя управляемой сборки (не включая расширение) или путь среды выполнения машинной сборки, в которой размещаются ресурсы (относительно расположения среды выполнения манифеста).|Обязательно|
|/manifest|Имя, присваиваемое созданному имажеманифест файлу. Это также может включать абсолютный или относительный путь для создания файла в другом расположении. Имя по умолчанию совпадает с именем сборки.<br /><br /> По умолчанию: \<Current Directory> \\<Assembly \> . имажеманифест|Необязательно|
|/гуиднаме|Имя, присваиваемое символу GUID для всех образов в создаваемом манифесте.<br /><br /> По умолчанию: Ассетсгуид|Необязательно|
|/рутпас|Корневой путь, который необходимо отключить перед созданием URI управляемых ресурсов. (Этот флаг используется в случаях, когда средство получает относительный путь URI, что приводит к сбою загрузки ресурсов.)<br /><br /> По умолчанию: \<Current Directory>|Необязательно|
|/recursive|Установка этого флага указывает средству выполнить рекурсивный поиск в любых каталогах в аргументе/ресаурцес. Пропуск этого флага приведет к поиску только каталогов верхнего уровня.|Необязательно|
|/иснативе|Установите этот флаг, если аргумент сборки является путем к машинной сборке. Пропустите этот флаг, если аргумент Assembly является именем управляемой сборки. (Дополнительные сведения об этом флаге см. в разделе "Примечания".)|Необязательно|
|/невгуидс|Установка этого флага указывает средству создавать новое значение для символа GUID образа вместо того, чтобы объединять его из существующего манифеста.|Необязательно|
|/невидс|Установка этого флага указывает средству создавать новые значения символов идентификатора для каждого изображения, а не объединять значения из существующего манифеста.|Необязательно|
|/nologo|Установка этого флага останавливает печать сведений о продукте и авторских правах.|Необязательно|
|/?|Вывод справочной информации.|Необязательно|
|/help|Вывод справочной информации.|Необязательный|

 **Примеры**

- Манифестфромресаурцес/ресаурцес: Д:\имажес/Assembly: My. Assembly. Name/Иснативе

- Манифестфромресаурцес/resources:D:\Images\Image1.png;D: \Images\Image1.xaml/Assembly: My. Assembly. Name/manifest: Мимажеманифест. имажеманифест

- Манифестфромресаурцес/resources:D:\Images\Image1.png;D: \Images\Image1.xaml/Assembly: My. Assembly. Name/Гуиднаме: MyImages/Невгуидс/Невидс

## <a name="notes"></a>Примечания

- Средство поддерживает только файлы PNG и XAML. Все остальные типы файлов или изображений будут игнорироваться. Предупреждение создается для всех неподдерживаемых типов, обнаруженных при анализе ресурсов. Если не удается найти поддерживаемые образы после завершения анализа ресурсов средством, будет сформирована ошибка.

- В соответствии с рекомендуемым форматом для изображений в формате PNG средство установит размер и значение размера для PNG-изображения в формате, даже если он отличается от фактического размера изображения.

- Формат ширины и высоты может быть опущен для изображений в формате PNG, но средство будет считывать фактическую ширину и высоту изображения и использовать их для размера или значения измерения.

- Запуск этого средства для одной и той же ленты изображений несколько раз для одного и того же элемента. имажеманифест приведет к дублированию записей манифеста, так как средство пытается разделить полосу изображений на отдельные изображения и добавить их в существующий манифест.

- Слияние (пропуск/Невгуидс или/Невидс) должно выполняться только для манифестов, созданных средствами. Манифесты, которые были настроены или созданы с помощью других средств, могут быть неправильно объединены.

- Манифесты, созданные для сборок в машинном коде, могут быть изменены вручную после создания, чтобы символы идентификатора совпадали с идентификаторами ресурсов из RC-файла сборки в машинном коде.

## <a name="sample-output"></a>Пример выходных данных
 **Простой манифест изображения**

 Манифест изображения будет похож на этот XML-файл:

```xml
<?xml version="1.0" encoding="utf-8"?>
<!-- This file was generated by the ManifestFromResources tool.-->
<!-- Version: 14.0.15197 -->
<ImageManifest xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns="http://schemas.microsoft.com/VisualStudio/ImageManifestSchema/2014">
  <Symbols>
    <String Name="Resources" Value="/My.Assembly.Name;Component/Resources/Images" />
    <Guid Name="AssetsGuid" Value="{fb41b7ef-6587-480c-aa27-5b559d42cfc9}" />
    <ID Name="MyImage" Value="0" />
  </Symbols>
  <Images>
    <Image Guid="$(AssetsGuid)" ID="$(MyImage)">
      <Source Uri="$(Resources)/Xaml/MyImage.xaml" />
      <Source Uri="$(Resources)/Png/MyImage.16.16.png">
        <Size Value="16" />
      </Source>
    </Image>
  </Images>
  <ImageLists />
</ImageManifest>
```

 **Манифест изображения для полосы изображений**

 Манифест изображения для полосы изображений будет похож на этот XML-файл:

```xml
<?xml version="1.0" encoding="utf-8"?>
<!-- This file was generated by the ManifestFromResources tool.-->
<!-- Version: 14.0.15197 -->
<ImageManifest xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns="http://schemas.microsoft.com/VisualStudio/ImageManifestSchema/2014">
  <Symbols>
    <String Name="Resources" Value="/My.Assembly.Name;Component/Resources/ImageStrip" />
    <Guid Name="AssetsGuid" Value="{fb41b7ef-6587-480c-aa27-5b559d42cfc9}" />
    <ID Name="MyImageStrip_0" Value="1" />
    <ID Name="MyImageStrip_1" Value="2" />
    <ID Name="MyImageStrip" Value="3" />
  </Symbols>
  <Images>
    <Image Guid="$(AssetsGuid)" ID="$(MyImageStrip_0)">
      <Source Uri="$(Resources)/MyImageStrip_0.png">
        <Size Value="16" />
      </Source>
    </Image>
    <Image Guid="$(AssetsGuid)" ID="$(MyImageStrip_1)">
      <Source Uri="$(Resources)/MyImageStrip_1.png">
        <Size Value="16" />
      </Source>
    </Image>
  </Images>
  <ImageLists>
    <ImageList Guid="$(AssetsGuid)" ID="$(MyImageStrip)">
      <ContainedImage Guid="$(AssetsGuid)" ID="$(MyImageStrip_0)" />
      <ContainedImage Guid="$(AssetsGuid)" ID="$(MyImageStrip_1)" />
    </ImageList>
  </ImageLists>
</ImageManifest>
```

 **Манифест образа для ресурсов машинного образа сборки**

 Манифест изображения для образов в машинном коде будет похож на этот XML-файл:

```xml
<?xml version="1.0" encoding="utf-8"?>
<!-- This file was generated by the ManifestFromResources tool.-->
<!-- Version: 14.0.15198 -->
<ImageManifest xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns="http://schemas.microsoft.com/VisualStudio/ImageManifestSchema/2014">
  <Symbols>
    <String Name="Resources" Value="..\Assembly\Folder\My.Assembly.Name" />
    <Guid Name="AssetsGuid" Value="{442d8739-efde-46a4-8f29-e3a1e5e7f8b4}" />
    <ID Name="MyImage1" Value="0" />
    <ID Name="MyImage2" Value="1" />
  </Symbols>
  <Images>
    <Image Guid="$(AssetsGuid)" ID="$(MyImage1)">
      <Source Uri="$(Resources)">
        <Size Value="16" />
        <NativeResource ID="$(MyImage1)" Type="PNG" />
      </Source>
    </Image>
    <Image Guid="$(AssetsGuid)" ID="$(MyImage2)">
      <Source Uri="$(Resources)">
        <Size Value="16" />
        <NativeResource ID="$(MyImage2)" Type="PNG" />
      </Source>
    </Image>
  </Images>
  <ImageLists />
</ImageManifest>
```
