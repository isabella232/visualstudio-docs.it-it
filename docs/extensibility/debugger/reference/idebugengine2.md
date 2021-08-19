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
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: bacc450f29e950f5fd2d339244ad3715dead711a
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122089186"
---
# <a name="idebugengine2"></a>IDebugEngine2
Questa interfaccia rappresenta un motore di debug (DE). Viene usato per gestire vari aspetti di una sessione di debug, dalla creazione di punti di interruzione all'impostazione e alla cancellazione delle eccezioni.

## <a name="syntax"></a>Sintassi

```
IDebugEngine2 : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Questa interfaccia viene implementata da un DE personalizzato per gestire il debug dei programmi. Questa interfaccia deve essere implementata dal de.

## <a name="notes-for-callers"></a>Note per i chiamanti
 Questa interfaccia viene chiamata da Gestione debug sessione (SDM) per gestire la sessione di debug, inclusa la gestione delle eccezioni, la creazione di punti di interruzione e la risposta agli eventi sincroni inviati dal de.

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
 Nella tabella seguente vengono illustrati i metodi di `IDebugEngine2` .

|Metodo|Descrizione|
|------------|-----------------|
|[EnumPrograms](../../../extensibility/debugger/reference/idebugengine2-enumprograms.md)|Crea un enumeratore per tutti i programmi di cui è in corso il debug da parte di un de.|
|[Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md)|Collega un de a un programma.|
|[CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md)|Crea un punto di interruzione in sospeso nel de.|
|[SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md)|Specifica la modalità di gestione di una determinata eccezione da parte del de.|
|[RemoveSetException](../../../extensibility/debugger/reference/idebugengine2-removesetexception.md)|Rimuove l'eccezione specificata in modo che non sia più gestita dal motore di debug.|
|[RemoveAllSetExceptions](../../../extensibility/debugger/reference/idebugengine2-removeallsetexceptions.md)|Rimuove l'elenco di eccezioni impostate dall'IDE per una particolare architettura o linguaggio di runtime.|
|[GetEngineID](../../../extensibility/debugger/reference/idebugengine2-getengineid.md)|Ottiene il GUID del de.|
|[DestroyProgram](../../../extensibility/debugger/reference/idebugengine2-destroyprogram.md)|Informa un de che il programma specificato è stato terminato atipicamente e che il de deve pulire tutti i riferimenti al programma e inviare un evento di eliminazione del programma.|
|[ContinueFromSynchronousEvent](../../../extensibility/debugger/reference/idebugengine2-continuefromsynchronousevent.md)|Chiamato da SDM per indicare che è stato ricevuto ed elaborato un evento di debug sincrono, inviato in precedenza dal de al modello SDM.|
|[SetLocale](../../../extensibility/debugger/reference/idebugengine2-setlocale.md)|Imposta le impostazioni locali del de.|
|[SetRegistryRoot](../../../extensibility/debugger/reference/idebugengine2-setregistryroot.md)|Imposta la radice del Registro di sistema attualmente in uso da DE.|
|[SetMetric](../../../extensibility/debugger/reference/idebugengine2-setmetric.md)|Imposta una metrica.|
|[CauseBreak](../../../extensibility/debugger/reference/idebugengine2-causebreak.md)|Richiede che tutti i programmi di cui viene eseguito il debug da questa dea arrestino l'esecuzione al successivo tentativo di esecuzione di uno dei thread.|

## <a name="requirements"></a>Requisiti
 Intestazione: Msdbg.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
- [GetEngine](../../../extensibility/debugger/reference/idebugenginecreateevent2-getengine.md)
