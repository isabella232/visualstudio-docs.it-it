---
title: Registrazione di un analizzatore di espressioni | Microsoft Docs
description: Informazioni su come l'analizzatore di espressioni deve registrarsi come class factory con l'ambiente COM Windows e Visual Studio.
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
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: f928c97961076eaa9d6062d3d812963b1522451b
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126634675"
---
# <a name="register-an-expression-evaluator"></a>Registrare un analizzatore di espressioni
> [!IMPORTANT]
> In Visual Studio 2015 questa modalità di implementazione degli analizzatori di espressioni è deprecata. Per informazioni sull'implementazione di analizzatori di espressioni [CLR,](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) vedere Analizzatori di espressioni CLR e Esempio di [analizzatore di espressioni gestite.](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)

 L'analizzatore di espressioni (edizione Enterprise) deve registrarsi come class factory con l'ambiente COM Windows e Visual Studio. Un edizione Enterprise viene configurato come DLL in modo che sia inserito nello spazio degli indirizzi del motore di debug (DE) o nello spazio indirizzi Visual Studio, a seconda dell'entità che crea un'istanza del edizione Enterprise.

## <a name="managed-code-expression-evaluator"></a>Analizzatore di espressioni di codice gestito
 Un edizione Enterprise codice gestito viene implementato come libreria di classi, ovvero una DLL che si registra con l'ambiente COM, in genere avviata da una chiamata al programma VSIP, *regpkg.exe*. Il processo effettivo di scrittura delle chiavi del Registro di sistema per l'ambiente COM viene gestito automaticamente.

 Un metodo della classe principale è contrassegnato con , a indicare che il metodo deve essere chiamato quando <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute> la DLL viene registrata con COM. Questo metodo di registrazione, spesso denominato `RegisterClass` , esegue l'attività di registrazione della DLL con Visual Studio. Un oggetto `UnregisterClass` corrispondente (contrassegnato con <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute> ), annulla gli effetti di quando la DLL viene `RegisterClass` disinstallata.
Le stesse voci del Registro di sistema vengono effettuate come per un edizione Enterprise scritto in codice non gestito; L'unica differenza è che non esiste alcuna funzione helper, ad `SetEEMetric` esempio per eseguire il lavoro per l'utente. Di seguito è riportato un esempio del processo di registrazione e annullamento della registrazione.

### <a name="example"></a>Esempio
 La funzione seguente illustra come un codice gestito edizione Enterprise registra e annulla la registrazione con Visual Studio.

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

## <a name="unmanaged-code-expression-evaluator"></a>Analizzatore di espressioni di codice non gestito
 La DLL edizione Enterprise implementa la `DllRegisterServer` funzione per registrarsi con l'ambiente COM e Visual Studio.

> [!NOTE]
> È possibile trovare il codice del Registro di sistema dell'esempio di codice MyCEE nel file *dllentry.cpp*, che si trova nell'installazione di VSIP in EnVSDK\MyCPkgs\MyCEE.

### <a name="dll-server-process"></a>Processo server DLL
 Quando si registra il edizione Enterprise, il server DLL:

1. Registra i relativi class factory `CLSID` in base alle normali convenzioni COM.

2. Chiama la funzione helper `SetEEMetric` per eseguire la registrazione Visual Studio le edizione Enterprise metriche illustrate nella tabella seguente. La funzione `SetEEMetric` e le metriche specificate come indicato di seguito fanno parte della libreria *dbgmetric.lib.* Per [informazioni dettagliate, vedere Helper SDK](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) per il debug.

    |Metrica|Descrizione|
    |------------|-----------------|
    |`metricCLSID`|`CLSID`del edizione Enterprise class factory|
    |`metricName`|Nome del edizione Enterprise come stringa visualizzabile|
    |`metricLanguage`|Nome della lingua che l'edizione Enterprise è progettato per valutare|
    |`metricEngine`|`GUID`dei motori di debug (DE) che funzionano con questo edizione Enterprise|

    > [!NOTE]
    > identifica `metricLanguage``GUID` la lingua in base al nome, ma è `guidLang` l'argomento per `SetEEMetric` che seleziona la lingua. Quando il compilatore genera il file di informazioni di debug, deve scrivere l'oggetto appropriato in modo che DE sappia `guidLang` edizione Enterprise da usare. De richiede in genere il provider di simboli per questo linguaggio `GUID` , che viene archiviato nel file di informazioni di debug.

3. Registra con Visual Studio creando chiavi in HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\\ *X.Y,* dove *X.Y* è la versione di Visual Studio con cui eseguire la registrazione.

### <a name="example"></a>Esempio
 La funzione seguente illustra come un codice non gestito (C++) edizione Enterprise registra e annulla la registrazione con Visual Studio.

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

## <a name="see-also"></a>Vedi anche
- [Scrittura di un analizzatore di espressioni CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
- [Helper SDK per il debug](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)
