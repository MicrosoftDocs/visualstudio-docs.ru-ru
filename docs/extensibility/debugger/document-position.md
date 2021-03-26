---
title: Расположение документа | Документация Майкрософт
description: Узнайте, как расположение документа в отладке Visual Studio предоставляет абстракцию расположения в исходном файле, как известно интегрированной среде разработки.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], contexts
ms.assetid: b59d739c-7572-427f-a70d-4e5df63d02c1
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 5d14f9619059735aaecabf72adef248c69ed247e
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105097257"
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
