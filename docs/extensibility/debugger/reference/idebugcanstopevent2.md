---
description: Questa interfaccia viene usata per chiedere a Gestione debug sessione (SDM) se arrestarsi nel percorso del codice corrente.
title: IDebugCanStopEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCanStopEvent2
helpviewer_keywords:
- IDebugBreakpointRequest2 interface
ms.assetid: 784bd5b1-4a3f-4455-b313-c4c9a82555a5
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 6232618832b9cf25dcec97c1b3d3048d2e39b7de
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126635140"
---
# <a name="idebugcanstopevent2"></a>IDebugCanStopEvent2
Questa interfaccia viene usata per chiedere a Gestione debug sessione (SDM) se arrestarsi nel percorso del codice corrente.

## <a name="syntax"></a>Sintassi

```
IDebugCanStopEvent2 : IUknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Il motore di debug implementa questa interfaccia per supportare l'esecuzione istruzione per istruzione del codice sorgente. [L'interfaccia IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) deve essere implementata nello stesso oggetto di questa interfaccia (SDM usa [QueryInterface](/cpp/atl/queryinterface) per accedere all'interfaccia). `IDebugEvent2`

 L'implementazione di questa interfaccia deve comunicare la chiamata di [CanStop](../../../extensibility/debugger/reference/idebugcanstopevent2-canstop.md) di SDM al motore di debug. Ad esempio, questa operazione può essere eseguita con un messaggio inviato al thread di gestione dei messaggi del motore di debug oppure l'oggetto che implementa questa interfaccia può contenere un riferimento al motore di debug e richiamare il motore di debug con il flag passato a `IDebugCanStopEvent2::CanStop` .

## <a name="notes-for-callers"></a>Note per i chiamanti
 De può inviare questo metodo ogni volta che viene richiesto di continuare l'esecuzione e de esegue il codice un'istruzione alla volta. Questo evento viene inviato usando la funzione di callback [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) fornita da SDM quando è collegato al programma di cui è in corso il debug.

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
 Nella tabella seguente vengono illustrati i metodi di `IDebugCanStopEvent2` .

|Metodo|Descrizione|
|------------|-----------------|
|[GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md)|Ottiene il motivo di questo evento.|
|[CanStop](../../../extensibility/debugger/reference/idebugcanstopevent2-canstop.md)|Specifica se il programma in fase di debug deve essere interrotto nel percorso di questo evento (e inviare un evento che descrive il motivo dell'arresto) o semplicemente continuare l'esecuzione.|
|[GetDocumentContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getdocumentcontext.md)|Ottiene il contesto del documento che descrive la posizione di questo evento.|
|[GetCodeContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getcodecontext.md)|Ottiene il contesto del codice che descrive la posizione di questo evento.|

## <a name="remarks"></a>Commenti
 De invia questa interfaccia se l'utente esegue l'esecuzione di una funzione e de trova informazioni di debug in tale posizione, ma de non sa se il codice sorgente può essere visualizzato per tale percorso.

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [IDebugStepCompleteEvent2](../../../extensibility/debugger/reference/idebugstepcompleteevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
