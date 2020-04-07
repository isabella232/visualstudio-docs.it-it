---
title: Metodi correlati ai punti di interruzione Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], breakpoint methods
- breakpoints, methods
ms.assetid: a6f77bf0-bf81-443f-8683-5f12075bbe10
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c72ec63e500ac86a4a5bd66a2956fe0fb06c8834
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739203"
---
# <a name="breakpoint-related-methods"></a>Metodi correlati ai punti di interruzione
Un motore di debug (DE) deve supportare l'impostazione dei punti di interruzione. Il debug di Visual Studio supporta i seguenti tipi di punti di interruzione:

- Bound

     Richiesto tramite l'interfaccia utente e associato correttamente a un percorso di codice specificato

- In sospeso

     Richiesto tramite l'interfaccia utente ma non ancora associato alle istruzioni effettive

## <a name="discussion"></a>Discussione
 Ad esempio, un punto di interruzione in sospeso si verifica quando le istruzioni non sono ancora caricate. Quando il codice viene caricato, i punti di interruzione in sospeso tentano di eseguire l'associazione al codice nella posizione prescritta, ovvero per inserire istruzioni di interruzione nel codice. Gli eventi vengono inviati al gestore di sessione di debug (SDM) per indicare l'associazione riuscita o per notificare che si sono verificati errori di associazione.

 Un punto di interruzione in sospeso gestisce anche il proprio elenco interno di punti di interruzione associati corrispondenti. Un punto di interruzione in sospeso può causare l'inserimento di molti punti di interruzione nel codice. L'interfaccia utente di debug di Visual Studio mostra una visualizzazione struttura ad albero dei punti di interruzione in sospeso e dei punti di interruzione associati corrispondenti.

 La creazione e l'utilizzo di punti di interruzione in sospeso richiedono l'implementazione del metodo [IDebugEngine2::CreatePendingBreakpoint,](../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md) nonché i seguenti metodi delle interfacce [IDebugPendingBreakpoint2.](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)

|Metodo|Descrizione|
|------------|-----------------|
|[CanBind](../../extensibility/debugger/reference/idebugpendingbreakpoint2-canbind.md)|Determina se un punto di interruzione in sospeso specificato può essere associato a un percorso di codice.|
|[Associare](../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)|Associa un punto di interruzione in sospeso specificato a uno o più percorsi di codice.|
|[GetState](../../extensibility/debugger/reference/idebugpendingbreakpoint2-getstate.md)|Ottiene lo stato di un punto di interruzione in sospeso.|
|[GetBreakpointRequest](../../extensibility/debugger/reference/idebugpendingbreakpoint2-getbreakpointrequest.md)|Ottiene la richiesta del punto di interruzione utilizzata per creare un punto di interruzione in sospeso.|
|[Abilitare](../../extensibility/debugger/reference/idebugpendingbreakpoint2-enable.md)|Attiva/disattiva lo stato abilitato di un punto di interruzione in sospeso.|
|[EnumBoundBreakpoints](../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md)|Enumera tutti i punti di interruzione associati da un punto di interruzione in sospeso.|
|[EnumErrorBreakpoints](../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md)|Enumera tutti i punti di interruzione di errore risultanti da un punto di interruzione in sospeso.|
|[Elimina](../../extensibility/debugger/reference/idebugpendingbreakpoint2-delete.md)|Elimina un punto di interruzione in sospeso e tutti i punti di interruzione associati da esso.|

 Per enumerare i punti di interruzione associati e di errore, è necessario implementare tutti i metodi di [IEnumDebugBoundBreakpoints2](../../extensibility/debugger/reference/ienumdebugboundbreakpoints2.md) e [di IEnumDebugErrorBreakpoints2](../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2.md).

 I punti di interruzione in sospeso associati a un percorso di codice richiedono l'implementazione dei seguenti metodi [IDebugBoundBreakpoint2.](../../extensibility/debugger/reference/idebugboundbreakpoint2.md)

|Metodo|Descrizione|
|------------|-----------------|
|[GetPendingBreakpoint](../../extensibility/debugger/reference/idebugboundbreakpoint2-getpendingbreakpoint.md)|Ottiene il punto di interruzione in sospeso che contiene un punto di interruzione.|
|[GetState](../../extensibility/debugger/reference/idebugboundbreakpoint2-getstate.md)|Ottiene lo stato di un punto di interruzione associato.|
|[GetBreakpointResolution](../../extensibility/debugger/reference/idebugboundbreakpoint2-getbreakpointresolution.md)|Ottiene la risoluzione del punto di interruzione che descrive un punto di interruzione.|
|[Abilitare](../../extensibility/debugger/reference/idebugboundbreakpoint2-enable.md)|Abilita o disabilita un punto di interruzione.|
|[Elimina](../../extensibility/debugger/reference/idebugboundbreakpoint2-delete.md)|Elimina un punto di interruzione associato.|

 Le informazioni sulla risoluzione e sulla richiesta richiedono l'implementazione dei seguenti metodi [IDebugBreakpointResolution2.](../../extensibility/debugger/reference/idebugbreakpointresolution2.md)

|Metodo|Descrizione|
|------------|-----------------|
|[GetBreakpointType](../../extensibility/debugger/reference/idebugbreakpointresolution2-getbreakpointtype.md)|Ottiene il tipo del punto di interruzione rappresentato da una risoluzione.|
|[GetResolutionInfo](../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md)|Ottiene le informazioni sulla risoluzione del punto di interruzione che descrivono un punto di interruzione.|

 La risoluzione degli errori che potrebbero verificarsi durante l'associazione richiede l'implementazione dei seguenti [Metodi IDebugErrorBreakpoint2.](../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)

|Metodo|Descrizione|
|------------|-----------------|
|[GetPendingBreakpoint](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getpendingbreakpoint.md)|Ottiene il punto di interruzione in sospeso che contiene un punto di interruzione di errore.|
|[GetBreakpointResolution](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getbreakpointresolution.md)|Ottiene la risoluzione degli errori del punto di interruzione che descrive un punto di interruzione di errore.|

 La risoluzione degli errori che potrebbero verificarsi durante l'associazione richiede anche i seguenti metodi di [IDebugErrorBreakpointResolution2](../../extensibility/debugger/reference/idebugerrorbreakpointresolution2.md).

|Metodo|Descrizione|
|------------|-----------------|
|[GetBreakpointType](../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getbreakpointtype.md)|Ottiene il tipo di un punto di interruzione.|
|[GetResolutionInfo](../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md)|Ottiene le informazioni sulla risoluzione di un punto di interruzione.|

 La visualizzazione del codice sorgente in corrispondenza di un punto di interruzione richiede l'implementazione dei metodi di [IDebugStackFrame2::GetDocumentContext e/o](../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md) i metodi di [IDebugStackFrame2::GetCodeContext](../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md).

## <a name="see-also"></a>Vedere anche
- [Controllo dell'esecuzione e valutazione dello stato](../../extensibility/debugger/execution-control-and-state-evaluation.md)
