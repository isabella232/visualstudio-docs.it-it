---
title: Metodi di Breakpoint-Related | Microsoft Docs
description: Il debug di Visual Studio supporta i punti di interruzione associati, che vengono associati correttamente a una posizione nel codice e ai punti di interruzione in sospeso, che non sono ancora associati.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], breakpoint methods
- breakpoints, methods
ms.assetid: a6f77bf0-bf81-443f-8683-5f12075bbe10
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: c20a92e847f120850d7cbd424cc073018903911d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99930824"
---
# <a name="breakpoint-related-methods"></a>Metodi correlati al punto di interruzione
Un motore di debug (DE) deve supportare l'impostazione dei punti di interruzione. Il debug di Visual Studio supporta i tipi di punti di interruzione seguenti:

- Bound

     Richiesto tramite l'interfaccia utente e associato correttamente a una posizione di codice specificata

- In sospeso

     Richiesto tramite l'interfaccia utente, ma non ancora associato a istruzioni effettive

## <a name="discussion"></a>Discussione
 Ad esempio, un punto di interruzione in sospeso si verifica quando le istruzioni non sono ancora state caricate. Quando il codice viene caricato, i punti di interruzione in sospeso tentano di eseguire l'associazione al codice nella posizione prescritta, ovvero, per inserire le istruzioni di interruzione nel codice. Gli eventi vengono inviati a gestione debug sessione (SDM) per indicare il corretto binding o per notificare la presenza di errori di associazione.

 Un punto di interruzione in sospeso gestisce anche il proprio elenco interno di punti di interruzione associati corrispondenti. Un punto di interruzione in sospeso può causare l'inserimento di molti punti di interruzione nel codice. L'interfaccia utente di debug di Visual Studio mostra una visualizzazione albero dei punti di interruzione in sospeso e dei punti di interruzione associati corrispondenti.

 Per la creazione e l'uso di punti di interruzione in sospeso è richiesta l'implementazione del metodo [IDebugEngine2:: CreatePendingBreakpoint](../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md) , oltre ai metodi seguenti di interfacce [IDebugPendingBreakpoint2](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) .

|Metodo|Descrizione|
|------------|-----------------|
|[CanBind](../../extensibility/debugger/reference/idebugpendingbreakpoint2-canbind.md)|Determina se un punto di interruzione in sospeso specificato può essere associato a una posizione di codice.|
|[Associare](../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)|Associa un punto di interruzione in sospeso specificato a una o più posizioni di codice.|
|[GetState](../../extensibility/debugger/reference/idebugpendingbreakpoint2-getstate.md)|Ottiene lo stato di un punto di interruzione in sospeso.|
|[GetBreakpointRequest](../../extensibility/debugger/reference/idebugpendingbreakpoint2-getbreakpointrequest.md)|Ottiene la richiesta del punto di interruzione utilizzata per creare un punto di interruzione in sospeso.|
|[Attiva](../../extensibility/debugger/reference/idebugpendingbreakpoint2-enable.md)|Attiva o imposta lo stato di attivazione di un punto di interruzione in sospeso.|
|[EnumBoundBreakpoints](../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md)|Enumera tutti i punti di interruzione associati da un punto di interruzione in sospeso.|
|[EnumErrorBreakpoints](../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md)|Enumera tutti i punti di interruzione di errore risultanti da un punto di interruzione in sospeso.|
|[Elimina](../../extensibility/debugger/reference/idebugpendingbreakpoint2-delete.md)|Elimina un punto di interruzione in sospeso e tutti i punti di interruzione associati.|

 Per enumerare i punti di interruzione e i punti di interruzione di errore associati, è necessario implementare tutti i metodi di [IEnumDebugBoundBreakpoints2](../../extensibility/debugger/reference/ienumdebugboundbreakpoints2.md) e di [IEnumDebugErrorBreakpoints2](../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2.md).

 I punti di interruzione in sospeso che si associano a una posizione del codice richiedono l'implementazione dei seguenti metodi [IDebugBoundBreakpoint2](../../extensibility/debugger/reference/idebugboundbreakpoint2.md) .

|Metodo|Descrizione|
|------------|-----------------|
|[GetPendingBreakpoint](../../extensibility/debugger/reference/idebugboundbreakpoint2-getpendingbreakpoint.md)|Ottiene il punto di interruzione in sospeso contenente un punto di interruzione.|
|[GetState](../../extensibility/debugger/reference/idebugboundbreakpoint2-getstate.md)|Ottiene lo stato di un punto di interruzione associato.|
|[GetBreakpointResolution](../../extensibility/debugger/reference/idebugboundbreakpoint2-getbreakpointresolution.md)|Ottiene la risoluzione del punto di interruzione che descrive un punto di interruzione.|
|[Attiva](../../extensibility/debugger/reference/idebugboundbreakpoint2-enable.md)|Abilita o Disabilita un punto di interruzione.|
|[Elimina](../../extensibility/debugger/reference/idebugboundbreakpoint2-delete.md)|Elimina un punto di interruzione associato.|

 Per informazioni sulla risoluzione e sulla richiesta è necessaria l'implementazione dei seguenti metodi [IDebugBreakpointResolution2](../../extensibility/debugger/reference/idebugbreakpointresolution2.md) .

|Metodo|Descrizione|
|------------|-----------------|
|[GetBreakpointType](../../extensibility/debugger/reference/idebugbreakpointresolution2-getbreakpointtype.md)|Ottiene il tipo del punto di interruzione rappresentato da una risoluzione.|
|[GetResolutionInfo](../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md)|Ottiene le informazioni di risoluzione del punto di interruzione che descrivono un punto di interruzione.|

 La risoluzione degli errori che potrebbero verificarsi durante l'associazione richiede l'implementazione dei seguenti metodi [IDebugErrorBreakpoint2](../../extensibility/debugger/reference/idebugerrorbreakpoint2.md) .

|Metodo|Descrizione|
|------------|-----------------|
|[GetPendingBreakpoint](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getpendingbreakpoint.md)|Ottiene il punto di interruzione in sospeso contenente un punto di interruzione dell'errore.|
|[GetBreakpointResolution](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getbreakpointresolution.md)|Ottiene la risoluzione degli errori dei punti di interruzione che descrive un punto di interruzione dell'errore.|

 La risoluzione degli errori che possono verificarsi durante l'associazione richiede anche i metodi di [IDebugErrorBreakpointResolution2](../../extensibility/debugger/reference/idebugerrorbreakpointresolution2.md)seguenti.

|Metodo|Descrizione|
|------------|-----------------|
|[GetBreakpointType](../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getbreakpointtype.md)|Ottiene il tipo di un punto di interruzione.|
|[GetResolutionInfo](../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md)|Ottiene le informazioni sulla risoluzione di un punto di interruzione.|

 Per visualizzare il codice sorgente in corrispondenza di un punto di interruzione, è necessario implementare i metodi di [IDebugStackFrame2:: GetDocumentContext](../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md) e/o i metodi di [IDebugStackFrame2:: GetCodeContext](../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md).

## <a name="see-also"></a>Vedi anche
- [Controllo di esecuzione e valutazione dello stato](../../extensibility/debugger/execution-control-and-state-evaluation.md)
