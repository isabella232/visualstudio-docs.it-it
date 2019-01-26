---
title: THREADPROPERTIES | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- THREADPROPERTIES
helpviewer_keywords:
- THREADPROPERTIES structure
ms.assetid: 7d397207-db03-4ec0-9f79-3794056ed89f
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3ad8b989b916e668fede0f8193c124d05785fd46
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "54922661"
---
# <a name="threadproperties"></a>THREADPROPERTIES
Vengono descritte le proprietà di un thread.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
typedef struct _tagTHREADPROPERTIES {   
   THREADPROPERTY_FIELDS dwFields;  
   DWORD                 dwThreadId;  
   DWORD                 dwSuspendCount;  
   DWORD                 dwThreadState;  
   BSTR                  bstrPriority;  
   BSTR                  bstrName;  
   BSTR                  bstrLocation;  
} THREADPROPERTIES;  
```  
  
```csharp  
public struct THREADPROPERTIES {   
   public uint   dwFields;  
   public uint   dwThreadId;  
   public uint   dwSuspendCount;  
   public uint   dwThreadState;  
   public string bstrPriority;  
   public string bstrName;  
   public string bstrLocation;  
};  
```  
  
## <a name="members"></a>Membri  
 dwFields  
 Una combinazione di flag dal [THREADPROPERTY_FIELDS](../../../extensibility/debugger/reference/threadproperty-fields.md) enumerazione, che indica quali campi in questa struttura sono validi.  
  
 dwThreadId  
 ID del thread.  
  
 dwSuspendCount  
 Il thread di conteggio di sospensione.  
  
 dwThreadState  
 Un valore compreso il [THREADSTATE](../../../extensibility/debugger/reference/threadstate.md) enumerazione che indica lo stato del thread operativo.  
  
 bstrPriority  
 Stringa che specifica la priorità del thread; ad esempio, "Superiore al normale", "Normal" o "Ora critiche".  
  
 bstName  
 Il nome del thread.  
  
 bstrLocation  
 Il percorso di thread (in genere il frame dello stack più in alto), in genere espresso come il nome del metodo in cui l'esecuzione è attualmente bloccata.  
  
## <a name="remarks"></a>Note  
 Questa struttura viene compilata tramite una chiamata per il [GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md) (metodo). Le informazioni restituite così vengano in genere utilizzate per il popolamento di **thread** finestra.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg.h  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Strutture e unioni](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md)   
 [THREADPROPERTY_FIELDS](../../../extensibility/debugger/reference/threadproperty-fields.md)   
 [THREADSTATE](../../../extensibility/debugger/reference/threadstate.md)