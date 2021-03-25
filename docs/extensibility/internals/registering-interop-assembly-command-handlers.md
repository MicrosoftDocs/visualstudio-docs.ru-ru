---
title: Регистрация обработчиков команд сборки взаимодействия | Документация Майкрософт
description: Сведения о базовом контракте команды, используемом всеми пакетами VSPackage для реализации команд с помощью сборок взаимодействия.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- interop assemblies, command handlers
- command handling with interop assemblies, registering
ms.assetid: 303cd399-e29d-4ea1-8abe-5e0b59c12a0c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 641a21658e490f94a27cbd9120d044539a7ec284
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105062763"
---
# <a name="registering-interop-assembly-command-handlers"></a>Регистрация обработчиков команд сборки взаимодействия
Пакет VSPackage должен быть зарегистрирован в [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , чтобы интегрированная среда разработки (IDE) правильно маршрутизирует свои команды.

 Реестр можно обновить либо вручную, либо с помощью файла регистратора (RGS). Для получения дополнительной информации см. [Creating Registrar Scripts](/cpp/atl/creating-registrar-scripts).

 Платформа управляемого пакета (MPF) предоставляет эту функцию через <xref:Microsoft.VisualStudio.Shell.ProvideMenuResourceAttribute> класс.

- [Справочные ресурсы по формату командной таблицы](/previous-versions/bb164647(v=vs.100)) находятся в неуправляемых библиотеках DLL ВСПОМОГАТЕЛЬных интерфейсов.

## <a name="command-handler-registration-of-a-vspackage"></a>Регистрация пакета VSPackage в обработчике команд
 Пакет VSPackage, выступающий в качестве обработчика для команд на основе ПОЛЬЗОВАТЕЛЬСКОГО интерфейса, требует наличия записи реестра с именем после пакета VSPackage `GUID` . Эта запись реестра указывает расположение файла ресурсов пользовательского интерфейса VSPackage и ресурс меню в этом файле. Сама запись реестра находится в разделе HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\\ *\<Version>* \менус, где *\<Version>* — это версия, например [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 9,0.

> [!NOTE]
> Корневой путь HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\\ *\<Version>* можно переопределить с помощью альтернативного корня при [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] инициализации оболочки. Дополнительные сведения о корневом пути см. в разделе [Установка пакетов VSPackage с помощью установщик Windows](../../extensibility/internals/installing-vspackages-with-windows-installer.md).

### <a name="the-ctmenu-resource-registry-entry"></a>Запись реестра ресурсов CTMENU
 Структура записи реестра:

```
HKEY_LOCAL_MACHINE\Software\VisualStudio\<Version>\
  Menus\
    <GUID> = <Resource Information>
```

 \<*GUID*> — Это пакет `GUID` VSPackage в форме {XXXXXX-XXXX-XXXX-XXXX-XXXXXXXXX}.

 *\<Resource Information>* состоит из трех элементов, разделенных запятыми. Эти элементы по порядку:

 \<*Path to Resource DLL*>, \<*Menu Resource ID*>, \<*Menu Version*>

 В следующей таблице описаны поля \<*Resource Information*> .

| Элемент | Описание |
|---------------------------| - |
| \<*Path to Resource DLL*> | Это полный путь к библиотеке DLL ресурсов, содержащей ресурс меню, или оставить это поле пустым, указывая на необходимость использования библиотеки DLL ресурсов VSPackage (как указано в подразделе Packages, где зарегистрирован пакет VSPackage).<br /><br /> Это поле остается незаполненным. |
| \<*Menu Resource ID*> | Это идентификатор ресурса `CTMENU` , который содержит все элементы пользовательского интерфейса для VSPackage, скомпилированные из [vsct](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md) -файла. |
| \<*Menu Version*> | Это число, используемое в качестве версии `CTMENU` ресурса. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] использует это значение для определения необходимости повторного слияния содержимого `CTMENU` ресурса со своим кэшем всех `CTMENU` ресурсов. Повторная слияние запускается при помощи команды установки devenv.<br /><br /> Изначально это значение должно быть равно 1 и увеличиваться после каждого изменения в `CTMENU` ресурсе и перед повторным слиянием. |

### <a name="example"></a>Пример
 Ниже приведен пример нескольких записей ресурсов:

```
HKEY_LOCAL_MACHINE\Software\VisualStudio\9.0Exp\
  Menus\
    {019971D6-4685-11D2-B48A-0000F87572EB} = ,1, 10
    {1b027a40-8f43-11d0-8d11-00a0c91bc942} = , 10211, 3
```

## <a name="see-also"></a>См. также
- [Как добавить элементы пользовательского интерфейса с помощью пакетов VSPackage](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Команды и меню, которые используют сборки взаимодействия](../../extensibility/internals/commands-and-menus-that-use-interop-assemblies.md)