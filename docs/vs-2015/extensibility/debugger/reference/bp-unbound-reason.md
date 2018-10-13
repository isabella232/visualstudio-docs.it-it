---
title: BP_UNBOUND_REASON | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- BP_UNBOUND_REASON
helpviewer_keywords:
- BP_UNBOUND_REASON enumeration
ms.assetid: 939b6f9c-113b-471d-9f30-b03871af6285
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 4d6060753a3208fd09485a52d0959daf31f6c3e0
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49250666"
---
# <a name="bpunboundreason"></a>BP_UNBOUND_REASON
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Indica il motivo che è stato dissociato un punto di interruzione.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
enum enum_BP_UNBOUND_REASON {   
   BPUR_UNKNOWN           = 0x0000,  
   BPUR_CODE_UNLOADED     = 0x0002,  
   BPUR_BREAKPOINT_REBIND = 0x0003,  
   BPUR_BREAKPOINT_ERROR  = 0x0004  
};  
typedef DWORD BP_UNBOUND_REASON;  
```  
  
```csharp  
public enum enum_BP_UNBOUND_REASON {   
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
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetReason](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2-getreason.md)

