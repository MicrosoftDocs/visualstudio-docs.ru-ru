---
title: SuspendTracking | Документы Майкрософт
description: Изучите синтаксис, требования и возвращаемое значение функции SuspendTracking MSBuild, которая приостанавливает отслеживание в текущем контексте.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
apiname:
- SuspendTracking
apilocation:
- filetracker.dll
apitype: COM
helpviewer_keywords:
- SuspendTracking
ms.assetid: f5e06e5a-8083-444c-99c1-07ba834226b5
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: e8be768bc48c1815fc00069640e5bf3f4370f434
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99945283"
---
# <a name="suspendtracking"></a>SuspendTracking

Приостанавливает отслеживание в текущем контексте.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT WINAPI SuspendTracking(void);
```

## <a name="return-value"></a>Возвращаемое значение

 **HRESULT** с установленным битом **SUCCEEDED**, если отслеживание было приостановлено.

## <a name="requirements"></a>Требования

 **Заголовок:** *FileTracker.h*

## <a name="see-also"></a>См. также статью

- [ResumeTracking](../msbuild/resumetracking.md)