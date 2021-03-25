---
title: Регистрация средства оценки выражений | Документация Майкрософт
description: Узнайте, как средство оценки выражений должно регистрироваться как фабрика классов с помощью среды Windows COM и Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluators, registering
ms.assetid: 236be234-e05f-4ad8-9200-24ce51768ecf
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 3cf6998a9dd8bc521d8d5c7b8bd3e598e9a4e3bc
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105070652"
---
# <a name="register-an-expression-evaluator"></a>Регистрация средства оценки выражений
> [!IMPORTANT]
> В Visual Studio 2015 такой способ реализации оценивающих выражений является устаревшим. Дополнительные сведения о реализации вычислителей выражений CLR см. в разделе средства [оценки выражений CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) и [Пример управляемого средства оценки выражений](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Средство оценки выражений (EE) должно зарегистрировать себя как фабрика класса как в среде Windows COM, так и в Visual Studio. EE настраивается как библиотека DLL, чтобы она была внедрена в адресное пространство отладчика (DE) или в адресное пространство Visual Studio в зависимости от того, какая сущность создает экземпляр EE.

## <a name="managed-code-expression-evaluator"></a>Средство оценки выражений управляемого кода
 Управляемый код EE реализуется как библиотека классов, которая является библиотекой DLL, которая регистрируется в среде COM, обычно запускаемой вызовом программы VSIP, *regpkg.exe*. Фактический процесс записи разделов реестра для среды COM осуществляется автоматически.

 Метод основного класса помечается атрибутом <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute> , указывающим, что метод должен вызываться при регистрации библиотеки DLL в com. Этот метод регистрации, часто называемый `RegisterClass` , выполняет задачу регистрации библиотеки DLL в Visual Studio. Соответствующий `UnregisterClass` (помеченный <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute> ), отменяет эффекты `RegisterClass` при удалении библиотеки DLL.
Те же записи реестра создаются так же, как и для EE, написанного в неуправляемом коде; Единственное отличие заключается в отсутствии вспомогательной функции, например, `SetEEMetric` для выполнения работы. Ниже приведен пример процесса регистрации и отмены регистрации.

### <a name="example"></a>Пример
 Следующая функция показывает, как управляемый код EE регистрируется и отменяет регистрацию в Visual Studio.

```csharp
namespace EEMC
{
    [GuidAttribute("462D4A3D-B257-4AEE-97CD-5918C7531757")]
    public class EEMCClass : IDebugExpressionEvaluator
    {
        #region Register and unregister.
        private static Guid guidMycLang = new Guid("462D4A3E-B257-4AEE-97CD-5918C7531757");
        private static string languageName = "MyC";
        private static string eeName = "MyC Expression Evaluator";

        private static Guid guidMicrosoftVendor = new Guid("994B45C4-E6E9-11D2-903F-00C04FA302A1");
        private static Guid guidCOMPlusOnlyEng = new Guid("449EC4CC-30D2-4032-9256-EE18EB41B62B");
        private static Guid guidCOMPlusNativeEng = new Guid("92EF0900-2251-11D2-B72E-0000F87572EF");

        /// <summary>
        /// Register the expression evaluator.
        /// Set "project properties/configuration properties/build/register for COM interop" to true.
        /// </summary>
         [ComRegisterFunctionAttribute]
        public static void RegisterClass(Type t)
        {
            // Get Visual Studio version (set by regpkg.exe)
            string hive = Environment.GetEnvironmentVariable("EnvSdk_RegKey");
            string s = @"SOFTWARE\Microsoft\VisualStudio\"
                        + hive
                        + @"\AD7Metrics\ExpressionEvaluator";

            RegistryKey rk = Registry.LocalMachine.CreateSubKey(s);
            if (rk == null)  return;

            rk = rk.CreateSubKey(guidMycLang.ToString("B"));
            rk = rk.CreateSubKey(guidMicrosoftVendor.ToString("B"));
            rk.SetValue("CLSID", t.GUID.ToString("B"));
            rk.SetValue("Language", languageName);
            rk.SetValue("Name", eeName);

            rk = rk.CreateSubKey("Engine");
            rk.SetValue("0", guidCOMPlusOnlyEng.ToString("B"));
            rk.SetValue("1", guidCOMPlusNativeEng.ToString("B"));
        }
        /// <summary>
        /// Unregister the expression evaluator.
        /// </summary>
         [ComUnregisterFunctionAttribute]
        public static void UnregisterClass(Type t)
        {
            // Get Visual Studio version (set by regpkg.exe)
            string hive = Environment.GetEnvironmentVariable("EnvSdk_RegKey");
            string s = @"SOFTWARE\Microsoft\VisualStudio\"
                        + hive
                        + @"\AD7Metrics\ExpressionEvaluator\"
                        + guidMycLang.ToString("B");
            RegistryKey key = Registry.LocalMachine.OpenSubKey(s);
            if (key != null)
            {
                key.Close();
                Registry.LocalMachine.DeleteSubKeyTree(s);
            }
        }
    }
}
```

## <a name="unmanaged-code-expression-evaluator"></a>Вычислители выражений неуправляемого кода
 Библиотека DLL EE реализует `DllRegisterServer` функцию для регистрации в среде com, а также в Visual Studio.

> [!NOTE]
> Пример кода реестра Мицее можно найти в файле *дллентри. cpp*, который находится в установке VSIP в разделе енвсдк\микпкгс\мицее.

### <a name="dll-server-process"></a>Серверный процесс DLL
 При регистрации EE — сервер DLL:

1. Регистрирует фабрику класса в `CLSID` соответствии с обычными соглашениями COM.

2. Вызывает вспомогательную функцию `SetEEMetric` для регистрации в Visual Studio метрики ee, показанные в следующей таблице. Функция `SetEEMetric` и метрики, указанные следующим образом, являются частью библиотеки *дбгметрик. lib* . Дополнительные сведения см. в разделе [вспомогательные методы SDK для отладки](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) .

    |Метрика|Описание|
    |------------|-----------------|
    |`metricCLSID`|`CLSID` фабрики класса EE|
    |`metricName`|Имя EE в виде отображаемой строки|
    |`metricLanguage`|Название языка, который должен быть рассчитан EE|
    |`metricEngine`|`GUID`модулей отладки (DE), работающих с этим EE|

    > [!NOTE]
    > `metricLanguage``GUID`Определяет язык по имени, но он является `guidLang` аргументом `SetEEMetric` , который выбирает язык. Когда компилятор создает файл отладочной информации, он должен записать соответствующее значение, `guidLang` чтобы параметр de знал, какой ee следует использовать. Обычно в параметре DE запрашивается поставщик символов для этого языка `GUID` , который хранится в файле отладочной информации.

3. Регистрирует в Visual Studio, создавая ключи в разделе HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\\ *X. y*, где *X. y* — это версия Visual Studio для регистрации.

### <a name="example"></a>Пример
 Следующая функция показывает, как неуправляемый код (C++) EE регистрирует и отменяет регистрацию в Visual Studio.

```cpp
/*---------------------------------------------------------
  Registration
-----------------------------------------------------------*/
#ifndef LREGKEY_VISUALSTUDIOROOT
    #define LREGKEY_VISUALSTUDIOROOT L"Software\\Microsoft\\VisualStudio\\8.0"
#endif

static HRESULT RegisterMetric( bool registerIt )
{
    // check where we should register
    const ULONG cchBuffer = _MAX_PATH;
    WCHAR wszRegistrationRoot[cchBuffer];
    DWORD cchFreeBuffer = cchBuffer - 1;
    wcscpy(wszRegistrationRoot, LREGKEY_VISUALSTUDIOROOT_NOVERSION);
    wcscat(wszRegistrationRoot, L"\\");

    // this is Environment SDK specific
    // we check for  EnvSdk_RegKey environment variable to
    // determine where to register
    DWORD cchDefRegRoot = lstrlenW(LREGKEY_VISUALSTUDIOROOT_NOVERSION) + 1;
    cchFreeBuffer = cchFreeBuffer - cchDefRegRoot;
    DWORD cchEnvVarRead = GetEnvironmentVariableW(
        /* LPCTSTR */ L"EnvSdk_RegKey", // environment variable name
        /* LPTSTR  */ &wszRegistrationRoot[cchDefRegRoot],// buffer for variable value
        /* DWORD   */ cchFreeBuffer);// size of buffer
    if (cchEnvVarRead >= cchFreeBuffer)
        return E_UNEXPECTED;
    // If the environment variable does not exist then we must use
    // LREGKEY_VISUALSTUDIOROOT which has the version number.
    if (0 == cchEnvVarRead)
        wcscpy(wszRegistrationRoot, LREGKEY_VISUALSTUDIOROOT);

    if (registerIt)
    {
        SetEEMetric(guidMycLang,
                    guidMicrosoftVendor,
                    metricCLSID,
                    CLSID_MycEE,
                    wszRegistrationRoot );
        SetEEMetric(guidMycLang,
                    guidMicrosoftVendor,
                    metricName,
                    GetString(IDS_INFO_MYCDESCRIPTION),
                    wszRegistrationRoot );
        SetEEMetric(guidMycLang,
                    guidMicrosoftVendor,
                    metricLanguage, L"MyC",
                    wszRegistrationRoot);

        GUID engineGuids[2];
        engineGuids[0] = guidCOMPlusOnlyEng;
        engineGuids[1] = guidCOMPlusNativeEng;
        SetEEMetric(guidMycLang,
                    guidMicrosoftVendor,
                    metricEngine,
                    engineGuids,
                    2,
                    wszRegistrationRoot);
    }
    else
    {
        RemoveEEMetric( guidMycLang,
                        guidMicrosoftVendor,
                        metricCLSID,
                        wszRegistrationRoot);
        RemoveEEMetric( guidMycLang,
                        guidMicrosoftVendor,
                        metricName,
                        wszRegistrationRoot );
        RemoveEEMetric( guidMycLang,
                        guidMicrosoftVendor,
                        metricLanguage,
                        wszRegistrationRoot );
        RemoveEEMetric( guidMycLang,
                        guidMicrosoftVendor,
                        metricEngine,
                        wszRegistrationRoot );
    }

    return S_OK;
}
```

## <a name="see-also"></a>См. также
- [Написание вычислителя выражений CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
- [Вспомогательные методы SDK для отладки](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)
