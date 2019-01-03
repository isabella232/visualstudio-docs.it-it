---
title: BP_UNBOUND_REASON | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- BP_UNBOUND_REASON
helpviewer_keywords:
- BP_UNBOUND_REASON enumeration
ms.assetid: 939b6f9c-113b-471d-9f30-b03871af6285
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 72e8975f67925976a0c6c446d798d048068c1ad6
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53848035"
---
# <a name="bpunboundreason"></a>BP_UNBOUND_REASON
Indica il motivo che è stato dissociato un punto di interruzione.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
enum enum_BP_UNBOUND_REASON {   
   BPUR_UNKNOWN           = 0x0000,  
   BPUR_CODE_UNLOADED     = 0x0002,  
   BPUR_BREAKPOINT_REBIND = 0x0003,  
   BPUR_BREAKPOINT_ERROR  = 0x0004  
};  
typedef DWORD BP_UNBOUND_REASON;  
```  
  
```csharp  
public enum enum_BP_UNBOUND_REASON {   
   BPUR_UNKNOWN           = 0x0000,  
   BPUR_CODE_UNLOADED     = 0x0002,  
   BPUR_BREAKPOINT_REBIND = 0x0003,  
   BPUR_BREAKPOINT_ERROR  = 0x0004  
};  
```  
  
## <a name="members"></a>Membri  
 BPUR_UNKNOWN  
 Il motivo è sconosciuto.  
  
 BPUR_CODE_UNLOADED  
 Il codice che contiene il punto di interruzione è stato scaricato.  
  
 BPUR_BREAKPOINT_REBIND  
 Il punto di interruzione è stato riassociato a un percorso diverso. Ciò può verificarsi dopo la modifica e continuare le operazioni quando si sposta il punto di interruzione o quando il punto di interruzione è associata a un file con un percorso che non è più valido.  
  
 BPUR_ BREAKPOINT_ERROR  
 Il punto di interruzione viene considerato in errore dopo l'associazione. In questo caso i punti di interruzione gestite le cui condizioni non sono più valide.  
  
## <a name="remarks"></a>Note  
 Restituito dal [GetReason](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2-getreason.md) (metodo).  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg.h  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetReason](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2-getreason.md)