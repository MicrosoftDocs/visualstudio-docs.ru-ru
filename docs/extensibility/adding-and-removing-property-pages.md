---
title: Добавление и удаление страниц свойств | Документация Майкрософт
description: Узнайте, как добавлять и удалять страницы свойств в конструкторе проектов, которые предоставляют централизованное расположение для управления свойствами проекта в Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- property pages, adding
- property pages, project subtypes
- property pages, removing
ms.assetid: 34853412-ab8a-4caa-9601-7d0727b2985d
author: leslierichardson95
ms.author: lerich
manager: jmartens
dev_langs:
- CSharp
- VB
ms.workload:
- vssdk
ms.openlocfilehash: df8323225074a1644621f9856fdb20a219e2c8e5
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105059994"
---
# <a name="add-and-remove-property-pages"></a>Добавление и удаление страниц свойств

Конструктор проектов предоставляет централизованное расположение для управления свойствами, параметрами и ресурсами проекта в [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] . Он отображается в виде одного окна в [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] интегрированной среде разработки (IDE) и содержит несколько панелей справа, доступ к которым осуществляется через вкладки слева. Панели (часто называемые страницами свойств) в конструкторе проектов зависят от типа и языка проекта. Доступ к конструктору проектов можно получить с помощью команды **Свойства** в меню **проект** .

Подтипу проекта часто требуется отображать дополнительные страницы свойств в конструкторе проектов. Аналогичным образом, некоторые подтипы проектов могут потребовать удаления встроенных страниц свойств. Для этого в подтипе проекта должен быть реализован <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> интерфейс и переопределен <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> метод. Переопределяя этот метод и используя `propId` параметр, содержащий одно из значений <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> перечисления, можно фильтровать, добавлять или удалять свойства проекта. Например, может потребоваться добавить страницу на страницы свойств, зависящие от конфигурации. Для этого необходимо отфильтровать страницы свойств, зависящие от конфигурации, а затем добавить новую страницу в существующий список.

## <a name="add-and-remove-property-pages-in-project-designer"></a>Добавление и удаление страниц свойств в конструкторе проектов

### <a name="remove-a-property-page"></a>Удаление страницы свойств

1. Переопределите `GetProperty(uint itemId, int propId, out object property)` метод, чтобы отфильтровать страницы свойств и получить `clsids` список.

    ```vb
    Protected Overrides int GetProperty(uint itemId, int propId, out object property)
    Protected Overrides Function GetProperty(ByVal itemId As UInteger, ByVal propId As Integer, ByRef [property] As Object) As Integer
        'Use propId to filter configuration-independent property pages.
        Select Case propId
            ....
            Case CInt(Fix(__VSHPROPID2.VSHPROPID_PropertyPagesCLSIDList))
                'Get a semicolon-delimited list of clsids of the configuration-independent property pages
                ErrorHandler.ThrowOnFailure(MyBase.GetProperty(itemId, propId, [property]))
                   Dim propertyPagesList As String = ((String)[property]).ToUpper(CultureInfo.InvariantCulture)
                'Remove the property page here
                   ....
            ....
        End Select
            ....
        Return MyBase.GetProperty(itemId, propId, [property])
    End Function

    ```

    ```csharp
    protected override int GetProperty(uint itemId, int propId, out object property)
    {
        //Use propId to filter configuration-independent property pages.
        switch (propId)
        {
            . . . .

            case (int)__VSHPROPID2.VSHPROPID_PropertyPagesCLSIDList:
                {
                    //Get a semicolon-delimited list of clsids of the configuration-independent property pages
                    ErrorHandler.ThrowOnFailure(base.GetProperty(itemId, propId, out property));
                    string propertyPagesList = ((string)property).ToUpper(CultureInfo.InvariantCulture);
                    //Remove the property page here
                    . . . .
                }
             . . . .
         }
            . . . .
        return base.GetProperty(itemId, propId, out property);
    }
    ```

2. Удаляет страницу « **события сборки** » из `clsids` списка полученных.

    ```vb
    Private buildEventsPageGuid As String = "{1E78F8DB-6C07-4D61-A18F-7514010ABD56}"
    Private index As Integer = propertyPagesList.IndexOf(buildEventsPageGuid)
    If index <> -1 Then
        ' GUIDs are separated by ';' so if you remove the last GUID, also remove the last ';'
        Dim index2 As Integer = index + buildEventsPageGuid.Length + 1
        If index2 >= propertyPagesList.Length Then
            propertyPagesList = propertyPagesList.Substring(0, index).TrimEnd(";"c)
        Else
            propertyPagesList = propertyPagesList.Substring(0, index) + propertyPagesList.Substring(index2)
        End If
    End If
    'New property value
    property = propertyPagesList
    ```

    ```csharp
    string buildEventsPageGuid = "{1E78F8DB-6C07-4D61-A18F-7514010ABD56}";
    int index = propertyPagesList.IndexOf(buildEventsPageGuid);
    if (index != -1)
    {
        // GUIDs are separated by ';' so if you remove the last GUID, also remove the last ';'
        int index2 = index + buildEventsPageGuid.Length + 1;
        if (index2 >= propertyPagesList.Length)
            propertyPagesList = propertyPagesList.Substring(0, index).TrimEnd(';');
        else
            propertyPagesList = propertyPagesList.Substring(0, index) + propertyPagesList.Substring(index2);
    }
    //New property value
    property = propertyPagesList;
    ```

