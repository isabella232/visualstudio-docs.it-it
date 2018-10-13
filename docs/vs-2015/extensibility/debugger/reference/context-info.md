---
title: CONTEXT_INFO | Microsoft Docs
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
- CONTEXT_INFO
helpviewer_keywords:
- CONTEXT_INFO structure
ms.assetid: 6b513f4e-e7b0-4969-adf0-2205ccc1e09b
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 37fa2bc4ecf31588f9f56082f2ce465cb9690908
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49214326"
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
 Una combinazione di flag da egli [CONTEXT_INFO_FIELDS](../../../extensibility/debugger/reference/context-info-fields.md) enumerazione che specifica quali campi vengono compilati **.**  
  
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
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Strutture e unioni](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [GetInfo](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md)   
 [CONTEXT_INFO_FIELDS](../../../extensibility/debugger/reference/context-info-fields.md)   
 [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)

