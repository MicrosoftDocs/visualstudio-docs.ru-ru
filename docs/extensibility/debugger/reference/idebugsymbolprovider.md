---
description: Этот интерфейс представляет поставщик символов, который предоставляет символы и типы, возвращая их в виде полей.
title: Идебугсимболпровидер | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugSymbolProvider
helpviewer_keywords:
- IDebugSymbolProvider interface
ms.assetid: df5f095f-1dee-46f9-84cf-92417c71d5fb
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: e0488520f8bde0ccd2638636810cb0055a7f3f4b
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102168430"
---
# <a name="idebugsymbolprovider"></a>IDebugSymbolProvider
Этот интерфейс представляет поставщик символов, который предоставляет символы и типы, возвращая их в виде полей.

## <a name="syntax"></a>Синтаксис

```
IDebugSymbolProvider : IUnknown
```

## <a name="notes-for-implementers"></a>Примечания для разработчиков
Поставщик символов должен реализовать этот интерфейс для передачи сведений о символах и типах в средство оценки выражений.

## <a name="notes-for-callers"></a>Примечания для вызывающих объектов
Этот интерфейс получается с помощью функции COM `CoCreateInstance` (для неуправляемых поставщиков символов) или путем загрузки соответствующей сборки управляемого кода и создания экземпляра поставщика символов на основе информации, найденной в этой сборке. Модуль отладки создает экземпляр поставщика символов для работы в координации с вычислителем выражений. См. пример для одного из подходов к созданию экземпляра этого интерфейса.

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
В следующей таблице показаны методы `IDebugSymbolProvider` .

|Метод|Описание|
|------------|-----------------|
|`Initialize`|Не рекомендуется. Не используется.|
|`Uninitialize`|Не рекомендуется. Не используется.|
|[GetContainerField](../../../extensibility/debugger/reference/idebugsymbolprovider-getcontainerfield.md)|Возвращает поле, содержащее адрес отладки.|
|`GetField`|Не рекомендуется. Не используется.|
|[GetAddressesFromPosition](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromposition.md)|Сопоставляет расположение документа с массивом адресов отладки.|
|[GetAddressesFromContext](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromcontext.md)|Сопоставляет контекст документа с массивом адресов отладки.|
|[GetContextFromAddress](../../../extensibility/debugger/reference/idebugsymbolprovider-getcontextfromaddress.md)|Сопоставляет адрес отладки с контекстом документа.|
|[GetLanguage](../../../extensibility/debugger/reference/idebugsymbolprovider-getlanguage.md)|Возвращает язык, используемый для компиляции кода по адресу отладки.|
|`GetGlobalContainer`|Не рекомендуется. Не используется.|
|[GetMethodFieldsByName](../../../extensibility/debugger/reference/idebugsymbolprovider-getmethodfieldsbyname.md)|Возвращает поле, представляющее полное имя метода.|
|[GetClassTypeByName](../../../extensibility/debugger/reference/idebugsymbolprovider-getclasstypebyname.md)|Возвращает тип поля класса, представляющий полное имя класса.|
|[GetNamespacesUsedAtAddress](../../../extensibility/debugger/reference/idebugsymbolprovider-getnamespacesusedataddress.md)|Создает перечислитель для пространств имен, связанных с адресом отладки.|
|[GetTypeByName](../../../extensibility/debugger/reference/idebugsymbolprovider-gettypebyname.md)|Сопоставляет имя символа с типом символа.|
|[GetNextAddress](../../../extensibility/debugger/reference/idebugsymbolprovider-getnextaddress.md)|Возвращает адрес отладки, следующий за заданным адресом отладки в методе.|

## <a name="remarks"></a>Комментарии
Этот интерфейс сопоставляет позиции документа с адресами отладки и наоборот.

## <a name="requirements"></a>Требования
Заголовок: sh. h

Пространство имен: Microsoft. VisualStudio. Debugger. Interop

Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="example"></a>Пример
В этом примере показано, как создать экземпляр поставщика символов с учетом его GUID (обработчик отладки должен иметь это значение).

```cpp
// A debug engine uses its own symbol provider and would know the GUID
// of that provider.
IDebugSymbolProvider *GetSymbolProvider(GUID *pSymbolProviderGuid)
{
    // This is typically defined globally. For this example, it is
    // defined here.
    static const WCHAR strRegistrationRoot[] = L"Software\\Microsoft\\VisualStudio\\8.0Exp";
    IDebugSymbolProvider *pProvider = NULL;
    if (pSymbolProviderGuid != NULL) {
        CLSID clsidProvider = { 0 };
        ::GetSPMetric(*pSymbolProviderGuid,
                      storetypeFile,
                      metricCLSID,
                      &clsidProvider,
                      strRegistrationRoot);
        if (IsEqualGUID(clsidProvider,GUID_NULL)) {
            // No file type provider, try metadata provider.
            ::GetSPMetric(*pSymbolProviderGuid,
                          ::storetypeMetadata,
                          metricCLSID,
                          &clsidProvider,
                          strRegistrationRoot);
        }
        if (!IsEqualGUID(clsidProvider,GUID_NULL)) {
            CComPtr<IDebugSymbolProvider> spSymbolProvider;
            spSymbolProvider.CoCreateInstance(clsidProvider);
            if (spSymbolProvider != NULL) {
                pProvider = spSymbolProvider.Detach();
            }
        }
    }
    return(pProvider);
}
```

## <a name="see-also"></a>См. также раздел
- [Интерфейсы поставщика символов](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
