---
title: '&lt;&gt;элемент всторунтиме (разработка решений Office в Visual Studio)'
titleSuffix: ''
description: Элемент Всторунтиме пространства имен vstav3 содержит поддерживаемую версию Инструменты Visual Studio для среды выполнения Office для конкретного решения Office.
ms.date: 02/02/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application manifests [Office development in Visual Studio], <vstoRuntime> element
- <vstoRuntime> element
- vstoRuntime element
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 7c856836bd2ba107a2fa6c3017c5ecb2694fcf6b
ms.sourcegitcommit: 8590cf6b3351e82827fd21159beefef0c02bf162
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/08/2021
ms.locfileid: "102468576"
---
# <a name="ltvstoruntimegt-element-office-development-in-visual-studio"></a>&lt;&gt;элемент всторунтиме (разработка решений Office в Visual Studio)
  Элемент `vstoRuntime` пространства имен `vstav3` содержит версию среды выполнения Набора инструментов Visual Studio для Office, поддерживаемую конкретным решением Office.

## <a name="syntax"></a>Синтаксис

```xml
<vstoRuntime
    release
    version
    supportUrl />
```

## <a name="elements-and-attributes"></a>Элементы и атрибуты
 Элемент `vstoRuntime` является обязательным и находится в пространстве имен `vstav3` . Если решение Office поддерживает две версии среды выполнения Набора инструментов Visual Studio для Office, в манифесте приложения будет два элемента `vstoRuntime` .

 Элемент `vstoRuntime` имеет перечисленные ниже атрибуты.

|attribute|Описание|
|---------------|-----------------|
|`release`|Обязательный. Выпускаемая версия среды выполнения Набора инструментов Visual Studio для Office.|
|`version`|Обязательный. Номер версии среды выполнения Набора инструментов Visual Studio для Office.|
|`supportUrl`|Необязательный параметр. Ссылка на расположение установки среды выполнения Набора инструментов Visual Studio для Office.|

 Элемент`vstoRuntime` не содержит элементов.

## <a name="example"></a>Пример
 В приведенном ниже примере кода показан элемент `vstoRuntime` манифеста приложения для решения Office, развертываемого с помощью [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Этот пример кода является частью большого примера, приведенного в разделе [манифесты приложений для решений Office](../vsto/application-manifests-for-office-solutions.md).

```xml
<vstav3:vstoRuntime
    release="VSTOR40Beta1"
    version="10.0.20303"
    supportUrl="http://www.microsoft.com" />
```

## <a name="see-also"></a>См. также раздел

- [Манифесты приложений для решений Office](../vsto/application-manifests-for-office-solutions.md)
- [Манифесты развертывания для решений Office](../vsto/deployment-manifests-for-office-solutions.md)
- [Манифест приложения ClickOnce](../deployment/clickonce-application-manifest.md)
