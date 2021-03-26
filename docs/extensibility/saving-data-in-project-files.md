---
title: Сохранение данных в файлах проекта | Документация Майкрософт
description: Сведения о интерфейсах, предоставляемых управляемой платформой пакетов для сохранения и извлечения данных, относящихся к подтипу, в файле проекта.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- data [Visual Studio], saving in project files
- project files
- project files, saving data
ms.assetid: a3d4b15b-a91e-41ba-b235-e62632d11bc5
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 24f3f0b84f22532187537c31ba6e47a823eef8f7
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105060501"
---
# <a name="save-data-in-project-files"></a>Сохранение данных в файлах проекта
Подтип проекта может сохранять и извлекать данные, относящиеся к подтипу, в файле проекта. Платформа управляемого пакета (MPF) предоставляет два интерфейса для выполнения этой задачи:

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage>Интерфейс позволяет получить доступ к значениям свойств из раздела **MSBuild** файла проекта. Методы, предоставляемые, <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage> могут вызываться любым пользователем каждый раз, когда пользователю нужно загружать или сохранять данные, связанные с построением.

- <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment>Используется для сохранения данных, не связанных с построением, в XML-коде свободной формы. Методы, предоставляемые методами, <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> вызываются при [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] каждом [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] необходимости сохранения данных, не связанных с построением, в файле проекта.

  Дополнительные сведения о том, как сохранять данные, связанные с построением и без сборки, см. [в разделе Сохранение данных в файле проекта MSBuild](../extensibility/internals/persisting-data-in-the-msbuild-project-file.md).

## <a name="save-and-retrieve-build-related-data"></a>Сохранение и извлечение данных, связанных с построением

### <a name="to-save-a-build-related-data-in-the-project-file"></a>Сохранение данных, связанных с построением, в файле проекта

- Вызовите <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetPropertyValue%2A> метод, чтобы сохранить полный путь к файлу проекта.

    ```
    private SpecializedProject project;
    IVsBuildPropertyStorage projectStorage = (IVsBuildPropertyStorage)project;
    string newFullPath = GetNewFullPath();
    // Set a full path of the project file.
    ErrorHandler.ThrowOnFailure(projectStorage.SetPropertyValue(
        "MSBuildProjectDirectory",
        String.Empty,
        (uint)_PersistStorageType.PST_PROJECT_FILE, newFullPath));
    ```

### <a name="to-retrieve-build-related-data-from-the-project-file"></a>Извлечение данных, связанных с построением, из файла проекта

- Вызовите <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.GetPropertyValue%2A> метод, чтобы получить полный путь к файлу проекта.

    ```
    private SpecializedProject project;
    IVsBuildPropertyStorage projectStorage = (IVsBuildPropertyStorage)project;
    string fullPath;
    // Get a full path of the project file.
    ErrorHandler.ThrowOnFailure(projectStorage.GetPropertyValue(
        "MSBuildProjectDirectory",
        String.Empty,
        (uint)_PersistStorageType.PST_PROJECT_FILE, out fullPath));
    ```

## <a name="save-and-retrieve-non-build-related-data"></a>Сохранение и извлечение данных, связанных без сборки

### <a name="to-save-non-build-related-data-in-the-project-file"></a>Сохранение данных, не связанных с построением, в файле проекта

1. Реализуйте <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.IsFragmentDirty%2A> метод, чтобы определить, изменился ли XML-фрагмент с момента последнего сохранения в текущий файл.

    ```
    public int IsFragmentDirty(uint storage, out int pfDirty)
    {
        pfDirty = 0;
        switch (storage)
        {
            case (uint)_PersistStorageType.PST_PROJECT_FILE:
            {
                if (isDirty)
                    pfDirty |= 1;
                break;
            }
            case (uint)_PersistStorageType.PST_USER_FILE:
            {
                // We do not store anything in the user file.
                break;
            }
        }

        // Forward the call to inner flavor(s)
        if (pfDirty == 0 && innerCfg != null && this.innerCfg is IPersistXMLFragment)
            return ((IPersistXMLFragment)this.innerCfg).IsFragmentDirty(storage, out pfDirty);

        return VSConstants.S_OK;

    }
    ```

