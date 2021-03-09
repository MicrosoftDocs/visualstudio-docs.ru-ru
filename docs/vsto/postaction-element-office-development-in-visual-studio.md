---
title: '&lt;&gt;элемент «действие» (разработка решений Office в Visual Studio)'
description: Элемент "действие" в пространстве имен vstav3 содержит элементы entryPoint и все элементы Постактиондата, связанные с действиями после развертывания, которые выполняются после установки решений Office.
ms.date: 02/02/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application manifests [Office development in Visual Studio], <postAction> element
- <postAction> element
- postAction element
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 04f8c92c52aeee9f7f1dd5ab67b3dcef3a295474
ms.sourcegitcommit: 8590cf6b3351e82827fd21159beefef0c02bf162
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/08/2021
ms.locfileid: "102470057"
---
# <a name="ltpostactiongt-element-office-development-in-visual-studio"></a>&lt;&gt;элемент «действие» (разработка решений Office в Visual Studio)
  Элемент `postAction` пространства имен `vstav3` содержит элементы `entrypoint` и все элементы `postActionData` , связанные с действиями после развертывания, которые выполняются после установки решений Office.

## <a name="syntax"></a>Синтаксис

```xml
<postAction>
  <entryPoint>
  </entryPoint>
  <postActionData>
  </postActionData>
</postAction>
```

## <a name="elements-and-attributes"></a>Элементы и атрибуты
 Элемент `postAction` является необязательным и находится в пространстве имен `vstav3` . В манифесте приложения определяется один элемент `postAction` для каждого выполняемого после развертывания действия.

 У элемента `postAction` нет атрибутов.

 У элемента`postAction` имеются перечисленные ниже элементы.

### <a name="entrypoint"></a>entryPoint
 Необязательный параметр. Роль `entryPoint` элемента в `vstav3` пространстве имен определяется в [&#60;entrypoint&#62; элемент &#40;разработке решений Office в&#41;Visual Studio ](../vsto/entrypoints-element-office-development-in-visual-studio.md).

### <a name="postactiondata"></a>postActionData
 Необязательный параметр. Роль `postActionData` элемента в `vstav3` пространстве имен определяется в [&#60;постактиондата&#62; элемент &#40;разработке решений Office в&#41;Visual Studio ](../vsto/postactiondata-element-office-development-in-visual-studio.md).

## <a name="post-deployment-action-example"></a>Пример действия, выполняемого после развертывания

### <a name="description"></a>Описание
 В приведенном ниже примере кода показан элемент `postAction` манифеста приложения для решения Office, развертываемого с помощью [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Этот пример кода является частью большого примера, приведенного в разделе [манифесты приложений для решений Office](../vsto/application-manifests-for-office-solutions.md).

### <a name="code"></a>Код

```xml
<vstav3:postAction>
  <vstav3:entryPoint
    class="PostDeploymentAction.PostDeploymentActionSample">
    <assemblyIdentity
      name="PostDeploymentAction"
      version="1.0.0.0"
      language="neutral"
      processorArchitecture="msil" />
  </vstav3:entryPoint>
  <vstav3:postActionData>
  </vstav3:postActionData>
</vstav3:postAction>
```

## <a name="see-also"></a>См. также

- [Манифесты приложений для решений Office](../vsto/application-manifests-for-office-solutions.md)
- [Манифесты развертывания для решений Office](../vsto/deployment-manifests-for-office-solutions.md)
- [Манифест приложения ClickOnce](../deployment/clickonce-application-manifest.md)
