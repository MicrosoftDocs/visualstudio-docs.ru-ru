---
title: Настраиваемый пользовательский интерфейс (пакет VSPackage системы управления версиями) | Документация Майкрософт
description: Узнайте, как создать настраиваемый пользовательский интерфейс в Visual Studio с помощью пакета VSPackage системы управления версиями для указания элементов пользовательского интерфейса.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- user interface, source control packages
- source control packages, user interface
ms.assetid: f35ddb24-53bf-461e-b34f-7414f657c082
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 1239b11e814ba08e4e481358f5e7fdd0e5dc666b
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105091036"
---
# <a name="custom-user-interface-source-control-vspackage"></a>Настраиваемый пользовательский интерфейс (пакет VSPackage системы управления версиями)
Пакет VSPackage объявляет свои пункты меню и их состояния по умолчанию через файл таблицы команд Visual Studio (*. vsct*). [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Интегрированная среда разработки (IDE) отображает пункты меню в их состояниях по умолчанию до тех пор, пока не будет загружен пакет VSPackage. Затем <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> метод вызывается для включения или отключения пунктов меню.

 VSPackage может установить раздел реестра, чтобы пакет VSPackage можно было автоматически загрузить в зависимости от контекста пользовательского интерфейса командной строки, хотя обычно пакет VSPackage системы управления версиями должен загружаться по требованию вместо простого переключения на определенный контекст пользовательского интерфейса. Дополнительные сведения о разделе реестра **аутолоадпаккажес** см. в разделе [Управление](../../extensibility/managing-vspackages.md)пакетами VSPackage.

## <a name="vspackage-ui"></a>Пользовательский интерфейс VSPackage
 Пакет системы управления версиями реализуется в виде VSPackage и не использует пользовательский интерфейс из [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . Каждый пакет VSPackage системы управления версиями должен указывать собственные элементы пользовательского интерфейса, такие как пункты меню, группы меню, окна инструментов, панели инструментов и любой необходимый пользовательский интерфейс для настройки параметров, характерных для пакета VSPackage системы управления версиями. Эти элементы пользовательского интерфейса могут быть включены статически или динамически. Статические элементы пользовательского интерфейса определяются в *vsct* -файле и отображаются независимо от того, загружен ли пакет VSPackage. Динамические элементы пользовательского интерфейса могут быть видимы в зависимости от конкретного контекста пользовательского интерфейса команды, например <xref:EnvDTE.Constants.vsContextNoSolution> , или в результате вызова <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> метода. Видимость динамических элементов пользовательского интерфейса соответствует стратегии отложенной загрузки пакетов VSPackage.

## <a name="ui-constraints-on-source-control-vspackages"></a>Ограничения пользовательского интерфейса для пакетов VSPackage системы управления версиями
 Поскольку пакет VSPackage системы управления версиями не может быть удален из IDE после загрузки, VSPackage должен иметь возможность войти в неактивное состояние. Когда VSPackage получает уведомление о том, что оно больше не активно, пакет VSPackage отключает его пользовательский интерфейс и игнорирует любое внешнее взаимодействие интегрированной среды разработки. Реализация <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> метода VSPackage должна скрывать команды, если пакет VSPackage неактивен.

 Каждый пакет VSPackage системы управления версиями должен реализовывать `IVsSccProvider` интерфейс. В пакете <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider.SetActive%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider.SetInactive%2A> VSPackage должны быть реализованы два метода интерфейса и.

 Пакет VSPackage системы управления версиями мог подписываться на различные события IDE, которые реализуются с помощью <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3> , <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2> и т. д. Кроме того, пакет VSPackage может реализовывать интерфейсы обратного вызова с поддержкой реестра, например <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence> . Все эти интерфейсы должны игнорироваться, если они неактивны.

 В следующем списке показаны интерфейсы, затрагиваемые активным состоянием пакета VSPackage системы управления версиями.

- Отслеживание событий документов проекта.

- События решения.

- Интерфейсы сохраняемости решения. В случае неактивности пакеты не должны выполнять запись в файлы *SLN* и *suo* .

- Расширители свойств.

  Обязательные <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2> и и <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2> , а также любые дополнительные интерфейсы, связанные с системой управления версиями, не вызываются, когда пакет VSPackage системы управления версиями неактивен.

  При [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] запуске интегрированной среды разработки [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] устанавливает для контекста пользовательского интерфейса команды идентификатор текущего идентификатора пакета управления версиями по умолчанию. В результате статический пользовательский интерфейс пакета VSPackage активного управления версиями будет отображаться в интегрированной среде разработки без фактической загрузки VSPackage. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] приостанавливает работу пакета VSPackage для регистрации с [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] помощью до <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterScciProvider> того, как он выполняет вызовы VSPackage.

  В следующей таблице приведены конкретные сведения о том, как [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Интегрированная среда разработки скрывает различные элементы пользовательского интерфейса.

| Элемент пользовательского интерфейса | Описание |
| - | - |
| Меню и панели инструментов | Пакет системы управления версиями должен установить состояние видимости исходного меню и панели инструментов в соответствии с ИДЕНТИФИКАТОРом пакета системы управления версиями в разделе [висибилитиконстраинтс](../../extensibility/visibilityconstraints-element.md) файла *vsct* . Это позволяет [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] интегрированной среде разработки устанавливать состояние пунктов меню соответствующим образом, не загружая VSPackage и не вызывая реализацию <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> метода. |
| Окна инструментов | Пакет VSPackage системы управления версиями скрывает все окна инструментов, которыми оно владеет, когда оно становится неактивным. |
| Страницы параметров пакета управления версиями, специфические для пакета VSPackage | Раздел реестра **хклм\софтваре\микрософт\висуалстудио\кс.и\тулсоптионспажес\висибилитикмдуиконтекстс** позволяет пакету VSPackage задать контексты, в которых требуется отобразить страницы параметров. Запись реестра в этом разделе должна быть создана с помощью идентификатора службы (SID) службы управления версиями и присвоения ей значения DWORD, равного 1. При каждом возникновении события пользовательского интерфейса в контексте пакет VSPackage, зарегистрированный в системе управления версиями, будет вызван, если он активен. |

## <a name="see-also"></a>См. также
- <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterScciProvider>
- <xref:EnvDTE.Constants.vsContextNoSolution>
- [Управление пакетами VSPackage](../../extensibility/managing-vspackages.md)
