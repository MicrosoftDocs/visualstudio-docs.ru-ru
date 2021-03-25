---
description: Этот интерфейс позволяет средству оценки выражений (EE) отображать значение свойства в любом формате.
title: Идебугкустомвиевер | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCustomViewer
helpviewer_keywords:
- IDebugCustomViewer interface
ms.assetid: 7aca27d3-c7b8-470f-b42c-d1e9d9115edd
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 3c44706549d7d638a8fbf3686de57780ffa6bf4e
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105077555"
---
# <a name="idebugcustomviewer"></a>IDebugCustomViewer
Этот интерфейс позволяет средству оценки выражений (EE) отображать значение свойства в любом формате.

## <a name="syntax"></a>Синтаксис

```
IDebugCustomViewer : IUknown
```

## <a name="notes-for-implementers"></a>Примечания для разработчиков
EE реализует этот интерфейс для вывода значения свойства в пользовательском формате.

## <a name="notes-for-callers"></a>Примечания для вызывающих объектов
Вызов `CoCreateInstance` функции COM создает экземпляр этого интерфейса. `CLSID`Переданный в параметр `CoCreateInstance` получается из реестра. Вызов [жеткустомвиеверлист](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) получает расположение в реестре. Дополнительные сведения, а также пример см. в разделе Примечания.

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
Этот интерфейс реализует следующий метод:

|Метод|Описание|
|------------|-----------------|
|[DisplayValue](../../../extensibility/debugger/reference/idebugcustomviewer-displayvalue.md)|Выполняет какие-либо необходимые для вывода заданного значения.|

## <a name="remarks"></a>Remarks
Этот интерфейс используется, если значение свойства не может быть отображено обычным способом, например с таблицей данных или другим типом сложного свойства. Пользовательское средство просмотра, представленное `IDebugCustomViewer` интерфейсом, отличается от визуализатора типов, который является внешней программой для отображения данных определенного типа, независимо от ee. В EE реализовано пользовательское средство просмотра, относящееся к EE. Пользователь выбирает, какой тип визуализатора использовать, является визуализатором типов или пользовательским средством просмотра. Дополнительные сведения об этом процессе см. в разделе [визуализация и просмотр данных](../../../extensibility/debugger/visualizing-and-viewing-data.md) .

Пользовательское средство просмотра регистрируется так же, как EE, и поэтому требует GUID языка и GUID поставщика. Точная метрика (или имя записи в реестре) известна только для EE. Эта метрика возвращается в структуре [DEBUG_CUSTOM_VIEWER](../../../extensibility/debugger/reference/debug-custom-viewer.md) , которая, в свою очередь, возвращается вызовом [жеткустомвиеверлист](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md). Значение, хранящееся в метрике, — это объект `CLSID` , который передается в `CoCreateInstance` функцию com (см. пример).

[Вспомогательные методы SDK для функции отладки](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) , `SetEEMetric` могут использоваться для регистрации пользовательского средства просмотра. `Debugging SDK Helpers`Конкретные разделы реестра, необходимые для пользовательского средства просмотра, см. в разделе «оценки выражений» раздела. Обратите внимание, что пользовательскому средству просмотра требуется только одна метрика (определяемая средством реализации EE), в то время как средство оценки выражений требует наличия нескольких предопределенных метрик.

Обычно пользовательское средство просмотра предоставляет доступное только для чтения представление данных, так как интерфейс [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) , переданный в [дисплайвалуе](../../../extensibility/debugger/reference/idebugcustomviewer-displayvalue.md) , не имеет методов для изменения значения свойства, за исключением строки. Для поддержки изменения произвольных блоков данных EE реализует пользовательский интерфейс для того же объекта, который реализует `IDebugProperty3` интерфейс. Этот пользовательский интерфейс затем предоставляет методы, необходимые для изменения произвольного блока данных.

## <a name="requirements"></a>Требования
Заголовок: мсдбг. h

Пространство имен: Microsoft. VisualStudio. Debugger. Interop

Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="example"></a>Пример
В этом примере показано, как получить первое пользовательское средство просмотра из свойства, если у этого свойства есть пользовательские средства просмотра.

```cpp
IDebugCustomViewer *GetFirstCustomViewer(IDebugProperty2 *pProperty)
{
    // This string is typically defined globally.  For this example, it
    // is defined here.
    static const WCHAR strRegistrationRoot[] = L"Software\\Microsoft\\VisualStudio\\8.0Exp";
    IDebugCustomViewer *pViewer = NULL;
    if (pProperty != NULL) {
        CComQIPtr<IDebugProperty3> pProperty3(pProperty);
        if (pProperty3 != NULL) {
            HRESULT hr;
            ULONG viewerCount = 0;
            hr = pProperty3->GetCustomViewerCount(&viewerCount);
            if (viewerCount > 0) {
                ULONG viewersFetched = 0;
                DEBUG_CUSTOM_VIEWER viewerInfo = { 0 };
                hr = pProperty3->GetCustomViewerList(0,
                                                     1,
                                                     &viewerInfo,
                                                     &viewersFetched);
                if (viewersFetched == 1) {
                    CLSID clsidViewer = { 0 };
                    CComPtr<IDebugCustomViewer> spCustomViewer;
                    // Get the viewer's CLSID from the registry.
                    ::GetEEMetric(viewerInfo.guidLang,
                                  viewerInfo.guidVendor,
                                  viewerInfo.bstrMetric,
                                  &clsidViewer,
                                  strRegistrationRoot);
                    if (!IsEqualGUID(clsidViewer,GUID_NULL)) {
                        // Instantiate the custom viewer.
                        spCustomViewer.CoCreateInstance(clsidViewer);
                        if (spCustomViewer != NULL) {
                            pViewer = spCustomViewer.Detach();
                        }
                    }
                }
            }
        }
    }
    return(pViewer);
}
```

## <a name="see-also"></a>См. также
- [Основные интерфейсы](../../../extensibility/debugger/reference/core-interfaces.md)
- [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md)
- [Вспомогательные пакеты SDK для отладки](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)
- [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)
