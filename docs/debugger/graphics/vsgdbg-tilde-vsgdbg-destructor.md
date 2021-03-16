---
description: Уничтожает экземпляр класса VsgDbg.
title: VsgDbg::~VsgDbg (деструктор) | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 7a3b97fb-d344-4df7-b195-9347d1edfcf7
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: d90664723695756ebd8acdc7c56bec1fcbd08a31
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102155230"
---
# <a name="vsgdbgvsgdbg-destructor"></a>VsgDbg::~VsgDbg (деструктор)
Уничтожает экземпляр класса `VsgDbg`. В случае интенсивной записи графических сведений файл журнала графики завершается и закрывается, а ресурсы, которые использовались при активном захвате графических данных, освобождаются.

## <a name="syntax"></a>Синтаксис

```C++
~VsgDbg();
```

## <a name="see-also"></a>См. также
- [VsgDbg::VsgDbg (конструктор)](vsgdbg-vsgdbg-constructor.md)
