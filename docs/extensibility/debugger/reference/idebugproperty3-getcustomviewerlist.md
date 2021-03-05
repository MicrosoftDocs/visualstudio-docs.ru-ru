---
description: Возвращает список пользовательских средств просмотра, связанных с этим свойством.
title: 'IDebugProperty3:: Жеткустомвиеверлист | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty3::GetCustomViewerList
helpviewer_keywords:
- IDebugProperty3::GetCustomViewerList
ms.assetid: 74490fd8-6f44-4618-beea-dab64961bb8a
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e772987a6e27dbe72a927dd83f8d33d043408fd0
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102166674"
---
# <a name="idebugproperty3getcustomviewerlist"></a>IDebugProperty3::GetCustomViewerList
Возвращает список пользовательских средств просмотра, связанных с этим свойством.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetCustomViewerList(
    ULONG                celtSkip,
    ULONG                celtRequested,
    DEBUG_CUSTOM_VIEWER* rgViewers,
    ULONG*               pceltFetched
);
```

```csharp
int GetCustomViewerList(
    uint                  celtSkip,
    uint                  celtRequested,
    DEBUG_CUSTOM_VIEWER[] rgViewers,
    out uint              pceltFetched
);
```

## <a name="parameters"></a>Параметры
`celtSkip`\
окне Число посетителей для пропуска.

`celtRequested`\
окне Число получаемых средств просмотра (также определяет размер `rgViewers` массива).

`rgViewers`\
[вход, выход] Массив [DEBUG_CUSTOM_VIEWERных](../../../extensibility/debugger/reference/debug-custom-viewer.md) структур, которые необходимо заполнить.

`pceltFetched`\
заполняет Фактическое число возвращаемых средств просмотра.

## <a name="return-value"></a>Возвращаемое значение
Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Комментарии
Для поддержки визуализаторов типов этот метод пересылает вызов методу [жеткустомвиеверлист](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md) . Если средство оценки выражений также поддерживает пользовательские средства просмотра для типа этого свойства, этот метод может добавлять к списку соответствующие пользовательские средства просмотра.

Дополнительные сведения о различиях между визуализаторами типов и пользовательскими средствами просмотра см. в разделе [Визуализатор типов и пользовательское средство](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md) .

## <a name="example"></a>Пример
В следующем примере показано, как реализовать этот метод для объекта **кпроперти** , предоставляющего интерфейс [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) .

```cpp
STDMETHODIMP CProperty::GetCustomViewerList(ULONG celtSkip, ULONG celtRequested, DEBUG_CUSTOM_VIEWER* prgViewers, ULONG* pceltFetched)
{
    if (NULL == prgViewers)
    {
        return E_POINTER;
    }

    if (GetVisualizerService())
    {
        return m_pIEEVisualizerService->GetCustomViewerList(celtSkip, celtRequested, prgViewers, pceltFetched);
    }
    else
    {
        return E_NOTIMPL;
    }
}
```

## <a name="see-also"></a>См. также раздел
- [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)
- [DEBUG_CUSTOM_VIEWER](../../../extensibility/debugger/reference/debug-custom-viewer.md)
- [GetCustomViewerList](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md)
- [Визуализатор типов и пользовательское средство просмотра](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)
