---
title: IDebugCoreServer2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugCoreServer2
helpviewer_keywords:
- IDebugCoreServer2 interface
ms.assetid: 9c47d0a6-9eb1-464e-bd44-fa2b552d4d36
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c0bca6ccd3738518df339084b0f6463be181e52d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68192908"
---
# <a name="idebugcoreserver2"></a>IDebugCoreServer2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Questa interfaccia viene utilizzata per rappresentare e ottenere informazioni da un server in un computer della rete.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IDebugCoreServer2 : IUknown  
```  
  
## <a name="notes-for-implementers"></a>Note per gli implementatori  
 Visual Studio implementa questa interfaccia per rappresentare un server. Ogni istanza di Visual Studio crea un'istanza di questa interfaccia.  
  
## <a name="notes-for-callers"></a>Note per i chiamanti  
 Un fornitore di porte personalizzato riceve questa interfaccia in una chiamata a un [evento](../../../extensibility/debugger/reference/idebugportevents2-event.md).  
  
 Un motore di debug può ottenere questa interfaccia indirettamente tramite una chiamata a [GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md) (che restituisce [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md), un'interfaccia derivata da `IDebugCoreServer2` ).  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
 La tabella seguente illustra i metodi di `IDebugCoreServer2` .  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[GetMachineInfo](../../../extensibility/debugger/reference/idebugcoreserver2-getmachineinfo.md)|Ottiene il nome e gli attributi di un computer.|  
|[GetMachineName](../../../extensibility/debugger/reference/idebugcoreserver2-getmachinename.md)|Ottiene il nome di un computer.|  
|[GetPortSupplier](../../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md)|Ottiene un fornitore di porte presente in un computer.|  
|[GetPort](../../../extensibility/debugger/reference/idebugcoreserver2-getport.md)|Ottiene una porta già esistente in un computer.|  
|[EnumPorts](../../../extensibility/debugger/reference/idebugcoreserver2-enumports.md)|Crea un enumeratore per tutte le porte in un computer.|  
|[EnumPortSuppliers](../../../extensibility/debugger/reference/idebugcoreserver2-enumportsuppliers.md)|Crea un enumeratore per tutti i fornitori di porte in un computer.|  
|[GetMachineUtilities_V7](../../../extensibility/debugger/reference/idebugcoreserver2-getmachineutilities-v7.md)|Ottiene le utilità del computer per un computer.|  
  
## <a name="remarks"></a>Osservazioni  
 Questa interfaccia viene usata anche da Visual Studio per esplorare i processi in esecuzione nei computer della rete.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg. h  
  
 Spazio dei nomi: Microsoft. VisualStudio. Debugger. Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)   
 [Evento](../../../extensibility/debugger/reference/idebugportevents2-event.md)   
 [GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md)   
 [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)
