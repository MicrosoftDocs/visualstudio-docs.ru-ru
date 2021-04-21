---
title: Настройка ленты для Outlook
description: Изучите, что при настройке ленты в Microsoft Office Outlook необходимо учесть, где в приложении будет отображаться настраиваемая лента.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Inspectors [Office development in Visual Studio]
- Outlook [Office development in Visual Studio], Ribbon
- customizing the Ribbon, about customizing the Ribbon
- custom Ribbon, about customizing the Ribbon
- Ribbon [Office development in Visual Studio], Outlook
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: df28de0f8a9497fabecff816c26db7593bf349bd
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/21/2021
ms.locfileid: "107828063"
---
# <a name="customize-a-ribbon-for-outlook"></a>Настройка ленты для Outlook
  При настройке ленты в Microsoft Office Outlook необходимо знать, где в приложении отображается настраиваемая лента. Outlook показывает ленту в пользовательском интерфейсе основного приложения и в окнах, открывающихся при выполнении пользователем определенных задач, таких как создание сообщений электронной почты. Эти окна приложения называются инспекторами.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="add-a-custom-ribbon-to-the-main-application-ui"></a>Добавление настраиваемой ленты в пользовательский интерфейс основного приложения
 Пользовательский интерфейс основного приложения в Outlook называется проводником. Если вы используете элемент **Лента (визуальный конструктор)** , можно добавить ленту в обозреватель, щелкнув свойство **RibbonType** ленты в окне **Свойства** , а затем выбрав **Microsoft. Outlook. Explorer**.

## <a name="assign-a-ribbon-to-an-inspector"></a>Назначение ленты инспектору
 Вы можете указать инспектор, который требуется настроить, выбрав тип ленты, соответствующий классу сообщений для инспектора.

 Если вы используете элемент **Лента (визуальный конструктор)** , щелкните свойство **RibbonType** ленты в окне **Свойства** , а затем выберите один или несколько идентификаторов ленты из списка значений.

 В проект можно добавить несколько лент. Если несколько лент имеют одинаковый идентификатор, переопределите метод `CreateRibbonExtensibilityObject` в классе `ThisAddin` проекта, чтобы указать, какую ленту следует отображать во время выполнения. Дополнительные сведения см. в статье [Общие сведения о ленте](../vsto/ribbon-overview.md). Дополнительные сведения о каждом типе ленты см. в технической статье [Настройка ленты в Outlook 2007](/previous-versions/office/developer/office-2007/bb226712(v=office.12)).

## <a name="specify-the-ribbon-type-by-using-ribbon-xml"></a>Указание типа ленты с помощью XML-ленты
 Если вы используете элемент **Ribbon (XML)** , проверьте значение параметра *ribbonId* в <xref:Microsoft.Office.Core.IRibbonExtensibility.GetCustomUI%2A> методе и верните соответствующую ленту.

 Метод <xref:Microsoft.Office.Core.IRibbonExtensibility.GetCustomUI%2A> автоматически создается средой Visual Studio в файле кода ленты. Параметр *ribbonId* — это строка, идентифицирующая обозреватель или конкретный тип инспектора. Полный список возможных значений параметра *ribbonId* см. в технической статье [Настройка ленты в Outlook 2007](/previous-versions/office/developer/office-2007/bb226712(v=office.12)).

 В следующем примере кода показано, как показывать настраиваемую ленту только в инспекторе `Microsoft.Outlook.Mail.Compose`. Этот инспектор открывается, когда пользователь создает сообщение электронной почты. Отображаемая лента указывается в `GetResourceText()` методе, который создается в классе **ленты** . Дополнительные сведения о классе **Ribbon** см. в разделе [Ribbon XML](../vsto/ribbon-xml.md).

 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_RibbonOutlookBasic/Ribbon1.cs" id="Snippet1":::
 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_RibbonOutlookBasic/Ribbon1.vb" id="Snippet1":::

## <a name="see-also"></a>См. также статью
- [Доступ к ленте во время выполнения](../vsto/accessing-the-ribbon-at-run-time.md)
- [Общие сведения о ленте](../vsto/ribbon-overview.md)
- [Конструктор ленты](../vsto/ribbon-designer.md)
- [Ribbon XML](../vsto/ribbon-xml.md)
