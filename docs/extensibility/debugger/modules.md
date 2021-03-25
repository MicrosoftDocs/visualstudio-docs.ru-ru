---
title: Модули | Документация Майкрософт
description: В этой статье описывается определение и роль модуля в архитектуре отладчика в Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- modules
- debugging [Debugging SDK], modules
ms.assetid: c4cf2809-dbdb-4e75-9273-b3d3d77b67d0
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: f40cb7d0c65822fcb6ba4d4ca0132147f62d9286
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105054768"
---
# <a name="modules"></a>Модули
В плане архитектуры отладчика это *модуль*:

- — Это физический контейнер кода, например исполняемый файл или библиотека DLL.

- Может перезагружать свои символы и описывать саму себя. Описания модулей отображаются в окне Модули интегрированной среды разработки.

- Представляется интерфейсом [IDebugModule2](../../extensibility/debugger/reference/idebugmodule2.md) , созданным модулем отладки для описания модуля.

## <a name="see-also"></a>См. также
- [Основные понятия отладчика](../../extensibility/debugger/debugger-concepts.md)
- [IDebugModule2](../../extensibility/debugger/reference/idebugmodule2.md)
