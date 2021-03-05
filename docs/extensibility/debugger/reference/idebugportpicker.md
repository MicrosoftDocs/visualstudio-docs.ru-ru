---
description: Представляет настраиваемый пользовательский интерфейс для выбора порта.
title: Идебугпортпиккер | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugPortPicker interface
ms.assetid: 8b7f6685-a3c5-4355-b706-c1b574f6ff84
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 335a954603505d064f32e8f901ce428d6cb8dfa1
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102142640"
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
