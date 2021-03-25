---
description: Описывает одну инструкцию дизассемблирования для отображаемой интегрированной среды разработки (IDE).
title: Дисассемблидата | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DisassemblyData
helpviewer_keywords:
- DisassemblyData structure
ms.assetid: 10e70aa7-9381-40d3-bdd1-d2cad78ef16c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 71d52c4f48f23368d83d81f88fba4bf0ba36f197
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105096126"
---
# <a name="disassemblydata"></a>DisassemblyData
Описывает одну инструкцию дизассемблирования для отображаемой интегрированной среды разработки (IDE).

## <a name="syntax"></a>Синтаксис

```cpp
typedef struct tagDisassemblyData {
    DISASSEMBLY_STREAM_FIELDS dwFields;
    BSTR                      bstrAddress;
    BSTR                      bstrAddressOffset;
    BSTR                      bstrCodeBytes;
    BSTR                      bstrOpcode;
    BSTR                      bstrOperands;
    BSTR                      bstrSymbol;
    UINT64                    uCodeLocationId;
    TEXT_POSITION             posBeg;
    TEXT_POSITION             posEnd;
    BSTR                      bstrDocumentUrl;
    DWORD                     dwByteOffset;
    DISASSEMBLY_FLAGS         dwFlags;
} DisassemblyData;
```

```csharp
public struct DisassemblyData { 
    public uint          dwFields;
    public string        bstrAddress;
    public string        bstrAddressOffset;
    public string        bstrCodeBytes;
    public string        bstrOpcode;
    public string        bstrOperands;
    public string        bstrSymbol;
    public ulong         uCodeLocationId;
    public TEXT_POSITION posBeg;
    public TEXT_POSITION posEnd;
    public string        bstrDocumentUrl;
    public uint          dwByteOffset;
    public uint          dwFlags;
};
```

## <a name="members"></a>Участники
`dwFields`\
Константа [DISASSEMBLY_STREAM_FIELDS](../../../extensibility/debugger/reference/disassembly-stream-fields.md) , указывающая, какие поля заполняются.

`bstrAddress`\
Адрес в виде смещения от некоторой начальной точки (обычно это начало связанной функции).

`bstrCodeBytes`\
Байты кода для этой инструкции.

`bstrOpcode`\
Код операции для этой инструкции.

`bstrOperands`\
Операнды для этой инструкции.

`bstrSymbol`\
Имя символа (если имеется), связанное с адресом (открытый символ, метка и т. д.).

`uCodeLocationId`\
Идентификатор расположения кода для этой разобранной строки. Если адрес контекста кода в одной строке больше, чем адрес другого контекста кода, то идентификатор местонахождения кода первого будет также больше, чем идентификатор расположения кода второго.

`posBeg`\
[TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) , соответствующий положению в документе, где начинаются данные дизассемблирования.

`posEnd`\
[TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) , соответствующий положению в документе, где заканчиваются Дизассемблированный данные.

`bstrDocumentUrl`\
Для текстовых документов, которые могут быть представлены в виде имен файлов, `bstrDocumentUrl` поле заполняется именем файла, в котором можно найти источник, используя формат `file://file name` .

Для текстовых документов, которые не могут быть представлены в виде имен файлов, `bstrDocumentUrl` является уникальным идентификатором документа, а модуль отладки должен реализовать метод [](../../../extensibility/debugger/reference/idebugdisassemblystream2-getdocument.md) GetText.

Это поле также может содержать дополнительные сведения о контрольных суммах. Дополнительные сведения см. в разделе "Примечания".

`dwByteOffset`\
Число байтов, на которое инструкция находится в начале строки кода.

`dwFlags`\
Константа [DISASSEMBLY_FLAGS](../../../extensibility/debugger/reference/disassembly-flags.md) , указывающая, какие флаги активны.

## <a name="remarks"></a>Remarks
Каждая `DisassemblyData` структура описывает одну инструкцию дизассемблирования. Массив этих структур возвращается методом [Read](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md) .

Структура [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) используется только для текстовых документов. Диапазон исходного кода для этой инструкции заполнен только для первой инструкции, созданной из инструкции или строки, например when `dwByteOffset == 0` .

Для документов, которые не являются текстовыми, контекст документа можно получить из кода, а `bstrDocumentUrl` поле должно иметь значение null. Если поле совпадает с `bstrDocumentUrl` `bstrDocumentUrl` полем в предыдущем `DisassemblyData` элементе массива, установите `bstrDocumentUrl` для параметра значение null.

Если `dwFlags` поле имеет `DF_DOCUMENT_CHECKSUM` установленный флаг, дополнительные сведения о контрольной сумме следуют за строкой, на которую указывает `bstrDocumentUrl` поле. В частности, после нулевого признака конца строки следует идентификатор GUID, определяющий алгоритм контрольной суммы, который, в свою очередь, за которым следует 4-байтовый параметр, указывающий число байтов в контрольной сумме, за которыми следуют контрольные суммы. См. пример в этом разделе о кодировании и декодировании этого поля в [!INCLUDE[csprcs](../../../data-tools/includes/csprcs_md.md)] .

