---
description: Элемент ADDIN пространства имен vstav3 содержит сведения, относящиеся к Microsoft Office надстройкам VSTO и настройкам на уровне документа, разработанным с помощью Visual Studio.
title: '&lt;&gt;элемент ADDIN (разработка решений Office в Visual Studio)'
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application manifests [Office development in Visual Studio], <addIn> element
- addin element
- <addin> element
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 4cfc59475b01fbf42c387b4a7a5ca533b313a322
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102227389"
---
# <a name="ltaddingt-element-office-development-in-visual-studio"></a>&lt;&gt;элемент ADDIN (разработка решений Office в Visual Studio)
  Элемент **ADDIN** `vstav3` пространства имен содержит сведения, относящиеся к Microsoft Office надстройкам VSTO и настройкам на уровне документа, разработанным с помощью Visual Studio.

## <a name="syntax"></a>Синтаксис

```xml
<addIn>
  <entryPointsCollection>
    <entryPoints>
      <entryPoint>
      </entryPoint>
    </entryPoints>
  </entryPointsCollection>
  <update></update>
  <postActions>
    <postAction>
      <postActionData>
      </postActionData>
    <postAction>
  </postActions>
  <application>
    <customization>
    </customization>
  </application
</addIn>
```

## <a name="elements-and-attributes"></a>Элементы и атрибуты
 Элемент **ADDIN** `vstav3` пространства имен содержит сведения о решении Office и приложении Microsoft Office. Этот элемент должен принадлежать следующему пространству имен: `vstav3=urn:schemas-microsoft-com:vsta.v3`. Дочерние элементы также необходимо включить в это пространство имен.

 У элемента `addin` нет атрибутов.

 Элемент `addin` имеет указанные ниже дочерние элементы.

### <a name="entrypoints"></a>entryPoints
 Обязательный. Элемент **EntryPoint** описан в разделе [&#60;entrypoint&#62; элемента &#40;разработке решений Office в Visual Studio&#41;](../vsto/entrypoints-element-office-development-in-visual-studio.md).

### <a name="update"></a>обновить
 Обязательный. Элемент **Update** описан в разделе [&#60;обновление&#62; элемента &#40;разработке решений Office в&#41;Visual Studio](../vsto/update-element-office-development-in-visual-studio.md).

### <a name="postactions"></a>postActions
 Необязательный параметр. Элемент « **действия** » описан в разделе [&#60;действия&#62; элемента &#40;разработке решений Office в Visual Studio&#41;](../vsto/postactions-element-office-development-in-visual-studio.md).

### <a name="application"></a>application
 Обязательный. Элемент **Application** описывается в [&#60;&#62; приложений &#40;разработки Office в Visual Studio&#41;](../vsto/application-element-office-development-in-visual-studio.md).

## <a name="document-level-customization-example"></a>Пример настройки на уровне документа

### <a name="description"></a>Описание
 В следующем примере кода показан элемент **ADDIN** в решении Office уровня документа, которое развертывается с помощью [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] . Этот пример кода является частью большого примера, приведенного в разделе [манифесты приложений для решений Office](../vsto/application-manifests-for-office-solutions.md).

### <a name="code"></a>Код

```xml
<vstav3:addIn
  xmlns:vstav3="urn:schemas-microsoft-com:vsta.v3">
  <vstav3:entryPointsCollection>
    <vstav3:entryPoints>
      <vstav3:entryPoint
        class="ContosoExcelWorkbook.ThisWorkbook">
        <assemblyIdentity
          name="ContosoExcelWorkbook"
          version="1.0.0.0"
          language="neutral"
          processorArchitecture="msil" />
      </vstav3:entryPoint>
      <vstav3:entryPoint
        class="ContosoExcelWorkbook.Sheet1">
        <assemblyIdentity
          name="ContosoExcelWorkbook"
          version="1.0.0.0"
          language="neutral"
          processorArchitecture="msil" />
      </vstav3:entryPoint>
      <vstav3:entryPoint
        class="ContosoExcelWorkbook.Sheet2">
        <assemblyIdentity
          name="ContosoExcelWorkbook"
          version="1.0.0.0"
          language="neutral"
          processorArchitecture="msil" />
      </vstav3:entryPoint>
      <vstav3:entryPoint
        class="ContosoExcelWorkbook.Sheet3">
        <assemblyIdentity
          name="ContosoExcelWorkbook"
          version="1.0.0.0"
          language="neutral"
          processorArchitecture="msil" />
      </vstav3:entryPoint>
    </vstav3:entryPoints>
  </vstav3:entryPointsCollection>
  <vstav3:update
    enabled="true">
    <vstav3:expiration
      maximumAge="7"
      unit="days" />
  </vstav3:update>
  <vstav3:application>
    <vstov4:customizations
      xmlns:vstov4="urn:schemas-microsoft-com:vsto.v4">
      <vstov4:customization>
        <vstov4:document
          solutionId="73e" />
      </vstov4:customization>
    </vstov4:customizations>
  </vstav3:application>
</vstav3:addIn>
```

## <a name="vsto-add-in-example"></a>Пример надстройки VSTO

### <a name="description"></a>Описание
 В следующем примере кода показан элемент **ADDIN** в решении Office уровня приложения, которое развертывается с помощью [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] . Этот пример кода является частью большого примера, приведенного в разделе [манифесты приложений для решений Office](../vsto/application-manifests-for-office-solutions.md).

### <a name="code"></a>Код

```xml
<vstav3:addIn
  xmlns:vstav3="urn:schemas-microsoft-com:vsta.v3">
  <vstav3:entryPointsCollection>
    <vstav3:entryPoints>
      <vstav3:entryPoint
        class="ContosoOutlookAddIn.ThisAddIn">
        <assemblyIdentity
          name="ContosoOutlookAddIn"
          version="1.0.0.0"
          language="neutral"
          processorArchitecture="msil" />
      </vstav3:entryPoint>
    </vstav3:entryPoints>
  </vstav3:entryPointsCollection>
  <vstav3:update
    enabled="true">
    <vstav3:expiration
      maximumAge="7"
      unit="days" />
  </vstav3:update>
  <vstav3:application>
    <vstov4:customizations
      xmlns:vstov4="urn:schemas-microsoft-com:vsto.v4">
      <vstov4:customization>
        <vstov4:appAddIn
          application="Outlook"
          loadBehavior="3"
          keyName="ContosoOutlookAddIn">
          <vstov4:friendlyName>
            ContosoOutlookAddIn
          </vstov4:friendlyName>
          <vstov4:description>
            ContosoOutlookAddIn - Outlook VSTO Add-in
            created with Visual Studio Tools for Office
          </vstov4:description>
          <vstov4:formRegions>
            <vstov4:formRegion
                name="OutlookAddIn1.FormRegion1">
              <vstov4:messageClass name="IPM.Note" />
              <vstov4:messageClass name="IPM.Contact" />
              <vstov4:messageClass name="IPM.Appointment" />
            </vstov4:formRegion>
          </vstov4:formRegions>
        </vstov4:appAddIn>
      </vstov4:customization>
    </vstov4:customizations>
  </vstav3:application>
</vstav3:addIn>
```

## <a name="see-also"></a>См. также

- [Манифесты приложений для решений Office](../vsto/application-manifests-for-office-solutions.md)
- [Манифесты развертывания для решений Office](../vsto/deployment-manifests-for-office-solutions.md)
- [Манифест приложения ClickOnce](../deployment/clickonce-application-manifest.md)
