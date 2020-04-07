---
title: Punti di interruzione di associazione . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- breakpoints, binding
ms.assetid: 70737387-c52f-4dae-8865-77d4b203bf25
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 680cff398a43d1ebe9ccf061ad42781500c7cf01
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739226"
---
# <a name="bind-breakpoints"></a>Associare punti di interruzioneBind breakpoints
Se l'utente imposta un punto di interruzione, ad esempio premendo **F9**, l'IDE formula la richiesta e richiede alla sessione di debug di creare il punto di interruzione.

## <a name="set-a-breakpoint"></a>Imposta punto di interruzione
 L'impostazione di un punto di interruzione è un processo in due passaggi, perché il codice o i dati interessati dal punto di interruzione potrebbero non essere ancora disponibili. In primo luogo, il punto di interruzione deve essere descritto e quindi, quando il codice o i dati diventano disponibili, deve essere associato a tale codice o dati, come indicato di seguito:First, the breakpoint must be described, and then, as code or data becomes available, it must be bound to that code or data, as follows:

1. Il punto di interruzione viene richiesto dai motori di debug pertinenti (DE, Relevant Debug Engine), quindi il punto di interruzione viene associato al codice o ai dati non appena diventa disponibile.

2. La richiesta del punto di interruzione viene inviata alla sessione di debug, che la invia a tutti i file DE pertinenti. Qualsiasi DE che sceglie di gestire il punto di interruzione crea un punto di interruzione in sospeso corrispondente.

3. La sessione di debug raccoglie i punti di interruzione in sospeso e li invia al pacchetto di debug (il componente di debug di Visual Studio).

4. Il pacchetto di debug richiede alla sessione di debug di associare il punto di interruzione in sospeso a codice o dati. La sessione di debug invia la richiesta a tutti i dE pertinenti.

5. Se il DE è in grado di associare il punto di interruzione, invia un evento associato punto di interruzione alla sessione di debug. In caso contrario, invia invece un evento di errore del punto di interruzione.

## <a name="pending-breakpoints"></a>Punti di interruzione in sospeso
 Un punto di interruzione in sospeso può essere associato a più percorsi di codice. Ad esempio, è possibile associare una riga di codice sorgente per un modello di C, ovvero a ogni sequenza di codice generata dal modello. La sessione di debug può utilizzare un evento associato a un punto di interruzione per enumerare i contesti di codice associati a un punto di interruzione al momento dell'invio dell'evento. Più contesti di codice possono essere associati in un secondo momento, in modo che il DE può inviare più eventi associati punto di interruzione per ogni richiesta di associazione. Tuttavia, un DE deve inviare solo un evento di errore punto di interruzione per ogni richiesta di associazione.

## <a name="implementation"></a>Implementazione
 A livello di codice, il pacchetto di debug chiama il gestore di debug della sessione (SDM) e gli assegna un [IDebugBreakpointRequest2](../../extensibility/debugger/reference/idebugbreakpointrequest2.md) interfaccia che esegue il wrapping di un [BP_REQUEST_INFO](../../extensibility/debugger/reference/bp-request-info.md) struttura, che descrive il punto di interruzione da impostare. Anche se i punti di interruzione possono essere di molte forme, in ultima analisi, si risolvono in un contesto di codice o dati.

 Il file SDM passa questa chiamata a ogni DE pertinente chiamando il relativo [CreatePendingBreakpoint](../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md) metodo. Se il DE sceglie di gestire il punto di interruzione, crea e restituisce un [IDebugPendingBreakpoint2](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) interfaccia. Il protocollo SDM raccoglie queste interfacce e le passa `IDebugPendingBreakpoint2` al pacchetto di debug come singola interfaccia.

 Finora non sono stati generati eventi.

 Il pacchetto di debug tenta quindi di associare il punto di interruzione in sospeso a codice o dati chiamando [Bind](../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md), che viene implementato dal DE.

 Se il punto di interruzione è associato, il DE invia un [IDebugBreakpointBoundEvent2](../../extensibility/debugger/reference/idebugbreakpointboundevent2.md) interfaccia evento al pacchetto di debug. Il pacchetto di debug utilizza questa interfaccia per enumerare tutti i contesti di codice (o il singolo contesto dati) associati al punto di interruzione chiamando [EnumBoundBreakpoints](../../extensibility/debugger/reference/idebugbreakpointboundevent2-enumboundbreakpoints.md), che restituisce una o più [interfacce IDebugBoundBreakpoint2.](../../extensibility/debugger/reference/idebugboundbreakpoint2.md) Il [GetBreakpointResolution](../../extensibility/debugger/reference/idebugboundbreakpoint2-getbreakpointresolution.md) interfaccia restituisce un [IDebugBreakpointResolution2](../../extensibility/debugger/reference/idebugbreakpointresolution2.md) interfaccia e [GetResolutionInfo](../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md) restituisce [un'unione BP_RESOLUTION_INFO](../../extensibility/debugger/reference/bp-resolution-info.md) contenente il codice o il contesto dati.

 Se il DE non è in grado di associare il punto di interruzione, invia una singola [IDebugBreakpointErrorEvent2](../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md) interfaccia evento al pacchetto di debug. Il pacchetto di debug recupera il tipo di errore (errore o avviso) e il messaggio informativo chiamando [GetErrorBreakpoint](../../extensibility/debugger/reference/idebugbreakpointerrorevent2-geterrorbreakpoint.md), seguito da [GetBreakpointResolution](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getbreakpointresolution.md) e [GetResolutionInfo](../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md). Restituisce un [BP_ERROR_RESOLUTION_INFO](../../extensibility/debugger/reference/bp-error-resolution-info.md) struttura che contiene il tipo di errore e il messaggio.

 Se un DE gestisce un punto di interruzione `BPET_TYPE_ERROR`ma non è in grado di associarlo, restituisce un errore di tipo . Il pacchetto di debug risponde visualizzando una finestra di dialogo di errore e l'IDE inserisce un glifo esclamativo all'interno del glifo del punto di interruzione a sinistra della riga del codice sorgente.

 Se un DE gestisce un punto di interruzione, non è possibile associarlo, ma alcuni altri DE potrebbero associarlo, restituisce un avviso. L'IDE risponde inserendo un glifo di domanda all'interno del glifo del punto di interruzione a sinistra della riga di codice sorgente.

## <a name="see-also"></a>Vedere anche
- [Attività di debugDebugging tasks](../../extensibility/debugger/debugging-tasks.md)
