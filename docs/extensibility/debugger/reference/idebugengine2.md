---
description: Questa interfaccia rappresenta un motore di debug .
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
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126710318"
---
# <a name="idebugengine2"></a>IDebugEngine2
Questa interfaccia rappresenta un motore di debug . Viene usato per gestire vari aspetti di una sessione di debug, dalla creazione di punti di interruzione all'impostazione e alla cancellazione delle eccezioni.

## <a name="syntax"></a>Sintassi

```
IDebugEngine2 : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Questa interfaccia viene implementata da un'istanza personalizzata di DE per gestire il debug dei programmi. Questa interfaccia deve essere implementata da DE.

## <a name="notes-for-callers"></a>Note per i chiamanti
 Questa interfaccia viene chiamata da Gestione debug sessione (SDM) per gestire la sessione di debug, inclusa la gestione delle eccezioni, la creazione di punti di interruzione e la risposta agli eventi sincroni inviati da DE.

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
 Nella tabella seguente vengono illustrati i metodi di `IDebugEngine2` .

|Metodo|Descrizione|
|------------|-----------------|
|[EnumPrograms](../../../extensibility/debugger/reference/idebugengine2-enumprograms.md)|Crea un enumeratore per tutti i programmi di cui è in corso il debug da parte di un de.|
|[Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md)|Collega un de a un programma.|
|[CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md)|Crea un punto di interruzione in sospeso in DE.|
|[SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md)|Specifica il modo in cui DE deve gestire una determinata eccezione.|
|[RemoveSetException](../../../extensibility/debugger/reference/idebugengine2-removesetexception.md)|Rimuove l'eccezione specificata in modo che non sia più gestita dal motore di debug.|
|[RemoveAllSetExceptions](../../../extensibility/debugger/reference/idebugengine2-removeallsetexceptions.md)|Rimuove l'elenco di eccezioni impostate dall'IDE per una particolare architettura o linguaggio di runtime.|
|[GetEngineID](../../../extensibility/debugger/reference/idebugengine2-getengineid.md)|Ottiene il GUID di DE.|
|[DestroyProgram](../../../extensibility/debugger/reference/idebugengine2-destroyprogram.md)|Informa un de che il programma specificato è stato terminato atipicamente e che de deve pulire tutti i riferimenti al programma e inviare un evento di eliminazione programma.|
|[ContinueFromSynchronousEvent](../../../extensibility/debugger/reference/idebugengine2-continuefromsynchronousevent.md)|Chiamato da SDM per indicare che è stato ricevuto ed elaborato un evento di debug sincrono inviato in precedenza da DE a SDM.|
|[SetLocale](../../../extensibility/debugger/reference/idebugengine2-setlocale.md)|Imposta le impostazioni locali del de.|
|[SetRegistryRoot](../../../extensibility/debugger/reference/idebugengine2-setregistryroot.md)|Imposta la radice del Registro di sistema attualmente in uso da DE.|
|[SetMetric](../../../extensibility/debugger/reference/idebugengine2-setmetric.md)|Imposta una metrica.|
|[CauseBreak](../../../extensibility/debugger/reference/idebugengine2-causebreak.md)|Richiede che l'esecuzione di tutti i programmi di cui è in corso il debug venga interrotta al successivo tentativo di esecuzione di uno dei relativi thread.|

## <a name="requirements"></a>Requisiti
 Intestazione: Msdbg.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
- [GetEngine](../../../extensibility/debugger/reference/idebugenginecreateevent2-getengine.md)
