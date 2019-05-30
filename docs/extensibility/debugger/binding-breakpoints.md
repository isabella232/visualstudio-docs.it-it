---
title: Associazione dei punti di interruzione | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- breakpoints, binding
ms.assetid: 70737387-c52f-4dae-8865-77d4b203bf25
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7f861875e15a9051ab05d1b7398ea5902189830b
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66332572"
---
# <a name="bind-breakpoints"></a>Eseguire l'associazione dei punti di interruzione
Se l'utente imposta un punto di interruzione, ad esempio premendo **F9**, l'IDE formula la richiesta e richiede la sessione di debug per creare il punto di interruzione.

## <a name="set-a-breakpoint"></a>Imposta punto di interruzione
 L'impostazione di un punto di interruzione è un processo in due passaggi, perché il codice o dati interessati dal punto di interruzione potrebbero non essere ancora disponibili. In primo luogo, il punto di interruzione deve essere descritte, e quindi, quando codice o dati diventano disponibili, deve essere associata a tale codice o dati, come indicato di seguito:

1. Il punto di interruzione viene richiesto dai motori di debug pertinenti (DEs), e quindi il punto di interruzione associata al codice o dati appena sarà disponibile.

2. La richiesta di punto di interruzione viene inviata alla sessione di debug, che lo invia a tutti DEs pertinenti. Qualsiasi Germania che sceglie di gestire il punto di interruzione consente di creare un oggetto corrispondente in sospeso punto di interruzione.

3. La sessione di debug raccoglie i punti di interruzione in sospeso e li invia al pacchetto di debug (il componente di debug di Visual Studio).

4. Il pacchetto di debug richiede la sessione di debug per associare il punto di interruzione in sospeso al codice o dati. La sessione di debug invia questa richiesta a tutti DEs pertinenti.

5. Se la Germania è in grado di associare il punto di interruzione, viene inviato che un punto di interruzione associato eventi alla sessione di debug. In caso contrario, invia un evento di errore del punto di interruzione.

## <a name="pending-breakpoints"></a>Punti di interruzione in sospeso
 Possibile associare un punto di interruzione in sospeso per più percorsi del codice. Ad esempio, una riga di codice sorgente per un modello di C++ è possibile associare a ogni sequenza di codice generato dal modello. La sessione di debug è possibile utilizzare un evento associato a punti di interruzione per enumerare i contesti di codice associati a un punto di interruzione al momento che dell'evento è stato inviato. Più contesti di codice possono essere associati in un secondo momento, in modo che la Germania potrebbe inviare che più punti di interruzione associata di eventi per ogni richiesta di associazione. Tuttavia, un CRI deve inviare solo un evento di errore di punto di interruzione per ogni richiesta di associazione.

## <a name="implementation"></a>Implementazione
 A livello di codice, il pacchetto di debug viene chiamato il debug di sessione manager (SDM) e gli assegna un [IDebugBreakpointRequest2](../../extensibility/debugger/reference/idebugbreakpointrequest2.md) interfaccia che esegue il wrapping di un [BP_REQUEST_INFO](../../extensibility/debugger/reference/bp-request-info.md) struttura, che descrive il punto di interruzione da impostare. Anche se i punti di interruzione possono essere di vario tipo, vengono risolte in un contesto di codice o dati.

 Il modello SDM passa la chiamata a ogni DE rilevanti chiamando relativi [CreatePendingBreakpoint](../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md) (metodo). Se la Germania sceglie di gestire il punto di interruzione, crea e restituisce un [IDebugPendingBreakpoint2](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) interfaccia. Il modello SDM raccoglie queste interfacce e li passa al pacchetto di debug come singolo `IDebugPendingBreakpoint2` interfaccia.

 Finora, gli eventi non sono stati generati.

 Il pacchetto di debug tenta quindi di associare il punto di interruzione in sospeso al codice o dati chiamando [associare](../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md), che viene implementato per la Germania.

 Se è associato il punto di interruzione, la Germania invia un' [IDebugBreakpointBoundEvent2](../../extensibility/debugger/reference/idebugbreakpointboundevent2.md) interfaccia evento per il pacchetto di debug. Gli utilizzi di pacchetto di debug questa interfaccia per enumerare tutti i contesti di codice (o il contesto di dati singolo) associata al punto di interruzione chiamando [EnumBoundBreakpoints](../../extensibility/debugger/reference/idebugbreakpointboundevent2-enumboundbreakpoints.md), che restituisce uno o più [IDebugBoundBreakpoint2](../../extensibility/debugger/reference/idebugboundbreakpoint2.md) interfacce. Il [GetBreakpointResolution](../../extensibility/debugger/reference/idebugboundbreakpoint2-getbreakpointresolution.md) interfaccia restituisce un' [IDebugBreakpointResolution2](../../extensibility/debugger/reference/idebugbreakpointresolution2.md) interfaccia, e [GetResolutionInfo](../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md) restituisce un [BP_ RESOLUTION_INFO](../../extensibility/debugger/reference/bp-resolution-info.md) unione che contiene il contesto di codice o dati.

 Se la Germania è in grado di associare il punto di interruzione, viene inviato un unico [IDebugBreakpointErrorEvent2](../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md) interfaccia evento per il pacchetto di debug. Il pacchetto di debug recupera il tipo di errore (errore o avviso) e un messaggio informativo mediante la chiamata [GetErrorBreakpoint](../../extensibility/debugger/reference/idebugbreakpointerrorevent2-geterrorbreakpoint.md), quindi su [GetBreakpointResolution](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getbreakpointresolution.md) e [ GetResolutionInfo](../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md). Restituisce un [BP_ERROR_RESOLUTION_INFO](../../extensibility/debugger/reference/bp-error-resolution-info.md) struttura che contiene il tipo di errore e il messaggio.

 Se un CRI gestisce un punto di interruzione, ma non è possibile eseguirne l'associazione, viene restituito un errore di tipo `BPET_TYPE_ERROR`. Il pacchetto di debug risponde visualizzando una finestra di dialogo di errore e l'IDE posiziona un'icona di punto esclamativo all'interno di glifo del punto di interruzione a sinistra della riga del codice sorgente.

 Se un CRI gestisce un punto di interruzione, non è possibile eseguire l'associazione, ma un altro Germania potrebbe eseguirne l'associazione, viene restituito un avviso. L'IDE risponde inserendo un glifo domanda all'interno di glifo del punto di interruzione a sinistra della riga del codice sorgente.

## <a name="see-also"></a>Vedere anche
- [Attività di debug](../../extensibility/debugger/debugging-tasks.md)