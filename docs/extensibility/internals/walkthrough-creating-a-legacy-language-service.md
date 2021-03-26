---
title: Пошаговое руководство. Создание языковой службы прежних версий | Документация Майкрософт
description: Узнайте, как использовать языковые классы платформы управляемых пакетов для реализации языковой службы на языке Visual C#.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- language services [managed package framework], creating
ms.assetid: 6a5dd2c2-261b-4efd-a3f4-8fb90b73dc82
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: ded5624aed40ac2e878c44fd8dabc7d35c4d1ac8
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105074279"
---
# <a name="walkthrough-creating-a-legacy-language-service"></a>Пошаговое руководство. Создание языковой службы прежних версий
Использование классов языка Managed Package Framework (MPF) для реализации языковой службы в [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] — это просто. Для размещения языковой службы, самой языковой службы и средства синтаксического анализа для вашего языка требуется пакет VSPackage.

## <a name="prerequisites"></a>Предварительные требования
 Для выполнения этого пошагового руководства необходимо установить пакет SDK для Visual Studio. Дополнительные сведения см. в разделе [пакет SDK для Visual Studio](../../extensibility/visual-studio-sdk.md).

## <a name="locations-for-the-visual-studio-package-project-template"></a>Расположения шаблона проекта пакета Visual Studio
 Шаблон проекта пакета Visual Studio можно найти в трех разных расположениях шаблонов в диалоговом окне **Новый проект** :

1. В разделе Visual Basic, "Расширяемость". Язык проекта по умолчанию — Visual Basic.

2. В разделе Visual C#, "Расширяемость". Язык проекта по умолчанию — C#.

3. В разделе "Другие типы проектов", "Расширяемость". Язык проекта по умолчанию — C++.

### <a name="create-a-vspackage"></a>Создание VSPackage

1. Создайте новый пакет VSPackage с шаблоном проекта пакета Visual Studio.

    Если вы добавляете языковую службу в существующий пакет VSPackage, пропустите следующие шаги и перейдите непосредственно к процедуре "Создание класса языковой службы".

2. Введите Милангуажепаккаже в качестве имени проекта и нажмите кнопку **ОК**.

    Вы можете использовать любое нужное имя. Эти процедуры, описанные здесь, предполагают, что Милангуажепаккаже в качестве имени.

3. Выберите в [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] качестве языка и параметр для создания нового файла ключа. Щелкните **Далее**.

4. Введите соответствующие сведения о компании и пакете. Щелкните **Далее**.

5. Выберите **команду меню**. Щелкните **Далее**.

    Если вы не собираетесь поддерживать фрагменты кода, можно просто нажать кнопку Готово и пропустить следующий шаг.

6. Введите **Вставить фрагмент** в качестве **имени команды** и `cmdidInsertSnippet` для **идентификатора команды**. Нажмите кнопку **Готово**.

    **Имя команды** и **идентификатор команды** могут быть любыми. это просто примеры.

### <a name="create-the-language-service-class"></a>Создание класса языковой службы

1. В **Обозреватель решений** щелкните правой кнопкой мыши проект милангуажепаккаже, выберите **Добавить**, **ссылка**, а затем нажмите кнопку **Добавить новую ссылку** .

2. В диалоговом окне **Добавление ссылки** выберите **Microsoft. VisualStudio. Package. лангуажесервице** на вкладке **.NET** и нажмите кнопку **ОК**.

     Это необходимо сделать только один раз для проекта языкового пакета.

3. В **Обозреватель решений** щелкните правой кнопкой мыши проект VSPackage и выберите **Добавить**, **класс**.

4. Убедитесь, что в списке Шаблоны выбран **класс** .

5. Введите **милангуажесервице. CS** в поле имя файла класса и нажмите кнопку **Добавить**.

     Вы можете использовать любое нужное имя. Эти процедуры предполагаются `MyLanguageService` в качестве имени.

