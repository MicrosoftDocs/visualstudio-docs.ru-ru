---
description: Представляет контрольную сумму для документа отладки и позволяет передавать контрольную сумму между компонентами.
title: IDebugDocumentChecksum2 | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugDocumentChecksum2 interface
ms.assetid: 6d22fa94-21aa-46cb-b5b5-32a6399ebb20
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 518e5b089d0d34e2492297b27dd0829e5f00ef2f
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105066741"
---
# <a name="idebugdocumentchecksum2"></a>IDebugDocumentChecksum2
Представляет контрольную сумму для документа отладки и позволяет передавать контрольную сумму между компонентами.

## <a name="syntax"></a>Синтаксис

```
IDebugDocumentChecksum2 : IUnknown
```

## <a name="notes-for-implementers"></a>Примечания для разработчиков
 Этот интерфейс может быть реализован любым компонентом, предоставляющим интерфейс [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) . Однако он реализуется механизмами отладки, чтобы контрольная сумма, внедренная в файл символов (*. pdb), могла быть передана обратно в интегрированную среду разработки и использована при поиске источника.

## <a name="methods"></a>Методы
 В следующей таблице показаны методы `IDebugDocumentChecksum2` .

|Метод|Описание|
|------------|-----------------|
|[GetChecksumAndAlgorithmId](../../../extensibility/debugger/reference/idebugdocumentchecksum2-getchecksumandalgorithmid.md)|Извлекает контрольную сумму документа и идентификатор алгоритма с учетом максимального числа используемых байтов.|

## <a name="requirements"></a>Требования
 Заголовок: Мсдбг. h

 Пространство имен: Microsoft. VisualStudio. Debugger. Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll
