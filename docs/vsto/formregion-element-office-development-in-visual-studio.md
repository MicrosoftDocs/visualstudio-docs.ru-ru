---
title: '&lt;&gt;элемент формрегион (разработка решений Office в Visual Studio)'
titleSuffix: ''
ms.custom: seodec18
ms.date: 02/02/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application manifests [Office development in Visual Studio], <formRegion> element
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 469b041ac879753e5fe4be0f9bd739be1030a942
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99970395"
---
# <a name="ltformregiongt-element-office-development-in-visual-studio"></a>&lt;&gt;элемент формрегион (разработка решений Office в Visual Studio)
  `formRegion`Элемент `vstov4` пространства имен определяет Microsoft Office область формы Outlook, связанную с надстройкой VSTO.

## <a name="syntax"></a>Синтаксис

```xml
<formRegion
  name>
  <messageClass
    name/>
</formRegion>
```

## <a name="elements-and-attributes"></a>Элементы и атрибуты
 Элемент `formRegion` пространства имен `vstov4` определяет область формы, связанную с надстройкой VSTO для Outlook. Этот элемент является обязательным только для надстроек VSTO для Outlook, в которых есть области форм.

 Для одной и той же надстройки VSTO можно определить несколько элементов `formRegion` в рамках элемента `formRegions` .

 Элемент `formRegion` имеет указанный ниже атрибут.

|Атрибут|Описание|
|---------------|-----------------|
|`name`|Обязательный элемент. Определяет имя области формы.|

 Элемент `formRegion` имеет указанные ниже дочерние элементы.

### <a name="messageclass"></a>messageClass
 Элемент `messageClass` определяет форму Outlook, которая связана с областью формы.

 Элемент `messageClass` имеет указанный ниже атрибут.

|Атрибут|Описание|
|---------------|-----------------|
|`name`|Обязательный элемент. Определяет форму, которая связана с областью формы.|

## <a name="example"></a>Пример
 В приведенном ниже примере кода показан элемент `formRegion` манифеста приложения для надстройки VSTO для Outlook, развертываемой с помощью [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Имеется три класса сообщений, связанных с одной и той же областью формы. Этот пример кода является частью большого примера, приведенного в разделе [манифесты приложений для решений Office](../vsto/application-manifests-for-office-solutions.md).

```xml
<vstov4:formRegion
    name="OutlookAddIn1.FormRegion1">
  <vstov4:messageClass name="IPM.Note" />
  <vstov4:messageClass name="IPM.Contact" />
  <vstov4:messageClass name="IPM.Appointment" />
</vstov4:formRegion>
```

## <a name="see-also"></a>См. также раздел

- [Создание областей формы Outlook](../vsto/creating-outlook-form-regions.md)
- [Манифесты приложений для решений Office](../vsto/application-manifests-for-office-solutions.md)
- [Манифесты развертывания для решений Office](../vsto/deployment-manifests-for-office-solutions.md)
- [Манифест приложения ClickOnce](../deployment/clickonce-application-manifest.md)