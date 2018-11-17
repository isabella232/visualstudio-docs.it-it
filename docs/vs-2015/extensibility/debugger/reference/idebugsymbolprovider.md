---
title: IDebugSymbolProvider | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugSymbolProvider
helpviewer_keywords:
- IDebugSymbolProvider interface
ms.assetid: df5f095f-1dee-46f9-84cf-92417c71d5fb
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: fb2535cdbb75a2012134b9d439fd522617e3231b
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/16/2018
ms.locfileid: "51775095"
---
# <a name="idebugsymbolprovider"></a>IDebugSymbolProvider
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Questa interfaccia rappresenta un provider di simboli che fornisce i simboli e i tipi, che vengono restituiti come campi.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IDebugSymbolProvider : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Note per gli implementatori  
 Un provider di simboli debba implementare questa interfaccia per fornire simboli e informazioni sui tipi per un analizzatore di espressioni.  
  
## <a name="notes-for-callers"></a>Note per i chiamanti  
 Questa interfaccia viene ottenuta tramite COM `CoCreateInstance` (funzione) (per i provider di simboli non gestito) o caricando appropriato gestiti assembly di codice e creazione di provider di simboli sulla base delle informazioni disponibili in tale assembly. Crea un'istanza di motore di debug al provider di simboli di lavorare insieme con l'analizzatore di espressioni. Vedere l'esempio per uno degli approcci per creare un'istanza di questa interfaccia.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
 Nella tabella seguente sono illustrati i metodi di `IDebugSymbolProvider`.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|`Initialize`|Deprecato. Non usare.|  
|`Uninitialize`|Deprecato. Non usare.|  
|[GetContainerField](../../../extensibility/debugger/reference/idebugsymbolprovider-getcontainerfield.md)|Ottiene il campo che contiene l'indirizzo di debug.|  
|`GetField`|Deprecato. Non usare.|  
|[GetAddressesFromPosition](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromposition.md)|Esegue il mapping di una posizione di documento in una matrice di indirizzi di debug.|  
|[GetAddressesFromContext](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromcontext.md)|Esegue il mapping di un contesto di documento in una matrice di indirizzi di debug.|  
|[GetContextFromAddress](../../../extensibility/debugger/reference/idebugsymbolprovider-getcontextfromaddress.md)|Esegue il mapping di un indirizzo di debug in un contesto di documento.|  
|[GetLanguage](../../../extensibility/debugger/reference/idebugsymbolprovider-getlanguage.md)|Ottiene il linguaggio utilizzato per compilare il codice in corrispondenza dell'indirizzo di debug.|  
|`GetGlobalContainer`|Deprecato. Non usare.|  
|[GetMethodFieldsByName](../../../extensibility/debugger/reference/idebugsymbolprovider-getmethodfieldsbyname.md)|Ottiene il campo che rappresenta un nome di metodo completo.|  
|[GetClassTypeByName](../../../extensibility/debugger/reference/idebugsymbolprovider-getclasstypebyname.md)|Ottiene il tipo di campo di classe che rappresenta il nome completo della classe.|  
|[GetNamespacesUsedAtAddress](../../../extensibility/debugger/reference/idebugsymbolprovider-getnamespacesusedataddress.md)|Crea un enumeratore per gli spazi dei nomi associato all'indirizzo di debug.|  
|[GetTypeByName](../../../extensibility/debugger/reference/idebugsymbolprovider-gettypebyname.md)|Nome di un simbolo viene eseguito il mapping a un tipo di simbolo.|  
|[GetNextAddress](../../../extensibility/debugger/reference/idebugsymbolprovider-getnextaddress.md)|Ottiene l'indirizzo di debug che segue un indirizzo di debug specificato in un metodo.|  
  
## <a name="remarks"></a>Note  
 Questa interfaccia viene eseguito il mapping delle posizioni di documento in indirizzi di debug e viceversa.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="example"></a>Esempio  
 In questo esempio viene illustrato come creare un'istanza del provider di simboli, dato il relativo GUID (un motore di debug deve conoscere questo valore).  
  
```cpp#  
// A debug engine uses its own symbol provider and would know the GUID  
// of that provider.  
IDebugSymbolProvider *GetSymbolProvider(GUID *pSymbolProviderGuid)  
{  
    // This is typically defined globally.  For this example, it is  
    // defined here.  
    static const WCHAR strRegistrationRoot[] = L"Software\\Microsoft\\VisualStudio\\8.0Exp";  
    IDebugSymbolProvider *pProvider = NULL;  
    if (pSymbolProviderGuid != NULL) {  
        CLSID clsidProvider = { 0 };  
        ::GetSPMetric(*pSymbolProviderGuid,  
                      storetypeFile,  
                      metricCLSID,  
                      &clsidProvider,  
                      strRegistrationRoot);  
        if (IsEqualGUID(clsidProvider,GUID_NULL)) {  
            // No file type provider, try metadata provider.  
            ::GetSPMetric(*pSymbolProviderGuid,  
                          ::storetypeMetadata,  
                          metricCLSID,  
                          &clsidProvider,  
                          strRegistrationRoot);  
        }  
        if (!IsEqualGUID(clsidProvider,GUID_NULL)) {  
            CComPtr<IDebugSymbolProvider> spSymbolProvider;  
            spSymbolProvider.CoCreateInstance(clsidProvider);  
            if (spSymbolProvider != NULL) {  
                pProvider = spSymbolProvider.Detach();  
            }  
        }  
    }  
    return(pProvider);  
}  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Interfacce del provider di simboli](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)

