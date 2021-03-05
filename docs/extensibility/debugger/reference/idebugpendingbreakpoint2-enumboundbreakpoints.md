---
description: Перечисляет все точки останова, привязанные к этой ожидающей точке останова.
title: 'IDebugPendingBreakpoint2:: Енумбаундбреакпоинтс | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPendingBreakpoint2::EnumBoundBreakpoints
helpviewer_keywords:
- EnumBoundBreakpoints method
- IDebugPendingBreakpoint2::EnumBoundBreakpoints method
ms.assetid: 179c7c54-8446-462d-b099-e0f9cf06dc52
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 198470afbf40f72b33c6163bcf4fe0eb19b956eb
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102169916"
---
# <a name="idebugpendingbreakpoint2enumboundbreakpoints"></a>IDebugPendingBreakpoint2::EnumBoundBreakpoints
Перечисляет все точки останова, привязанные к этой ожидающей точке останова.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT EnumBoundBreakpoints( 
   IEnumDebugBoundBreakpoints2** ppEnum
);
```

```csharp
int EnumBoundBreakpoints( 
   out IEnumDebugBoundBreakpoints2 ppEnum
);
```

## <a name="parameters"></a>Параметры
`ppEnum`\
заполняет Возвращает объект [IEnumDebugBoundBreakpoints2](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2.md) , перечисляющий привязанные точки останова.

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки. Возвращает значение `E_BP_DELETED` , если точка останова была удалена.

## <a name="example"></a>Пример
 В следующем примере показано, как реализовать этот метод для простого `CPendingBreakpoint` объекта, предоставляющего интерфейс [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) .

```cpp
HRESULT CPendingBreakpoint::EnumBoundBreakpoints(IEnumDebugBoundBreakpoints2** ppEnum)
{
   HRESULT hr;

   // Verify that the passed IEnumDebugBoundBreakpoints2 interface pointer
   // is valid.
   if (ppEnum)
   {
      *ppEnum = NULL;

      // Verify that the pending breakpoint has not been deleted. If
      // deleted, then return hr = E_BP_DELETED.
      if (m_state.state != PBPS_DELETED)
      {
         // If the bound breakpoint member variable is valid.
         if (m_pBoundBP)
         {
            // Get the bound breakpoint.
            CComPtr<IDebugBoundBreakpoint2> spBoundBP;
            hr = m_pBoundBP->QueryInterface(&spBoundBP);
            assert(hr == S_OK);
            if (hr == S_OK)
            {
               // Create the bound breakpoint enumerator.
               CComObject<CEnumDebugBoundBreakpoints>* pBoundEnum;
               hr = CComObject<CEnumDebugBoundBreakpoints>::CreateInstance(&pBoundEnum);
               assert(hr == S_OK);
               if (hr == S_OK)
               {
                  // Initialize the enumerator of bound breakpoints with
                  // the IDebugBoundBreakpoint2 information.
                  IDebugBoundBreakpoint2* rgBoundBP[] = { spBoundBP.p };
                  hr = pBoundEnum->Init(rgBoundBP, &(rgBoundBP[1]), NULL, AtlFlagCopy);
                  if (hr == S_OK)
                  {
                     // Verify that the passed IEnumDebugBoundBreakpoints2
                     // interface can be queried by the created
                     // CEnumDebugBoundBreakpoints object.
                     hr = pBoundEnum->QueryInterface(ppEnum);
                     assert(hr == S_OK);
                  }

                  // Otherwise, delete the CEnumDebugBoundBreakpoints object.
                  if (FAILED(hr))
                  {
                     delete pBoundEnum;
                  }
               }
            }
         }
         else
         {
            hr = S_FALSE;
         }
      }
      else
      {
         hr = E_BP_DELETED;
      }
   }
   else
   {
      hr = E_INVALIDARG;
   }

   return hr;
}
```

## <a name="see-also"></a>См. также раздел
- [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)
- [IEnumDebugBoundBreakpoints2](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2.md)
