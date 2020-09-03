---
title: DOCCONTEXT_COMPARE | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- DOCCONTEXT_COMPARE
helpviewer_keywords:
- DOCCONTEXT_COMPARE enumeration
ms.assetid: ed947c34-b07e-4b69-8381-b6e7cb842862
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6d0fd8cff2f352c8ede674be64062a738c1f3d02
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68198791"
---
# <a name="doccontext_compare"></a>DOCCONTEXT_COMPARE
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Specifica i criteri per il confronto di due contesti di documento.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
enum enum_DOCCONTEXT_COMPARE {   
   DOCCONTEXT_EQUAL         = 0x0001,  
   DOCCONTEXT_LESS_THAN     = 0x0002,  
   DOCCONTEXT_GREATER_THAN  = 0x0003,  
   DOCCONTEXT_SAME_DOCUMENT = 0x0004  
};  
typedef DWORD DOCCONTEXT_COMPARE;  
```  
  
```csharp  
enum enum_DOCCONTEXT_COMPARE {   
   DOCCONTEXT_EQUAL         = 0x0001,  
   DOCCONTEXT_LESS_THAN     = 0x0002,  
   DOCCONTEXT_GREATER_THAN  = 0x0003,  
   DOCCONTEXT_SAME_DOCUMENT = 0x0004  
};  
```  
  
## <a name="members"></a>Membri  
 DOCCONTEXT_EQUAL  
 Trovare il primo contesto del documento nell'elenco uguale al contesto del documento di destinazione.  
  
 DOCCONTEXT_LESS_THAN  
 Trovare il primo contesto del documento nell'elenco inferiore al contesto del documento di destinazione.  
  
 DOCCONTEXT_GREATER_THAN  
 Trovare il primo contesto del documento nell'elenco maggiore del contesto del documento di destinazione.  
  
 DOCCONTEXT_SAME_DOCUMENT  
 Trovare il primo contesto del documento nell'elenco che si trova nello stesso documento del contesto del documento di destinazione.  
  
## <a name="remarks"></a>Osservazioni  
 Passato come argomento al metodo [compare](../../../extensibility/debugger/reference/idebugdocumentcontext2-compare.md) .  
  
 Questi valori vengono utilizzati per specificare un criterio di confronto per individuare il primo contesto del documento in un elenco. A un contesto del documento viene assegnato un elenco di contesti di documenti da confrontare con il `IDebugDocumentContext2::Compare` metodo. Viene quindi restituito il primo contesto del documento nell'elenco per il quale viene restituito l'operatore di confronto `true` .  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg. h  
  
 Spazio dei nomi: Microsoft. VisualStudio. Debugger. Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [Confronta](../../../extensibility/debugger/reference/idebugdocumentcontext2-compare.md)
