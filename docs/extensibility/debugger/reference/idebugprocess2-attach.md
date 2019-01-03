---
title: IDebugProcess2::Attach | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugProcess2::Attach
helpviewer_keywords:
- IDebugProcess2::Attach
ms.assetid: 40d78417-fde2-45c3-96c9-16e06bd9008d
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 717be88ebc0b7312bbb4c8a092fbe34969ddfc7a
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53860134"
---
# <a name="idebugprocess2attach"></a>IDebugProcess2::Attach
Collega gestore di sessione di debug (SDM) al processo.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT Attach(   
   IDebugEventCallback2* pCallback,  
   GUID*                 rgguidSpecificEngines,  
   DWORD                 celtSpecificEngines,  
   HRESULT*              rghrEngineAttach  
);  
```  
  
```csharp  
int Attach(   
   IDebugEventCallback2 pCallback,  
   Guid[]               rgguidSpecificEngines,  
   uint                 celtSpecificEngines,  
   int[]                rghrEngineAttach  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pCallback`  
 [in] Un' [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) oggetto utilizzato per la notifica degli eventi di debug.  
  
 `rgguidSpecificEngines`  
 [in] Una matrice di GUID dei motori di debug da utilizzare per il debug dei programmi in esecuzione nel processo. Questo parametro può essere un valore null. Per informazioni dettagliate, vedere la sezione Osservazioni.  
  
 `celtSpecificEngines`  
 [in] Il numero di debug motori nel `rgguidSpecificEngines` matrice e la dimensione del `rghrEngineAttach` matrice.  
  
 `rghrEngineAttach`  
 [in, out] Matrice di codici HRESULT restituiti dai motori di debug. La dimensione di questa matrice viene specificata nel `celtSpecificEngines` parametro. Ogni codice è generalmente `S_OK` o `S_ATTACH_DEFERRED`. Quest'ultimo indica che la Germania è attualmente connesso a nessun programma.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore. Nella tabella seguente mostra altri valori possibili.  
  
|Value|Descrizione|  
|-----------|-----------------|  
|`E_ATTACH_DEBUGGER_ALREADY_ATTACHED`|Il processo specificato è già collegato al debugger.|  
|`E_ATTACH_DEBUGGEE_PROCESS_SECURITY_VIOLATION`|Si è verificata una violazione della sicurezza durante la procedura di collegamento.|  
|`E_ATTACH_CANNOT_ATTACH_TO_DESKTOP`|Un processo del desktop non è possibile collegare il debugger.|  
  
## <a name="remarks"></a>Note  
 Connessione a un processo associa il modello SDM per tutti i programmi in esecuzione in tale processo che è possibile eseguire il debug per i motori di debug (DE) specificati nel `rgguidSpecificEngines` matrice. Impostare il `rgguidSpecificEngines` parametro in un valore null valore o includere `GUID_NULL` nella matrice da collegare a tutti i programmi nel processo.  
  
 Tutti gli eventi di debug che si verificano nel processo vengono inviati per il dato [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) oggetto. Ciò `IDebugEventCallback2` oggetto viene fornito quando il modello SDM chiama questo metodo.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)