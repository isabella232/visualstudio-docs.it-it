---
title: IDebugPropertyCreateEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugPropertyCreateEvent2
helpviewer_keywords:
- IDebugPropertyCreateEvent2 interface
ms.assetid: 33b3082b-a42e-488a-a1e4-dadf506f922c
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: edbd781fbaba285b56afca027aed657ee7585f3f
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "55003142"
---
# <a name="idebugpropertycreateevent2"></a>IDebugPropertyCreateEvent2
Questa interfaccia viene inviata dal motore di debug (DE) al gestore di sessione di debug (SDM) durante la creazione di una proprietà che è associata a un documento specifico.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IDebugPropertyCreateEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Note per gli implementatori  
 La Germania implementa questa interfaccia per segnalare che una proprietà sia stata creata. Il [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) interfaccia deve essere implementata per lo stesso oggetto di questa interfaccia. Usa il modello SDM [QueryInterface](/cpp/atl/queryinterface) per l'accesso di `IDebugEvent2` interfaccia. Questa interfaccia viene implementata se la Germania ha creato una proprietà associata a uno script che è stato caricato o creato e se lo script deve essere visualizzato nell'IDE.  
  
## <a name="notes-for-callers"></a>Note per i chiamanti  
 La Germania crea e invia l'oggetto evento al report che è stata creata una proprietà. L'evento viene inviato tramite il [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) funzione di callback che viene fornito per il modello SDM quando è associato al programma in fase di debug.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
 La tabella seguente illustra il metodo di `IDebugPropertyCreateEvent2` interfaccia.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[GetDebugProperty](../../../extensibility/debugger/reference/idebugpropertycreateevent2-getdebugproperty.md)|Ottiene la nuova proprietà.|  
  
## <a name="remarks"></a>Note  
 Se una proprietà ha un documento specifico o script associati, la Germania possa inviare questo evento per il modello SDM per aggiornare il **documenti Script** finestra con il nome del documento. Il modello SDM chiamerà [GetExtendedInfo](../../../extensibility/debugger/reference/idebugproperty2-getextendedinfo.md) con l'argomento `guidDocument` per recuperare un `VARIANT` contenenti un [IUnknown](/cpp/atl/iunknown) puntatore. Il modello SDM chiamerà [QueryInterface](/cpp/atl/queryinterface) su questo puntatore per recuperare il [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) interfaccia che consente di aggiornare il **documenti Script** finestra.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg.h  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)