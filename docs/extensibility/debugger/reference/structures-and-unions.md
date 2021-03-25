---
title: Структуры и объединения | Документация Майкрософт
description: В этой статье приведены ссылки на описания структур и объединений в пакете SDK для отладки Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- structures [Visual Studio SDK]
ms.assetid: 9ff0a8f8-1ee6-4fdd-8b80-206436ff589b
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 055c8972643a94bd8f13aa6e5e6bc5dde600140b
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105061476"
---
# <a name="structures-and-unions"></a>Структуры и объединения
Ниже представлены структуры и объединения в пакете SDK для отладки Visual Studio.

- [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) Указывает идентификатор процесса, который может быть либо системным ИДЕНТИФИКАТОРом, либо идентификатором GUID.

- [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md) Описывает условия, при которых будет срабатывать точка останова.

- [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md) Описывает разрешение точки останова по ошибке, включая расположение, программу и поток.

- [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md) Указывает тип структуры, используемой для описания расположения точки останова.

- [BP_LOCATION_CODE_ADDRESS](../../../extensibility/debugger/reference/bp-location-code-address.md) Определяет компоненты, описывающие расположение точки останова по адресу в коде.

- [BP_LOCATION_CODE_CONTEXT](../../../extensibility/debugger/reference/bp-location-code-context.md) Описывает расположение точки останова, привязанной непосредственно к адресу в отлаживаемой программе.

- [BP_LOCATION_CODE_FILE_LINE](../../../extensibility/debugger/reference/bp-location-code-file-line.md) Описывает расположение точки останова в строке исходного файла кода.

- [BP_LOCATION_CODE_FUNC_OFFSET](../../../extensibility/debugger/reference/bp-location-code-func-offset.md) Описывает положение смещения точки останова в функции в коде.

- [BP_LOCATION_CODE_STRING](../../../extensibility/debugger/reference/bp-location-code-string.md) Используется для задания точек останова в коде на основе строки, которую пользователь может ввести из интегрированной среды разработки.

- [BP_LOCATION_DATA_STRING](../../../extensibility/debugger/reference/bp-location-data-string.md) Используется для установки точек останова по данным, основанных на строке, которую пользователь может вводить из интегрированной среды разработки.

- [BP_LOCATION_RESOLUTION](../../../extensibility/debugger/reference/bp-location-resolution.md) Описывает разрешение точки останова в определенном месте.

- [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md) Описывает количество и условия, при которых точка останова будет срабатывать после передачи ранее.

- [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) Содержит сведения, необходимые для реализации точки останова.

- [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) Содержит сведения, необходимые для реализации точки останова (то же, что структура [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) , но включает GUID поставщика, ограничение и сведения о точке отслеживания).

- [BP_RESOLUTION_CODE](../../../extensibility/debugger/reference/bp-resolution-code.md) Описывает расположение точки останова в коде.

- [BP_RESOLUTION_DATA](../../../extensibility/debugger/reference/bp-resolution-data.md) Описывает результат привязки точки останова в данных.

- [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md) Описывает сведения о привязанной точке останова для точки останова в коде или точки останова в данных.

- [BP_RESOLUTION_LOCATION](../../../extensibility/debugger/reference/bp-resolution-location.md) Задает структуру расположения разрешения точки останова.

- [BSTR_ARRAY](../../../extensibility/debugger/reference/bstr-array.md) Описывает массив строк.

- [BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md) Задает сведения о типе поля, взятого из метаданных.

- [CODE_PATH](../../../extensibility/debugger/reference/code-path.md) Описывает вызов функции или метода.

- [COMPUTER_INFO](../../../extensibility/debugger/reference/computer-info.md) Описывает компьютер, на котором работает отладчик.

- [CONST_GUID_ARRAY](../../../extensibility/debugger/reference/const-guid-array.md) Описывает список идентификаторов GUID.

- [CONTEXT_INFO](../../../extensibility/debugger/reference/context-info.md) Описывает контекст памяти или контекст кода.

- [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) Описывает адрес в отлаживаемой программе.

- [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md) Представляет один из нескольких различных видов адресов.

