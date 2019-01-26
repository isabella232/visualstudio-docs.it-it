---
title: La registrazione di un analizzatore di espressioni | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluators, registering
ms.assetid: 236be234-e05f-4ad8-9200-24ce51768ecf
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6007b7c7ab3dfd6d327cf4665af23386069ddc4b
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "55000753"
---
# <a name="register-an-expression-evaluator"></a>Registrare un analizzatore di espressioni
> [!IMPORTANT]
>  In Visual Studio 2015, questa modalità di implementazione analizzatori di espressioni è deprecata. Per informazioni sull'implementazione di analizzatori di espressioni CLR, vedere [analizzatori di espressioni CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) e [esempio analizzatore di espressioni gestite](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 L'analizzatore di espressioni (EE) deve registrarsi come una class factory con l'ambiente Windows COM e Visual Studio. Un EE è configurare sotto forma di DLL in modo che viene inserito nello spazio degli indirizzi (DE) del motore di debug o lo spazio degli indirizzi di Visual Studio, a seconda di quale entità crea un'istanza di motore di esecuzione.  
  
## <a name="managed-code-expression-evaluator"></a>Analizzatore di espressioni di codice gestito  
 Un codice gestito EE viene implementato come una libreria di classi, che è una DLL che si registra con l'ambiente COM, in genere avviato da una chiamata al programma VSIP *regpkg.exe*. Il processo effettivo di scrivere le chiavi del Registro di sistema per l'ambiente COM viene gestito automaticamente.  
  
 Un metodo della classe principale è contrassegnato con <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute>, che indica che il metodo da chiamare quando la DLL da registrare con COM. Questo metodo di registrazione, spesso denominato `RegisterClass`, esegue l'attività di registrazione della DLL con Visual Studio. Un oggetto corrispondente `UnregisterClass` (contrassegnato con il <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute>), Annulla gli effetti di `RegisterClass` quando viene disinstallata la DLL.  
 Le stesse voci del Registro di sistema vengono effettuate per un EE scritti in codice non gestito. l'unica differenza è che non vi sia alcuna funzione di supporto, ad esempio `SetEEMetric` per svolgere il lavoro per l'utente. Ecco un esempio del processo di registrazione e annullamento della registrazione.  
  
### <a name="example"></a>Esempio  
 La funzione seguente viene illustrato un codice gestito EE registra e Annulla la registrazione di se stesso con Visual Studio.  
  
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
 La DLL EE implementa il `DllRegisterServer` funzione per registrarsi con l'ambiente COM, oltre a Visual Studio.  
  
> [!NOTE]
>  È possibile trovare il codice di MyCEE codice esempio del Registro di sistema nel file *dllentry.cpp*, che si trova nell'installazione VSIP sotto EnVSDK\MyCPkgs\MyCEE.  
  
### <a name="dll-server-process"></a>Processo server DLL  
 Quando si registra l'analizzatore di Espressioni, il server DLL:  
  
1.  Registra la class factory `CLSID` in base alle convenzioni COM normale.  
  
2.  Chiama la funzione helper `SetEEMetric` da registrare con Visual Studio le metriche EE illustrate nella tabella seguente. La funzione `SetEEMetric` e la metrica specificata come indicato di seguito fanno parte del *dbgmetric.lib* libreria. Visualizzare [helper SDK per eseguire il debug](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) per informazioni dettagliate.  
  
    |Metrica|Descrizione|  
    |------------|-----------------|  
    |`metricCLSID`|`CLSID` della class factory EE|  
    |`metricName`|Nome del motore di esecuzione sotto forma di stringa visualizzabile|  
    |`metricLanguage`|Il nome del linguaggio che l'analizzatore di Espressioni è progettato per valutare|  
    |`metricEngine`|`GUID`i motori di debug (DE) che funzionano con questo EE s|  
  
    > [!NOTE]
    >  Il `metricLanguage``GUID` identifica la lingua da nome, ma è il `guidLang` argomento `SetEEMetric` che consente di selezionare la lingua. Quando il compilatore genera il file di informazioni di debug, consigliabile scrivere appropriato `guidLang` in modo che la Germania sappia quali EE da utilizzare. La Germania richiede in genere il provider di simboli per questa lingua `GUID`, che viene archiviato nel file di informazioni di debug.  
  
3.  Registra con Visual Studio tramite la creazione di chiavi in HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\\*x. y*, dove *x. y* è la versione di Visual Studio per registrarsi.  
  
### <a name="example"></a>Esempio  
 La funzione seguente viene illustrato un codice non gestito (C++) EE registra e Annulla la registrazione di se stesso con Visual Studio.  
  
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
 [La scrittura di un analizzatore di espressioni CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)   
 [Helper SDK per eseguire il debug](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)
