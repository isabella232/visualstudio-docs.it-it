---
title: IDebugEngine2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine2
helpviewer_keywords:
- IDebugEngine2 interface
ms.assetid: 1f0e9ac0-6dfb-461a-976c-888d82144cdb
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ce60ffb1143dd763ea14390b0b55e105f74d1b53
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66352561"
---
# <a name="idebugengine2"></a>IDebugEngine2
Questa interfaccia rappresenta un motore di debug (DE). Viene utilizzato per gestire diversi aspetti di una sessione di debug, dalla creazione di punti di interruzione all'impostazione e la cancellazione delle eccezioni.

## <a name="syntax"></a>Sintassi

```
IDebugEngine2 : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Questa interfaccia viene implementata da un CRI personalizzato per la gestione debug dei programmi. Questa interfaccia deve essere implementata per la Germania.

## <a name="notes-for-callers"></a>Note per i chiamanti
 Questa interfaccia viene chiamata dal gestore di sessione di debug (SDM) per gestire la sessione di debug, tra cui la gestione delle eccezioni, la creazione dei punti di interruzione e risposta agli eventi sincroni inviati per la Germania.

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
 Nella tabella seguente sono illustrati i metodi di `IDebugEngine2`.

|Metodo|Descrizione|
|------------|-----------------|
|[EnumPrograms](../../../extensibility/debugger/reference/idebugengine2-enumprograms.md)|Crea un enumeratore per tutti i programmi in fase di debug da un CRI.|
|[Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md)|Collega un CRI a un programma.|
|[CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md)|Crea un punto di interruzione in sospeso il DE.|
|[SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md)|Specifica come la Germania deve gestire una determinata eccezione.|
|[RemoveSetException](../../../extensibility/debugger/reference/idebugengine2-removesetexception.md)|Rimuove l'eccezione specificata in modo che non viene più gestito dal motore di debug.|
|[RemoveAllSetExceptions](../../../extensibility/debugger/reference/idebugengine2-removeallsetexceptions.md)|Rimuove l'elenco delle eccezioni che nell'IDE è impostata per un linguaggio o una particolare architettura della fase di esecuzione.|
|[GetEngineID](../../../extensibility/debugger/reference/idebugengine2-getengineid.md)|Ottiene il GUID della DE.|
|[DestroyProgram](../../../extensibility/debugger/reference/idebugengine2-destroyprogram.md)|Informa un CRI che il programma specificato è stato terminato insolitamente e che la Germania deve pulire tutti i riferimenti al programma e inviare un programma un evento di eliminazione.|
|[ContinueFromSynchronousEvent](../../../extensibility/debugger/reference/idebugengine2-continuefromsynchronousevent.md)|Chiamato per il modello SDM per indicare che un evento di debug sincrono, inviato in precedenza dal DE per il modello SDM, è stato ricevuto ed elaborato.|
|[SetLocale](../../../extensibility/debugger/reference/idebugengine2-setlocale.md)|Imposta le impostazioni locali della DE.|
|[SetRegistryRoot](../../../extensibility/debugger/reference/idebugengine2-setregistryroot.md)|Imposta la radice del Registro di sistema attualmente in uso per la Germania.|
|[SetMetric](../../../extensibility/debugger/reference/idebugengine2-setmetric.md)|Imposta una metrica.|
|[CauseBreak](../../../extensibility/debugger/reference/idebugengine2-causebreak.md)|Richiede che tutti i programmi in fase di debug da questo DE arresti la volta successiva che uno dei relativi thread tenta di eseguire l'esecuzione.|

## <a name="requirements"></a>Requisiti
 Intestazione: Msdbg.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche
- [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
- [GetEngine](../../../extensibility/debugger/reference/idebugenginecreateevent2-getengine.md)