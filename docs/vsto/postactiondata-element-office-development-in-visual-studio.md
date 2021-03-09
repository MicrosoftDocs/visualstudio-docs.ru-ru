---
title: '&lt;&gt;элемент постактиондата (разработка решений Office)'
description: Элемент Постактиондата пространства имен vstav3 указывает данные, связанные с любым действием после развертывания, которое выполняется после установки решений Office.
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- <postActionData> element
- application manifests [Office development in Visual Studio], <postActionData> element
- postActionData element
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: a75f61c6d1f80a127f49d96c4e3f4910c66dd8aa
ms.sourcegitcommit: 8590cf6b3351e82827fd21159beefef0c02bf162
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/08/2021
ms.locfileid: "102470070"
---
# <a name="ltpostactiondatagt-element-office-development"></a>&lt;&gt;элемент постактиондата (разработка решений Office)
  Элемент `postActionData` пространства имен `vstav3` указывает данные, связанные с действиями, выполняемыми после развертывания при установке решений Office.

## <a name="syntax"></a>Синтаксис

```xml
<postActionData>
</postActionData>
```

## <a name="elements-and-attributes"></a>Элементы и атрибуты
 Элемент `postActionData` является необязательным и находится в пространстве имен `vstav3` . В манифесте приложения определяется один элемент `postActionData` для каждого выполняемого после развертывания действия.

 У элемента `postActions` нет атрибутов.

 У элемента`postActions` нет дочерних элементов.

## <a name="post-deployment-action-example"></a>Пример действия, выполняемого после развертывания

### <a name="description"></a>Описание
 В приведенном ниже примере кода показан элемент `postAction` манифеста приложения для решения Office, развертываемого с помощью [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Этот пример кода является частью большого примера, приведенного в разделе [манифесты приложений для решений Office](../vsto/application-manifests-for-office-solutions.md).

### <a name="code"></a>Код

```xml
<vstav3:postActionData>
  data in any format
</vstav3:postActionData>
```

## <a name="see-also"></a>См. также

- [Манифесты приложений для решений Office](../vsto/application-manifests-for-office-solutions.md)
- [Манифесты развертывания для решений Office](../vsto/deployment-manifests-for-office-solutions.md)
- [Манифест приложения ClickOnce](../deployment/clickonce-application-manifest.md)
