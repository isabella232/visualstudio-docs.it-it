---
title: PARSEFLAGS | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- PARSEFLAGS
helpviewer_keywords:
- PARSEFLAGS enumeration
ms.assetid: 47943f0a-54cb-4493-a62e-5dba97bd4c35
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ccf50c5bd85ae6a69a24da3a3d830009e3297be8
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47532954"
---
# <a name="parseflags"></a>PARSEFLAGS
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [PARSEFLAGS](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/parseflags).  
  
Specifica la modalità di analisi dell'espressione.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
enum enum_PARSEFLAGS {   
   PARSE_EXPRESSION            = 0x0001,  
   PARSE_FUNCTION_AS_ADDRESS   = 0x0002,  
   PARSE_DESIGN_TIME_EXPR_EVAL = 0x1000  
};  
typedef DWORD PARSEFLAGS;  
```  
  
```csharp  
public enum enum_PARSEFLAGS {   
   PARSE_EXPRESSION            = 0x0001,  
   PARSE_FUNCTION_AS_ADDRESS   = 0x0002,  
   PARSE_DESIGN_TIME_EXPR_EVAL = 0x1000  
};  
```  
  
## <a name="members"></a>Membri  
 PARSE_EXPRESSION  
 Indica che l'espressione non è un'istruzione.  
  
 PARSE_FUNCTION_AS_ADDRESS  
 Indica che l'espressione deve essere analizzato (e valutate in un secondo momento) come un indirizzo.  
  
 PARSE_DESIGN_TIME_EXPR_EVAL  
 Indica che l'espressione viene analizzato durante la fase di progettazione (ovvero, quando una finestra di progettazione è aperto).  
  
## <a name="remarks"></a>Note  
 Passato come parametro per il [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) e [analizzare](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) metodi.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)   
 [Analisi](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md)

