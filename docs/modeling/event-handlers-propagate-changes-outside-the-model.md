---
title: Обработчики событий распространяют изменения за пределы модели
description: В пакете SDK для визуализации и моделирования можно определить обработчики событий хранилища, чтобы распространить изменения на ресурсы за пределами хранилища.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, programming domain models
- Domain-Specific Language, events
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 115d26840f321792712392367794e443e41543a2
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2021
ms.locfileid: "112388949"
---
# <a name="event-handlers-propagate-changes-outside-the-model"></a>Обработчики событий распространяют изменения за пределы модели

В пакете SDK для визуализации и моделирования можно определить обработчики событий хранилища, чтобы распространить изменения на ресурсы за пределами хранилища, такие как переменные, не связанные с хранением, файлы, модели в других магазинах или другие расширения Visual Studio. Обработчики событий хранилища выполняются после окончания транзакции, в которой произошло событие, вызывающее срабатывание. Они также выполняются при выполнении операции отмены или повтора. Таким образом, в отличие от правил хранения, события хранилища наиболее полезны для обновления значений, находящихся за пределами хранилища. В отличие от событий .NET, обработчики событий хранилища регистрируются для прослушивания класса: вам не нужно регистрировать отдельный обработчик для каждого экземпляра. Дополнительные сведения о выборе между различными способами для управления изменениями см. [в разделе реагирование на изменения и их распространение](../modeling/responding-to-and-propagating-changes.md).

Графические поверхности и другие элементы управления пользовательского интерфейса — это примеры внешних ресурсов, которые могут обрабатываться событиями магазина.

### <a name="to-define-a-store-event"></a>Определение события магазина

1. Выберите тип события, которое требуется отслеживать. Чтобы получить полный список, просмотрите свойства <xref:Microsoft.VisualStudio.Modeling.EventManagerDirectory> . Каждое свойство соответствует типу события. Чаще всего используются следующие типы событий:

    - `ElementAdded` — активируется при создании элемента модели, связи, фигуры или соединителя.

    - Елементпропертичанжед — активируется при `Normal` изменении значения свойства домена. Событие активируется только в том случае, если новые и старые значения не равны. Событие не может применяться к вычисляемым и пользовательским свойствам хранилища.

         Его нельзя применить к свойствам роли, которые соответствуют связям связей. Вместо этого используйте `ElementAdded` для отслеживания доменной связи.

    - `ElementDeleted` -активируется после удаления элемента модели, связи, фигуры или соединителя. Вы по-прежнему можете получить доступ к значениям свойств элемента, но он не будет иметь связей с другими элементами.

2. Добавьте определение разделяемого класса для _йоурдсл_**DocData** в отдельный файл кода в проекте **DslPackage** .

3. Напишите код события как метод, как показано в следующем примере. Это может быть `static` , если вы не хотите обращаться к `DocData` .

4. Переопределите `OnDocumentLoaded()` для регистрации обработчика. При наличии нескольких обработчиков их можно зарегистрировать в одном месте.

Расположение регистрационного кода не является критическим. `DocView.LoadView()` является альтернативным расположением.

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using Microsoft.VisualStudio.Modeling;

namespace Company.MusicLib
{
  partial class MusicLibDocData
  {
    // Register store events here or in DocView.LoadView().
    protected override void OnDocumentLoaded()
    {
      base.OnDocumentLoaded(); // Don't forget this.

      #region Store event handler registration.
      Store store = this.Store;
      EventManagerDirectory emd = store.EventManagerDirectory;
      DomainRelationshipInfo linkInfo = store.DomainDataDirectory
          .FindDomainRelationship(typeof(ArtistAppearsInAlbum));
      emd.ElementAdded.Add(linkInfo,
          new EventHandler<ElementAddedEventArgs>(AddLink));
      emd.ElementDeleted.Add(linkInfo,
          new EventHandler<ElementDeletedEventArgs>(RemoveLink));

      #endregion Store event handlers.
    }

