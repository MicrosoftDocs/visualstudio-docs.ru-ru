---
description: Включает средство оценки выражений (EE) для указания интерфейса обратного вызова, который подсистема отладчика (DE) будет использовать для считывания параметров метрик.
title: 'IDebugExpressionEvaluator2:: Сеткаллбакк | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugExpressionEvaluator2::SetCallback
- SetCallback
ms.assetid: 31e3a99e-e784-44a3-8b19-cc5ef31ed546
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: fc858ab5d26ccffe33d26296e033ac577ddba440
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102152394"
---
# <a name="idebugexpressionevaluator2setcallback"></a>IDebugExpressionEvaluator2::SetCallback
Включает средство оценки выражений (EE) для указания интерфейса обратного вызова, который подсистема отладчика (DE) будет использовать для считывания параметров метрик.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT SetCallback (
    IDebugSettingsCallback2* pCallback
);
```

```csharp
int SetCallback (
    IDebugSettingsCallback2 pCallback
);
```

## <a name="parameters"></a>Параметры
`pCallback`\
окне Интерфейс, используемый для обратного вызова параметров.

## <a name="return-value"></a>Возвращаемое значение
Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Комментарии
Этот метод предоставляет интерфейс диспетчеру отладки сеанса, который средство оценки выражений может использовать для чтения параметров метрики. Для чтения метрик на компьютере полезно использовать удаленную отладку [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] .

## <a name="example"></a>Пример
В следующих примерах показано, как реализовать этот метод для объекта **CEE** , предоставляющего интерфейс [IDebugSettingsCallback2](../../../extensibility/debugger/reference/idebugsettingscallback2.md) .

```cpp
HRESULT CEE::SetCallback(IDebugSettingsCallback2* in_pCallback)
{
    // precondition
    INVARIANT( this );

    // function body
    if (NULL != this->m_LanguageSpecificUseCases.pfSetCallback)
    {
        EEDomain::fSetCallback DomainVal =
        {
            in_pCallback
        };

        BOOL bSuccess = (*this->m_LanguageSpecificUseCases.pfSetCallback)(DomainVal);
        ENSURE( bSuccess );
    }

    // postcondition
    INVARIANT( this );

    return S_OK;
}
```

## <a name="see-also"></a>См. также раздел
- [IDebugExpressionEvaluator2](../../../extensibility/debugger/reference/idebugexpressionevaluator2.md)
