---
title: IEnumCodePaths2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IEnumCodePaths2
helpviewer_keywords:
- IEnumCodePaths2 interface
ms.assetid: 17ec9f9e-dc06-4532-b5db-da52efcc8630
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e43491c329753e50e7c733afb55ecd4f415d11a0
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53965233"
---
# <a name="ienumcodepaths2"></a>IEnumCodePaths2
Questa interfaccia rappresenta un elenco di percorsi del codice.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IEnumCodePaths2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Note per gli implementatori  
 Il motore di debug (DE) implementa questa interfaccia per rappresentare un elenco di percorsi del codice.  
  
## <a name="notes-for-callers"></a>Note per i chiamanti  
 Chiamare [EnumCodePaths](../../../extensibility/debugger/reference/idebugprogram2-enumcodepaths.md) per ottenere questa interfaccia.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
 Nella tabella seguente sono illustrati i metodi di `IEnumCodePaths2`.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[avanti](../../../extensibility/debugger/reference/ienumcodepaths2-next.md)|Recupera un determinato numero di percorsi di codice in una sequenza di enumerazione.|  
|[Skip](../../../extensibility/debugger/reference/ienumcodepaths2-skip.md)|Ignora un determinato numero di percorsi di codice in una sequenza di enumerazione.|  
|[Reset](../../../extensibility/debugger/reference/ienumcodepaths2-reset.md)|Reimposta una sequenza di enumerazione all'inizio.|  
|[Clone](../../../extensibility/debugger/reference/ienumcodepaths2-clone.md)|Crea un enumeratore che contiene lo stesso stato di enumerazione dell'enumeratore corrente.|  
|[GetCount](../../../extensibility/debugger/reference/ienumcodepaths2-getcount.md)|Ottiene il numero di percorsi di codice in un enumeratore.|  
  
## <a name="remarks"></a>Note  
 Un percorso di codice rappresenta una chiamata di punto o una funzione di branch in un programma. Un elenco di percorsi di codice rappresenta il percorso attraverso cui ha avuto l'esecuzione del codice.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg.h  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)