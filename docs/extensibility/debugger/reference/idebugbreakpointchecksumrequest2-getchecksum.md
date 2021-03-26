---
description: Извлекает контрольную сумму документа для запроса точки останова по заданному уникальному идентификатору алгоритма контрольной суммы для использования.
title: IDebugBreakpointChecksumRequest2::/CHECKSUM | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugBreakpointChecksumRequest2::GetChecksum
ms.assetid: ec434882-e5c0-4d76-a58b-22c260d8626e
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e9d4fc1d20b8b41d3462ad931a50de6485b920a5
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105078101"
---
# <a name="idebugbreakpointchecksumrequest2getchecksum"></a>IDebugBreakpointChecksumRequest2::GetChecksum
Извлекает контрольную сумму документа для запроса точки останова по заданному уникальному идентификатору алгоритма контрольной суммы для использования.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetChecksum(
    REFGUID        guidAlgorithm,
    CHECKSUM_DATA *pChecksumData
);
```

```csharp
public int GetChecksum(
    ref Guid               guidAlgorithm,
    out enum_CHECKSUM_DATA pChecksumData
);
```

## <a name="parameters"></a>Параметры
`guidAlgorithm`\
окне Уникальный идентификатор алгоритма контрольной суммы.

`pChecksumData`\
заполняет Контрольная сумма документа для запроса точки останова.

## <a name="return-value"></a>Возвращаемое значение
Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="example"></a>Пример
В следующем примере показана функция, которая проверяет, соответствует ли контрольная сумма документа, который должен быть привязан, сопоставляется с одним из элементов пользовательского интерфейса.

```cpp
bool CDebugProgram::DoChecksumsMatch(CDebugPendingBreakpoint *pPending, CDebugCodeContext *pContext)
{
    bool fRet = false;
    HRESULT hRes;

    // Get the checksum for the document we are about to bind to from the pdb side
    GUID guidAlgorithmId;
    BYTE *pChecksum = NULL;
    ULONG cNumBytes = 0;

    hRes = pContext->GetDocumentChecksumAndAlgorithmId(&guidAlgorithmId, &pChecksum, &cNumBytes);

    if ( S_OK == hRes )
    {
        // Get checksum data for the document from the UI (request) side
        CComPtr<IDebugBreakpointChecksumRequest2> pChecksumRequest;

        hRes = pPending->GetChecksumRequest(&pChecksumRequest);

        if ( S_OK == hRes )
        {
            CHECKSUM_DATA data;

            hRes = pChecksumRequest->GetChecksum(guidAlgorithmId, &data);

            if ( S_OK == hRes )
            {
                if ( data.ByteCount == cNumBytes && memcmp(data.pBytes, pChecksum, cNumBytes) == 0 )
                    fRet = true;
                else
                    fRet = false;

                // Free up data allocated for checksum data
                CoTaskMemFree(data.pBytes);
            }
            else
                fRet = true; // checksums not available - user disabed checksums
        }
        else
            fRet = true; // we couldn't get checksum from UI - default to past behavior

        // free up space allocated for checksum from pdb
        CoTaskMemFree(pChecksum);
    }
    else
        fRet = true; // we don't have a checksum to compare with.

    return ( fRet );
}
```

## <a name="see-also"></a>См. также
- [IDebugBreakpointChecksumRequest2](../../../extensibility/debugger/reference/idebugbreakpointchecksumrequest2.md)
