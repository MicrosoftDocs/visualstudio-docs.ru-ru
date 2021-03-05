---
description: Запускает исполняемый файл.
title: 'IDebugPortEx2:: Лаунчсуспендед | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortEx2::LaunchSuspended
helpviewer_keywords:
- IDebugPortEx2::LaunchSuspended
ms.assetid: 34b2cf99-2e52-4757-8969-1d12ac517ec0
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b5982ad665333aa4d11e2098d3b148db88e77c32
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102142833"
---
# <a name="idebugportex2launchsuspended"></a>IDebugPortEx2::LaunchSuspended
Запускает исполняемый файл.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT LaunchSuspended( 
   LPCOLESTR        pszExe,
   LPCOLESTR        pszArgs,
   LPCOLESTR        pszDir,
   BSTR             bstrEnv,
   DWORD            hStdInput,
   DWORD            hStdOutput,
   DWORD            hStdError,
   IDebugProcess2** ppPortProcess
);
```

```csharp
int LaunchSuspended( 
   string             pszExe,
   string             pszArgs,
   string             pszDir,
   string             bstrEnv,
   uint               hStdInput,
   uint               hStdOutput,
   uint               hStdError,
   out IDebugProcess2 ppPortProcess
);
```

## <a name="parameters"></a>Параметры
`pszExe`\
окне Имя исполняемого файла, который необходимо запустить. Это может быть полный путь или относительно рабочего каталога, указанного в `pszDir` параметре.

`pszArgs`\
окне Аргументы для передачи в исполняемый файл. Может иметь значение null, если аргументы отсутствуют.

`pszDir`\
окне Имя рабочего каталога, используемого исполняемым файлом. Может иметь значение null, если рабочий каталог не требуется.

`bstrEnv`\
окне Блок среды строк, заканчивающихся нулем, за которыми следует дополнительный символ NULL.

`hStdInput`\
окне Обработчик для альтернативного входного потока. Может иметь значение 0, если перенаправление не требуется.

`hStdOutput`\
окне Обработчик для альтернативного выходного потока. Может иметь значение 0, если перенаправление не требуется.

`hStdError`\
окне Обработчик альтернативного выходного потока ошибок. Может иметь значение 0, если перенаправление не требуется.

`ppPortProcess`\
заполняет Возвращает объект [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) , представляющий запущенный процесс.

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Комментарии
 Этот метод должен запустить процесс, чтобы он был приостановлен и не выполнял никакого кода. Метод [ресумепроцесс](../../../extensibility/debugger/reference/idebugportex2-resumeprocess.md) вызывается для возобновления процесса.

 Программу также можно запустить из модуля отладки. Дополнительные сведения см. [в разделе Запуск программы](../../../extensibility/debugger/launching-a-program.md).

## <a name="see-also"></a>См. также раздел
- [IDebugPortEx2](../../../extensibility/debugger/reference/idebugportex2.md)
- [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)
- [ResumeProcess](../../../extensibility/debugger/reference/idebugportex2-resumeprocess.md)
- [Запуск программы](../../../extensibility/debugger/launching-a-program.md)
