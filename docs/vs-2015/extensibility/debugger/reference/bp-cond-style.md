---
title: BP_COND_STYLE | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- BP_COND_STYLE
helpviewer_keywords:
- BP_COND_STYLE enumeration
ms.assetid: a93b1412-f447-48a1-af9d-38f3dbb3092f
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: fbb2674381992bd86f0144af103615f0a3922fcf
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58966883"
---
# <a name="bpcondstyle"></a>BP_COND_STYLE
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Specifica lo stile di condizione punto di interruzione per in sospeso e associati i punti di interruzione.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
enum enum_BP_COND_STYLE {   
   BP_COND_NONE         = 0x0000,  
   BP_COND_WHEN_TRUE    = 0x0001,  
   BP_COND_WHEN_CHANGED = 0x0002  
};  
typedef DWORD BP_COND_STYLE;  
```  
  
```csharp  
public enum enum_BP_COND_STYLE {   
   BP_COND_NONE         = 0x0000,  
   BP_COND_WHEN_TRUE    = 0x0001,  
   BP_COND_WHEN_CHANGED = 0x0002  
};  
```  
  
## <a name="members"></a>Membri  
 BP_COND_NONE  
 Quando viene raggiunta la posizione del punto di interruzione, viene attivato il punto di interruzione. Nessuna condizione di punto di interruzione specificati.  
  
 BP_COND_WHEN_TRUE  
 Viene attivato il punto di interruzione solo quando il punto di interruzione associata l'espressione condizionale restituisce `true`.  
  
 BP_COND_WHEN_CHANGED  
 Viene attivato il punto di interruzione solo quando il valore dell'espressione condizionale associato il punto di interruzione è stato modificato da relativo valutazione precedente.  
  
## <a name="remarks"></a>Note  
 Utilizzato per il `styleCondition` membro della [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md) struttura.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg.h  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md)
