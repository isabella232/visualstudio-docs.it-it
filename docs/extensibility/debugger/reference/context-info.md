---
title: CONTEXT_INFO | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- CONTEXT_INFO
helpviewer_keywords:
- CONTEXT_INFO structure
ms.assetid: 6b513f4e-e7b0-4969-adf0-2205ccc1e09b
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 43f3ead0a927786a183c547e6d87d1cb71adda12
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "54966608"
---
# <a name="contextinfo"></a>CONTEXT_INFO
Questa struttura descrive un contesto in memoria o il contesto del codice.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
typedef struct _tagCONTEXT_INFO {   
   CONTEXT_INFO_FIELDS dwFields;  
   BSTR                bstrModuleUrl;  
   BSTR                bstrFunction;  
   TEXT_POSITION       posFunctionOffset;  
   BSTR                bstrAddress;  
   BSTR                bstrAddressOffset;  
   BSTR                bstrAddressAbsolute;  
} CONTEXT_INFO;  
```  
  
```csharp  
public struct CONTEXT_INFO {  
   public uint          dwFields;  
   public string        bstrModuleUrl;  
   public string        bstrFunction;  
   public TEXT_POSITION posFunctionOffset;  
   public string        bstrAddress;  
   public string        bstrAddressOffset;  
   public string        bstrAddressAbsolute;  
};  
```  
  
## <a name="members"></a>Membri  
 dwFields  
 Una combinazione di flag da egli [CONTEXT_INFO_FIELDS](../../../extensibility/debugger/reference/context-info-fields.md) enumerazione che specifica quali campi vengono compilati<strong>.</strong>  
  
 bstrModuleUrl  
 Il nome del modulo in cui si trova il contesto.  
  
 bstrFunction  
 Il nome della funzione in cui si trova il contesto.  
  
 posFunctionOffset  
 Oggetto [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) struttura che identifica l'offset di riga e alla colonna della funzione associata al contesto del codice.  
  
 bstrAddress  
 L'indirizzo nel codice in cui si trova nel contesto specificato.  
  
 bstrAddressOffset  
 L'offset dell'indirizzo nel codice in cui si trova nel contesto specificato.  
  
 bstrAddressAbsolute  
 L'indirizzo assoluto in memoria in cui si trova nel contesto specificato.  
  
## <a name="remarks"></a>Note  
 Questa struttura viene restituita da una chiamata per il [GetInfo](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md) (metodo).  
  
 Un utilizzo tipico per questa struttura è supportare una **memoria** finestra di debug.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg.h  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Strutture e unioni](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [GetInfo](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md)   
 [CONTEXT_INFO_FIELDS](../../../extensibility/debugger/reference/context-info-fields.md)   
 [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)