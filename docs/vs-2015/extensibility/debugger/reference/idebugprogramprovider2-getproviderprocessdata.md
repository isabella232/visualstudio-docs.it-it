---
title: IDebugProgramProvider2::GetProviderProcessData | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProgramProvider2::GetProviderProcessData
helpviewer_keywords:
- IDebugProgramProvider2::GetProviderProcessData
ms.assetid: 90cf7b7f-53d2-487e-b793-94501a6e24dd
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a50faf4531a098dde544adcffe535ed26e9c5cd8
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "68148513"
---
# <a name="idebugprogramprovider2getproviderprocessdata"></a>IDebugProgramProvider2::GetProviderProcessData
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Recupera un elenco di programmi in esecuzione da un processo specificato.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT GetProviderProcessData(  
   PROVIDER_FLAGS         Flags,  
   IDebugDefaultPort2*    pPort,  
   AD_PROCESS_ID          processId,  
   CONST_GUID_ARRAY       EngineFilter,  
   PROVIDER_PROCESS_DATA* pProcess  
);  
```  
  
```csharp  
int GetProviderProcessData(  
   enum_PROVIDER_FLAGS     Flags,  
   IDebugDefaultPort2      pPort,  
   AD_PROCESS_ID           ProcessId,  
   CONST_GUID_ARRAY        EngineFilter,  
   PROVIDER_PROCESS_DATA[] pProcess  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `Flags`  
 [in] Una combinazione di flag dal [PROVIDER_FLAGS](../../../extensibility/debugger/reference/provider-flags.md) enumerazione. I flag seguenti sono più comuni per questa chiamata:  
  
|Flag|Descrizione|  
|----------|-----------------|  
|`PFLAG_REMOTE_PORT`|Chiamante è in esecuzione nel computer remoto.|  
|`PFLAG_DEBUGGEE`|Chiamante è in corso il debug (verranno restituite informazioni aggiuntive sul marshalling per ogni nodo).|  
|`PFLAG_ATTACHED_TO_DEBUGGEE`|Chiamante è stato collegato a ma non avviare dal debugger.|  
|`PFLAG_GET_PROGRAM_NODES`|Chiamante è richiesto un elenco dei nodi di programma da restituire.|  
  
 `pPort`  
 [in] La porta del processo chiamante è in corso.  
  
 `processId`  
 [in] Un' [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) struttura che contiene l'ID del processo che contiene il programma in questione.  
  
 `EngineFilter`  
 [in] Una matrice di GUID per i motori di debug assegnato per il debug del processo (questi verrà utilizzati per filtrare i programmi che sono effettivamente restituiti basati su ciò che supportano i motori di fornito; se nessun motore vengono specificato, quindi verranno restituiti tutti i programmi).  
  
 `pProcess`  
 [out] Oggetto [PROVIDER_PROCESS_DATA](../../../extensibility/debugger/reference/provider-process-data.md) struttura compilata con le informazioni richieste.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 Questo metodo viene chiamato in genere da un processo per ottenere un elenco di programmi in esecuzione in tale processo. Le informazioni restituite sono elencate [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) oggetti.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)   
 [IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md)   
 [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md)   
 [CONST_GUID_ARRAY](../../../extensibility/debugger/reference/const-guid-array.md)   
 [PROVIDER_FLAGS](../../../extensibility/debugger/reference/provider-flags.md)   
 [PROVIDER_PROCESS_DATA](../../../extensibility/debugger/reference/provider-process-data.md)   
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
