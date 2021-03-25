---
title: Регистрация генераторов одного файла | Документация Майкрософт
description: Узнайте, как зарегистрировать пользовательское средство в Visual Studio, чтобы создать его экземпляр и связать его с определенным типом проекта.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- registration, custom tools
- custom tools, defining registry settings
ms.assetid: db7592c0-1273-4843-9617-6e2ddabb6ca8
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: ee110defb06d308c017230a36cebc2b04b3c63b9
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105062685"
---
# <a name="registering-single-file-generators"></a>Регистрация генераторов одного файла
Чтобы сделать пользовательский инструмент доступным в [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , необходимо зарегистрировать его, чтобы он [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] мог создать экземпляр и связать его с определенным типом проекта.

### <a name="to-register-a-custom-tool"></a>Регистрация пользовательского средства

1. Зарегистрируйте библиотеку DLL пользовательских средств либо в [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] локальном реестре, либо в системном реестре в разделе HKEY_CLASSES_ROOT.

    Например, ниже приведены сведения о регистрации для управляемого пользовательского инструмента Мсдатасетженератор, который поставляется вместе с [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] :

   ```
   [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\14.0\CLSID\{E76D53CC-3D4F-40A2-BD4D-4F3419755476}]
   @="COM+ class: Microsoft.VSDesigner.CodeGenerator.TypedDataSourceGenerator.DataSourceGeneratorWrapper"
   "InprocServer32"="C:\\WINDOWS\\system32\\mscoree.dll"
   "ThreadingModel"="Both"
   "Class"="Microsoft.VSDesigner.CodeGenerator.TypedDataSourceGenerator.DataSourceGeneratorWrapper"
   "Assembly"="Microsoft.VSDesigner, Version=14.0.0.0, Culture=Neutral, PublicKeyToken=b03f5f7f11d50a3a"
   ```

2. Создайте раздел реестра в нужном [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] кусте под \\ *идентификатором GUID* генераторов, где *GUID* — это идентификатор GUID, определенный системой или службой проекта конкретного языка. Имя ключа превращается в программное имя пользовательского инструмента. Пользовательский ключ инструмента имеет следующие значения:

   - (по умолчанию)

        Необязательный параметр. Предоставляет понятное описание пользовательского инструмента. Этот параметр является необязательным, но рекомендуется.

   - CLSID

        Обязательный. Задает идентификатор библиотеки классов COM-компонента, реализующего интерфейс <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator> .

   - женератесдесигнтимесаурце

        Обязательный. Указывает, доступны ли типы из файлов, созданных этим пользовательским инструментом, в визуальных конструкторах. Значение этого параметра должно быть (ноль) 0 для типов, недоступных для визуальных конструкторов или (один) 1 для типов, доступных для визуальных конструкторов.

   > [!NOTE]
   > Пользовательское средство необходимо зарегистрировать отдельно для каждого языка, для которого необходимо, чтобы пользовательский инструмент был доступен.

    Например, Мсдатасетженератор регистрируется один раз для каждого языка:

   ```
   [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\14.0\Generators\{164b10b9-b200-11d0-8c61-00a0c91e29d5}\MSDataSetGenerator]
   @="Microsoft VB Code Generator for XSD"
   "CLSID"="{E76D53CC-3D4F-40a2-BD4D-4F3419755476}"
   "GeneratesDesignTimeSource"=dword:00000001

   [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\14.0\Generators\{fae04ec1-301f-11d3-bf4b-00c04f79efbc}\MSDataSetGenerator]
   @="Microsoft C# Code Generator for XSD"
   "CLSID"="{E76D53CC-3D4F-40a2-BD4D-4F3419755476}"
   "GeneratesDesignTimeSource"=dword:00000001
   ```

## <a name="see-also"></a>См. также
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>
- [Реализация генераторов одного файла](../../extensibility/internals/implementing-single-file-generators.md)
- [Предоставление типов конструкторам визуальных элементов](../../extensibility/internals/exposing-types-to-visual-designers.md)
- [Знакомство с объектом BuildManager](/previous-versions/8f9kffa8(v=vs.140))