---
title: Xamarin
description: 'Использование Xamarin в Visual Studio для Mac позволяет создавать кроссплатформенные приложения, предназначенные для iOS, Mac, Android, tvOS и watchOS '
author: heiligerdankgesang
ms.author: dominicn
ms.date: 02/12/2019
ms.assetid: 339F6051-5F90-48DC-8237-EBBC8A03A32B
ms.topic: overview
ms.openlocfilehash: e5d03c27ef1e6fefc2fa29d60727851be0954d8b
ms.sourcegitcommit: 08ee19f260164271e18bdbafe624301508f554ce
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/24/2021
ms.locfileid: "104999606"
---
# <a name="xamarin-mobile-app-development"></a>Разработка мобильных приложений Xamarin

Первоклассная поддержка [Xamarin](/xamarin) позволяет разрабатывать эффективные собственные интерфейсы для Android, macOS, iOS, tvOS и watchOS. Кроссплатформенные приложения Xamarin.Forms позволяют использовать код пользовательского интерфейса на основе XAML в Android, iOS и macOS без ограничения доступ к встроенной функциональности.

## <a name="android"></a>Android

Visual Studio для Mac имеет собственный диспетчер пакета SDK для Android, предоставляя вам доступ к необходимому SDK для приложения.

Visual Studio для Mac включает собственный конструктор для приложений Android, который работает с файлами `.axml` из Android и поддерживает визуальное создание пользовательских интерфейсов. Visual Studio для Mac открывает эти файлы в Android Designer, как показано на следующем рисунке:

![Конструктор пользовательского интерфейса Android](media/intro-image31.png)

См. [обзор Xamarin.Android Designer](/xamarin/android/user-interface/android-designer/index) для получения дополнительных сведений.

## <a name="ios"></a>iOS

Конструктор iOS полностью интегрирован с Visual Studio для Mac и позволяет визуально редактировать XIB-файлы и файлы раскадровки для создания пользовательских интерфейсов и переходов iOS, tvOS и WatchOS. Весь пользовательский интерфейс можно создавать с помощью перетаскивания между панелью элементов и областью конструктора; при этом предлагается интуитивный подход к обработке событий. Конструктор iOS также поддерживает [пользовательские элементы управления](/xamarin/ios/user-interface/designer/ios-designable-controls-overview) с возможностью их отрисовки во время разработки.

![Конструктор раскадровки iOS](media/intro-image30.png)

Дополнительные сведения об использовании конструктора iOS см. в руководствах по [конструктору](/xamarin/ios/user-interface/designer/?tabs=macos).

### <a name="mac"></a>Mac

Xamarin включает собственные привязки к API для Mac, позволяющие создавать эффектно выглядящие Mac-приложения.

Дополнительные сведения о написании приложений Mac с помощью Visual Studio для Mac см. в руководствах по [Xamarin.Mac](/xamarin/mac/get-started/index).

## <a name="xamarin-enterprise-features"></a>Функции Xamarin Enterprise

> [!Note]
> Эти продукты можно использовать только с подпиской Visual Studio Enterprise.

### <a name="profiler"></a>профилировщик

В Xamarin Profiler доступно три инструмента для профилирования. В руководстве [Introduction to the Xamarin Profiler](/xamarin/tools/profiler/index?tabs=macos) (Знакомство с Xamarin Profiler) рассказывается, что измеряют эти инструменты и как они анализируют приложение, а также поясняется значение данных, представленных на каждом экране.

### <a name="inspector"></a>Inspector

Xamarin Inspector предлагает интерактивную консоль C# с пользовательскими инструментами. Ее можно использовать в отладке и диагностике работающих приложений, в качестве средства обучения, инструмента для создания документации и для экспериментов.

![Xamarin Inspector](media/intro-inspector.png)

Это полнофункциональная консоль C#, которая представляет собой автономное приложение для программирования под различные платформы (Android, iOS, Mac и Windows) и интегрируется с рабочим процессом отладки вашей IDE.

Дополнительные сведения см. в руководстве по [Xamarin Inspector](/xamarin/tools/inspector/release-notes/1.5).
