---
title: Registrazione di un analizzatore di espressioni | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluators, registering
ms.assetid: 236be234-e05f-4ad8-9200-24ce51768ecf
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 3595daa51fddf5c9c027d5643382918d85f83cc1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "90840313"
---
# <a name="registering-an-expression-evaluator"></a>Registrazione di un analizzatore di espressioni
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

> [!IMPORTANT]
> In Visual Studio 2015, questo metodo di implementazione degli analizzatori di espressioni è deprecato. Per informazioni sull'implementazione degli analizzatori di espressioni CLR, vedere l'esempio degli [analizzatori](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) di espressioni CLR e dell' [analizzatore di espressioni gestite](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 L'analizzatore di espressioni (EE) deve registrarsi come class factory con l'ambiente COM Windows e Visual Studio. Un EE viene implementato come DLL in modo che possa essere inserito nello spazio degli indirizzi del motore di debug (DE) o nello spazio degli indirizzi di Visual Studio, a seconda dell'entità che crea un'istanza di EE.  
  
## <a name="managed-code-expression-evaluator"></a>Analizzatore di espressioni del codice gestito  
 Un codice gestito EE viene implementato come libreria di classi, ovvero una DLL che si registra con l'ambiente COM, in genere avviata da una chiamata al programma VSIP, **regpkg.exe**. Il processo effettivo di scrittura delle chiavi del registro di sistema per l'ambiente COM viene gestito automaticamente.  
  
 Un metodo della classe principale è contrassegnato con <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute> , che indica che il metodo deve essere chiamato quando la dll viene registrata con com. Questo metodo di registrazione, spesso chiamato `RegisterClass` , esegue l'attività di registrazione della dll con Visual Studio. Oggetto corrispondente `UnregisterClass` (contrassegnato con <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute> ), che annulla gli effetti del `RegisterClass` momento in cui la dll viene disinstallata.  
  
 Le stesse voci del registro di sistema vengono apportate come per un EE scritto in codice non gestito; l'unica differenza è che non esiste alcuna funzione di supporto, ad esempio `SetEEMetric` per eseguire il lavoro. Un esempio di questo processo di registrazione/annullamento della registrazione ha un aspetto simile al seguente:  
  
### <a name="example"></a>Esempio  
 Questa funzione Mostra come un codice gestito EE registra e Annulla la registrazione con Visual Studio.  
  
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
 La DLL EE implementa la `DllRegisterServer` funzione per la registrazione con l'ambiente com e con Visual Studio.  
  
> [!NOTE]
> Il codice di esempio del registro di sistema MyCEE è disponibile nel file DLLEntry. cpp, disponibile nell'installazione di VSIP in EnVSDK\MyCPkgs\MyCEE.  
  
### <a name="dll-server-process"></a>Processo server DLL  
 Quando si registra l'EE, il server DLL:  
  
1. Registra la class factory `CLSID` come per le normali convenzioni com.  
  
2. Chiama la funzione helper `SetEEMetric` per registrare con Visual Studio le metriche EE mostrate nella tabella seguente. La funzione `SetEEMetric` e le metriche specificate di seguito fanno parte della libreria dbgmetric. lib. Per informazioni dettagliate, vedere [Helper SDK per il debug](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) .  
  
    |Metrica|Descrizione|  
    |------------|-----------------|  
    |`metricCLSID`|`CLSID` del class factory EE|  
    |`metricName`|Nome dell'EE come stringa visualizzabile|  
    |`metricLanguage`|Nome della lingua progettata per la valutazione dell'EE|  
    |`metricEngine`|`GUID`s dei motori di debug (DE) che funzionano con questo EE|  
  
    > [!NOTE]
    > `metricLanguage``GUID`Identifica la lingua in base al nome, ma è l' `guidLang` argomento a `SetEEMetric` che seleziona la lingua. Quando il compilatore genera il file di informazioni di debug, deve scrivere l'oggetto appropriato `guidLang` in modo che conosca l'EE da usare. Il DE richiede in genere il provider di simboli per questa lingua `GUID` , archiviata nel file di informazioni di debug.  
  
3. Esegue la registrazione con Visual Studio mediante la creazione di chiavi in HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\VisualStudio \\ *x. y*, dove *x. y* è la versione di Visual Studio con cui eseguire la registrazione.  
  
### <a name="example"></a>Esempio  
 Questa funzione Mostra come un codice non gestito (C++) EE registra e Annulla la registrazione con Visual Studio.  
  
```cpp#  
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
 [Scrittura di un analizzatore di espressioni CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)   
 [Helper SDK per il debug](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)
