---
title: Interfaccia IJsDebugFrame | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 5af46b18-9d25-4a23-b8d1-fa23bea3efcf
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 57f5a848967148705a2b8dcd3f6b75dcb3a5db26
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2019
ms.locfileid: "58156814"
---
# <a name="ijsdebugframe-interface"></a>Interfaccia IJsDebugFrame
Rappresenta uno stack frame.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
IJsDebugFrame : public IUnknown;  
```  
  
## <a name="members"></a>Membri  
  
### <a name="public-methods"></a>Metodi pubblici  
  
|Nome|Descrizione|  
|----------|-----------------|  
|[Metodo IJsDebugFrame::Evaluate](../../winscript/reference/ijsdebugframe-evaluate-method.md)|Valutare un'espressione nel contesto di questo frame dello stack.|  
|[Metodo IJsDebugFrame::GetDebugProperty](../../winscript/reference/ijsdebugframe-getdebugproperty-method.md)|Restituisce un visualizzatore proprietà per questo stack frame.|  
|[Metodo IJsDebugFrame::GetDocumentPositionWithId](../../winscript/reference/ijsdebugframe-getdocumentpositionwithid-method.md)|Restituisce la posizione corrente dello stack frame all'interno del documento a livello di utente.|  
|[Metodo IJsDebugFrame::GetDocumentPositionWithName](../../winscript/reference/ijsdebugframe-getdocumentpositionwithname-method.md)|Restituisce la posizione corrente dello stack frame all'interno del documento a livello di utente.|  
|[Metodo IJsDebugFrame::GetName](../../winscript/reference/ijsdebugframe-getname-method.md)|Ottiene il nome descrittivo dello stack frame.|  
|[Metodo IJsDebugFrame::GetReturnAddress](../../winscript/reference/ijsdebugframe-getreturnaddress-method.md)|Ottiene l'indirizzo di ritorno inserito "all'inizio" (vedere GetStackRange) del frame.|  
|[Metodo IJsDebugFrame::GetStackRange](../../winscript/reference/ijsdebugframe-getstackrange-method.md)|Restituisce l'intervallo di indirizzi assoluti dello stack frame JavaScript logico.|  
  
## <a name="requirements"></a>Requisiti  
 **Intestazione:** jscript9diag.h  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimenti sulle interfacce Windows Script](../../winscript/reference/windows-script-interfaces-reference.md)