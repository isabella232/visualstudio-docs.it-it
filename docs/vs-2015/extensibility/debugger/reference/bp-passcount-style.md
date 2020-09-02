---
title: BP_PASSCOUNT_STYLE | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- BP_PASSCOUNT_STYLE
helpviewer_keywords:
- BP_PASSCOUNT_STYLE structure
ms.assetid: 0a647047-e2d5-4724-a0b8-68108425ecad
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: deb4ce7c464e8518faff55957e1873ef1cd92c39
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68153363"
---
# <a name="bp_passcount_style"></a>BP_PASSCOUNT_STYLE
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Specifica la condizione associata al numero di passaggi del punto di interruzione che determina l'attivazione del punto di interruzione.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
enum enum_BP_PASSCOUNT_STYLE {   
   BP_PASSCOUNT_NONE             = 0x0000,  
   BP_PASSCOUNT_EQUAL            = 0x0001,  
   BP_PASSCOUNT_EQUAL_OR_GREATER = 0x0002,  
   BP_PASSCOUNT_MOD              = 0x0003  
};  
typedef DWORD BP_PASSCOUNT_STYLE;  
```  
  
```csharp  
public enum enum_BP_PASSCOUNT_STYLE {   
   BP_PASSCOUNT_NONE             = 0x0000,  
   BP_PASSCOUNT_EQUAL            = 0x0001,  
   BP_PASSCOUNT_EQUAL_OR_GREATER = 0x0002,  
   BP_PASSCOUNT_MOD              = 0x0003  
};  
```  
  
## <a name="members"></a>Membri  
 BP_PASSCOUNT_NONE  
 Non specifica alcuno stile di conteggio passaggi del punto di interruzione.  
  
 BP_PASSCOUNT_EQUAL  
 Imposta lo stile del conteggio pass per il punto di interruzione su uguale. Il punto di interruzione viene attivato quando il numero di volte in cui viene raggiunto il punto di interruzione è uguale al numero di passaggi.  
  
 BP_PASSCOUNT_EQUAL_OR_GREATER  
 Imposta lo stile del conteggio pass per il punto di interruzione su uguale o maggiore. Il punto di interruzione viene attivato quando il numero di volte in cui viene raggiunto il punto di interruzione è maggiore o uguale al numero di passaggi.  
  
 BP_PASSCOUNT_MOD  
 Specifica un numero di passaggi modulo. Se, ad esempio, il numero di passaggi è del tipo `BP_PASSCOUNT_MOD` e il valore del numero di passaggi è 4, il punto di interruzione viene attivato ogni volta che il numero di passaggi è un multiplo di 4.  
  
## <a name="remarks"></a>Osservazioni  
 Utilizzato per il `stylePassCount` membro della struttura [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md) che è a sua volta un membro delle strutture [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) e [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) .  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg. h  
  
 Spazio dei nomi: Microsoft. VisualStudio. Debugger. Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md)   
 [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)   
 [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)
