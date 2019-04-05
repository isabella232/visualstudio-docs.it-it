---
title: IEnumDebugCodeContexts2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IEnumDebugCodeContexts2
helpviewer_keywords:
- IEnumDebugCodeContexts2
ms.assetid: 72915146-215f-4c99-a034-131b2b474e0e
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f36da19e6bc47d70010dd96a26256537803ccb29
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58965558"
---
# <a name="ienumdebugcodecontexts2"></a>IEnumDebugCodeContexts2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Questa interfaccia enumera i contesti di codice associati, la sessione di debug oppure con un particolare programma o il documento.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IEnumDebugCodeContexts2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Note per gli implementatori  
 Il motore di debug (DE) implementa questa interfaccia per rappresentare un elenco di contesti di codice per una posizione di testo specifico in un programma o un elenco di contesti di codice per un contesto di documento specifico.  
  
## <a name="notes-for-callers"></a>Note per i chiamanti  
 Chiamare [EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md) per ottenere questa interfaccia che rappresenta un elenco di contesti di codice per una posizione di testo specifico nel documento di origine del programma.  
  
 Chiamare [EnumCodeContexts](../../../extensibility/debugger/reference/idebugdocumentcontext2-enumcodecontexts.md) per ottenere questa interfaccia che rappresenta un elenco di tutti i contesti di codice in un documento di origine specifico.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
 Nella tabella seguente sono illustrati i metodi di `IEnumDebugCodeContexts2`.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[avanti](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-next.md)|Recupera un determinato numero di contesti di codice in una sequenza di enumerazione.|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-skip.md)|Ignora un determinato numero di contesti di codice in una sequenza di enumerazione.|  
|[Reset](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-reset.md)|Reimposta una sequenza di enumerazione all'inizio.|  
|[Clone](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-clone.md)|Crea un enumeratore che contiene lo stesso stato di enumerazione dell'enumeratore corrente.|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-getcount.md)|Ottiene il numero di contesti di codice in un enumeratore.|  
  
## <a name="remarks"></a>Note  
 Le chiamate di Visual Studio [EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md) per popolare un elenco di contesti di codice l'utente può scegliere rispetto a quando l'impostazione dell'istruzione successiva o che mostra il disassembly per un file di origine. Più contesti di codice possono verificarsi, ad esempio, quando sono presenti più istanze di un modello di tipo C++.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg.h  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md)   
 [EnumCodeContexts](../../../extensibility/debugger/reference/idebugdocumentcontext2-enumcodecontexts.md)
