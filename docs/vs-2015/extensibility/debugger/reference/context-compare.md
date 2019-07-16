---
title: CONTEXT_COMPARE | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- CONTEXT_COMPARE
helpviewer_keywords:
- CONTEXT_COMPARE enumeration
ms.assetid: 701ed61c-a320-4c20-a335-0b840024abc0
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a9cf283cf7239b5ed74e38ca534538a286a477c2
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "68179965"
---
# <a name="contextcompare"></a>CONTEXT_COMPARE
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Specifica i criteri per il confronto di due contesti di memoria.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
enum enum_CONTEXT_COMPARE {   
   CONTEXT_EQUAL                 = 0x0001,  
   CONTEXT_LESS_THAN             = 0x0002,  
   CONTEXT_GREATER_THAN          = 0x0003,  
   CONTEXT_LESS_THAN_OR_EQUAL    = 0x0004,  
   CONTEXT_GREATER_THAN_OR_EQUAL = 0x0005,  
   CONTEXT_SAME_SCOPE            = 0x0006,  
   CONTEXT_SAME_FUNCTION         = 0x0007,  
   CONTEXT_SAME_MODULE           = 0x0008,  
   CONTEXT_SAME_PROCESS          = 0x0009  
};  
typedef DWORD CONTEXT_COMPARE;  
```  
  
```csharp  
public enum enum_CONTEXT_COMPARE {   
   CONTEXT_EQUAL                 = 0x0001,  
   CONTEXT_LESS_THAN             = 0x0002,  
   CONTEXT_GREATER_THAN          = 0x0003,  
   CONTEXT_LESS_THAN_OR_EQUAL    = 0x0004,  
   CONTEXT_GREATER_THAN_OR_EQUAL = 0x0005,  
   CONTEXT_SAME_SCOPE            = 0x0006,  
   CONTEXT_SAME_FUNCTION         = 0x0007,  
   CONTEXT_SAME_MODULE           = 0x0008,  
   CONTEXT_SAME_PROCESS          = 0x0009  
};  
```  
  
## <a name="members"></a>Members  
 CONTEXT_EQUAL  
 Trovare il primo contesto di memoria nell'elenco uguale al contesto di destinazione di memoria.  
  
 CONTEXT_LESS_THAN  
 Trovare il primo contesto di memoria nell'elenco che è minore rispetto al contesto di memoria di destinazione.  
  
 CONTEXT_GREATER_THAN  
 Trovare il primo contesto di memoria nell'elenco che è maggiore rispetto al contesto di memoria di destinazione.  
  
 CONTEXT_LESS_THAN_OR_EQUAL  
 Trovare il primo contesto di memoria nell'elenco che è minore o uguale al contesto di destinazione di memoria.  
  
 CONTEXT_GREATER_THAN_OR_EQUAL  
 Trovare il primo contesto di memoria nell'elenco che è maggiore o uguale al contesto di destinazione di memoria.  
  
 CONTEXT_SAME_SCOPE  
 Trovare il primo contesto di memoria nell'elenco che è nello stesso ambito il contesto di memoria di destinazione.  
  
 CONTEXT_SAME_FUNCTION  
 Trovare il primo contesto di memoria nell'elenco che è la stessa funzione dell'ambito della memoria di destinazione.  
  
 CONTEXT_SAME_MODULE  
 Trovare il primo contesto di memoria nell'elenco che è nello stesso modulo del contesto di destinazione di memoria.  
  
 CONTEXT_SAME_PROCESS  
 Trovare il primo contesto di memoria nell'elenco che è nello stesso processo come contesto di memoria di destinazione.  
  
## <a name="remarks"></a>Note  
 Passato come argomento per il [confrontare](../../../extensibility/debugger/reference/idebugmemorycontext2-compare.md) (metodo).  
  
 Questi valori vengono usati per trovare il primo contesto di memoria in un elenco che soddisfa i criteri di confronto specificate. Un contesto in memoria viene assegnato un elenco di contesti di memoria di confrontarsi con tramite il `IDebugMemoryContext2::Compare` (metodo). Il primo contesto di memoria nell'elenco per il quale l'operatore di confronto è `true` viene quindi restituito.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg.h  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [Compare](../../../extensibility/debugger/reference/idebugmemorycontext2-compare.md)
