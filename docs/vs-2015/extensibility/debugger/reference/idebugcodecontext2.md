---
title: IDebugCodeContext2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugCodeContext2
helpviewer_keywords:
- IDebugCodeContext2 interface
ms.assetid: 3670439e-2171-405d-9d77-dedb0f1cba93
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2e06fd709b2d076b6fa8de7f104e907eb1b35a42
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68190951"
---
# <a name="idebugcodecontext2"></a>IDebugCodeContext2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Questa interfaccia rappresenta la posizione iniziale di un'istruzione di codice. Per la maggior parte delle architetture di runtime oggi, un contesto di codice può essere considerato come un indirizzo nel flusso di esecuzione di un programma.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IDebugCodeContext2 : IDebugMemoryContext2  
```  
  
## <a name="notes-for-implementers"></a>Note per gli implementatori  
 Il motore di debug implementa questa interfaccia per correlare la posizione di un'istruzione del codice a una posizione del documento.  
  
## <a name="notes-for-callers"></a>Note per i chiamanti  
 I metodi su molte interfacce restituiscono questa interfaccia, in genere [GetCodeContext](../../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md). Viene anche usato ampiamente con l'interfaccia [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md) , oltre che con le informazioni di risoluzione del punto di interruzione.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
 Oltre ai metodi sull'interfaccia [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) , questa interfaccia implementa i metodi seguenti:  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[GetDocumentContext](../../../extensibility/debugger/reference/idebugcodecontext2-getdocumentcontext.md)|Ottiene il contesto del documento che corrisponde al contesto del codice attivo.|  
|[GetLanguageInfo](../../../extensibility/debugger/reference/idebugcodecontext2-getlanguageinfo.md)|Ottiene le informazioni sulla lingua per questo contesto del codice.|  
  
## <a name="remarks"></a>Osservazioni  
 La differenza principale tra un' `IDebugCodeContext2` interfaccia e un'interfaccia [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) è che un `IDebugCodeContext2` è sempre allineato all'istruzione. Ciò significa che un oggetto `IDebugCodeContext2` sta sempre puntando all'inizio di un'istruzione, mentre un `IDebugMemoryContext2` può puntare a qualsiasi byte di memoria nell'architettura di run-time. `IDebugCodeContext2` viene incrementato in base alle istruzioni anziché alle dimensioni di archiviazione di base (in genere byte).  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg. h  
  
 Spazio dei nomi: Microsoft. VisualStudio. Debugger. Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md)   
 [CanSetNextStatement](../../../extensibility/debugger/reference/idebugthread2-cansetnextstatement.md)   
 [SetNextStatement](../../../extensibility/debugger/reference/idebugthread2-setnextstatement.md)   
 [GetCodeContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getcodecontext.md)   
 [GetCodeContext](../../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md)   
 [Prossimo](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-next.md)   
 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)
