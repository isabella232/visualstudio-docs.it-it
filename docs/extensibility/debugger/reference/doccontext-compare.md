---
title: DOCCONTEXT_COMPARE | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- DOCCONTEXT_COMPARE
helpviewer_keywords:
- DOCCONTEXT_COMPARE enumeration
ms.assetid: ed947c34-b07e-4b69-8381-b6e7cb842862
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 8f092666833b80dd59ed4b7b3345c379078ce2bf
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49862957"
---
# <a name="doccontextcompare"></a>DOCCONTEXT_COMPARE
Specifica i criteri per il confronto di due contesti di documento.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
enum enum_DOCCONTEXT_COMPARE {   
   DOCCONTEXT_EQUAL         = 0x0001,  
   DOCCONTEXT_LESS_THAN     = 0x0002,  
   DOCCONTEXT_GREATER_THAN  = 0x0003,  
   DOCCONTEXT_SAME_DOCUMENT = 0x0004  
};  
typedef DWORD DOCCONTEXT_COMPARE;  
```  
  
```csharp  
enum enum_DOCCONTEXT_COMPARE {   
   DOCCONTEXT_EQUAL         = 0x0001,  
   DOCCONTEXT_LESS_THAN     = 0x0002,  
   DOCCONTEXT_GREATER_THAN  = 0x0003,  
   DOCCONTEXT_SAME_DOCUMENT = 0x0004  
};  
```  
  
## <a name="members"></a>Membri  
 DOCCONTEXT_EQUAL  
 Trovare il primo contesto del documento nell'elenco che è uguale al contesto di documento di destinazione.  
  
 DOCCONTEXT_LESS_THAN  
 Trovare il primo contesto del documento nell'elenco che è minore rispetto al contesto di documento di destinazione.  
  
 DOCCONTEXT_GREATER_THAN  
 Trovare il primo contesto del documento nell'elenco che è maggiore rispetto al contesto di documento di destinazione.  
  
 DOCCONTEXT_SAME_DOCUMENT  
 Trovare il primo contesto del documento nell'elenco che è nello stesso documento come contesto di documento di destinazione.  
  
## <a name="remarks"></a>Note  
 Passato come argomento per il [confrontare](../../../extensibility/debugger/reference/idebugdocumentcontext2-compare.md) (metodo).  
  
 Questi valori vengono utilizzati per specificare un criterio di confronto per trovare il primo contesto del documento in un elenco. Un contesto di documento viene fornito un elenco di contesti di documento di confrontarsi con tramite il `IDebugDocumentContext2::Compare` (metodo). Il contesto del documento prima nell'elenco per il quale l'operatore di confronto è `true` viene quindi restituito.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [Compare](../../../extensibility/debugger/reference/idebugdocumentcontext2-compare.md)