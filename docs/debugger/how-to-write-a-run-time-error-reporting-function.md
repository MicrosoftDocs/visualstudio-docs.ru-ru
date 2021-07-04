---
title: Написание функции, сообщающей об ошибке во время выполнения (C++) | Документация Майкрософт
description: Примеры написания пользовательской функции, сообщающей об ошибке во время выполнения, в Visual Studio. Такая функция должна иметь то же объявление, что и _CrtDbgReportW, и возвращать значение 1.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- run-time errors, reporting functions
- reporting function
ms.assetid: 989bf312-5038-44f3-805f-39a34d18760e
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 6ff82afdfda8af746533f07f21d330c359a1618c
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2021
ms.locfileid: "112385143"
---
# <a name="how-to-write-a-run-time-error-reporting-function-c"></a>Практическое руководство. Написание функции, сообщающей об ошибке во время выполнения (C++)
Настраиваемая функция, сообщающая об ошибках, возникающих во время выполнения, должна иметь такое же объявление, что и `_CrtDbgReportW`. Она должна возвращать отладчику значение 1.

В следующем примере показано, как определяется настраиваемая функция, сообщающая об ошибках.

## <a name="example-1"></a>Пример 1

```cpp
#include <stdio.h>
int errorhandler = 0;
void configureMyErrorFunc(int i)
{
    errorhandler = i;
}

int MyErrorFunc(int errorType, const wchar_t *filename,
                int linenumber, const wchar_t *moduleName,
                const wchar_t *format, ...)
{
    switch (errorhandler)
    {
    case 0:
    case 1:
        wprintf(L"Error type %d at %s line %d in %s",
                errorType, filename, linenumber, moduleName);
        break;
    case 2:
    case 3:
        fprintf(stderr, "Error type");
        break;
    }

    return 1;
}
```

## <a name="example-2"></a>Пример 2
В следующем примере показана более сложная настраиваемая функция, сообщающая об ошибках. В данном примере оператор переключателя обрабатывает ошибки различных типов, как определено в параметре `reportType` функции `_CrtDbgReportW`. Поскольку `_CrtDbgReportW` заменяется, использовать `_CrtSetReportMode` нельзя. Функция должна обрабатывать выходные данные. Первый аргумент-переменная в этой функции принимает номер ошибки, возникшей во время выполнения. Дополнительные сведения см. в разделе [_RTC_SetErrorType](/cpp/c-runtime-library/reference/rtc-seterrortype).

```cpp
#include <windows.h>
#include <stdarg.h>
#include <rtcapi.h>
#include <malloc.h>
#pragma runtime_checks("", off)
int Catch_RTC_Failure(int errType, const wchar_t *file, int line,
                      const wchar_t *module, const wchar_t *format, ...)
{
    // Prevent re-entrance.
    static long running = 0;
    while (InterlockedExchange(&running, 1))
        Sleep(0);
    // Now, disable all RTC failures.
    int numErrors = _RTC_NumErrors();
    int *errors=(int*)_alloca(numErrors);
    for (int i = 0; i < numErrors; i++)
        errors[i] = _RTC_SetErrorType((_RTC_ErrorNumber)i, _RTC_ERRTYPE_IGNORE);

    // First, get the rtc error number from the var-arg list.
    va_list vl;
    va_start(vl, format);
    _RTC_ErrorNumber rtc_errnum = va_arg(vl, _RTC_ErrorNumber);
    va_end(vl);

    wchar_t buf[512];
    const char *err = _RTC_GetErrDesc(rtc_errnum);
    swprintf_s(buf, 512, L"%S\nLine #%d\nFile:%s\nModule:%s",
        err,
        line,
        file ? file : L"Unknown",
        module ? module : L"Unknown");
    int res = (MessageBox(NULL, buf, L"RTC Failed...", MB_YESNO) == IDYES) ? 1 : 0;
    // Now, restore the RTC errortypes.
    for(int i = 0; i < numErrors; i++)
        _RTC_SetErrorType((_RTC_ErrorNumber)i, errors[i]);
    running = 0;
    return res;
}
#pragma runtime_checks("", restore)
```

## <a name="example-3"></a>Пример 3
Используйте `_RTC_SetErrorFuncW`для установки настраиваемой функции вместо `_CrtDbgReportW`. Дополнительные сведения см. в разделе [_RTC_SetErrorFuncW](/cpp/c-runtime-library/reference/rtc-seterrorfuncw). `_RTC_SetErrorFuncW` является предшествующей функцией, сообщающей об ошибках, которую можно сохранить и, при необходимости, восстановить:

```cpp
#include <rtcapi.h>
int main()
{
    _RTC_error_fnW oldfunction, newfunc;
    oldfunction = _RTC_SetErrorFuncW(&MyErrorFunc);
    // Run some code.
    newfunc = _RTC_SetErrorFuncW(oldfunction);
    // newfunc == &MyErrorFunc;
    // Run some more code.
}
```

## <a name="see-also"></a>См. также
[Настройка проверок во время выполнения машинного кода](../debugger/native-run-time-checks-customization.md)
