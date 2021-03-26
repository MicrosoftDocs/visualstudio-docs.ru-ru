---
description: Представляет настраиваемый пользовательский интерфейс для выбора порта.
title: Идебугпортпиккер | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugPortPicker interface
ms.assetid: 8b7f6685-a3c5-4355-b706-c1b574f6ff84
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 8390c8a055a9c919bb1a35d8f3288fc810e5329d
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105072251"
---
# <a name="idebugportpicker"></a>IDebugPortPicker
Представляет настраиваемый пользовательский интерфейс для выбора порта.

## <a name="syntax"></a>Синтаксис

```
IDebugPortPicker : IUnknown
```

## <a name="notes-for-implementers"></a>Примечания для разработчиков
 Этот интерфейс реализуется поставщиками портов. Поставщик порта определяет его средство выбора портов, предоставляя его в качестве идентификатора CLSID и указывая `metricPortPickerCLSID` метрику на предоставленном CLSID.

## <a name="methods"></a>Методы
 В следующей таблице показаны методы `IDebugPortPicker` .

|Метод|Описание|
|------------|-----------------|
|[DisplayPortPicker](../../../extensibility/debugger/reference/idebugportpicker-displayportpicker.md)|Отображает указанное диалоговое окно, позволяющее пользователю выбрать порт.|
|[SetSite](../../../extensibility/debugger/reference/idebugportpicker-setsite.md)|Задает поставщик служб.|

## <a name="requirements"></a>Требования
 Заголовок: Мсдбг. h

 Пространство имен: Microsoft. VisualStudio. Debugger. Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll
