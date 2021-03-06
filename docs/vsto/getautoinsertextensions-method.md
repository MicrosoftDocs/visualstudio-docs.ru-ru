---
description: Возвращает сведения о приложениях для Office, которые будут автоматически вставляться во время отладки.
title: Метод GetAutoInsertExtensions
ms.date: 02/02/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: c4a49942f50a79db604d2363cf2d85762c5ddce5
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102223437"
---
# <a name="getautoinsertextensions-method"></a>Метод GetAutoInsertExtensions
  Возвращает сведения о приложениях для Office, которые будут автоматически вставляться во время отладки.

 Этот метод зарезервирован для использования в будущем.

## <a name="syntax"></a>Синтаксис

```csharp
HRESULT GetAutoInsertExtensions(
    [out, retval] SAFEARRAY(BSTR)* psaExtensionNames
);
```

### <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------------|-----------------|
|*псаекстенсионнамес*|Имена расширений приложений для Office.|

## <a name="return-value"></a>Возвращаемое значение
 Значение HRESULT, указывающее, успешно ли завершен метод.

## <a name="remarks"></a>Комментарии
 Каждое добавляемое приложение для Office возвращается как имя расширения приложения Office, которое соответствует значению в разделе **HKEY_CURRENT_USER\Software\Microsoft\Office\WEF\Developer**. Узел должен искать эти значения в реестре, а затем автоматически вставлять расширения.
