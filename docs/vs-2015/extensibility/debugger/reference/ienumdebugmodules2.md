---
title: IEnumDebugModules2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IEnumDebugModules2
helpviewer_keywords:
- IEnumDebugModules2
ms.assetid: 4fe28074-a960-41ad-b74d-b57f04c0c0ad
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 9f66587f462e1bbfb60704c5c75dc2299cb9ce36
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68160976"
---
# <a name="ienumdebugmodules2"></a>IEnumDebugModules2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Questa interfaccia enumera un elenco di moduli.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IEnumDebugModules2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Note per gli implementatori  
 Il motore di debug (DE) implementa questa interfaccia per rappresentare un elenco di moduli caricati per un programma.  
  
## <a name="notes-for-callers"></a>Note per i chiamanti  
 Visual Studio chiama [EnumModules](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md) per ottenere questa interfaccia.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
 La tabella seguente illustra i metodi di `IEnumDebugModules2` .  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[Avanti](../../../extensibility/debugger/reference/ienumdebugmodules2-next.md)|Recupera un numero specificato di moduli in una sequenza di enumerazione.|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugmodules2-skip.md)|Ignora un numero specificato di moduli in una sequenza di enumerazione.|  
|[Reimpostazione](../../../extensibility/debugger/reference/ienumdebugmodules2-reset.md)|Riporta all'inizio la sequenza di enumerazione.|  
|[Clone](../../../extensibility/debugger/reference/ienumdebugmodules2-clone.md)|Crea un enumeratore che contiene lo stesso stato di enumerazione dell'enumeratore corrente.|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugmodules2-getcount.md)|Ottiene il numero di moduli.|  
  
## <a name="remarks"></a>Osservazioni  
 Visual Studio usa questa interfaccia principalmente per aggiornare la finestra **moduli** .  
  
 Ai fini del debug in Visual Studio, un programma è una sequenza logica di istruzioni di codice che possono superare i limiti dei moduli, quindi la necessità di un elenco di moduli per una singola interfaccia [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) . Il primo modulo dell'elenco contiene in genere il punto di ingresso iniziale per il programma associato.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg. h  
  
 Spazio dei nomi: Microsoft. VisualStudio. Debugger. Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [EnumModules](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md)
