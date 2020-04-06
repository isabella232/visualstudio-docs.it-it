---
title: Proprietà IDebugCanStopEvent2 . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCanStopEvent2
helpviewer_keywords:
- IDebugBreakpointRequest2 interface
ms.assetid: 784bd5b1-4a3f-4455-b313-c4c9a82555a5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f0a3710756f02d7c622be94bab6c3056fb051827
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80734519"
---
# <a name="idebugcanstopevent2"></a>IDebugCanStopEvent2
Questa interfaccia viene utilizzata per chiedere al gestore di sessione di debug (SDM) se interrompere nel percorso del codice corrente.

## <a name="syntax"></a>Sintassi

```
IDebugCanStopEvent2 : IUknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Il motore di debug (DE) implementa questa interfaccia per supportare l'esecuzione del codice sorgente. Il [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) interfaccia deve essere implementata sullo stesso oggetto di questa interfaccia `IDebugEvent2` (il modello SDM utilizza [QueryInterface](/cpp/atl/queryinterface) per accedere all'interfaccia).

 L'implementazione di questa interfaccia deve comunicare la chiamata del file SDM di [CanStop](../../../extensibility/debugger/reference/idebugcanstopevent2-canstop.md) al motore di debug. Ad esempio, questa operazione può essere eseguita con un messaggio inviato al thread di gestione dei messaggi del motore di debug oppure `IDebugCanStopEvent2::CanStop`l'oggetto che implementa questa interfaccia può contenere un riferimento al motore di debug e richiamare il motore di debug con il flag passato in .

## <a name="notes-for-callers"></a>Note per i chiamanti
 Il DE può inviare questo metodo ogni volta che il DE viene chiesto di continuare l'esecuzione e il DE viene eseguito il codice un'istruzione alla volta. Questo evento viene inviato utilizzando la funzione di callback [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) fornita dal modello SDM quando è collegato al programma in fase di debug.

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
 Nella tabella seguente vengono `IDebugCanStopEvent2`illustrati i metodi di .

|Metodo|Descrizione|
|------------|-----------------|
|[GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md)|Ottiene il motivo di questo evento.|
|[CanStop](../../../extensibility/debugger/reference/idebugcanstopevent2-canstop.md)|Specifica se il programma in fase di debug deve interrompersi nel percorso di questo evento (e inviare un evento che descrive il motivo dell'arresto) o semplicemente continuare l'esecuzione.|
|[GetDocumentContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getdocumentcontext.md)|Ottiene il contesto del documento che descrive la posizione di questo evento.|
|[GetCodeContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getcodecontext.md)|Ottiene il contesto di codice che descrive la posizione di questo evento.|

## <a name="remarks"></a>Osservazioni
 Il DE invia questa interfaccia se l'utente entra in una funzione e il DE non trova informazioni di debug o informazioni di debug esistono, ma il DE non sa se il codice sorgente può essere visualizzato per tale posizione.

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche
- [IDebugStepCompleteEvent2](../../../extensibility/debugger/reference/idebugstepcompleteevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
