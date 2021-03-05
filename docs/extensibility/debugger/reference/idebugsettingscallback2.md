---
description: Включает модули отладки для удаленного считывания параметров метрик.
title: IDebugSettingsCallback2 | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugSettingsCallback2 interface
ms.assetid: 7e525d0b-7d7a-4d1c-8b78-e1398fa922f2
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 7053c45ba86f4bea54befc3bde67d831cc9c822e
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102168664"
---
# <a name="idebugsettingscallback2"></a>IDebugSettingsCallback2
Включает модули отладки для удаленного считывания параметров метрик.

## <a name="syntax"></a>Синтаксис

```
IDebugSettingsCallback2D : IUnknown
```

## <a name="notes-for-implementers"></a>Примечания для разработчиков
Этот интерфейс реализуется обратным вызовом события диспетчером отладки сеанса и используется механизмами отладки. Его также можно использовать локально вместо Дбгметрик [d]. lib.

## <a name="methods"></a>Методы
В следующей таблице показаны методы `IDebugSettingsCallback2` .

|Метод|Описание|
|------------|-----------------|
|[EnumEEs](../../../extensibility/debugger/reference/idebugsettingscallback2-enumees.md)|Перечисляет доступные средства оценки выражений по идентификаторам языка и поставщика.|
|[GetEELocalObject](../../../extensibility/debugger/reference/idebugsettingscallback2-geteelocalobject.md)|Извлекает локальный объект средства оценки выражений, заданный метрикой.|
|[GetEEMetricDword](../../../extensibility/debugger/reference/idebugsettingscallback2-geteemetricdword.md)|Извлекает значение, соответствующее заданной метрике средства оценки выражений.|
|[GetEEMetricFile](../../../extensibility/debugger/reference/idebugsettingscallback2-geteemetricfile.md)|Извлекает файл метрики средства оценки выражений по заданному имени или метрике.|
|[GetEEMetricGuid](../../../extensibility/debugger/reference/idebugsettingscallback2-geteemetricguid.md)|Возвращает уникальный идентификатор для метрики средства оценки выражений по заданному имени.|
|[GetEEMetricString](../../../extensibility/debugger/reference/idebugsettingscallback2-geteemetricstring.md)|Получает строку значений метрики средства оценки выражений по его имени.|
|[GetMetricDword](../../../extensibility/debugger/reference/idebugsettingscallback2-getmetricdword.md)|Извлекает значение метрики по ее имени.|
|[GetMetricGuid](../../../extensibility/debugger/reference/idebugsettingscallback2-getmetricguid.md)|Извлекает уникальный идентификатор метрики по ее имени.|
|[GetMetricString](../../../extensibility/debugger/reference/idebugsettingscallback2-getmetricstring.md)|Возвращает строку значения метрики, заданную ее именем.|

## <a name="requirements"></a>Требования
Заголовок: Мсдбг. h

Пространство имен: Microsoft. VisualStudio. Debugger. Interop

Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="example"></a>Пример
В следующем примере показана функция, которая принимает объект **IDebugSettingsCallback2** в качестве параметра.

```cpp
HRESULT GetDebugSettingsCallback (IDebugSettingsCallback2 **ppCallback)
{
    HRESULT hRes = E_FAIL;

    if ( ppCallback )
    {
        if ( EVAL(m_pdec) )
            hRes = m_pdec->QueryInterface(IID_IDebugSettingsCallback2, (void **)ppCallback);
        else
            hRes = E_FAIL;
    }
    else
        hRes = E_INVALIDARG;

    return ( hRes );
}
```
