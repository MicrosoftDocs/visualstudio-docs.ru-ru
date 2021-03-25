---
title: Модель языковой службы прежних версий | Документация Майкрософт
description: Используйте эту модель минимальной языковой службы для редактора основных компонентов Visual Studio в качестве руководств по созданию языковой службы.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services, model
ms.assetid: d8ae1c0c-ee3d-4937-a581-ee78d0499793
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 216bfaf9400847c265820e4bb5967fd3c992caa7
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105063229"
---
# <a name="model-of-a-legacy-language-service"></a>Модель языковой службы прежних версий
Языковая служба определяет элементы и функции для конкретного языка и используется для предоставления редактора со сведениями, характерными для этого языка. Например, редактору необходимо получить сведения об элементах и ключевых словах языка для поддержки цветов синтаксиса.

 Языковая служба тесно взаимодействует с текстовым буфером, который управляется редактором, и представлением, содержащим редактор. Параметр **краткие сведения** Microsoft IntelliSense — это пример функции, предоставляемой языковой службой.

## <a name="a-minimal-language-service"></a>Минимальная языковая служба
 Самая базовая языковая служба содержит два следующих объекта:

- *Языковая служба* реализует <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> интерфейс. Языковая служба содержит сведения о языке, включая его имя, расширения имен файлов, диспетчер окон кода и тонированный цвет.

- Он *реализует* <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> интерфейс.

  На следующем концептуальном рисунке показана модель базовой языковой службы.

  ![График модели языковой службы](../../extensibility/media/vslanguageservicemodel.gif "вслангуажесервицемодел") Модель языковой службы Basic

  В окне документа размещается *представление документа* редактора, в данном случае это [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] основной редактор. Представление документа и текстовый буфер принадлежат редактору. Эти объекты работают с [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] помощью специализированного окна документа, называемого *окном кода*. Окно кода содержится в <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> объекте, который создается и управляется интегрированной средой разработки.

  При загрузке файла с заданным расширением редактор находит языковую службу, связанную с этим расширением, и передает ее в окно кода, вызывая <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetCodeWindowManager%2A> метод. Языковая служба возвращает *Диспетчер окон кода*, который реализует <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> интерфейс.

  В следующей таблице приведены общие сведения об объектах в модели.

| Компонент | Объект | Функция |
|------------------| - | - |
| Текстовый буфер | <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> | Поток текста для чтения и записи в Юникоде. В тексте можно использовать другие кодировки. |
| Окно кода | <xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow> | Окно документа, содержащее одно или несколько текстовых представлений. Если [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] находится в режиме многодокументного интерфейса (MDI), окно кода является дочерним ЭЛЕМЕНТОМ MDI. |
| Текстовое представление | <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView> | Окно, позволяющее пользователю перемещаться по тексту и просматривать его с помощью клавиатуры и мыши. Текстовое представление отображается для пользователя в виде редактора. Текстовые представления можно использовать в обычных окнах редактора, в окне вывода и в окне интерпретации. Кроме того, можно настроить одно или несколько текстовых представлений в окне кода. |
| Диспетчер текста | Управляется <xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager> службой, с которой вы получаете <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManager> указатель | Компонент, который поддерживает общие сведения, общие для всех описанных выше компонентов. |
| Языковая служба | Зависит от реализации; внедрен <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> | Объект, предоставляющий редактору сведения о конкретном языке, такие как выделение синтаксиса, завершение операторов и сопоставление фигурных скобок. |

## <a name="see-also"></a>См. также
- [Данные документа и представление документа в специализированных редакторах](../../extensibility/document-data-and-document-view-in-custom-editors.md)