6. В файле Милангуажесервице. cs добавьте следующие `using` директивы.

     [!code-csharp[CreatingALanguageService(ManagedPackageFramework)#1](../../extensibility/internals/codesnippet/CSharp/walkthrough-creating-a-legacy-language-service_1.cs)]
     [!code-vb[CreatingALanguageService(ManagedPackageFramework)#1](../../extensibility/internals/codesnippet/VisualBasic/walkthrough-creating-a-legacy-language-service_1.vb)]

7. Измените `MyLanguageService` класс, производный от <xref:Microsoft.VisualStudio.Package.LanguageService> класса:

     [!code-csharp[CreatingALanguageService(ManagedPackageFramework)#2](../../extensibility/internals/codesnippet/CSharp/walkthrough-creating-a-legacy-language-service_2.cs)]
     [!code-vb[CreatingALanguageService(ManagedPackageFramework)#2](../../extensibility/internals/codesnippet/VisualBasic/walkthrough-creating-a-legacy-language-service_2.vb)]

8. Установите курсор на «Лангуажесервице» и в меню **Правка**, **IntelliSense** выберите **реализовать абстрактный класс**. Это добавляет минимум необходимых методов для реализации класса языковой службы.

9. Реализуйте абстрактные методы, как описано в статье [Реализация устаревшей языковой службы](../../extensibility/internals/implementing-a-legacy-language-service2.md).

### <a name="register-the-language-service"></a>Регистрация языковой службы

1. Откройте файл Милангуажепаккажепаккаже. cs и добавьте следующие `using` директивы:

     [!code-vb[CreatingALanguageService(ManagedPackageFramework)#3](../../extensibility/internals/codesnippet/VisualBasic/walkthrough-creating-a-legacy-language-service_3.vb)]
     [!code-csharp[CreatingALanguageService(ManagedPackageFramework)#3](../../extensibility/internals/codesnippet/CSharp/walkthrough-creating-a-legacy-language-service_3.cs)]

2. Зарегистрируйте свой класс языковой службы, как описано в статье [Регистрация устаревшей языковой службы](../../extensibility/internals/registering-a-legacy-language-service1.md). К ним относятся атрибуты Провидекскс и разделы "Профферинг языковая служба". Используйте Милангуажесервице, где в этом разделе используется Тестлангуажесервице.

### <a name="the-parser-and-scanner"></a>Средство синтаксического анализа и проверки

1. Реализуйте средство синтаксического анализа и сканера для своего языка, как описано в разделе [анализатор и сканер языковой службы прежних версий](../../extensibility/internals/legacy-language-service-parser-and-scanner.md).

     Реализация средства синтаксического анализа и сканера выполняется полностью и выходит за рамки данного раздела.

## <a name="language-service-features"></a>Функции языковой службы
 Для реализации каждой функции языковой службы обычно создается производный класс от соответствующего класса языковой службы MPF, при необходимости реализуется любой абстрактный метод и переопределяются соответствующие методы. Классы, которые создаются и (или) являются производными от, зависят от возможностей, которые вы собираетесь поддерживать. Эти функции подробно рассматриваются в разделе [функции устаревшей языковой службы](../../extensibility/internals/legacy-language-service-features1.md). Следующая процедура является общим подходом к наследованию класса из классов MPF.

#### <a name="deriving-from-an-mpf-class"></a>Наследование от класса MPF

1. В **Обозреватель решений** щелкните правой кнопкой мыши проект VSPackage и выберите **Добавить**, **класс**.

2. Убедитесь, что в списке Шаблоны выбран **класс** .

     Введите подходящее имя для файла класса и нажмите кнопку **Добавить**.

3. Добавьте в новый файл класса следующие `using` директивы.

     [!code-csharp[CreatingALanguageService(ManagedPackageFramework)#4](../../extensibility/internals/codesnippet/CSharp/walkthrough-creating-a-legacy-language-service_4.cs)]
     [!code-vb[CreatingALanguageService(ManagedPackageFramework)#4](../../extensibility/internals/codesnippet/VisualBasic/walkthrough-creating-a-legacy-language-service_4.vb)]

4. Измените класс, производный от нужного класса MPF.

5. Добавьте конструктор класса, принимающий по крайней мере те же параметры, что и конструктор базового класса, и передайте параметры конструктора в конструктор базового класса.

     Например, конструктор для класса, производного от класса, <xref:Microsoft.VisualStudio.Package.Source> может выглядеть следующим образом:

     [!code-csharp[CreatingALanguageService(ManagedPackageFramework)#5](../../extensibility/internals/codesnippet/CSharp/walkthrough-creating-a-legacy-language-service_5.cs)]
     [!code-vb[CreatingALanguageService(ManagedPackageFramework)#5](../../extensibility/internals/codesnippet/VisualBasic/walkthrough-creating-a-legacy-language-service_5.vb)]

6. В меню **Правка**, **IntelliSense** выберите **реализовать абстрактный класс** , если базовый класс содержит любые абстрактные методы, которые должны быть реализованы.

7. В противном случае поместите курсор внутрь класса и введите метод, который необходимо переопределить.

     Например, введите, `public override` чтобы просмотреть список всех методов, которые могут быть переопределены в этом классе.

## <a name="see-also"></a>См. также
- [Реализация языковой службы прежних версий](../../extensibility/internals/implementing-a-legacy-language-service1.md)
