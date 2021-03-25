---
title: Как создать веб-канал Atom для закрытой коллекции | Документация Майкрософт
description: Вы можете создать канал Atom (RSS) в интрасети, который содержит расширения, и добавить веб-канал к расширениям и обновлениям в виде частной коллекции.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- Atom feed, VSIX private galleries
- VSIX private galleries, Atom feed
ms.assetid: 5897f538-9c41-486f-97d9-a1976d20d9fd
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 2a83d5aa68f6f631243fbbfcad7cf28b25e7bc70
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105057381"
---
# <a name="how-to-create-an-atom-feed-for-a-private-gallery"></a>Как создать веб-канал Atom для частной коллекции
Вы можете создать канал Atom (RSS) в интрасети, который содержит расширения, и добавить веб-канал к **расширениям и обновлениям** в виде частной коллекции. Дополнительные сведения см. в статье [Закрытые коллекции](../extensibility/private-galleries.md).

## <a name="create-an-atom-feed"></a>Создание веб-канала Atom
 Чтобы создать веб-канал Atom в виде частной коллекции, сначала необходимо собрать расширения (*VSIX* -файлы) в папку. При необходимости их можно упорядочить по вложенным папкам. Кроме того, вам понадобятся следующие ресурсы:

- Файл *atom.xml* , который делает расширения доступными в виде частной коллекции. Сведения о том, как подключить файл *atom.xml* к **расширениям и обновлениям**, см. в разделе [частные галереи](../extensibility/private-galleries.md).

- Папка, содержащая все файлы изображений, извлеченные из расширений (например, снимки экрана). Файл *atom.xml* содержит относительные ссылки на эти изображения, чтобы они были доступны в **расширениях и обновлениях**.

  Например, предположим, что в папку собираются следующие два расширения:

- *Template_Wizard_239. VSIX*, который является пустым шаблоном проекта VSIX.

- *Селектионхигхлигхт. VSIX*— инструмент для выделения всех экземпляров выбранного слова.

  Содержимое файла *atom.xml* будет выглядеть следующим образом:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<feed xmlns="http://www.w3.org/2005/Atom">
  <title type="text" />
  <id>uuid:bcecded5-97c8-4d24-96f1-7d9e16652433;id=1</id>
  <updated>2011-04-14T21:25:48Z</updated>
  <entry>
    <id>SelectionHighlight..a14874d2-8199-4a60-af8a-11d6447813aa</id>
    <title type="text">Highlight all occurrences of selected word</title>
    <summary type="text">This extends the editor to highlight ....</summary>
    <published>2011-04-14T14:24:51-07:00</published>
    <updated>2011-04-14T14:24:22-07:00</updated>
    <author>
      <name>Microsoft</name>
    </author>
    <link rel="icon" href="VSIXImages/SelectionHighlight..a14874d2-8199-4a60-af8a-11d6447813aa_Icon_SelectionHighlightIcon.jpg" />
    <link rel="previewimage" href="VSIXImages/SelectionHighlight..a14874d2-8199-4a60-af8a-11d6447813aa_PreviewImage_SelectionHighlight.jpg" />
    <content type="application/octet-stream" src="SelectionHighlight.vsix" />
    <Vsix xmlns="http://schemas.microsoft.com/developer/vsx-syndication-schema/2010" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
      <Id>SelectionHighlight..a14874d2-8199-4a60-af8a-11d6447813aa</Id>
      <Version>1.31</Version>
      <References />
      <Rating xsi:nil="true" />
      <RatingCount xsi:nil="true" />
      <DownloadCount xsi:nil="true" />
    </Vsix>
  </entry>
  <entry>
    <id>Template_Wizard_239.Microsoft.3b38a7e3-5cbc-4389-a92a-d82tyc2ed592</id>
    ...
  </entry>
</feed>
```

 Обратите внимание, что два тега ссылки ссылаются на снимки экрана в создаваемой папке изображений.

## <a name="see-also"></a>См. также
- [Частные коллекции](../extensibility/private-galleries.md)
