---
title: IDebugMemoryBytes2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugMemoryBytes2
helpviewer_keywords:
- IDebugMemoryBytes2 interface
ms.assetid: d7647575-0e06-4190-88f5-ca40b82209a4
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 1e23588e8da41b981f372210def65fa34a7e55bf
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "68180544"
---
# <a name="idebugmemorybytes2"></a>IDebugMemoryBytes2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Questa interfaccia rappresenta i byte di memoria.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IDebugMemoryBytes2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Note per gli implementatori  
 Il motore di debug (DE) implementa questa interfaccia per rappresentare i byte nella memoria.  
  
## <a name="notes-for-callers"></a>Note per i chiamanti  
 [GetMemoryBytes](../../../extensibility/debugger/reference/idebugprogram2-getmemorybytes.md) restituisce questa interfaccia per fornire l'accesso alla memoria di sistema. [GetMemoryBytes](../../../extensibility/debugger/reference/idebugproperty2-getmemorybytes.md) e [GetMemoryBytes](../../../extensibility/debugger/reference/idebugreference2-getmemorybytes.md) restituire questa interfaccia per fornire l'accesso a byte di un oggetto.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
 Nella tabella seguente sono illustrati i metodi di `IDebugMemoryBytes2`.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[ReadAt](../../../extensibility/debugger/reference/idebugmemorybytes2-readat.md)|Legge una sequenza di byte, a partire da una posizione specificata.|  
|[WriteAt](../../../extensibility/debugger/reference/idebugmemorybytes2-writeat.md)|Scrive `dwCount` byte a partire `pStartContext`.|  
|[GetSize](../../../extensibility/debugger/reference/idebugmemorybytes2-getsize.md)|Ottiene la dimensione, espressa in byte, della memoria rappresentata da questa interfaccia.|  
  
## <a name="remarks"></a>Note  
 Per le proprietà, un [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) interfaccia che rappresenta una matrice fornisce un `IDebugMemoryBytes2` interfaccia per accedere ai valori della matrice.  
  
 Visual Studio **visualizzazione per la memoria** chiamate [GetMemoryBytes](../../../extensibility/debugger/reference/idebugprogram2-getmemorybytes.md) per recuperare un `IDebugMemoryBytes2` interfaccia per l'accesso a memoria di sistema. L'indirizzo a cui accedere viene ottenuto l'analisi dell'espressione immessa come indirizzo nella visualizzazione della memoria e quindi valutando l'espressione analizzata usando [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) per ottenere un `IDebugProperty2` interfaccia. Una chiamata a [GetMemoryContext](../../../extensibility/debugger/reference/idebugproperty2-getmemorycontext.md) restituisce il [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) che descrive l'indirizzo di memoria. In questo contesto in memoria viene quindi passato a [ReadAt](../../../extensibility/debugger/reference/idebugmemorybytes2-readat.md) e [WriteAt](../../../extensibility/debugger/reference/idebugmemorybytes2-writeat.md).  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg.h  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [GetMemoryBytes](../../../extensibility/debugger/reference/idebugprogram2-getmemorybytes.md)   
 [GetMemoryBytes](../../../extensibility/debugger/reference/idebugproperty2-getmemorybytes.md)   
 [GetMemoryBytes](../../../extensibility/debugger/reference/idebugreference2-getmemorybytes.md)   
 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)
