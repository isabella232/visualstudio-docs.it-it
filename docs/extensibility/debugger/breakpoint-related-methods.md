---
title: Breakpoint-Related metodi | Microsoft Docs
description: Visual Studio debug supporta i punti di interruzione associati, che vengono associati correttamente a una posizione nel codice, e i punti di interruzione in sospeso, che non sono ancora associati.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- debugging [Debugging SDK], breakpoint methods
- breakpoints, methods
ms.assetid: a6f77bf0-bf81-443f-8683-5f12075bbe10
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: ad634ddce8f42c8bf5e183ebdf8f75389553dba5
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122073435"
---
# <a name="breakpoint-related-methods"></a>Metodi correlati ai punti di interruzione
Un motore di debug deve supportare l'impostazione dei punti di interruzione. Visual Studio debug supporta i tipi di punti di interruzione seguenti:

- Bound

     Richiesto tramite l'interfaccia utente e associato correttamente a una posizione di codice specificata

- In sospeso

     Richiesta tramite l'interfaccia utente, ma non ancora associata a istruzioni effettive

## <a name="discussion"></a>Discussione
 Ad esempio, un punto di interruzione in sospeso si verifica quando le istruzioni non sono ancora caricate. Quando il codice viene caricato, i punti di interruzione in sospeso tentano di eseguire l'associazione al codice nella posizione specificata, ad esempio per inserire istruzioni di interruzione nel codice. Gli eventi vengono inviati alla gestione del debug di sessione (SDM) per indicare l'associazione riuscita o per notificare la presenza di errori di associazione.

 Un punto di interruzione in sospeso gestisce anche il proprio elenco interno di punti di interruzione associati corrispondenti. Un punto di interruzione in sospeso può causare l'inserimento di molti punti di interruzione nel codice. L'interfaccia Visual Studio di debug mostra una visualizzazione albero dei punti di interruzione in sospeso e dei punti di interruzione associati corrispondenti.

 La creazione e l'uso di punti di interruzione in sospeso richiedono l'implementazione del metodo [IDebugEngine2::CreatePendingBreakpoint,](../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md) nonché i metodi seguenti delle [interfacce IDebugPendingBreakpoint2.](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)

|Metodo|Descrizione|
|------------|-----------------|
|[CanBind](../../extensibility/debugger/reference/idebugpendingbreakpoint2-canbind.md)|Determina se un punto di interruzione in sospeso specificato può essere associato a una posizione del codice.|
|[Associare](../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)|Associa un punto di interruzione in sospeso specificato a una o più posizioni del codice.|
|[GetState](../../extensibility/debugger/reference/idebugpendingbreakpoint2-getstate.md)|Ottiene lo stato di un punto di interruzione in sospeso.|
|[GetBreakpointRequest](../../extensibility/debugger/reference/idebugpendingbreakpoint2-getbreakpointrequest.md)|Ottiene la richiesta del punto di interruzione utilizzata per creare un punto di interruzione in sospeso.|
|[Abilita](../../extensibility/debugger/reference/idebugpendingbreakpoint2-enable.md)|Attiva o disattiva lo stato abilitato di un punto di interruzione in sospeso.|
|[EnumBoundBreakpoints](../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md)|Enumera tutti i punti di interruzione associati da un punto di interruzione in sospeso.|
|[EnumErrorBreakpoints](../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md)|Enumera tutti i punti di interruzione di errore risultanti da un punto di interruzione in sospeso.|
|[Elimina](../../extensibility/debugger/reference/idebugpendingbreakpoint2-delete.md)|Elimina un punto di interruzione in sospeso e tutti i punti di interruzione associati.|

 Per enumerare i punti di interruzione associati e i punti di interruzione di errore, è necessario implementare tutti i metodi di [IEnumDebugBoundBreakpoints2](../../extensibility/debugger/reference/ienumdebugboundbreakpoints2.md) e [di IEnumDebugErrorBreakpoints2](../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2.md).

 I punti di interruzione in sospeso associati a una posizione del codice richiedono l'implementazione dei metodi [IDebugBoundBreakpoint2](../../extensibility/debugger/reference/idebugboundbreakpoint2.md) seguenti.

|Metodo|Descrizione|
|------------|-----------------|
|[GetPendingBreakpoint](../../extensibility/debugger/reference/idebugboundbreakpoint2-getpendingbreakpoint.md)|Ottiene il punto di interruzione in sospeso che contiene un punto di interruzione.|
|[GetState](../../extensibility/debugger/reference/idebugboundbreakpoint2-getstate.md)|Ottiene lo stato di un punto di interruzione associato.|
|[GetBreakpointResolution](../../extensibility/debugger/reference/idebugboundbreakpoint2-getbreakpointresolution.md)|Ottiene la risoluzione del punto di interruzione che descrive un punto di interruzione.|
|[Abilita](../../extensibility/debugger/reference/idebugboundbreakpoint2-enable.md)|Abilita o disabilita un punto di interruzione.|
|[Elimina](../../extensibility/debugger/reference/idebugboundbreakpoint2-delete.md)|Elimina un punto di interruzione associato.|

 Le informazioni sulla risoluzione e sulla richiesta richiedono l'implementazione dei metodi [IDebugBreakpointResolution2](../../extensibility/debugger/reference/idebugbreakpointresolution2.md) seguenti.

|Metodo|Descrizione|
|------------|-----------------|
|[GetBreakpointType](../../extensibility/debugger/reference/idebugbreakpointresolution2-getbreakpointtype.md)|Ottiene il tipo del punto di interruzione rappresentato da una risoluzione.|
|[GetResolutionInfo](../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md)|Ottiene le informazioni sulla risoluzione del punto di interruzione che descrivono un punto di interruzione.|

 La risoluzione degli errori che possono verificarsi durante l'associazione richiede l'implementazione dei metodi [IDebugErrorBreakpoint2](../../extensibility/debugger/reference/idebugerrorbreakpoint2.md) seguenti.

|Metodo|Descrizione|
|------------|-----------------|
|[GetPendingBreakpoint](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getpendingbreakpoint.md)|Ottiene il punto di interruzione in sospeso che contiene un punto di interruzione dell'errore.|
|[GetBreakpointResolution](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getbreakpointresolution.md)|Ottiene la risoluzione degli errori del punto di interruzione che descrive un punto di interruzione dell'errore.|

 La risoluzione degli errori che potrebbero verificarsi durante l'associazione richiede anche i metodi seguenti di [IDebugErrorBreakpointResolution2.](../../extensibility/debugger/reference/idebugerrorbreakpointresolution2.md)

|Metodo|Descrizione|
|------------|-----------------|
|[GetBreakpointType](../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getbreakpointtype.md)|Ottiene il tipo di un punto di interruzione.|
|[GetResolutionInfo](../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md)|Ottiene le informazioni sulla risoluzione di un punto di interruzione.|

 Per visualizzare il codice sorgente in corrispondenza di un punto di interruzione, è necessario implementare i metodi di [IDebugStackFrame2::GetDocumentContext](../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md) e/o i metodi di [IDebugStackFrame2::GetCodeContext](../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md).

## <a name="see-also"></a>Vedi anche
- [Controllo dell'esecuzione e valutazione dello stato](../../extensibility/debugger/execution-control-and-state-evaluation.md)
