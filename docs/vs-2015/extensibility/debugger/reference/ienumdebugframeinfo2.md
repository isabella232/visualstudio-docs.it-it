---
title: IEnumDebugFrameInfo2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IEnumDebugFrameInfo2
helpviewer_keywords:
- IEnumDebugFrameInfo2
ms.assetid: 994e30ad-435a-4f9e-9272-d96d9e01099c
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6cc6a0ff332fd6feac72ce4abf38b5319e63c913
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68161017"
---
# <a name="ienumdebugframeinfo2"></a>IEnumDebugFrameInfo2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Questa interfaccia enumera le strutture [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) .  
  
## <a name="syntax"></a>Sintassi  
  
```  
IEnumDebugFrameInfo2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Note per gli implementatori  
 Il motore di debug (DE) implementa questa interfaccia per fornire un elenco di strutture che descrivono lo stack di chiamate corrente.  
  
## <a name="notes-for-callers"></a>Note per i chiamanti  
 Visual Studio chiama [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) per ottenere questa interfaccia ogni volta che viene eseguito un punto di interruzione, un'eccezione o un'interruzione in un programma di cui è in corso il debug.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
 La tabella seguente illustra i metodi di `IEnumDebugFrameInfo2` .  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[Avanti](../../../extensibility/debugger/reference/ienumdebugframeinfo2-next.md)|Recupera un numero specificato di strutture [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) in una sequenza di enumerazione.|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugframeinfo2-skip.md)|Ignora un numero specificato di strutture [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) in una sequenza di enumerazione.|  
|[Reimpostazione](../../../extensibility/debugger/reference/ienumdebugframeinfo2-reset.md)|Riporta all'inizio la sequenza di enumerazione.|  
|[Clone](../../../extensibility/debugger/reference/ienumdebugframeinfo2-clone.md)|Crea un enumeratore che contiene lo stesso stato di enumerazione dell'enumeratore corrente.|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugframeinfo2-getcount.md)|Ottiene il numero di strutture [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) in un enumeratore.|  
  
## <a name="remarks"></a>Osservazioni  
 Visual Studio ottiene questa interfaccia come primo passaggio per la gestione di un punto di interruzione, un'eccezione o una pausa generata dall'utente sul programma di cui è in corso il debug. L'elenco di strutture [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) rappresenta lo stack di chiamate corrente, con la chiamata di funzione corrente all'inizio dell'elenco e la chiamata di funzione meno recente alla fine dell'elenco. Ogni `FRAMEINFO` rappresenta una stack frame, un contesto in cui le espressioni possono essere valutate e le variabili locali esaminate.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg. h  
  
 Spazio dei nomi: Microsoft. VisualStudio. Debugger. Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)   
 [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)
