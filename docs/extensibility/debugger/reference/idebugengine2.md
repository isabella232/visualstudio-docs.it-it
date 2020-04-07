---
title: Proprietà IDebugEngine2 . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine2
helpviewer_keywords:
- IDebugEngine2 interface
ms.assetid: 1f0e9ac0-6dfb-461a-976c-888d82144cdb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5e00751db052adeefee828829ec89309a3adba4b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80730856"
---
# <a name="idebugengine2"></a>IDebugEngine2
Questa interfaccia rappresenta un motore di debug (DE). Viene utilizzato per gestire vari aspetti di una sessione di debug, dalla creazione di punti di interruzione all'impostazione e la cancellazione delle eccezioni.

## <a name="syntax"></a>Sintassi

```
IDebugEngine2 : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Questa interfaccia viene implementata da un DE personalizzato per gestire il debug dei programmi. Questa interfaccia deve essere implementata dal DE.

## <a name="notes-for-callers"></a>Note per i chiamanti
 Questa interfaccia viene chiamata dal gestore di sessione di debug (SDM) per gestire la sessione di debug, inclusa la gestione delle eccezioni, la creazione di punti di interruzione e la risposta agli eventi sincroni inviati dal DE.

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
 Nella tabella seguente vengono `IDebugEngine2`illustrati i metodi di .

|Metodo|Descrizione|
|------------|-----------------|
|[EnumPrograms](../../../extensibility/debugger/reference/idebugengine2-enumprograms.md)|Crea un enumeratore per tutti i programmi sottoposti a debug da un DE.|
|[Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md)|Associa un DE a un programma.|
|[CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md)|Crea un punto di interruzione in sospeso nel DE.|
|[SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md)|Specifica come il DE deve gestire una determinata eccezione.|
|[RemoveSetException](../../../extensibility/debugger/reference/idebugengine2-removesetexception.md)|Rimuove l'eccezione specificata in modo che non venga più gestita dal motore di debug.|
|[RemoveAllSetExceptions](../../../extensibility/debugger/reference/idebugengine2-removeallsetexceptions.md)|Rimuove l'elenco delle eccezioni che l'IDE ha impostato per una particolare architettura di runtime o linguaggio.|
|[GetEngineID](../../../extensibility/debugger/reference/idebugengine2-getengineid.md)|Ottiene il GUID del file DE.|
|[DestroyProgram](../../../extensibility/debugger/reference/idebugengine2-destroyprogram.md)|Informa un DE che il programma specificato è stato in genere terminato e che il DE deve pulire tutti i riferimenti al programma e inviare un evento di eliminazione del programma.|
|[ContinueFromSynchronousEvent](../../../extensibility/debugger/reference/idebugengine2-continuefromsynchronousevent.md)|Chiamato dal modello SDM per indicare che è stato ricevuto ed elaborato un evento di debug sincrono, precedentemente inviato dal DE al modello SDM.|
|[SetLocale](../../../extensibility/debugger/reference/idebugengine2-setlocale.md)|Imposta le impostazioni locali del DE.|
|[SetRegistryRoot](../../../extensibility/debugger/reference/idebugengine2-setregistryroot.md)|Imposta la radice del Registro di sistema attualmente in uso dal DE.|
|[SetMetric](../../../extensibility/debugger/reference/idebugengine2-setmetric.md)|Imposta una metrica.|
|[CauseBreak](../../../extensibility/debugger/reference/idebugengine2-causebreak.md)|Richiede che tutti i programmi sottoposti a debug da questo DE interrompano l'esecuzione alla successiva esecuzione di uno dei relativi thread.|

## <a name="requirements"></a>Requisiti
 Intestazione: Msdbg.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche
- [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
- [GetEngine](../../../extensibility/debugger/reference/idebugenginecreateevent2-getengine.md)
