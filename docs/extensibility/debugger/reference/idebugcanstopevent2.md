---
title: IDebugCanStopEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCanStopEvent2
helpviewer_keywords:
- IDebugBreakpointRequest2 interface
ms.assetid: 784bd5b1-4a3f-4455-b313-c4c9a82555a5
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 87306e1373d746479ce59c96b6625fa41ef119fb
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99903243"
---
# <a name="idebugcanstopevent2"></a>IDebugCanStopEvent2
Questa interfaccia viene utilizzata per richiedere alla gestione del debug della sessione (SDM) se arrestare in corrispondenza della posizione del codice corrente.

## <a name="syntax"></a>Sintassi

```
IDebugCanStopEvent2 : IUknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Il motore di debug (DE) implementa questa interfaccia per supportare l'esecuzione del codice sorgente. L'interfaccia [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) deve essere implementata nello stesso oggetto di questa interfaccia (il SDM USA [QueryInterface](/cpp/atl/queryinterface) per accedere all' `IDebugEvent2` interfaccia).

 L'implementazione di questa interfaccia deve comunicare la chiamata di [CanStop](../../../extensibility/debugger/reference/idebugcanstopevent2-canstop.md) di SDM al motore di debug. Ad esempio, questa operazione può essere eseguita con un messaggio inviato al thread di gestione dei messaggi del motore di debug o l'oggetto che implementa questa interfaccia potrebbe contenere un riferimento al motore di debug e richiamarlo nel motore di debug con il flag passato a `IDebugCanStopEvent2::CanStop` .

## <a name="notes-for-callers"></a>Note per i chiamanti
 Il DE può inviare questo metodo ogni volta che viene richiesta la continuazione dell'esecuzione e l'istruzione DE passa attraverso il codice. Questo evento viene inviato utilizzando la funzione di callback [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) fornita da SDM quando è collegata al programma di cui è in corso il debug.

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
 La tabella seguente illustra i metodi di `IDebugCanStopEvent2` .

|Metodo|Descrizione|
|------------|-----------------|
|[GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md)|Ottiene il motivo di questo evento.|
|[CanStop](../../../extensibility/debugger/reference/idebugcanstopevent2-canstop.md)|Specifica se il programma di cui è in corso il debug deve arrestarsi in corrispondenza della posizione di questo evento (e inviare un evento che descrive il motivo dell'arresto) o semplicemente continuare l'esecuzione.|
|[GetDocumentContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getdocumentcontext.md)|Ottiene il contesto del documento che descrive la posizione di questo evento.|
|[GetCodeContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getcodecontext.md)|Ottiene il contesto del codice che descrive la posizione di questo evento.|

## <a name="remarks"></a>Commenti
 Il DE Invia questa interfaccia se l'utente passa a una funzione e la DE non trova informazioni di debug o se sono presenti informazioni di debug, ma non sa se il codice sorgente può essere visualizzato per tale percorso.

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg. h

 Spazio dei nomi: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [IDebugStepCompleteEvent2](../../../extensibility/debugger/reference/idebugstepcompleteevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
