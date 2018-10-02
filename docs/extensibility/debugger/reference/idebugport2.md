---
title: IDebugPort2 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugPort2
helpviewer_keywords:
- IDebugPort2 interface
ms.assetid: 8fd87f05-a950-4d14-b925-98be29d4facc
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 29b16652cdbed4f6e4ee2ab6b98e52ee3a868c48
ms.sourcegitcommit: ad5fb20f18b23eb8bd2568717f61edc6b7eee5e7
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47858236"
---
# <a name="idebugport2"></a>IDebugPort2
Questa interfaccia rappresenta una porta di debug in un computer.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IDebugPort2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Note per gli implementatori  
 Un fornitore di porte personalizzato implementa questa interfaccia per rappresentare una porta di debug in un computer.  
  
 Se la porta di supporta l'invio degli eventi porta, è necessario implementare anche il <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer> interfaccia per supportare un' <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint> interfaccia che a sua volta fornisce la [IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md) interfaccia.  
  
## <a name="notes-for-callers"></a>Note per i chiamanti  
 Le chiamate a [GetPort](../../../extensibility/debugger/reference/idebugportsupplier2-getport.md) oppure [Aggiungi porta](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md) restituire questa interfaccia, che rappresenta la porta richiesta.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
 Nella tabella seguente sono illustrati i metodi di `IDebugPort2`.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[GetPortName](../../../extensibility/debugger/reference/idebugport2-getportname.md)|Restituisce il nome della porta.|  
|[GetPortId](../../../extensibility/debugger/reference/idebugport2-getportid.md)|Restituisce l'identificatore di porta.|  
|[GetPortRequest](../../../extensibility/debugger/reference/idebugport2-getportrequest.md)|Restituisce la richiesta utilizzata per creare una porta (se disponibile).|  
|[GetPortSupplier](../../../extensibility/debugger/reference/idebugport2-getportsupplier.md)|Restituisce il fornitore della porta per questa porta.|  
|[GetProcess](../../../extensibility/debugger/reference/idebugport2-getprocess.md)|Restituisce un'interfaccia per il processo dato identificatore del processo.|  
|[EnumProcesses](../../../extensibility/debugger/reference/idebugport2-enumprocesses.md)|Enumera tutti i processi in esecuzione su una porta.|  
  
## <a name="remarks"></a>Note  
 La porta locale fornisce l'accesso a tutti i processi e i programmi in esecuzione nel computer locale. Le altre porte potrebbero rappresentare una connessione via cavo seriale di un dispositivo basato su Windows CE o una connessione di rete a un computer non DCOM. Il `IDebugPort2` interfaccia viene utilizzata per trovare il nome e l'identificatore di una porta ed enumerare tutti i processi in esecuzione sulla porta. Funzionalità per l'avvio e terminazione dei processi sulla porta vengono implementate nel `IDebugPortEx2` interfaccia.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)   
 [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)