---
title: IDebugEngine2::Attach | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugEngine2::Attach
helpviewer_keywords:
- IDebugEngine2::Attach
ms.assetid: 173dcbda-5019-4c5e-bca9-a071838b5739
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 9d08ceb5db30b23d9e8df77bec12c0f9cb1c2c77
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53854243"
---
# <a name="idebugengine2attach"></a>IDebugEngine2::Attach
Collega un motore di debug (DE) a una o più programmi. Chiamato dal gestore di sessione di debug (SDM) quando il DE è in esecuzione in-process per il modello SDM.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT Attach(   
   IDebugProgram2**      pProgram,  
   IDebugProgramNode2**  rgpProgramNodes,  
   DWORD                 celtPrograms,  
   IDebugEventCallback2* pCallback,  
   ATTACH_REASON         dwReason  
);  
```  
  
```csharp  
int Attach(   
   IDebugProgram2[]     pProgram,  
   IDebugProgramNode2[] rgpProgramNodes,  
   uint                 celtPrograms,  
   IDebugEventCallback2 pCallback,  
   Enum_ATTACH_REASON   dwReason  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pProgram`  
 [in] Matrice di [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) gli oggetti che rappresentano i programmi da collegare alle. Si tratta di porting di programmi.  
  
 `rgpProgramNodes`  
 [in] Matrice di [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) gli oggetti che rappresentano i nodi di programma, uno per ogni programma. I nodi di programma nella matrice rappresentano gli stessi programmi come in `pProgram`. I nodi di programma vengono assegnati in modo che la Germania possa identificare i programmi a cui connettersi.  
  
 `celtPrograms`  
 [in] Numero di programmi e/o nodi programma il `pProgram` e `rgpProgramNodes` matrici.  
  
 `pCallback`  
 [in] Il [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) oggetto da utilizzare per inviare gli eventi di debug per il modello SDM.  
  
 `dwReason`  
 [in] Un valore compreso il [ATTACH_REASON](../../../extensibility/debugger/reference/attach-reason.md) enumerazione che specifica il motivo per il collegamento di questi programmi. Per altre informazioni, vedere la sezione Osservazioni.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 Esistono tre motivi per la connessione a un programma, come indicato di seguito:  
  
- `ATTACH_REASON_LAUNCH` indica che la Germania riguarda il collegamento al programma perché l'utente ha avviato il processo che lo contiene.  
  
- `ATTACH_REASON_USER` indica che l'utente ha richiesto in modo esplicito il DE collegare a un programma (o il processo che contiene un programma).  
  
- `ATTACH_REASON_AUTO` indica che la Germania riguarda il collegamento a un particolare programma perché è già il debug di altri programmi in un determinato processo. Detta anche connessione automatica.  
  
  Quando questo metodo viene chiamato, la Germania deve inviare questi eventi nella sequenza:  
  
1. [IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md) (se non si sono già stato inviato per una particolare istanza del motore di debug)  
  
2. [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)  
  
3. [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md)  
  
   Inoltre, se è il motivo per il collegamento `ATTACH_REASON_LAUNCH`, la Germania è necessario inviare il [IDebugEntryPointEvent2](../../../extensibility/debugger/reference/idebugentrypointevent2.md) evento.  
  
   Una volta il recupera DE il [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) dell'oggetto corrispondente per il programma sottoposto a debug, è possibile eseguire query per qualsiasi interfaccia privata.  
  
   Prima di chiamare i metodi di un nodo di programma nella matrice specificata da `pProgram` oppure `rgpProgramNodes`, la rappresentazione, se necessario, deve essere abilitata sul `IDebugProgram2` interfaccia che rappresenta il nodo di programma. In genere, tuttavia, questo passaggio non è necessario. Per altre informazioni, vedere [problemi di sicurezza](../../../extensibility/debugger/security-issues.md).  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)   
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [ATTACH_REASON](../../../extensibility/debugger/reference/attach-reason.md)   
 [IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md)   
 [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)   
 [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md)   
 [IDebugEntryPointEvent2](../../../extensibility/debugger/reference/idebugentrypointevent2.md)