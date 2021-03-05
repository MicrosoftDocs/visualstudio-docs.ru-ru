---
description: Позволяет пользовательскому интерфейсу Visual Studio отображать текст в разделе "сведения о транспорте" диалогового окна "присоединение к процессу".
title: IDebugPortSupplierDescription2 | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugPortSupplierDescription2 interface
ms.assetid: dd19b9d6-0703-44b3-9498-cedffa0ce5b7
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 8c3cd8d6fbeaf020ea772c9bd5cae783b6e8d127
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102150384"
---
# <a name="idebugportsupplierdescription2"></a>IDebugPortSupplierDescription2
Позволяет [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] пользовательскому интерфейсу отображать текст в разделе **сведения о транспортировке** диалогового окна **Присоединение к процессу** .

## <a name="syntax"></a>Синтаксис

```
IDebugPortSupplierDescription2 : IUnknown
```

## <a name="notes-for-implementers"></a>Примечания для разработчиков
 Этот интерфейс реализуется поставщиками портов.

## <a name="methods"></a>Методы
 В следующей таблице показаны методы `IDebugPortSupplierDescription2` .

|Метод|Описание|
|------------|-----------------|
|[GetDescription](../../../extensibility/debugger/reference/idebugportsupplierdescription2-getdescription.md)|Извлекает метаданные описания и описания для поставщика порта.|

## <a name="requirements"></a>Требования
 Заголовок: Мсдбг. h

 Пространство имен: Microsoft. VisualStudio. Debugger. Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll
