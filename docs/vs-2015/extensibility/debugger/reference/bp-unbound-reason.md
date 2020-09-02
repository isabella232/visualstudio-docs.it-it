---
title: BP_UNBOUND_REASON | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- BP_UNBOUND_REASON
helpviewer_keywords:
- BP_UNBOUND_REASON enumeration
ms.assetid: 939b6f9c-113b-471d-9f30-b03871af6285
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ddff6130e2243d10c00cefec160d057516d60932
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68153273"
---
# <a name="bp_unbound_reason"></a>BP_UNBOUND_REASON
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Indica il motivo per cui un punto di interruzione non è associato.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
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
 Il punto di interruzione è stato riassociato a una posizione diversa. Questo problema può verificarsi dopo le operazioni di modifica e continuazione quando il punto di interruzione si sposta o quando il punto di interruzione è associato a un file con un percorso non più valido.  
  
 BPUR_ BREAKPOINT_ERROR  
 Il punto di interruzione viene determinato come errore dopo l'associazione. Questa situazione si verifica nei punti di interruzione gestiti le cui condizioni non sono più valide.  
  
## <a name="remarks"></a>Osservazioni  
 Restituito dal metodo [GetReason](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2-getreason.md) .  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg. h  
  
 Spazio dei nomi: Microsoft. VisualStudio. Debugger. Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetReason](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2-getreason.md)
