---
title: Опубликовать расширение с помощью командной строки
description: Узнайте, как использовать командную строку для публикации расширения в Visual Studio Marketplace, что позволяет разработчикам просматривать новые и обновленные расширения.
ms.custom: SEO-VS-2020
ms.date: 07/12/2018
ms.topic: how-to
helpviewer_keywords:
- publishing extensions
- extension, publishing
ms.assetid: 6ff9efc4-919d-4071-a80d-6dbdd2ceb2f8
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: d3548c9a206e874848756944fb48d447c34e28cc
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105078374"
---
# <a name="walkthrough-publishing-a-visual-studio-extension-via-command-line"></a>Пошаговое руководство. публикация расширения Visual Studio с помощью командной строки

В этом пошаговом руководстве показано, как опубликовать расширение Visual Studio в Visual Studio Marketplace с помощью командной строки. При добавлении расширения в Marketplace разработчики могут использовать диалоговое окно [**расширения и обновления**](../ide/finding-and-using-visual-studio-extensions.md) для просмотра новых и обновленных расширений.

VsixPublisher.exe — это программа командной строки для публикации расширений Visual Studio в Marketplace. Доступ к нему можно получить из $ {VSInstallDir} \VSSDK\VisualStudioIntegration\Tools\Bin\VsixPublisher.exe. В этом средстве доступны следующие команды: **Publish**, **креатепублишер**, **делетепублишер**, **делетикстенсион**, **Login**, **logout**.

## <a name="commands"></a>Команды

### <a name="publish"></a>Опубликовать

Публикует расширение в Marketplace. Расширение может быть расширением VSIX, файлом EXE или MSI или ссылкой. Если расширение уже существует в той же версии, расширение будет перезаписано. Если расширение еще не существует, оно создаст новое расширение.

|Параметры команды |Описание |
|---------|---------|
|полезные данные (обязательный) | Путь к полезной нагрузке для публикации или ссылка для использования в качестве URL-адреса дополнительной информации. |
|Публишманифест (обязательно) | Путь к файлу манифеста публикации для использования. |
|игнореварнингс | Список предупреждений, игнорируемых при публикации расширения. Эти предупреждения отображаются в виде сообщений командной строки при публикации расширения. (например, "VSIXValidatorWarning01, VSIXValidatorWarning02")
|персоналакцесстокен | Персональный маркер доступа (PAT), используемый для проверки подлинности издателя. Если не указано, то PAT запрашивается у вошедших в систему пользователей. |

```
VsixPublisher.exe publish -payload "{path to vsix}" -publishManifest "{path to vs-publish.json}" -ignoreWarnings "VSIXValidatorWarning01,VSIXValidatorWarning02"
```

### <a name="createpublisher"></a>креатепублишер

Создает издатель в Marketplace. Также записывает издатель на компьютер для будущих действий (например, путем удаления или публикации расширения).

|Параметры команды |Описание |
|---------|---------|
|displayName (обязательно) | Отображаемое имя издателя. |
|publisherName (обязательно) | Имя издателя (например, идентификатор). |
|Персоналакцесстокен (обязательно) | Личный маркер доступа, используемый для проверки подлинности издателя. |
|shortDescription | Краткое описание издателя (а не файла). |
|лонгдескриптион | Длинное описание издателя (не файл). |

```
VsixPublisher.exe createPublisher -publisherName "{Publisher Name}" -displayName "{Publisher Display Name}" -personalAccessToken "{Personal Access Token}"
```

### <a name="deletepublisher"></a>делетепублишер

Удаляет издатель в Marketplace.

|Параметры команды |Описание |
|---------|---------|
|publisherName (обязательно) | Имя издателя (например, идентификатор). |
|Персоналакцесстокен (обязательно) | Личный маркер доступа, используемый для проверки подлинности издателя. |

```
VsixPublisher.exe deletePublisher -publisherName "{Publisher Name}" -personalAccessToken "{Personal Access Token}"
```

### <a name="deleteextension"></a>делетикстенсион

Удаляет расширение из Marketplace.

|Параметры команды |Описание |
|---------|---------|
|extensionName (обязательно) | Имя удаляемого расширения. |
|publisherName (обязательно) | Имя издателя (например, идентификатор). |
|персоналакцесстокен | Личный маркер доступа, используемый для проверки подлинности издателя. Если не указано, то Pat запрашивается у вошедших в систему пользователей. |

```
VsixPublisher.exe deleteExtension -extensionName "{Extension Name}" -publisherName "{Publisher Name}"
```

### <a name="login"></a>login

Записывает издатель на компьютер.

