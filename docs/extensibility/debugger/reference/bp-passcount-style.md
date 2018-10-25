---
title: BP_PASSCOUNT_STYLE | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- BP_PASSCOUNT_STYLE
helpviewer_keywords:
- BP_PASSCOUNT_STYLE structure
ms.assetid: 0a647047-e2d5-4724-a0b8-68108425ecad
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: f382c83813eb794fc48e33310ba8381030b424fc
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49846122"
---
# <a name="bppasscountstyle"></a>BP_PASSCOUNT_STYLE
Specifica la condizione associata con il punto di interruzione pass che fa sì che il punto di interruzione da attivare.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
enum enum_BP_PASSCOUNT_STYLE {   
   BP_PASSCOUNT_NONE             = 0x0000,  
   BP_PASSCOUNT_EQUAL            = 0x0001,  
   BP_PASSCOUNT_EQUAL_OR_GREATER = 0x0002,  
   BP_PASSCOUNT_MOD              = 0x0003  
};  
typedef DWORD BP_PASSCOUNT_STYLE;  
```  
  
```csharp  
public enum enum_BP_PASSCOUNT_STYLE {   
   BP_PASSCOUNT_NONE             = 0x0000,  
   BP_PASSCOUNT_EQUAL            = 0x0001,  
   BP_PASSCOUNT_EQUAL_OR_GREATER = 0x0002,  
   BP_PASSCOUNT_MOD              = 0x0003  
};  
```  
  
## <a name="members"></a>Membri  
 BP_PASSCOUNT_NONE  
 Specifica nessuno stile di punto di interruzione pass conteggio.  
  
 BP_PASSCOUNT_EQUAL  
 Imposta lo stile di conteggio pass punto di interruzione deve essere uguale a. Il punto di interruzione viene attivato quando il numero di volte in cui che viene raggiunto il punto di interruzione uguale al conteggio pass.  
  
 BP_PASSCOUNT_EQUAL_OR_GREATER  
 Imposta lo stile di punto di interruzione pass conteggio maggiore o uguale. Il punto di interruzione viene attivato quando il numero di volte in cui che viene raggiunto il punto di interruzione è uguale o maggiore del numero di pass.  
  
 BP_PASSCOUNT_MOD  
 Specifica un modulo conteggio esecuzioni di test. Ad esempio, se il conteggio di pass è del tipo `BP_PASSCOUNT_MOD` e il valore del conteggio pass è 4, viene attivato ogni volta che il numero di passaggi è un multiplo di 4 il punto di interruzione.  
  
## <a name="remarks"></a>Note  
 Utilizzato per il `stylePassCount` membro del [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md) struttura che a sua volta è un membro del [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) e [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) strutture.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md)   
 [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)   
 [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)