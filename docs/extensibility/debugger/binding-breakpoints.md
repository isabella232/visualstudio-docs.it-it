---
title: Punti di interruzione dell'associazione | Microsoft Docs
description: Informazioni sul modo in cui l'IDE formula la richiesta di un punto di interruzione e chiede alla sessione di debug di creare il punto di interruzione quando un utente imposta un punto di interruzione.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- breakpoints, binding
ms.assetid: 70737387-c52f-4dae-8865-77d4b203bf25
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 0d7da8cfdb2b7995b77364e5a5de62667b13e52c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99895011"
---
# <a name="bind-breakpoints"></a>Associa punti di interruzione
Se l'utente imposta un punto di interruzione, ad esempio premendo **F9**, l'IDE formula la richiesta e chiede alla sessione di debug di creare il punto di interruzione.

## <a name="set-a-breakpoint"></a>Imposta punto di interruzione
 L'impostazione di un punto di interruzione è un processo in due passaggi, perché il codice o i dati interessati dal punto di interruzione potrebbero non essere ancora disponibili. Prima di tutto, è necessario descrivere il punto di interruzione e quindi, quando il codice o i dati diventano disponibili, è necessario che siano associati a tale codice o dati, come indicato di seguito:

1. Il punto di interruzione viene richiesto dai motori di debug pertinenti (DEs), quindi il punto di interruzione viene associato al codice o ai dati non appena diventano disponibili.

2. La richiesta del punto di interruzione viene inviata alla sessione di debug, che lo invia a tutte le DEs pertinenti. Qualsiasi DE che sceglie di gestire il punto di interruzione crea un punto di interruzione in sospeso corrispondente.

3. La sessione di debug raccoglie i punti di interruzione in sospeso e li invia nuovamente al pacchetto di debug (componente di debug di Visual Studio).

4. Il pacchetto di debug richiede alla sessione di debug di associare il punto di interruzione in sospeso al codice o ai dati. La sessione di debug Invia la richiesta a tutte le DEs pertinenti.

5. Se l'oggetto DE è in grado di associare il punto di interruzione, invia un evento associato al punto di interruzione alla sessione di debug. In caso contrario, viene inviato un evento di errore del punto di interruzione.

## <a name="pending-breakpoints"></a>Punti di interruzione in sospeso
 Un punto di interruzione in sospeso può essere associato a più posizioni di codice. Ad esempio, una riga di codice sorgente per un modello C++ può essere associata a ogni sequenza di codice generata dal modello. La sessione di debug può usare un evento associato a un punto di interruzione per enumerare i contesti di codice associati a un punto di interruzione nel momento in cui l'evento è stato inviato. Un maggior numero di contesti di codice può essere associato in un secondo momento, quindi il DE può inviare più eventi associati al punto di interruzione per ogni richiesta di binding. Tuttavia, un DE deve inviare un solo evento di errore del punto di interruzione per ogni richiesta di binding.

## <a name="implementation"></a>Implementazione
 A livello di codice, il pacchetto di debug chiama il gestore di debug della sessione (SDM) e fornisce un'interfaccia [IDebugBreakpointRequest2](../../extensibility/debugger/reference/idebugbreakpointrequest2.md) che esegue il wrapping di una struttura di [BP_REQUEST_INFO](../../extensibility/debugger/reference/bp-request-info.md) , che descrive il punto di interruzione da impostare. Sebbene i punti di interruzione possano essere di molti formati, vengono risolti in un contesto di codice o di dati.

 Il SDM passa questa chiamata a ogni DE pertinente chiamando il relativo metodo [CreatePendingBreakpoint](../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md) . Se l'oggetto DE sceglie di gestire il punto di interruzione, crea e restituisce un'interfaccia [IDebugPendingBreakpoint2](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) . SDM raccoglie queste interfacce e le passa di nuovo al pacchetto di debug come una singola `IDebugPendingBreakpoint2` interfaccia.

 Finora non è stato generato alcun evento.

 Il pacchetto di debug tenta quindi di associare il punto di interruzione in sospeso al codice o ai dati chiamando [Bind](../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md), che viene implementato da de.

 Se il punto di interruzione è associato, il DE Invia un'interfaccia evento [IDebugBreakpointBoundEvent2](../../extensibility/debugger/reference/idebugbreakpointboundevent2.md) al pacchetto di debug. Il pacchetto di debug usa questa interfaccia per enumerare tutti i contesti di codice, o il singolo contesto dati, associato al punto di interruzione chiamando [EnumBoundBreakpoints](../../extensibility/debugger/reference/idebugbreakpointboundevent2-enumboundbreakpoints.md), che restituisce una o più interfacce [IDebugBoundBreakpoint2](../../extensibility/debugger/reference/idebugboundbreakpoint2.md) . L'interfaccia [GetBreakpointResolution](../../extensibility/debugger/reference/idebugboundbreakpoint2-getbreakpointresolution.md) restituisce un'interfaccia [IDebugBreakpointResolution2](../../extensibility/debugger/reference/idebugbreakpointresolution2.md) e [GetResolutionInfo](../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md) restituisce un'Unione [BP_RESOLUTION_INFO](../../extensibility/debugger/reference/bp-resolution-info.md) che contiene il codice o il contesto dati.

 Se il DE non è in grado di associare il punto di interruzione, invia una singola interfaccia evento [IDebugBreakpointErrorEvent2](../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md) al pacchetto di debug. Il pacchetto di debug Recupera il tipo di errore (errore o avviso) e il messaggio informativo chiamando [GetErrorBreakpoint](../../extensibility/debugger/reference/idebugbreakpointerrorevent2-geterrorbreakpoint.md), seguito da [GetBreakpointResolution](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getbreakpointresolution.md) e [GetResolutionInfo](../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md). Viene restituito un [BP_ERROR_RESOLUTION_INFO](../../extensibility/debugger/reference/bp-error-resolution-info.md) struttura che contiene il tipo di errore e il messaggio.

 Se un oggetto DE gestisce un punto di interruzione ma non è in grado di associarlo, viene restituito un errore di tipo `BPET_TYPE_ERROR` . Il pacchetto di debug risponde visualizzando una finestra di dialogo di errore e l'IDE inserisce un glifo esclamativo all'interno dell'icona del punto di interruzione a sinistra della riga del codice sorgente.

 Se un DE gestisce un punto di interruzione, non è in grado di associarlo, ma è possibile che venga associato da un altro oggetto, viene restituito un avviso. L'IDE risponde inserendo un glifo della domanda all'interno dell'icona del punto di interruzione a sinistra della riga del codice sorgente.

## <a name="see-also"></a>Vedi anche
- [Attività di debug](../../extensibility/debugger/debugging-tasks.md)