2. Реализуйте <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.Save%2A> метод, чтобы сохранить XML-данные в файле проекта.

    ```
    public int Save(ref Guid guidFlavor, uint storage, out string pbstrXMLFragment, int fClearDirty)
    {
        pbstrXMLFragment = null;

        if (IsMyFlavorGuid(ref guidFlavor))
        {
            switch (storage)
            {
                case (uint)_PersistStorageType.PST_PROJECT_FILE:
                {
                    // Create XML for our data.
                    XmlDocument doc = new XmlDocument();
                    XmlNode root = doc.CreateElement(this.GetType().Name);

                    XmlNode node = doc.CreateElement(targetsTag);
                    node.AppendChild(doc.CreateTextNode(this.TargetsToExecute));
                    root.AppendChild(node);

                    node = doc.CreateElement(updateTargetsTag);
                    node.AppendChild(doc.CreateTextNode(this.UpdateTargetList.ToString()));
                    root.AppendChild(node);

                    doc.AppendChild(root);
                    // Get XML fragment representing our data
                    pbstrXMLFragment = doc.InnerXml;

                    if (fClearDirty != 0)
                        isDirty = false;
                    break;
                }
                case (uint)_PersistStorageType.PST_USER_FILE:
                {
                    // We do not store anything in the user file.
                    break;
                }
            }
        }

        // Forward the call to inner flavor(s)
        if (this.innerCfg != null && this.innerCfg is IPersistXMLFragment)
            return ((IPersistXMLFragment)this.innerCfg).Save(ref guidFlavor, storage, out pbstrXMLFragment, fClearDirty);

        return VSConstants.S_OK;
    }
    ```

### <a name="to-retrieve-non-build-related-data-in-the-project-file"></a>Извлечение данных, не связанных с построением, в файле проекта

1. Реализуйте <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.InitNew%2A> метод для инициализации свойств расширения проекта и других данных, не зависящих от сборки. Этот метод вызывается, если в файле проекта отсутствуют данные конфигурации XML.

    ```
    public int InitNew(ref Guid guidFlavor, uint storage)
    {
        //Return,if it is our guid.
        if (IsMyFlavorGuid(ref guidFlavor))
            return VSConstants.S_OK;

        //Forward the call to inner flavor(s).
        if (this.innerCfg != null && this.innerCfg is IPersistXMLFragment)
            return ((IPersistXMLFragment)this.innerCfg).InitNew(ref guidFlavor, storage);

        return VSConstants.S_OK;
    ```

2. Реализуйте <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.Load%2A> метод для загрузки XML-данных из файла проекта.

    ```
    public int Load(ref Guid guidFlavor, uint storage, string pszXMLFragment)
    {
        if (IsMyFlavorGuid(ref guidFlavor))
        {
            switch (storage)
            {
                case (uint)_PersistStorageType.PST_PROJECT_FILE:
                {
                    // Load our data from the XML fragment.
                    XmlDocument doc = new XmlDocument();
                    XmlNode node = doc.CreateElement(this.GetType().Name);
                    node.InnerXml = pszXMLFragment;
                    if (node == null
                        || node.FirstChild == null
                        || node.FirstChild.ChildNodes.Count == 0
                        || node.FirstChild.ChildNodes[0].Name != targetsTag)
                        break;
                    this.TargetsToExecute = node.FirstChild.ChildNodes[0].InnerText;

                    if (node.FirstChild.ChildNodes.Count <= 1
                        || node.FirstChild.ChildNodes[1].Name != updateTargetsTag)
                        break;
                    this.UpdateTargetList = bool.Parse(node.FirstChild.ChildNodes[1].InnerText);
                    break;
                }
                case (uint)_PersistStorageType.PST_USER_FILE:
                {
                    // We do not store anything in the user file.
                    break;
                }
            }
        }

        // Forward the call to inner flavor(s)
        if (this.innerCfg != null && this.innerCfg is IPersistXMLFragment)
            return ((IPersistXMLFragment)this.innerCfg).Load(ref guidFlavor, storage, pszXMLFragment);

        return VSConstants.S_OK;
    }
    ```

> [!NOTE]
> Все примеры кода, приведенные в этом разделе, являются частями более крупного примера в примерах [VSSDK](https://github.com/Microsoft/VSSDK-Extensibility-Samples).

## <a name="see-also"></a>См. также
- [Сохранение данных в файле проекта MSBuild](../extensibility/internals/persisting-data-in-the-msbuild-project-file.md)