|Параметры команды |Описание |
|---------|---------|
|Персоналакцесстокен (обязательно | Личный маркер доступа, используемый для проверки подлинности издателя. |
|publisherName (обязательно) | Имя издателя (например, идентификатор). |
|перезапись | Указывает, что любой существующий издатель должен быть перезаписан с новым личным маркером доступа. |

```
VsixPublisher.exe login -personalAccessToken "{Personal Access Token}" -publisherName "{Publisher Name}"
```

### <a name="logout"></a>logout

Записывает издатель на компьютере.

|Параметры команды |Описание |
|---------|---------|
|publisherName (обязательно) | Имя издателя (например, идентификатор). |
|игноремиссингпублишер | Указывает, что средство не должно выдавать ошибку, если указанный издатель еще не вошел в систему. |

```
VsixPublisher.exe logout -publisherName "{Publisher Name}"
```

## <a name="publishmanifest-file"></a>файл Публишманифест

Файл Публишманифест используется командой **Publish** . Он представляет все метаданные о расширении, которое необходимо узнать в Marketplace. Если передаваемый модуль имеет расширение VSIX, свойство Identity должно иметь только набор "Интерналнаме". Это связано с тем, что остальные свойства Identity можно создать из файла VSIXMANIFEST. Если расширение — это расширение MSI/exe или ссылка, пользователь должен предоставить обязательные поля в свойстве Identity. Остальная часть манифеста содержит сведения, относящиеся к Marketplace (например, категории, независимо от того, включено ли в Q&A и т. д.).

Образец файла Публишманифест расширения VSIX:

```json
{
    "$schema": "http://json.schemastore.org/vsix-publish",
    "categories": [ "build", "coding" ],  // The categories of the extension. Between 1 and 3 categories are required.
    "identity": {
        "internalName": "MyVsixExtension" // If not specified, we try to generate the name from the display name of the extension in the vsixmanifest file.
                                            // Required if the display name is not the actual name of the extension.
    },
    "overview": "overview.md",            // Path to the "readme" file that gets uploaded to the Marketplace. Required.
    "priceCategory": "free",              // Either "free", "trial", or "paid". Defaults to "free".
    "publisher": "MyPublisherName",       // The name of the publisher. Required.
    "private": false,                     // Specifies whether or not the extension should be public when uploaded. Defaults to false.
    "qna": true,                          // Specifies whether or not the extension should have a Q&A section. Defaults to true.
    "repo": "https://github.com/MyPublisherName/MyVsixExtension" // Not required.
}
```

Файл MSI/EXE или LINK Публишманифест File Sample:

```json
{
    "$schema": "http://json.schemastore.org/vsix-publish",
    "categories": [ "build", "coding" ],
    "identity": {
        "description": "My extension.", // The description of the extension. Required for non-vsix extensions.
        "displayName": "My Extension",  // The display name of the extension. Required for non-vsix extensions.
        "icon": "\\path\\to\\icon.ico", // The path to an icon file (can be relative to the json file location). Required for non-vsix extensions.
        "installTargets": [             // The installation targets for the extension. Required for non-vsix extensions.
            {
                "sku": "Microsoft.VisualStudio.Community",
                "version": "[10.0, 16.0)"
            }
        ],
        "internalName": "MyExtension",
        "language": "en-US",            // The default language id of the extension. Can be in the "1033" or "en-US" format. Required for non-vsix extensions.
        "tags": [ "tag1", "tag2" ],     // The tags for the extension. Not required.
        "version": "3.7.0",             // The version of the extension. Required for non-vsix extensions.
        "vsixId": "MyExtension",        // The vsix id of the extension. Not required but useful for showing updates to installed extensions.
    },
    "overview": "overview.md",
    "priceCategory": "free",
    "publisher": "MyPublisherName",
    "private": false,
    "qna": true,
    "repo": "https://github.com/MyPublisherName/MyVsixExtension"
}
```

## <a name="asset-files"></a>Файлы ресурсов

Для внедрения таких файлов, как изображения в файле сведений, можно указать файлы ресурсов. Например, если расширение имеет следующий Markdown документ "Обзор":

```markdown
TestExtension
...
This is test extension.
![Test logo](images/testlogo.png "Test logo")
```

Чтобы разрешить "образы/testlogo.png" в предыдущем примере, пользователь может предоставить "assetFiles" в манифесте публикации, как показано ниже:

```json
{
    "assetFiles": [
        {
            "pathOnDisk": "\\path\\to\\logo.png",
            "targetPath": "images/logo.png"
        }
    ],
    // other required fields
}
```

## <a name="publishing-walkthrough"></a>Пошаговое руководство по публикации

### <a name="prerequisites"></a>Предварительные требования

Для выполнения этого пошагового руководства необходимо установить пакет SDK для Visual Studio. Дополнительные сведения см. [в разделе Установка пакета SDK для Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).

### <a name="create-a-visual-studio-extension"></a>Создание расширения Visual Studio

В этом случае мы будем использовать расширение VSPackage по умолчанию, но те же действия допустимы для каждого типа расширения.

1. Создайте пакет VSPackage на языке C# с именем «Тестпублиш», который содержит команду меню. Дополнительные сведения см. [в разделе Создание первого расширения: Hello World](../extensibility/extensibility-hello-world.md).

### <a name="package-your-extension"></a>Упаковка расширения

1. Обновите расширение vsixmanifest, указав правильные сведения об имени продукта, авторе и версии.

   ![обновить расширение vsixmanifest](media/update-extension-vsixmanifest.png)

2. Создайте расширение в режиме **выпуска** . Теперь расширение будет упаковано как VSIX в папку \bin\Release.

3. Чтобы проверить установку, можно дважды щелкнуть VSIX.

### <a name="test-the-extension"></a>Тестирование расширения

 Перед распространением расширения выполните сборку и тестирование, чтобы убедиться, что оно правильно установлено в экспериментальном экземпляре Visual Studio.

1. В Visual Studio запустите отладку. , чтобы открыть экспериментальный экземпляр Visual Studio.

2. В экспериментальном экземпляре перейдите в меню **Сервис** и выберите **расширения и обновления.**... Расширение Тестпублиш должно отображаться в центральной области и быть включено.

3. В меню **Сервис** убедитесь, что вы видите команду test.

### <a name="publish-the-extension-to-the-marketplace-via-command-line"></a>Публикация расширения в Marketplace с помощью командной строки

1. Убедитесь, что вы создали окончательную версию расширения и что она актуальна.

2. Убедитесь, что вы создали publishmanifest.jsдля файлов и overview.md.

3. Откройте командную строку и перейдите в каталог $ {VSInstallDir} \Вссдк\висуалстудиоинтегратион\тулс\бин\.

4. Чтобы создать новый издатель, используйте следующую команду:

   ```
   VsixPublisher.exe createPublisher -publisherName "TestVSIXPublisher" -displayName "Test VSIX Publisher" -personalAccessToken "{Personal Access Token that is used to authenticate the publisher. If not provided, the pat is acquired from the logged-in users.}"
   ```

5. При успешном создании издателя вы увидите следующее сообщение командной строки:

   ```
   Added 'Test VSIX Publisher' as a publisher on the Marketplace.
   ```

6. Новый созданный издатель можно проверить, перейдя к [Visual Studio Marketplace](https://marketplace.visualstudio.com/manage/publishers)

7. Чтобы опубликовать новое расширение, используйте следующую команду:

   ```
   VsixPublisher.exe publish -payload "{Path to vsix file}"  -publishManifest "{path to publishManifest file}"
   ```

8. При успешном создании издателя вы увидите следующее сообщение командной строки:

   ```
   Uploaded 'MyVsixExtension' to the Marketplace.
   ```

9. Вы можете проверить новое опубликованное расширение, перейдя к [Visual Studio Marketplace](https://marketplace.visualstudio.com/)

### <a name="install-the-extension-from-the-visual-studio-marketplace"></a>Установите расширение из Visual Studio Marketplace

Теперь, когда расширение Опубликовано, установите его в Visual Studio и протестируйте его.

1. В Visual Studio в меню **Сервис** выберите **расширения и обновления.**...

2. Щелкните в **сети** и выполните поиск по запросу тестпублиш.

3. Щелкните элемент **Загрузить**. Затем расширение будет запланировано к установке.

4. Чтобы завершить установку, закройте все экземпляры Visual Studio.

## <a name="remove-the-extension"></a>Удаление расширения

Расширение можно удалить из Visual Studio Marketplace и с компьютера.

### <a name="to-remove-the-extension-from-the-marketplace-via-command-line"></a>Удаление расширения из Marketplace с помощью командной строки

1. Если вы хотите удалить расширение, используйте следующую команду:

   ```
   VsixPublisher.exe deleteExtension -publisherName "TestVSIXPublisher" -extensionName "MyVsixExtension"
   ```

2. При успешном удалении расширения вы увидите следующее сообщение командной строки:

   ```
   Removed 'MyVsixExtension' from the Marketplace.
   ```

### <a name="to-remove-the-extension-from-your-computer"></a>Удаление расширения с компьютера

1. В Visual Studio в меню **Сервис** выберите **расширения и обновления**.

2. Выберите "Мивсиксекстенсион" и нажмите кнопку " **Удалить**". После этого расширение будет запланировано к удалению.

3. Чтобы завершить удаление, закройте все экземпляры Visual Studio.
