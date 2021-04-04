---
title: Ресурсы в пакетах VSPackage | Документация Майкрософт
description: Узнайте, какие типы локализованных ресурсов можно внедрять в пакеты VSPackage. Вы также можете внедрять ресурсы во встроенные DLL-библиотеки пользовательского интерфейса или управляемые вспомогательные библиотеки DLL.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- managed VSPackages, resources in
- resources, managed VSPackages
- VSPackages, managed resources
ms.assetid: cc8c17a6-b190-4856-b001-0c1104f104b2
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: a80fc4fbfaf9a308492345ba897363d31d4669ca
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/02/2021
ms.locfileid: "106216544"
---
# <a name="resources-in-vspackages"></a>Ресурсы в пакетах VSPackage
Локализованные ресурсы можно внедрять в встроенные библиотеки DLL пользовательского интерфейса, управляемые вспомогательные библиотеки DLL или в самом управляемом пакете VSPackage.

 Некоторые ресурсы не могут быть внедрены в пакеты VSPackage. Можно внедрить следующие управляемые типы:

- Строки

- Ключи загрузки пакета (которые также являются строками)

- Значки окна инструментов

- Скомпилированные файлы вывода командной таблицы (CTO)

- Точечные рисунки CTO

- Справка по командной строке

- О данных диалоговых окон

  Ресурсы в управляемом пакете выбираются по ИДЕНТИФИКАТОРу ресурса. Исключением является файл CTO, который должен иметь имя CTMENU. Файл CTO должен отображаться в таблице ресурсов как `byte[]` . Все остальные элементы ресурсов идентифицируются по типу.

  Чтобы <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute> указать [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , что управляемые ресурсы доступны, можно использовать атрибут.

  :::code language="csharp" source="../../snippets/csharp/VS_Snippets_VSSDK/vssdkresources/cs/vssdkresourcespackage.cs" id="Snippet1":::
  :::code language="vb" source="../../snippets/visualbasic/VS_Snippets_VSSDK/vssdkresources/vb/vssdkresourcespackage.vb" id="Snippet1":::

  <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute>Таким образом, этот параметр указывает, что [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] при поиске ресурсов следует пропускать неуправляемые вспомогательные библиотеки DLL, например с помощью <xref:Microsoft.VisualStudio.Shell.Interop.IVsShell.LoadPackageString%2A> . Если [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] встречает два или больше ресурсов с одинаковым идентификатором ресурса, используется первый найденный ресурс.

## <a name="example"></a>Пример
 В следующем примере представлено управляемое представление значка окна инструментов.

```
<data name="1001"
type="System.Resources.ResXFileRef,System.Windows.Forms">
     <value>
     MyToolWinIcon.bmp;
     System.Drawing.Bitmap,
     System.Drawing,
     Version=1.0.0.0,
     Culture=neutral,
     PublicKeyToken=b03f5f7f11d50a3a
     </value>
</data>
```

 В следующем примере показано, как внедрить массив байтов CTO, который должен иметь имя CTMENU.

```
<data name="CTMENU"
type="System.Resources.ResXFileRef,System.Windows.Forms">
     <value>
     MyPackage.cto;
     System.Byte[],
     mscorlib,
     Version=1.0.0.0,
     Culture=neutral,
     PublicKeyToken=b03f5f7f11d50a3a
     </value>
</data>
```

## <a name="implementation-notes"></a>Примечания по реализации
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] При возможности задерживает загрузку пакетов VSPackage. Следствием внедрения файла CTO в VSPackage является то, что [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] должен загружать все такие пакеты VSPackage в памяти во время установки, то есть при построении Объединенной командной таблицы. Ресурсы можно извлечь из пакета VSPackage, проверив метаданные без выполнения кода в VSPackage. В настоящее время пакет VSPackage не инициализирован, поэтому снижение производительности является минимальным.

 При [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] запросе ресурса из пакета VSPackage после установки этот пакет, скорее всего, уже загружен и инициализирован, поэтому снижение производительности будет минимальным.

## <a name="see-also"></a>См. также раздел
- [Управление пакетами VSPackage](../../extensibility/managing-vspackages.md)
- [Локализованные ресурсы в приложениях MFC: вспомогательные библиотеки DLL](/cpp/build/localized-resources-in-mfc-applications-satellite-dlls)