    private void AddLink(object sender, ElementAddedEventArgs e)
    {
      ArtistAppearsInAlbum link = e.ModelElement as ArtistAppearsInAlbum;
      if (link != null)
            ExternalDatabase.Add(link.Artist.Name, link.Album.Title);
    }
    private void RemoveLink(object sender, ElementDeletedEventArgs e)
    {
      ArtistAppearsInAlbum link = e.ModelElement as ArtistAppearsInAlbum;
      if (link != null)
            ExternalDatabase.Delete(link.Artist.Name, link.Album.Title);
    }
  }
}
```

## <a name="use-events-to-make-undoable-adjustments-in-the-store"></a>Использование событий для внесения отменяемых корректировок в хранилище

События хранилища обычно не используются для распространения изменений в хранилище, так как обработчик событий выполняется после фиксации транзакции. Вместо этого следует использовать правило магазина. Дополнительные сведения см. [в разделе правила распространяют изменения в модели](../modeling/rules-propagate-changes-within-the-model.md).

Однако можно использовать обработчик событий для внесения дополнительных обновлений в хранилище, если вы хотите, чтобы пользователь мог отменить дополнительные обновления отдельно от исходного события. Например, предположим, что буквы в нижнем регистре являются обычным соглашением для названий альбомов. Можно написать обработчик событий хранилища, исправляет заголовок в нижний регистр после ввода пользователем в верхнем регистре. Но пользователь может использовать команду Отменить, чтобы отменить исправление, восстановив символы верхнего регистра. Вторая операция отмены приведет к удалению изменений пользователя.

Напротив, если вы написали правило хранения, чтобы сделать то же самое, изменение и исправление пользователя будут находиться в той же транзакции, чтобы пользователь не мог отменить корректировку без потери первоначального изменения.

```csharp
partial class MusicLibDocView
{
    // Register store events here or in DocData.OnDocumentLoaded().
    protected override void LoadView()
    {
      /* Register store event handler for Album Title property. */
      // Get reflection data for property:
      DomainPropertyInfo propertyInfo =
        this.DocData.Store.DomainDataDirectory
        .FindDomainProperty(Album.TitleDomainPropertyId);
      // Add to property handler list:
      this.DocData.Store.EventManagerDirectory
        .ElementPropertyChanged.Add(propertyInfo,
        new EventHandler<ElementPropertyChangedEventArgs>
             (AlbumTitleAdjuster));

      /*
      // Alternatively, you can set one handler for
      // all properties of a class.
      // Your handler has to determine which property changed.
      DomainClassInfo classInfo = this.Store.DomainDataDirectory
           .FindDomainClass(typeof(Album));
      this.Store.EventManagerDirectory
          .ElementPropertyChanged.Add(classInfo,
        new EventHandler<ElementPropertyChangedEventArgs>
             (AlbumTitleAdjuster));
       */
      return base.LoadView();
    }

// Undoable adjustment after a property is changed.
// Method can be static since no local access.
private static void AlbumTitleAdjuster(object sender,
         ElementPropertyChangedEventArgs e)
{
  Album album = e.ModelElement as Album;
  Store store = album.Store;

  // We mustn't update the store in an Undo:
  if (store.InUndoRedoOrRollback
      || store.InSerializationTransaction)
      return;

  if (e.DomainProperty.Id == Album.TitleDomainPropertyId)
  {
    string newValue = (string)e.NewValue;
    string lowerCase = newValue.ToLowerInvariant();
    if (!newValue.Equals(lowerCase))
    {
      using (Transaction t = store.TransactionManager
            .BeginTransaction("adjust album title"))
      {
        album.Title = lowerCase;
        t.Commit();
      } // Beware! This could trigger the event again.
    }
  }
  // else other properties of this class.
}
```

При написании события, которое обновляет хранилище:

- Используйте `store.InUndoRedoOrRollback` , чтобы избежать внесения изменений в элементы модели в случае отмены. Диспетчер транзакций задаст все данные в хранилище обратно в исходное состояние.

- Используйте `store.InSerializationTransaction` , чтобы избежать внесения изменений во время загрузки модели из файла.

- Изменения приведут к срабатыванию дальнейших событий. Убедитесь, что не существует бесконечного цикла.

## <a name="store-event-types"></a>Хранение типов событий

Каждый тип события соответствует коллекции в Store. Евентманажердиректори. Обработчики событий можно добавлять и удалять в любое время, но обычно они добавляются при загрузке документа.

|`EventManagerDirectory` Имя свойства|Выполняется, когда|
|-|-|
|елементаддед|Создается экземпляр класса домена, отношения домена, фигуры, соединитель или схема.|
|елементделетед|Элемент модели был удален из каталога элементов хранилища и больше не является источником или целевым объектом какой-либо связи. Элемент фактически не удаляется из памяти, но сохраняется в случае последующей отмены.|
|елементевентсбегун|Вызывается в конце внешней транзакции.|
|елементевентсендед|Вызывается, когда обрабатывались все другие события.|
|елементмовед|Элемент модели был перемещен из одного раздела хранилища в другой.<br /><br /> Это не связано с расположением фигуры на схеме.|
|елементпропертичанжед|Значение свойства домена изменилось. Это выполняется только в том случае, если старое и новое значения не равны.|
|ролеплайерчанжед|Одна из двух ролей (окончаний) связи ссылается на новый элемент.|
|ролеплайерордерчанжед|В роли с кратностью больше 1 последовательность ссылок изменилась.|
|трансактионбегиннинг||
|трансактионкоммиттед||
|трансактионролледбакк||

## <a name="see-also"></a>См. также

- [Реагирование на изменения и их распространение](../modeling/responding-to-and-propagating-changes.md)
- [Пример кода: схемы цепи](https://code.msdn.microsoft.com/Visualization-Modeling-SDK-763778e8)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]
