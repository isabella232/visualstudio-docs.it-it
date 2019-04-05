---
title: CONTEXT_INFO | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- CONTEXT_INFO
helpviewer_keywords:
- CONTEXT_INFO structure
ms.assetid: 6b513f4e-e7b0-4969-adf0-2205ccc1e09b
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f4e8c1b438cd2fa2721e81f055695e5836c26d12
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58968869"
---
# <a name="contextinfo"></a>CONTEXT_INFO
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Questa struttura descrive un contesto in memoria o il contesto del codice.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
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