### <a name="add-a-property-page"></a>Добавление страницы свойств

1. Создайте страницу свойств, которую нужно добавить.

    ```vb
    Class DeployPropertyPage
            Inherits Form
            Implements Microsoft.VisualStudio.OLE.Interop.IPropertyPage
        'Summary: Return a stucture describing your property page.
        ....
        Public Sub GetPageInfo(ByVal pPageInfo As Microsoft.VisualStudio.OLE.Interop.PROPPAGEINFO())
            Dim info As PROPPAGEINFO = New PROPPAGEINFO()
            info.cb = CUInt(Marshal.SizeOf(GetType(PROPPAGEINFO)))
            info.dwHelpContext = 0
            info.pszDocString = Nothing
            info.pszHelpFile = Nothing
            info.pszTitle = "Deployment" 'Assign tab name
            info.SIZE.cx = Me.Size.Width
            info.SIZE.cy = Me.Size.Height
            If Not pPageInfo Is Nothing AndAlso pPageInfo.Length > 0 Then
                pPageInfo(0) = info
            End If
        End Sub
    End Class
    ```

    ```csharp
    class DeployPropertyPage : Form, Microsoft.VisualStudio.OLE.Interop.IPropertyPage
    {
        . . . .
        //Summary: Return a stucture describing your property page.
        public void GetPageInfo(Microsoft.VisualStudio.OLE.Interop.PROPPAGEINFO[] pPageInfo)
        {
            PROPPAGEINFO info = new PROPPAGEINFO();
            info.cb = (uint)Marshal.SizeOf(typeof(PROPPAGEINFO));
            info.dwHelpContext = 0;
            info.pszDocString = null;
            info.pszHelpFile = null;
            info.pszTitle = "Deployment";  //Assign tab name
            info.SIZE.cx = this.Size.Width;
            info.SIZE.cy = this.Size.Height;
            if (pPageInfo != null && pPageInfo.Length > 0)
                pPageInfo[0] = info;
        }
    }
    ```

2. Зарегистрируйте новую страницу свойств.

    ```vb
    <MSVSIP.ProvideObject(GetType(DeployPropertyPage), RegisterUsing = RegistrationMethod.CodeBase)>
    ```

    ```csharp
    [MSVSIP.ProvideObject(typeof(DeployPropertyPage), RegisterUsing = RegistrationMethod.CodeBase)]
    ```

3. Переопределите `GetProperty(uint itemId, int propId, out object property)` метод, чтобы отфильтровать страницы свойств, получить `clsids` список и добавить новую страницу свойств.

    ```vb
    Protected Overrides Function GetProperty(ByVal itemId As UInteger, ByVal propId As Integer, ByRef [property] As Object) As Integer
        'Use propId to filter configuration-dependent property pages.
        Select Case propId
            ....
            case CInt(Fix(__VSHPROPID2.VSHPROPID_CfgPropertyPagesCLSIDList)):
                'Get a semicolon-delimited list of clsids of the configuration-dependent property pages.
                ErrorHandler.ThrowOnFailure(MyBase.GetProperty(itemId, propId, [property]))
                'Add the Deployment property page.
                [property] &= ";"c + GetType(DeployPropertyPage).GUID.ToString("B")
        End Select
            ....
            Return MyBase.GetProperty(itemId, propId, [property])
    End Function
    ```

    ```csharp
    protected override int GetProperty(uint itemId, int propId, out object property)
    {
        //Use propId to filter configuration-dependent property pages.
        switch (propId)
        {
            . . . .
            case (int)__VSHPROPID2.VSHPROPID_CfgPropertyPagesCLSIDList:
                {
                    //Get a semicolon-delimited list of clsids of the configuration-dependent property pages.
                    ErrorHandler.ThrowOnFailure(base.GetProperty(itemId, propId, out property));
                    //Add the Deployment property page.
                    property += ';' + typeof(DeployPropertyPage).GUID.ToString("B");
                }
         }
            . . . .
        return base.GetProperty(itemId, propId, out property);
    }
    ```

## <a name="see-also"></a>См. также

- [Подтипы проектов](../extensibility/internals/project-subtypes.md)
