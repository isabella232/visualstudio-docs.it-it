---
description: Questa interfaccia rappresenta un motore di debug (DE).
title: IDebugEngine2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine2
helpviewer_keywords:
- IDebugEngine2 interface
ms.assetid: 1f0e9ac0-6dfb-461a-976c-888d82144cdb
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: f6e32c4798ad1bea65a9aadcf8a0d73052acc238
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105066152"
---
# <a name="idebugengine2"></a>IDebugEngine2
Questa interfaccia rappresenta un motore di debug (DE). Viene usato per gestire vari aspetti di una sessione di debug, dalla creazione di punti di interruzione all'impostazione e alla cancellazione delle eccezioni.

## <a name="syntax"></a>Sintassi

```
IDebugEngine2 : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Questa interfaccia viene implementata da un DE personalizzato per gestire il debug dei programmi. Questa interfaccia deve essere implementata da DE.

## <a name="notes-for-callers"></a>Note per i chiamanti
 Questa interfaccia viene chiamata da gestione debug sessione (SDM) per gestire la sessione di debug, inclusa la gestione delle eccezioni, la creazione di punti di interruzione e la risposta a eventi sincroni inviati da DE.

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
 La tabella seguente illustra i metodi di `IDebugEngine2` .

|Metodo|Descrizione|
|------------|-----------------|
|[EnumPrograms](../../../extensibility/debugger/reference/idebugengine2-enumprograms.md)|Crea un enumeratore per tutti i programmi di cui è in corso il debug da un DE.|
|[Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md)|Connette un DE a un programma.|
|[CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md)|Crea un punto di interruzione in sospeso nell'oggetto DE.|
|[SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md)|Specifica la modalità di gestione di un'eccezione specificata da parte di.|
|[RemoveSetException](../../../extensibility/debugger/reference/idebugengine2-removesetexception.md)|Rimuove l'eccezione specificata in modo che non venga più gestita dal motore di debug.|
|[RemoveAllSetExceptions](../../../extensibility/debugger/reference/idebugengine2-removeallsetexceptions.md)|Rimuove l'elenco di eccezioni impostate dall'IDE per un'architettura o una lingua di runtime particolare.|
|[GetEngineID](../../../extensibility/debugger/reference/idebugengine2-getengineid.md)|Ottiene il GUID dell'oggetto DE.|
|[DestroyProgram](../../../extensibility/debugger/reference/idebugengine2-destroyprogram.md)|Informa un DE che il programma specificato è stato interrotto in modo atipico e che il DE dovrebbe pulire tutti i riferimenti al programma e inviare un evento di eliminazione del programma.|
|[ContinueFromSynchronousEvent](../../../extensibility/debugger/reference/idebugengine2-continuefromsynchronousevent.md)|Chiamato da SDM per indicare che è stato ricevuto ed elaborato un evento di debug sincrono, precedentemente inviato da DE a SDM.|
|[SetLocale](../../../extensibility/debugger/reference/idebugengine2-setlocale.md)|Imposta le impostazioni locali della DE.|
|[SetRegistryRoot](../../../extensibility/debugger/reference/idebugengine2-setregistryroot.md)|Imposta la radice del registro di sistema attualmente utilizzata dal DE.|
|[SetMetric](../../../extensibility/debugger/reference/idebugengine2-setmetric.md)|Imposta una metrica.|
|[CauseBreak](../../../extensibility/debugger/reference/idebugengine2-causebreak.md)|Richiede che tutti i programmi sottoposti a debug da questa interruzione di esecuzione al successivo tentativo di esecuzione di uno dei thread.|

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg. h

 Spazio dei nomi: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
- [GetEngine](../../../extensibility/debugger/reference/idebugenginecreateevent2-getengine.md)