## <a name="example"></a>Пример
`bstrDocumentUrl`Поле может содержать дополнительные сведения, кроме строки, если установлен `DF_DOCUMENT_CHECKSUM` флаг. Процесс создания и чтения этой закодированной строки прост в [!INCLUDE[vcprvc](../../../code-quality/includes/vcprvc_md.md)] . Однако в это [!INCLUDE[csprcs](../../../data-tools/includes/csprcs_md.md)] еще один вопрос. Для тех, кто интересует, в следующем примере показан один из способов создания закодированной строки из [!INCLUDE[csprcs](../../../data-tools/includes/csprcs_md.md)] и один способ декодирования закодированной строки в [!INCLUDE[csprcs](../../../data-tools/includes/csprcs_md.md)] .

```csharp
using System;
using System.Runtime.InteropServices;

namespace MyNamespace
{
    class MyClass
    {
        string EncodeData(string documentString,
                          Guid checksumGuid,
                          byte[] checksumData)
        {
            string returnString = documentString;

            if (checksumGuid == null || checksumData == null)
            {
                // Nothing more to do. Just return the string.
                return returnString;
            }

            returnString += '\0'; // separating null value

            // Add checksum GUID to string.
            byte[] guidDataArray  = checksumGuid.ToByteArray();
            int    guidDataLength = guidDataArray.Length;
            IntPtr pBuffer        = Marshal.AllocCoTaskMem(guidDataLength);
            for (int i = 0; i < guidDataLength; i++)
            {
                Marshal.WriteByte(pBuffer, i, guidDataArray[i]);
            }
            // Copy guid data bytes to string as wide characters.
            // Assumption: sizeof(char) == 2.
            for (int i = 0; i < guidDataLength / sizeof(char); i++)
            {
                returnString += (char)Marshal.ReadInt16(pBuffer, i * sizeof(char));
            }

            // Add checksum count (a 32-bit value).
            Int32 checksumCount = checksumData.Length;
            Marshal.StructureToPtr(checksumCount, pBuffer, true);
            for (int i = 0; i < sizeof(Int32) / sizeof(char); i++)
            {
                returnString += (char)Marshal.ReadInt16(pBuffer, i * sizeof(char));
            }

            // Add checksum data.
            pBuffer = Marshal.AllocCoTaskMem(checksumCount);
            for (int i = 0; i < checksumCount; i++)
            {
                Marshal.WriteByte(pBuffer, i, checksumData[i]);
            }
            for (int i = 0; i < checksumCount / sizeof(char); i++)
            {
                returnString += (char)Marshal.ReadInt16(pBuffer, i * sizeof(char));
            }
            Marshal.FreeCoTaskMem(pBuffer);

            return returnString;
        }

        void DecodeData(    string encodedString,
                        out string documentString,
                        out Guid   checksumGuid,
                        out byte[] checksumData)
        {
            documentString = String.Empty;
            checksumGuid = Guid.Empty;
            checksumData = null;

            IntPtr pBuffer = Marshal.StringToBSTR(encodedString);
            if (null != pBuffer)
            {
                int bufferOffset = 0;

                // Parse string out. String is assumed to be Unicode.
                documentString = Marshal.PtrToStringUni(pBuffer);
                bufferOffset += (documentString.Length + 1) * sizeof(char);

                // Parse Guid out.
                // Read guid bytes from buffer and store in temporary
                // buffer that contains only the guid bytes. Then the
                // Marshal.PtrToStructure() can work properly.
                byte[] guidDataArray  = checksumGuid.ToByteArray();
                int    guidDataLength = guidDataArray.Length;
                IntPtr pGuidBuffer    = Marshal.AllocCoTaskMem(guidDataLength);
                for (int i = 0; i < guidDataLength; i++)
                {
                    Marshal.WriteByte(pGuidBuffer, i,
                                      Marshal.ReadByte(pBuffer, bufferOffset + i));
                }
                bufferOffset += guidDataLength;
                checksumGuid = (Guid)Marshal.PtrToStructure(pGuidBuffer, typeof(Guid));
                Marshal.FreeCoTaskMem(pGuidBuffer);

                // Parse out the number of checksum data bytes (always 32-bit value).
                int dataCount = Marshal.ReadInt32(pBuffer, bufferOffset);
                bufferOffset += sizeof(Int32);

                // Parse out the checksum data.
                checksumData = new byte[dataCount];
                for (int i = 0; i < dataCount; i++)
                {
                    checksumData[i] = Marshal.ReadByte(pBuffer, bufferOffset + i);
                }
            }
        }
    }
}
```

## <a name="see-also"></a>См. также
- [Структуры и объединения](../../../extensibility/debugger/reference/structures-and-unions.md)
- [Чтение](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md)
- [DISASSEMBLY_STREAM_FIELDS](../../../extensibility/debugger/reference/disassembly-stream-fields.md)
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
- [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)
- [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)
- [DISASSEMBLY_FLAGS](../../../extensibility/debugger/reference/disassembly-flags.md)
