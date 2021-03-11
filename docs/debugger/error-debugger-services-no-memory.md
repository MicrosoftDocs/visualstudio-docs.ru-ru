---
description: Службам отладки не хватило памяти, что привело к завершению сеанса отладки.
title: Службам отладки недостаточно памяти | Документация Майкрософт
ms.date: 07/10/2019
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.debug_no_memory
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugger
author: isadorasophia
ms.author: isgarcia
manager: caslan
ms.workload:
- multiple
ms.openlocfilehash: d881248652d644e9a82725b0d083d095ff72f885
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102147046"
---
# <a name="debugger-services-running-out-of-memory"></a>Службам отладки недостаточно памяти
Службам отладки не хватило памяти, что привело к завершению сеанса отладки.

## <a name="to-investigate-this-error-on-windows"></a>Анализ этой ошибки в Windows
- Чтобы определить, наблюдается ли резкое увеличение потребления памяти в целевом приложении, можно проверить график памяти процесса в окне **Средства диагностики**. Если это так, используйте средство **Использование памяти** для диагностики базовой проблемы. См. раздел об [анализе использования памяти](../profiling/memory-usage.md).

- Если целевое приложение не потребляет много памяти, используйте окно **Диспетчер задач** для получения сведений об использовании памяти в Visual Studio (процесс devenv.exe), рабочем процессе (msvsmon.exe) или VS Code (vsdbg.exe или vsdbg-ui.exe), чтобы определить, связана ли проблема с отладчиком. Если процесс, которому не хватает памяти, — devenv.exe, попробуйте сократить количество запущенных расширений Visual Studio.

## <a name="see-also"></a>См. также
- [Запись блога. Анализ ресурсов ЦП и памяти во время отладки](https://devblogs.microsoft.com/visualstudio/analyze-cpu-memory-while-debugging/)
- [Управление памятью](/windows/win32/memory/about-memory-management)
