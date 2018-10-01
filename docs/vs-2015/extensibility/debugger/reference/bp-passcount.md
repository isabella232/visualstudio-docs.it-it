---
title: BP_PASSCOUNT | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- BP_PASSCOUNT
helpviewer_keywords:
- BP_PASSCOUNT structure
ms.assetid: 791ac175-b897-4c70-873e-240da7e0ac89
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d0706ddf3ee032d612ba72f31c59c7675376aae4
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47517171"
---
# <a name="bppasscount"></a>BP_PASSCOUNT
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [BP_PASSCOUNT](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/bp-passcount).  
  
Descrive il numero e le condizioni in cui viene attivato un punto di interruzione condizionale.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
typedef struct _BP_PASSCOUNT {   
   DWORD              dwPassCount;  
   BP_PASSCOUNT_STYLE stylePassCount;  
} BP_PASSCOUNT;  
```  
  
```csharp  
public struct BP_PASSCOUNT {   
   public uint dwPassCount;  
   public uint stylePassCount;  
};  
```  
  
## <a name="members"></a>Membri  
 `dwPassCount`  
 Il numero di volte in cui passa sopra il punto di interruzione prima che venga attivata.  
  
 `stylePassCount`  
 Un valore compreso il [BP_PASSCOUNT_STYLE](../../../extensibility/debugger/reference/bp-passcount-style.md) conteggio esecuzioni di test di enumerazione che specifica lo stile del punto di interruzione.  
  
## <a name="remarks"></a>Note  
 Questa struttura è un membro del [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) struttura.  
  
 Questa struttura viene anche passata come parametro per il[SetPassCount](../../../extensibility/debugger/reference/idebugboundbreakpoint2-setpasscount.md) e[SetPassCount](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-setpasscount.md) metodi.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Strutture e unioni](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)   
 [SetPassCount](../../../extensibility/debugger/reference/idebugboundbreakpoint2-setpasscount.md)   
 [SetPassCount](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-setpasscount.md)   
 [BP_PASSCOUNT_STYLE](../../../extensibility/debugger/reference/bp-passcount-style.md)

