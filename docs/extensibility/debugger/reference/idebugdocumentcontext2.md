---
description: Этот интерфейс представляет расположение в исходном файле документа.
title: IDebugDocumentContext2 | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentContext2
helpviewer_keywords:
- IDebugDocumentContext2
ms.assetid: 2a446c71-8100-4c09-a1cc-fd446bd74030
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: a20473d2076932987ecc352c8719f1d9133ed198
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105066520"
---
# <a name="idebugdocumentcontext2"></a>IDebugDocumentContext2
Этот интерфейс представляет расположение в исходном файле документа.

## <a name="syntax"></a>Синтаксис

```
IDebugDocumentContext2 : IUnknown
```

## <a name="notes-for-implementers"></a>Примечания для разработчиков
 Модуль отладки (DE) реализует этот интерфейс в рамках поддержки отладки на уровне исходного кода. В дополнение к положению в исходном коде этот интерфейс предоставляет методы для сравнения контекстов и перехода по документу исходного кода.

## <a name="notes-for-callers"></a>Примечания для вызывающих объектов
 Методы в нескольких интерфейсах, обычно это интерфейсы [жетдокументконтекст](../../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md) и [жетдокументконтекст](../../../extensibility/debugger/reference/idebugcodecontext2-getdocumentcontext.md) , возвращают этот интерфейс.

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
 В следующей таблице показаны методы `IDebugDocumentContext2` .

|Метод|Описание|
|------------|-----------------|
|[GetDocument](../../../extensibility/debugger/reference/idebugdocumentcontext2-getdocument.md)|Возвращает документ, содержащий этот контекст документа.|
|[GetName](../../../extensibility/debugger/reference/idebugdocumentcontext2-getname.md)|Возвращает отображаемое имя документа, содержащего этот контекст документа.|
|[EnumCodeContexts](../../../extensibility/debugger/reference/idebugdocumentcontext2-enumcodecontexts.md)|Извлекает список всех контекстов кода, связанных с этим контекстом документа.|
|[GetLanguageInfo](../../../extensibility/debugger/reference/idebugdocumentcontext2-getlanguageinfo.md)|Возвращает язык, связанный с этим контекстом документа.|
|[GetStatementRange](../../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md)|Возвращает диапазон инструкций File для этого контекста документа.|
|[GetSourceRange](../../../extensibility/debugger/reference/idebugdocumentcontext2-getsourcerange.md)|Возвращает диапазон исходных файлов этого контекста документа.|
|[Сравнить](../../../extensibility/debugger/reference/idebugdocumentcontext2-compare.md)|Сравнивает данный контекст документа с заданным массивом контекстов документа.|
|[Seek](../../../extensibility/debugger/reference/idebugdocumentcontext2-seek.md)|Перемещает контекст документа на заданное количество инструкций или строк.|

## <a name="requirements"></a>Требования
 Заголовок: мсдбг. h

 Пространство имен: Microsoft. VisualStudio. Debugger. Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [GetDocumentContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getdocumentcontext.md)
- [GetDocumentContext](../../../extensibility/debugger/reference/idebugactivatedocumentevent2-getdocumentcontext.md)
- [GetDocumentContext](../../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md)
- [GetDocumentContext](../../../extensibility/debugger/reference/idebugcodecontext2-getdocumentcontext.md)
