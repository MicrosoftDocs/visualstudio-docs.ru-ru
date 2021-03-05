---
description: Этот интерфейс перечисляет контексты кода, связанные с сеансом отладки, или с определенной программой или документом.
title: IEnumDebugCodeContexts2 | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugCodeContexts2
helpviewer_keywords:
- IEnumDebugCodeContexts2
ms.assetid: 72915146-215f-4c99-a034-131b2b474e0e
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 82e3583333c784fffa55abf2e86f5a7335aeb7c1
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102226934"
---
# <a name="ienumdebugcodecontexts2"></a>IEnumDebugCodeContexts2
Этот интерфейс перечисляет контексты кода, связанные с сеансом отладки, или с определенной программой или документом.

## <a name="syntax"></a>Синтаксис

```
IEnumDebugCodeContexts2 : IUnknown
```

## <a name="notes-for-implementers"></a>Примечания для разработчиков
 Модуль отладки (DE) реализует этот интерфейс для представления списка контекстов кода для определенной позицией текста в программе или списка контекстов кода для конкретного контекста документа.

## <a name="notes-for-callers"></a>Примечания для вызывающих объектов
 Вызовите [енумкодеконтекстс](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md) , чтобы получить этот интерфейс, представляющий список контекстов кода для определенной позицией текста в исходном документе программы.

 Вызовите [енумкодеконтекстс](../../../extensibility/debugger/reference/idebugdocumentcontext2-enumcodecontexts.md) , чтобы получить этот интерфейс, представляющий список всех контекстов кода в определенном исходном документе.

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
 В следующей таблице показаны методы `IEnumDebugCodeContexts2` .

|Метод|Описание|
|------------|-----------------|
|[Вперед](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-next.md)|Извлекает указанное число контекстов кода в последовательности перечисления.|
|[Skip](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-skip.md)|Пропускает указанное число контекстов кода в последовательности перечисления.|
|[Сброс](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-reset.md)|Сбрасывает последовательность перечислений в начало.|
|[Клонировать](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-clone.md)|Создает перечислитель, который содержит то же состояние перечисления, что и текущий перечислитель.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-getcount.md)|Возвращает количество контекстов кода в перечислителе.|

## <a name="remarks"></a>Комментарии
 Visual Studio вызывает [енумкодеконтекстс](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md) для заполнения списка контекстов кода, которые пользователь может выбрать при настройке следующей инструкции или отображения дизассемблированного кода для исходного файла. Может произойти несколько контекстов кода, например при наличии нескольких экземпляров шаблона в стиле C++.

## <a name="requirements"></a>Требования
 Заголовок: мсдбг. h

 Пространство имен: Microsoft. VisualStudio. Debugger. Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также раздел
- [Базовые интерфейсы](../../../extensibility/debugger/reference/core-interfaces.md)
- [EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md)
- [EnumCodeContexts](../../../extensibility/debugger/reference/idebugdocumentcontext2-enumcodecontexts.md)
