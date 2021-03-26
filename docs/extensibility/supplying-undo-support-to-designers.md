---
title: Предоставление поддержки отмены для конструкторов | Документация Майкрософт
description: 'Узнайте, как обеспечить поддержку отмены в конструкторах: автоматически или с помощью функций пакета SDK для Visual Studio.'
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- designers [Visual Studio SDK], undo support
ms.assetid: 43eb1f14-b129-404a-8806-5bf9b099b67b
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 6b56eb762cf4a2746af04ed69c7c4c49afc15dec
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105056315"
---
# <a name="supply-undo-support-to-designers"></a>Предоставление поддержки отмены в конструкторах

Конструкторам, например редакторам, обычно требуется поддержка операций отмены, чтобы пользователи могли обратить свои последние изменения при изменении элемента кода.

Большинство конструкторов, реализованных в Visual Studio, поддерживают "отмену", автоматически предоставляемую средой.

Реализации конструктора, которые должны обеспечивать поддержку функции отмены:

- Обеспечение управления отменой путем реализации абстрактного базового класса <xref:System.ComponentModel.Design.UndoEngine>

- Предоставьте поддержку сохраняемости и CodeDOM, реализовав <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService> классы и  <xref:System.ComponentModel.Design.IComponentChangeService> .

Дополнительные сведения о создании конструкторов с помощью платформа .NET Framework см. в статье [расширение поддержки Design-Time](/previous-versions/37899azc(v=vs.140)).

[!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)]Предоставляет инфраструктуру отмены по умолчанию:

- Предоставление реализации управления отменой с помощью <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit> классов и.

- Предоставление поддержки сохраняемости и CodeDOM с помощью реализаций по умолчанию <xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService> и <xref:System.ComponentModel.Design.IComponentChangeService> .

## <a name="obtain-undo-support-automatically"></a>Получить поддержку отмены автоматически

Любой конструктор, созданный в Visual Studio, имеет автоматическую и полную поддержку отмены, если конструктор:

- Использует <xref:System.Windows.Forms.Control> класс на основе пользовательского интерфейса.

- Использует стандартную систему создания и анализа кода на основе CodeDOM для создания и сохранения кода.

   Дополнительные сведения о работе с поддержкой CodeDOM в Visual Studio см. в разделе [Динамическое создание и компиляция исходного кода](/dotnet/framework/reflection-and-codedom/dynamic-source-code-generation-and-compilation).

## <a name="when-to-use-explicit-designer-undo-support"></a>Когда следует использовать явную поддержку отмены конструктора
 Конструкторы должны предоставлять собственные способы отмены, если они используют графический пользовательский интерфейс, который называется адаптером представления, отличным от интерфейса, предоставленного <xref:System.Windows.Forms.Control> .

 Примером этого может быть создание продукта с помощью веб-интерфейса графического дизайна, а не графического интерфейса на основе платформа .NET Framework.

 В таких случаях необходимо зарегистрировать этот адаптер представления в Visual Studio с помощью <xref:Microsoft.VisualStudio.Shell.Design.ProvideViewAdapterAttribute> и предоставить явное управление отменой.

 Конструкторам необходимо предоставить поддержку CodeDOM и сохраняемости, если они не используют модель создания кода Visual Studio, указанную в <xref:System.CodeDom> пространстве имен.

## <a name="undo-support-features-of-the-designer"></a>Отмена поддержки функций конструктора
 Пакет SDK для среды предоставляет реализации по умолчанию интерфейсов, необходимых для обеспечения поддержки отмены, которые могут использоваться конструкторами, не использующими <xref:System.Windows.Forms.Control> классы на основе для своих пользовательских интерфейсов или стандартных моделей CodeDOM и модели сохраняемости.

 <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine>Класс является производным от класса платформа .NET Framework, <xref:System.ComponentModel.Design.UndoEngine> используя реализацию <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager> класса для управления операциями отмены.

 Visual Studio предоставляет следующие возможности для отмены конструктора:

- Связанные функции отмены в нескольких конструкторах.

- Дочерние элементы в конструкторе могут взаимодействовать с их родителями путем реализации <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoUnit> и <xref:Microsoft.VisualStudio.OLE.Interop.IOleParentUndoUnit> включения <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit> .

Пакет SDK для среды предоставляет поддержку CodeDOM и сохраняемости, предоставляя:

- <xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService> в качестве реализации класса <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService>

- Объект, <xref:System.ComponentModel.Design.IComponentChangeService> предоставляемый узлом разработки Visual Studio.

## <a name="use-the-environment-sdk-features-to-supply-undo-support"></a>Использование функций пакета SDK среды для предоставления поддержки отмены

Чтобы получить поддержку отмены, объект, реализующий конструктор, должен создать и инициализировать экземпляр <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> класса с допустимой <xref:System.IServiceProvider> реализацией. Этот <xref:System.IServiceProvider> класс должен предоставлять следующие службы:

- <xref:System.ComponentModel.Design.IDesignerHost>.

- <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService>

   Конструкторы, использующие сериализацию Visual Studio CodeDOM, могут использовать <xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService> предоставленный в [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] качестве его реализации <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService> .

   В этом случае класс, <xref:System.IServiceProvider> предоставленный <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> конструктору, должен возвращать этот объект как реализацию <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService> класса.

- <xref:System.ComponentModel.Design.IComponentChangeService>

   Конструкторы, использующие по умолчанию, <xref:System.ComponentModel.Design.DesignSurface> предоставляемые узлом разработки Visual Studio, гарантированно используют реализацию класса по умолчанию <xref:System.ComponentModel.Design.IComponentChangeService> .

Конструкторы, реализующие <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> механизм отмены на основе, автоматически отслеживают изменения, если:

- Изменения свойств вносятся через <xref:System.ComponentModel.TypeDescriptor> объект.

- <xref:System.ComponentModel.Design.IComponentChangeService> события создаются вручную при фиксации изменения, которое может быть отменено.

- Изменение в конструкторе было создано в контексте <xref:System.ComponentModel.Design.DesignerTransaction> .

- Конструктор выбирает явное создание блоков отмены с помощью стандартной единицы отмены, предоставляемой реализацией <xref:System.ComponentModel.Design.UndoEngine.UndoUnit> , или реализации, относящейся к Visual Studio <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit> , которая является производной от класса, <xref:System.ComponentModel.Design.UndoEngine.UndoUnit> а также предоставляет реализацию <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoUnit> и <xref:Microsoft.VisualStudio.OLE.Interop.IOleParentUndoUnit> .

## <a name="see-also"></a>См. также

- <xref:System.ComponentModel.Design.UndoEngine>
- <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine>
- [Расширение поддержки Design-Time](/previous-versions/37899azc(v=vs.140))
