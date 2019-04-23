---
title: I metodi correlati al punto di interruzione | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], breakpoint methods
- breakpoints, methods
ms.assetid: a6f77bf0-bf81-443f-8683-5f12075bbe10
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c1781e6aab84bfcdc665ef0d779130decc9c6421
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60091954"
---
# <a name="breakpoint-related-methods"></a>Metodi correlati al punto di interruzione
Un motore di debug (DE) deve supportare l'impostazione di punti di interruzione. Debug in Visual Studio supporta i seguenti tipi di punti di interruzione:

- Associato

     Richiesta tramite l'interfaccia utente ed è stato associato a una posizione di codice specificato

- In sospeso

     Richiesta tramite l'interfaccia utente, ma istruzioni non è ancora associate a effettivo

## <a name="discussion"></a>Discussione
 Ad esempio, un punto di interruzione in sospeso si verifica quando le istruzioni non sono ancora state caricate. Quando il codice viene caricato, in attesa di provare a punti di interruzione da associare al codice in corrispondenza della posizione prescritta, vale a dire, per inserire le istruzioni di interruzione nel codice. Gli eventi vengono inviati al gestore di sessione di debug (SDM) per indicare l'associazione ha esito positivo oppure per notificare che si sono verificati errori di associazione.

 Un punto di interruzione in sospeso gestisce anche il proprio elenco interno dei punti di interruzione associate corrispondente. Una in sospeso punto di interruzione può causare l'inserimento di numerosi punti di interruzione nel codice. Debug dell'interfaccia utente di Visual Studio Mostra una visualizzazione albero delle interruzioni in sospeso e i relativi punti di interruzione associati.

 Creare e utilizzare in sospeso i punti di interruzione richiedono l'implementazione del [IDebugEngine2::CreatePendingBreakpoint](../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md) metodo, nonché i metodi seguenti della [IDebugPendingBreakpoint2](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) interfacce.

|Metodo|Descrizione|
|------------|-----------------|
|[CanBind](../../extensibility/debugger/reference/idebugpendingbreakpoint2-canbind.md)|Determina se un oggetto in sospeso punto di interruzione è possibile associare a un percorso di codice.|
|[Bind](../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)|Associa un oggetto specificato in sospeso punto di interruzione in uno o più percorsi di codice.|
|[GetState](../../extensibility/debugger/reference/idebugpendingbreakpoint2-getstate.md)|Ottiene lo stato di un punto di interruzione in sospeso.|
|[GetBreakpointRequest](../../extensibility/debugger/reference/idebugpendingbreakpoint2-getbreakpointrequest.md)|Ottiene la richiesta del punto di interruzione consente di creare un punto di interruzione in sospeso.|
|[Enable](../../extensibility/debugger/reference/idebugpendingbreakpoint2-enable.md)|Attiva/disattiva lo stato di abilitazione di un punto di interruzione in sospeso.|
|[EnumBoundBreakpoints](../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md)|Enumera tutti i punti di interruzione associati da un punto di interruzione in sospeso.|
|[EnumErrorBreakpoints](../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md)|Enumera tutti i punti di interruzione di errore risultanti da un punto di interruzione in sospeso.|
|[Eliminazione](../../extensibility/debugger/reference/idebugpendingbreakpoint2-delete.md)|Elimina un punto di interruzione in sospeso e tutti i punti di interruzione associati da quest'ultimo.|

 Per enumerare i punti di interruzione associati e i punti di interruzione di errore, è necessario implementare tutti i metodi del [IEnumDebugBoundBreakpoints2](../../extensibility/debugger/reference/ienumdebugboundbreakpoints2.md) e di [IEnumDebugErrorBreakpoints2](../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2.md).

 In attesa di punti di interruzione da associare a un codice di percorso richiedono l'implementazione delle operazioni seguenti [IDebugBoundBreakpoint2](../../extensibility/debugger/reference/idebugboundbreakpoint2.md) metodi.

|Metodo|Descrizione|
|------------|-----------------|
|[GetPendingBreakpoint](../../extensibility/debugger/reference/idebugboundbreakpoint2-getpendingbreakpoint.md)|Ottiene il punto di interruzione in sospeso che contiene un punto di interruzione.|
|[GetState](../../extensibility/debugger/reference/idebugboundbreakpoint2-getstate.md)|Ottiene lo stato di un punto di interruzione associato.|
|[GetBreakpointResolution](../../extensibility/debugger/reference/idebugboundbreakpoint2-getbreakpointresolution.md)|Ottiene la risoluzione di punto di interruzione che descrive un punto di interruzione.|
|[Enable](../../extensibility/debugger/reference/idebugboundbreakpoint2-enable.md)|Abilita o disabilita un punto di interruzione.|
|[Eliminazione](../../extensibility/debugger/reference/idebugboundbreakpoint2-delete.md)|Elimina un punto di interruzione associato.|

 Risoluzione e richiedere informazioni richiedono l'implementazione delle operazioni seguenti [IDebugBreakpointResolution2](../../extensibility/debugger/reference/idebugbreakpointresolution2.md) metodi.

|Metodo|Descrizione|
|------------|-----------------|
|[GetBreakpointType](../../extensibility/debugger/reference/idebugbreakpointresolution2-getbreakpointtype.md)|Ottiene il tipo del punto di interruzione rappresentato da una risoluzione.|
|[GetResolutionInfo](../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md)|Ottiene le informazioni di risoluzione dei punti di interruzione che descrive un punto di interruzione.|

 Risoluzione degli errori che potrebbero verificarsi durante l'associazione è necessaria l'implementazione delle operazioni seguenti [IDebugErrorBreakpoint2](../../extensibility/debugger/reference/idebugerrorbreakpoint2.md) metodi.

|Metodo|Descrizione|
|------------|-----------------|
|[GetPendingBreakpoint](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getpendingbreakpoint.md)|Ottiene il punto di interruzione in sospeso che contiene un punto di interruzione di errore.|
|[GetBreakpointResolution](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getbreakpointresolution.md)|Ottiene la risoluzione degli errori di punto di interruzione che descrive un punto di interruzione di errore.|

 Risoluzione degli errori che potrebbero verificarsi durante l'associazione richiede inoltre i metodi seguenti della [IDebugErrorBreakpointResolution2](../../extensibility/debugger/reference/idebugerrorbreakpointresolution2.md).

|Metodo|Descrizione|
|------------|-----------------|
|[GetBreakpointType](../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getbreakpointtype.md)|Ottiene il tipo di un punto di interruzione.|
|[GetResolutionInfo](../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md)|Ottiene le informazioni sulla risoluzione di un punto di interruzione.|

 Visualizzazione del codice sorgente in un punto di interruzione è necessario implementare i metodi della [IDebugStackFrame2::GetDocumentContext](../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md) e/o i metodi del [IDebugStackFrame2::GetCodeContext](../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md).

## <a name="see-also"></a>Vedere anche
- [Valutazione di controllo e lo stato di esecuzione](../../extensibility/debugger/execution-control-and-state-evaluation.md)