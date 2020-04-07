---
title: Registrazione di un analizzatore di espressioni . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluators, registering
ms.assetid: 236be234-e05f-4ad8-9200-24ce51768ecf
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 600f7c8a2e2957cddf23ccc82b0872617e491940
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80713202"
---
# <a name="register-an-expression-evaluator"></a>Registrare un analizzatore di espressioniRegister an expression evaluator
> [!IMPORTANT]
> In Visual Studio 2015, questo modo di implementare gli analizzatori di espressioni è deprecato. Per informazioni sull'implementazione degli analizzatori di espressioni CLR, vedere [Analizzatori](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) di espressioni CLR e Esempio di [analizzatore di espressioni gestite](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 L'analizzatore di espressioni (EE) deve registrarsi come class factory sia con l'ambiente COM di Windows che con Visual Studio. Un EE è impostato come una DLL in modo che venga inserito nello spazio degli indirizzi del motore di debug (DE) o nello spazio degli indirizzi di Visual Studio, a seconda di quale entità crea un'istanza di EE.

## <a name="managed-code-expression-evaluator"></a>Analizzatore di espressioni di codice gestito
 Un EE di codice gestito viene implementato come libreria di classi, ovvero una DLL che si registra con l'ambiente COM, in genere avviata da una chiamata al programma VSIP, *regpkg.exe*. Il processo effettivo di scrittura delle chiavi del Registro di sistema per l'ambiente COM viene gestito automaticamente.

 Un metodo della classe main <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute>è contrassegnato con , a indicare che il metodo deve essere chiamato quando la DLL viene registrata con COM. Questo metodo di `RegisterClass`registrazione, spesso chiamato , esegue l'attività di registrazione della DLL con Visual Studio. Un `UnregisterClass` corrispondente (contrassegnato con il <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute> `RegisterClass` ), annulla gli effetti di quando la DLL viene disinstallata.
Le stesse voci del Registro di sistema vengono effettuate come per un EE scritto in codice non gestito; l'unica differenza è che non `SetEEMetric` esiste alcuna funzione di supporto come fare il lavoro per voi. Di seguito è riportato un esempio del processo di registrazione e annullamento della registrazione.

### <a name="example"></a>Esempio
 La funzione seguente mostra come un codice gestito EE registra e annulla la registrazione con Visual Studio.The following function shows how a managed code EE registers and unregisters itself with Visual Studio.

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

## <a name="unmanaged-code-expression-evaluator"></a>Analizzatore di espressioni di codice non gestitoUnmanaged code expression evaluator
 La DLL EE `DllRegisterServer` implementa la funzione per registrarsi con l'ambiente COM e Visual Studio.

> [!NOTE]
> Il codice del codice MyCEE è codice del Registro di sistema di esempio nel file *dllentry.cpp*, che si trova nell'installazione di VSIP in EnVSDK, MyCPkgkgs, MyCEE.

### <a name="dll-server-process"></a>Processo server DLL
 Durante la registrazione di EE, il server DLL:

1. Registra la class `CLSID` factory in base alle normali convenzioni COM.

2. Chiama la `SetEEMetric` funzione di supporto per registrare con Visual Studio le metriche Di EE illustrate nella tabella seguente. La `SetEEMetric` funzione e le metriche specificate come segue fanno parte della libreria *dbgmetric.lib.* Per informazioni dettagliate, vedere [gli helper SDK per il debug.](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)

    |Metrica|Descrizione|
    |------------|-----------------|
    |`metricCLSID`|`CLSID`della fabbrica di classi EE|
    |`metricName`|Nome dell'EE come stringa visualizzabile|
    |`metricLanguage`|Il nome della lingua a cui è destinato l'EE|
    |`metricEngine`|`GUID`s dei motori di debug (DE) che funzionano con questo EE|

    > [!NOTE]
    > Identifica `metricLanguage``GUID` la lingua in base al `guidLang` `SetEEMetric` nome, ma è l'argomento che seleziona la lingua. Quando il compilatore genera il file di `guidLang` informazioni di debug, deve scrivere l'appropriato in modo che il DE sappia quale EE utilizzare. Il DE richiede in genere `GUID`il provider di simboli per questa lingua , che viene archiviato nel file di informazioni di debug.

3. Esegue la registrazione con Visual Studio creando le chiavi\\*X.Y*in HKEY_LOCAL_MACHINE SOFTWARE , dove *X.Y* è la versione di Visual Studio con cui eseguire la registrazione.

### <a name="example"></a>Esempio
 La funzione seguente mostra come un codice non gestito (C ) EE registra e annulla la registrazione con Visual Studio.

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

## <a name="see-also"></a>Vedere anche
- [Scrittura di un analizzatore di espressioni CLRWriting a CLR expression evaluator](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
- [Helper SDK per il debug](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)
