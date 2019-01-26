---
title: IDebugExceptionEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugExceptionEvent2
helpviewer_keywords:
- IDebugExceptionEvent2 interface
ms.assetid: 53d32e59-a84b-4710-833e-c5ab08100516
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1ac5c3aceb9519d66c185f78bdde37861467ecdf
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "54983874"
---
# <a name="idebugexceptionevent2"></a>IDebugExceptionEvent2
Il motore di debug (DE) invia questa interfaccia al gestore di sessione di debug (SDM) quando viene generata un'eccezione del programma in fase di esecuzione.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IDebugExceptionEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Note per gli implementatori  
 La Germania implementa questa interfaccia al report che si è verificata un'eccezione nel programma sottoposto a debug. Il [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) interfaccia deve essere implementata per lo stesso oggetto di questa interfaccia. Usa il modello SDM [QueryInterface](/cpp/atl/queryinterface) per l'accesso di `IDebugEvent2` interfaccia.  
  
## <a name="notes-for-callers"></a>Note per i chiamanti  
 La Germania crea e invia l'oggetto evento per segnalare un'eccezione. L'evento verrà inviato usando il [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) funzione di callback che viene fornito per il modello SDM quando associato al programma in fase di debug.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
 Nella tabella seguente sono illustrati i metodi di `IDebugExceptionEvent2`.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[GetException](../../../extensibility/debugger/reference/idebugexceptionevent2-getexception.md)|Ottiene informazioni dettagliate sull'eccezione che ha generato questo evento.|  
|[GetExceptionDescription](../../../extensibility/debugger/reference/idebugexceptionevent2-getexceptiondescription.md)|Ottiene una descrizione leggibile dall'utente per l'eccezione generata un'eccezione che ha generato questo evento.|  
|[CanPassToDebuggee](../../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md)|Determina se il motore di debug (DE) supporta la possibilità di passare questa eccezione per il programma in fase di debug quando si riprende l'esecuzione.|  
|[PassToDebuggee](../../../extensibility/debugger/reference/idebugexceptionevent2-passtodebuggee.md)|Specifica se l'eccezione deve essere passata per il programma in fase di debug quando si riprende l'esecuzione o se l'eccezione deve essere eliminato.|  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg.h  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="remarks"></a>Note  
 Prima di inviare l'evento, il DE controlla per verificare se questo evento di eccezione è stato designato un'eccezione first-chance o secondo-chance da una chiamata precedente a [SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md). Se è stata designata come un'eccezione first-chance, la `IDebugExceptionEvent2` evento viene inviato per il modello SDM. In caso contrario la Germania offre la possibilità di gestire l'eccezione dell'applicazione. Se non viene fornito alcun gestore di eccezioni e se l'eccezione è stata designata come un'eccezione second-chance, la `IDebugExceptionEvent2` evento viene inviato per il modello SDM. In caso contrario, il DE riprende l'esecuzione del programma e il sistema operativo o il runtime gestisce l'eccezione.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)