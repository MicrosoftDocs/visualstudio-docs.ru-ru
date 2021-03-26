---
title: Поддержка параметров пользователя | Документация Майкрософт
description: Узнайте, как включить сохраняемость категорий параметров с помощью API параметров в пакете SDK для Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Custom Settings Points
- user settings [Visual Studio SDK], registering persistence support
- persistence, registering settings
ms.assetid: ad9beac3-4f8d-4093-ad0e-6fb00444a709
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: e0128ce1f27674010d1b624457815ddb1016e016
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105080649"
---
# <a name="support-for-user-settings"></a>Поддержка параметров пользователя
VSPackage может определять одну или несколько категорий параметров, которые являются группами переменных состояния, которые сохраняются, когда пользователь выбирает команду **Импорт/экспорт параметров** в меню **Сервис** . Чтобы включить эту сохраняемость, используйте API параметров в [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] .

 Запись реестра, называемая пользовательской точкой параметров, а идентификатор GUID, определяет категорию параметров VSPackage. Пакет VSPackage может поддерживать несколько категорий параметров, каждый из которых определяется настраиваемой точкой параметров.

- Реализации параметров, основанных на сборках взаимодействия (с использованием <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings> интерфейса), должны создавать пользовательские точки параметров путем изменения реестра или использования скрипта регистратора (RGS-файла). Для получения дополнительной информации см. [Creating Registrar Scripts](/cpp/atl/creating-registrar-scripts).

- Код, использующий платформу Managed Package Framework (MPF), должен создавать точки настраиваемых параметров, присоединяя <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> к VSPackage для каждой точки настраиваемых параметров.

     Если один пакет VSPackage поддерживает несколько точек настраиваемых параметров, каждая точка настраиваемых параметров реализуется отдельным классом, каждый из которых регистрируется уникальным экземпляром <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> класса. Следовательно, параметры, реализующие класс, могут поддерживать более одной категории параметров.

## <a name="custom-settings-point-registry-entry-details"></a>Сведения о записи реестра для точки пользовательских параметров
 Пользовательские точки параметров создаются в записи реестра в следующем расположении: Хклм\софтваре\микрософт\висуалстудио \\ *\<Version>* \усерсеттингс \\ `<CSPName>` , где `<CSPName>` — это имя настраиваемых параметров, поддерживаемых VSPackage, а *\<Version>* — это версия [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , например 8,0.

> [!NOTE]
> Корневой путь HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\\ *\<Version>* можно переопределить с помощью альтернативного корня при [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] инициализации интегрированной среды разработки (IDE). Дополнительные сведения см. в разделе [Параметры командной строки](../../extensibility/command-line-switches-visual-studio-sdk.md).

 Структура записи реестра показана ниже:

 Хклм\софтваре\микрософт\висуалстудио \\ *\<Version>* \усерсеттингс\

 `<CSPName`>= s "#12345"

 Package = "{XXXXXX XXXX XXXX XXXX XXXXXXXXX}"

 Category = ' {ИИИИИИ гггг гггг гггг ИИИИИИИИИ} '

 Ресаурцепаккаже = ' {ЗЗЗЗЗЗ ZZZZ ZZZZ ZZZZ ЗЗЗЗЗЗЗЗЗ} '

 Алтернатепарент = Категория

| Имя | Type | Данные | Описание |
|-----------------|--------| - | - |
| (по умолчанию) | REG_SZ | Имя точки настраиваемых параметров | Имя ключа, `<CSPName`>, является нелокализованным именем точки настраиваемых параметров.<br /><br /> Для реализаций, основанных на MPF, имя ключа получается путем объединения `categoryName` аргументов и `objectName` <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> конструктора в `categoryName_objectName` .<br /><br /> Ключ может быть пустым или содержать идентификатор ссылки на локализованную строку во вспомогательной библиотеке DLL. Это значение получается из `objectNameResourceID` аргумента в <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> конструктор. |
| Пакет | REG_SZ | Код GUID | Идентификатор пакета VSPackage, который реализует пользовательскую точку параметров.<br /><br /> Реализации, основанные на MPF с помощью <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> класса, используют `objectType` для получения этого значения аргумент конструктора, содержащий VSPackage <xref:System.Type> и Reflection. |
| Категория | REG_SZ | Код GUID | Идентификатор GUID, определяющий категорию параметров.<br /><br /> Для реализаций, основанных на сборках взаимодействия, это значение может быть произвольно выбираемым идентификатором GUID, который [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Среда IDE передает <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings.ExportSettings%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings.ImportSettings%2A> методам и. Все реализации этих двух методов должны проверять свои аргументы GUID.<br /><br /> Для реализаций, основанных на MPF, этот идентификатор GUID получается <xref:System.Type> классом, реализующим [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] механизм параметров. |
| ResourcePackage | REG_SZ | Код GUID | Необязательный параметр.<br /><br /> Путь к вспомогательной библиотеке DLL, содержащей локализованные строки, если реализующий пакет VSPackage не предоставляет их.<br /><br /> MPF использует отражение для получения правильного пакета VSPackage ресурсов, поэтому <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> класс не задает этот аргумент. |
| алтернатепарент | REG_SZ | Имя папки на странице параметров инструментов, содержащей эту точку настраиваемых параметров. | Необязательный параметр.<br /><br /> Это значение необходимо задавать только в том случае, если реализация параметров поддерживает страницы **параметров инструментов** , которые используют механизм сохраняемости в, [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] а не механизм в модели автоматизации для сохранения состояния.<br /><br /> В этих случаях значение в ключе Алтернатепарент является `topic` разделом `topic.sub-topic` строки, используемой для задания конкретной **тулсоптионс** страницы. Например, для страницы **тулсоптионс** `"TextEditor.Basic"` значение алтернатепарент будет `"TextEditor"` .<br /><br /> При <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> создании точки настраиваемых параметров она совпадает с именем категории. |
