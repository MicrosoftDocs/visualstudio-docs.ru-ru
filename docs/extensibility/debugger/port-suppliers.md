---
title: Поставщики портов | Документация Майкрософт
description: В этой статье описывается определение и роль поставщика порта в архитектуре отладчика в Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- port suppliers
- debugging [Debugging SDK], port suppliers
ms.assetid: a8f3db96-1a13-4e93-9ef6-0861880369e0
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 7ace9a7072287fa26aee3fa2abd083cc9f7f1314
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105067807"
---
# <a name="port-suppliers"></a>Поставщики портов
В архитектуре отладчика *поставщик порта*:

- Содержится в сервере и предоставляет порты по запросу к этому серверу.

- Может добавлять и удалять порты на содержащем сервере.

- Может перечислить все порты, предоставленные серверу.

- Представляется интерфейсом [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md) , который зарегистрирован в Visual Studio в реестре. Этот интерфейс можно получить, вызвав [жетпортсупплиер](../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md).

  [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] предоставляет поставщик порта по умолчанию и порт по умолчанию. Если необходимо реализовать пользовательский порт, для предоставления этих настраиваемых портов также необходимо реализовать пользовательский порт.

## <a name="see-also"></a>См. также
- [Серверы](../../extensibility/debugger/servers-visual-studio-sdk.md)
- [Порты](../../extensibility/debugger/ports.md)
- [Основные понятия отладчика](../../extensibility/debugger/debugger-concepts.md)
- [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md)
- [GetPortSupplier](../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md)
