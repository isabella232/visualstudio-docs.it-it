---
title: IDebugProgramProvider2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProgramProvider2
helpviewer_keywords:
- IDebugProgramProvider2 interface
ms.assetid: a9ec7b3e-a59c-4069-b2ee-6f45916eeb78
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6a3ccac5dc60c10983d3b1a33978196fad5197d6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68146315"
---
# <a name="idebugprogramprovider2"></a>IDebugProgramProvider2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Questa interfaccia registrata consente a gestione debug sessione (SDM) di ottenere informazioni sui programmi che sono stati "pubblicati" tramite l'interfaccia [IDebugProgramPublisher2](../../../extensibility/debugger/reference/idebugprogrampublisher2.md) .  
  
## <a name="syntax"></a>Sintassi  
  
```  
IDebugProgramProvider2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Note per gli implementatori  
 Il motore di debug (DE) implementa questa interfaccia per fornire informazioni sui programmi di cui è in corso il debug. Questa interfaccia è registrata nella sezione DE del registro di sistema usando la metrica `metricProgramProvider` , come descritto in [Helper SDK per il debug](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md).  
  
## <a name="notes-for-callers"></a>Note per i chiamanti  
 Chiamare `CoCreateInstance` la funzione com con il `CLSID` del provider di programmi ottenuto dal registro di sistema. Vedere l'esempio.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine vtable  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[GetProviderProcessData](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md)|Ottiene informazioni sui programmi in esecuzione, filtrati in diversi modi.|  
|[GetProviderProgramNode](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprogramnode.md)|Ottiene un nodo di programma, in base a un ID di processo specifico.|  
|[WatchForProviderEvents](../../../extensibility/debugger/reference/idebugprogramprovider2-watchforproviderevents.md)|Stabilisce un callback da controllare per gli eventi del provider associati a tipi specifici di processi.|  
|[SetLocale](../../../extensibility/debugger/reference/idebugprogramprovider2-setlocale.md)|Stabilisce le impostazioni locali per tutte le risorse specifiche della lingua richieste da DE.|  
  
## <a name="remarks"></a>Osservazioni  
 In genere, un processo usa questa interfaccia per individuare i programmi in esecuzione in tale processo.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg. h  
  
 Spazio dei nomi: Microsoft. VisualStudio. Debugger. Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="example"></a>Esempio  
  
```cpp#  
IDebugProgramProvider2 *GetProgramProvider(GUID *pDebugEngineGuid)  
{  
    // This is typically defined globally.  For this example, it is  
    // defined here.  
    static const WCHAR strRegistrationRoot[] = L"Software\\Microsoft\\VisualStudio\\8.0Exp";  
    IDebugProgramProvider2 *pProvider = NULL;  
    if (pDebugEngineGuid != NULL) {  
        CLSID clsidProvider = { 0 };  
        ::GetMetric(NULL,  
                    metrictypeEngine,  
                    *pDebugEngineGuid,  
                    metricProgramProvider,  
                    &clsidProvider,  
                    strRegistrationRoot);  
        if (!IsEqualGUID(clsidProvider,GUID_NULL)) {  
            CComPtr<IDebugProgramProvider2> spProgramProvider;  
            spProgramProvider.CoCreateInstance(clsidProvider);  
            if (spProgramProvider != NULL) {  
                pProvider = spProgramProvider.Detach();  
            }  
        }  
    }  
    return(pProvider);  
}  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgramPublisher2](../../../extensibility/debugger/reference/idebugprogrampublisher2.md)   
 [Helper SDK per il debug](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)
