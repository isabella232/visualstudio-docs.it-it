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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68179936"
---
# <a name="context_info"></a>CONTEXT_INFO
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Questa struttura descrive un contesto di memoria o un contesto di codice.  
  
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
 Combinazione di flag di [CONTEXT_INFO_FIELDS](../../../extensibility/debugger/reference/context-info-fields.md) enumerazione che specifica i campi che vengono compilati<strong>.</strong>  
  
 bstrModuleUrl  
 Nome del modulo in cui si trova il contesto.  
  
 bstrFunction  
 Nome della funzione in cui si trova il contesto.  
  
 posFunctionOffset  
 Struttura [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) che identifica l'offset di riga e di colonna della funzione associata al contesto del codice.  
  
 bstrAddress  
 Indirizzo nel codice in cui si trova il contesto specificato.  
  
 bstrAddressOffset  
 Offset dell'indirizzo nel codice in cui si trova il contesto specificato.  
  
 bstrAddressAbsolute  
 Indirizzo assoluto in memoria in cui si trova il contesto specificato.  
  
## <a name="remarks"></a>Osservazioni  
 Questa struttura viene restituita da una chiamata al metodo [GetInfo](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md) .  
  
 Un uso tipico di questa struttura è il supporto di una finestra di debug della **memoria** .  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg. h  
  
 Spazio dei nomi: Microsoft. VisualStudio. Debugger. Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Strutture e unioni](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [GetInfo](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md)   
 [CONTEXT_INFO_FIELDS](../../../extensibility/debugger/reference/context-info-fields.md)   
 [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)