- [DEBUG_CUSTOM_VIEWER](../../../extensibility/debugger/reference/debug-custom-viewer.md) Определяет пользовательское средство просмотра или визуализатор типов.

- [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) Описывает свойство Debug, которое в свою очередь описывает объект иерархической природы с именем, типом и значением.

- [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) Описывает ссылку.

- [Дисассемблидата](../../../extensibility/debugger/reference/disassemblydata.md) Описывает дизассемблирование в интегрированную среду разработки для вывода.

- [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md) Описывает исключение или ошибку времени выполнения, вызванную отлаживаемой программой.

- [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md) Описывает локальную переменную, параметр или другое поле.

- [Фрамеинфо](../../../extensibility/debugger/reference/frameinfo.md) Описывает кадр стека.

- [GUID_ARRAY](../../../extensibility/debugger/reference/guid-array.md) Описывает массив уникальных идентификаторов для доступных модулей отладки.

- [JMC_CODE_SPEC](../../../extensibility/debugger/reference/jmc-code-spec.md) Используется для задания сведений Жустмикоде для модуля.

- [MACHINE_INFO](../../../extensibility/debugger/reference/machine-info.md) Описывает конкретный компьютер.

- [METADATA_ADDRESS_ARRAYELEM](../../../extensibility/debugger/reference/metadata-address-arrayelem.md) Описывает элемент массива в массиве.

- [METADATA_ADDRESS_FIELD](../../../extensibility/debugger/reference/metadata-address-field.md) Описывает адрес поля класса или структуры.

- [METADATA_ADDRESS_LOCAL](../../../extensibility/debugger/reference/metadata-address-local.md) Описывает адрес локальной переменной в области (обычно это функция или метод).

- [METADATA_ADDRESS_METHOD](../../../extensibility/debugger/reference/metadata-address-method.md) Описывает адрес метода класса.

- [METADATA_ADDRESS_PARAM](../../../extensibility/debugger/reference/metadata-address-param.md) Описывает параметр метода или функции.

- [METADATA_ADDRESS_RETVAL](../../../extensibility/debugger/reference/metadata-address-retval.md) Описывает возвращаемое значение из метода или функции.

- [METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md) Описывает тип поля, взятого из метаданных.

- [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md) Описывает конкретный модуль (DLL, EXE или сборку).

- [MODULE_SYMBOL_SEARCH_INFO](../../../extensibility/debugger/reference/module-symbol-search-info.md) Описание сведений о состоянии поиска символов в поисковых путях.

- [NATIVE_ADDRESS](../../../extensibility/debugger/reference/native-address.md) Описывает собственный адрес.

- [PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md) Описывает тип поля, взятого из символа PDB.

- [PENDING_BP_STATE_INFO](../../../extensibility/debugger/reference/pending-bp-state-info.md) Описывает состояние точки останова, готовой к привязке к расположению кода.

- [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md) Описывает процесс.

- [PROGRAM_NODE_ARRAY](../../../extensibility/debugger/reference/program-node-array.md) Описывает список объектов [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) , представляющих узлы программы.

- [PROVIDER_PROCESS_DATA](../../../extensibility/debugger/reference/provider-process-data.md) Описывает процессы, выполняемые на компьютере.

- [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) Описывает положение строк и столбцов в заданном тексте.

- [Среадпропертиес](../../../extensibility/debugger/reference/threadproperties.md) Описывает свойства потока.

- [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md) Описывает тип поля.

- [UNMANAGED_ADDRESS_PHYSICAL](../../../extensibility/debugger/reference/unmanaged-address-physical.md) Описывает физический адрес.

- [UNMANAGED_ADDRESS_THIS_RELATIVE](../../../extensibility/debugger/reference/unmanaged-address-this-relative.md) Описывает адрес, который является относительным по отношению к `this` указателю ( `Me` в Visual Basic).

## <a name="requirements"></a>Требования
 Заголовок: мсдбг. h, sh. h или ee. h

 Пространство имен: Microsoft. VisualStudio. Debugger. Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Справочник по интерфейсам API](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)
