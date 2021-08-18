---
title: Associazione di punti di interruzione | Microsoft Docs
description: Informazioni su come l'IDE formula la richiesta di un punto di interruzione e richiede alla sessione di debug di creare il punto di interruzione quando un utente imposta un punto di interruzione.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- breakpoints, binding
ms.assetid: 70737387-c52f-4dae-8865-77d4b203bf25
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 128877b9a5324f78eb4b935586020bbdb999fdf5
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122051066"
---
# <a name="bind-breakpoints"></a>Associare punti di interruzione
Se l'utente imposta un punto di interruzione, ad esempio premendo **F9,** l'IDE formula la richiesta e richiede alla sessione di debug di creare il punto di interruzione.

## <a name="set-a-breakpoint"></a>Imposta punto di interruzione
 L'impostazione di un punto di interruzione è un processo in due passaggi, perché il codice o i dati interessati dal punto di interruzione potrebbero non essere ancora disponibili. In primo luogo, il punto di interruzione deve essere descritto e quindi, quando il codice o i dati diventano disponibili, devono essere associati al codice o ai dati, come indicato di seguito:

1. Il punto di interruzione viene richiesto dai motori di debug (DE) pertinenti, quindi il punto di interruzione viene associato al codice o ai dati non appena diventa disponibile.

2. La richiesta del punto di interruzione viene inviata alla sessione di debug, che la invia a tutte le DE pertinenti. Qualsiasi de che sceglie di gestire il punto di interruzione crea un punto di interruzione in sospeso corrispondente.

3. La sessione di debug raccoglie i punti di interruzione in sospeso e li invia di nuovo al pacchetto di debug (il componente di debug di Visual Studio).

4. Il pacchetto di debug richiede alla sessione di debug di associare il punto di interruzione in sospeso al codice o ai dati. La sessione di debug invia questa richiesta a tutte le DE pertinenti.

5. Se il de è in grado di associare il punto di interruzione, invia un evento associato al punto di interruzione alla sessione di debug. In caso contrario, invia invece un evento di errore del punto di interruzione.

## <a name="pending-breakpoints"></a>Punti di interruzione in sospeso
 Un punto di interruzione in sospeso può essere associato a più percorsi del codice. Ad esempio, una riga di codice sorgente per un modello C++ può essere associata a ogni sequenza di codice generata dal modello. La sessione di debug può usare un evento associato a un punto di interruzione per enumerare i contesti di codice associati a un punto di interruzione al momento dell'invio dell'evento. È possibile associare più contesti di codice in un secondo momento, quindi il de può inviare più eventi associati a punti di interruzione per ogni richiesta di associazione. Tuttavia, un DE deve inviare un solo evento di errore del punto di interruzione per ogni richiesta di associazione.

## <a name="implementation"></a>Implementazione
 A livello di codice, il pacchetto di debug chiama gestione debug sessione (SDM) e fornisce [un'interfaccia IDebugBreakpointRequest2](../../extensibility/debugger/reference/idebugbreakpointrequest2.md) che esegue il wrapping di una struttura [BP_REQUEST_INFO,](../../extensibility/debugger/reference/bp-request-info.md) che descrive il punto di interruzione da impostare. Anche se i punti di interruzione possono essere di molti formati, si risolvono in un codice o in un contesto dati.

 SDM passa questa chiamata a ogni DE pertinente chiamando il relativo [metodo CreatePendingBreakpoint.](../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md) Se il DE sceglie di gestire il punto di interruzione, crea e restituisce [un'interfaccia IDebugPendingBreakpoint2.](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) SDM raccoglie queste interfacce e le passa di nuovo al pacchetto di debug come un'unica `IDebugPendingBreakpoint2` interfaccia.

 Finora non sono stati generati eventi.

 Il pacchetto di debug tenta quindi di associare il punto di interruzione in sospeso al codice o ai dati chiamando [Bind](../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md), implementato dal de.

 Se il punto di interruzione è associato, il DE invia [un'interfaccia di evento IDebugBreakpointBoundEvent2](../../extensibility/debugger/reference/idebugbreakpointboundevent2.md) al pacchetto di debug. Il pacchetto di debug usa questa interfaccia per enumerare tutti i contesti di codice (o il singolo contesto dati) associati al punto di interruzione chiamando [EnumBoundBreakpoints](../../extensibility/debugger/reference/idebugbreakpointboundevent2-enumboundbreakpoints.md), che restituisce una o più [interfacce IDebugBoundBreakpoint2.](../../extensibility/debugger/reference/idebugboundbreakpoint2.md) [L'interfaccia GetBreakpointResolution](../../extensibility/debugger/reference/idebugboundbreakpoint2-getbreakpointresolution.md) restituisce un'interfaccia [IDebugBreakpointResolution2](../../extensibility/debugger/reference/idebugbreakpointresolution2.md) e [](../../extensibility/debugger/reference/bp-resolution-info.md) [GetResolutionInfo](../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md) restituisce un'unione BP_RESOLUTION_INFO contenente il codice o il contesto dati.

 Se de non è in grado di associare il punto di interruzione, invia una singola interfaccia di evento [IDebugBreakpointErrorEvent2](../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md) al pacchetto di debug. Il pacchetto di debug recupera il tipo di errore (errore o avviso) e il messaggio informativo chiamando [GetErrorBreakpoint](../../extensibility/debugger/reference/idebugbreakpointerrorevent2-geterrorbreakpoint.md), seguito da [GetBreakpointResolution](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getbreakpointresolution.md) e [GetResolutionInfo](../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md). Verrà restituita una [BP_ERROR_RESOLUTION_INFO](../../extensibility/debugger/reference/bp-error-resolution-info.md) che contiene il tipo di errore e il messaggio.

 Se un DE gestisce un punto di interruzione ma non può associarlo, restituisce un errore di tipo `BPET_TYPE_ERROR` . Il pacchetto di debug risponde visualizzando una finestra di dialogo di errore e l'IDE inserisce un glifo esclamativo all'interno del glifo del punto di interruzione a sinistra della riga di codice sorgente.

 Se un DE gestisce un punto di interruzione, non può associarlo, ma un altro DE potrebbe associarlo, restituisce un avviso. L'IDE risponde inserendo un glifo della domanda all'interno del glifo del punto di interruzione a sinistra della riga di codice sorgente.

## <a name="see-also"></a>Vedi anche
- [Attività di debug](../../extensibility/debugger/debugging-tasks.md)
