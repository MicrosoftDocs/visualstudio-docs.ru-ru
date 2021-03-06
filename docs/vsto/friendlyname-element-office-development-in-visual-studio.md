---
description: Элемент friendlyName пространства имен vstov4 хранит имя, которое отображается в списке установленных программ.
title: '&lt;&gt;элемент friendlyName (разработка решений Office в Visual Studio)'
titleSuffix: ''
ms.custom: seodec18
ms.date: 02/02/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application manifests [Office development in Visual Studio], <friendlyName> element
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: adcf46a2c232176026181283549c0c59fc713603
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102223450"
---
# <a name="ltfriendlynamegt-element-office-development-in-visual-studio"></a>&lt;&gt;элемент friendlyName (разработка решений Office в Visual Studio)
  Элемент `friendlyName` пространства имен `vstov4` хранит имя, которое отображается в списке установленных программ.

## <a name="syntax"></a>Синтаксис

```xml
<friendlyName>
</friendlyName>
```

## <a name="elements-and-attributes"></a>Элементы и атрибуты
 Элемент `friendlyName` находится в пространстве имен `vstov4` . Значение отображается в списке программ, установленных на компьютере, и в диалоговом окне "Надстройки COM VSTO" приложений Microsoft Office.

 У элемента `friendlyName` нет атрибутов и дочерних элементов.

## <a name="vsto-add-in-example"></a>Пример надстройки VSTO

### <a name="description"></a>Описание
 В приведенном ниже примере кода показан элемент `friendlyName` в решении на уровне приложения, которое развертывается с помощью [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Этот пример кода является частью большого примера, приведенного в разделе [манифесты приложений для решений Office](../vsto/application-manifests-for-office-solutions.md).

### <a name="code"></a>Код

```xml
<vstov4:friendlyName>
  ContosoOutlookAddIn
</vstov4:friendlyName>
```

## <a name="see-also"></a>См. также

- [Манифесты приложений для решений Office](../vsto/application-manifests-for-office-solutions.md)
- [Манифесты развертывания для решений Office](../vsto/deployment-manifests-for-office-solutions.md)
- [Манифест приложения ClickOnce](../deployment/clickonce-application-manifest.md)
