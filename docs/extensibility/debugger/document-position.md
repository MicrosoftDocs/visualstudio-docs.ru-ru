---
title: Расположение документа | Документация Майкрософт
description: Узнайте, как расположение документа в отладке Visual Studio предоставляет абстракцию расположения в исходном файле, как известно интегрированной среде разработки.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- debugging [Debugging SDK], contexts
ms.assetid: b59d739c-7572-427f-a70d-4e5df63d02c1
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 58a3ac3db62619c5d0eaa9e89e09d7d5def06ff1
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/25/2021
ms.locfileid: "112898166"
---
# <a name="document-position"></a>Расположение документа
В [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] отладке, *расположение документа*:

- Предоставляет абстракцию расположения в исходном файле, как известно интегрированной среде разработки. В настоящее время для большинства языков расположение документа можно рассматривать как расположение в исходном файле.

- Описывает расположение в исходном документе для модуля отладки.

- Реализуется с помощью интерфейса [IDebugDocumentPosition2](../../extensibility/debugger/reference/idebugdocumentposition2.md) .

## <a name="see-also"></a>См. также
- [Контекст кода](../../extensibility/debugger/code-context.md)
- [Контекст документа](../../extensibility/debugger/document-context.md)
- [Поставщик символов](../../extensibility/debugger/symbol-provider.md)
- [Интерфейсы поставщика символов](../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [Контексты отладчика](../../extensibility/debugger/debugger-contexts.md)
