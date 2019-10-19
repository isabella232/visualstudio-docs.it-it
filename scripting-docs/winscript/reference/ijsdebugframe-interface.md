---
title: Interfaccia metodo ijsdebugframe | Microsoft Docs
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
ms.openlocfilehash: 91fe8cdf91b0c2121f4a1a7f111794b0fbe36669
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575109"
---
# <a name="ijsdebugframe-interface"></a>Interfaccia IJsDebugFrame
Rappresenta uno stack frame.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
IJsDebugFrame : public IUnknown;  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-methods"></a>Metodi pubblici  
  
|Name|Descrizione|  
|----------|-----------------|  
|[Metodo IJsDebugFrame::Evaluate](../../winscript/reference/ijsdebugframe-evaluate-method.md)|Valutare un'espressione nel contesto di questo stack frame.|  
|[Metodo IJsDebugFrame::GetDebugProperty](../../winscript/reference/ijsdebugframe-getdebugproperty-method.md)|Restituisce un visualizzatore proprietà per questo stack frame.|  
|[Metodo IJsDebugFrame::GetDocumentPositionWithId](../../winscript/reference/ijsdebugframe-getdocumentpositionwithid-method.md)|Restituisce la posizione corrente di questo stack frame all'interno del documento a livello di utente.|  
|[Metodo IJsDebugFrame::GetDocumentPositionWithName](../../winscript/reference/ijsdebugframe-getdocumentpositionwithname-method.md)|Restituisce la posizione corrente di questo stack frame all'interno del documento a livello di utente.|  
|[Metodo IJsDebugFrame::GetName](../../winscript/reference/ijsdebugframe-getname-method.md)|Ottiene il nome descrittivo dello stack frame.|  
|[Metodo IJsDebugFrame::GetReturnAddress](../../winscript/reference/ijsdebugframe-getreturnaddress-method.md)|Ottiene l'indirizzo mittente inserito in corrispondenza di ' Start ' (vedere GetStackRange) del frame.|  
|[Metodo IJsDebugFrame::GetStackRange](../../winscript/reference/ijsdebugframe-getstackrange-method.md)|Restituisce l'intervallo di indirizzi assoluto della stack frame JavaScript logica.|  
  
## <a name="requirements"></a>Requisiti  
 **Intestazione:** jscript9diag. h  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimenti sulle interfacce Windows Script](../../winscript/reference/windows-script-interfaces-reference.md)