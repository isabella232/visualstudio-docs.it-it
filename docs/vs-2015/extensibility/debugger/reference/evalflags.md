---
title: EVALFLAGS | Microsoft Docs
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
- EVALFLAGS
helpviewer_keywords:
- EVALFLAGS enumeration
ms.assetid: 7b2cb14a-511a-4fef-9e4f-308139719fba
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 088c63fb1683bdf277ed1c3c5aba06a3156efbbf
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47525727"
---
# <a name="evalflags"></a>EVALFLAGS
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [EVALFLAGS](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/evalflags).  
  
Specifica i flag che controllano la valutazione dell'espressione.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
enum enum_EVALFLAGS {  
   EVAL_RETURNVALUE = 0x0002,  
   EVAL_NOSIDEEFFECTS = 0x0004,  
   EVAL_ALLOWBPS = 0x0008,  
   EVAL_ALLOWERRORREPORT = 0x0010,  
   EVAL_FUNCTION_AS_ADDRESS = 0x0040,  
   EVAL_NOFUNCEVAL = 0x0080,  
   EVAL_NOEVENTS = 0x1000  
};  
typedef DWORD EVALFLAGS;  
```  
  
```csharp  
public enum enum_EVALFLAGS {  
   EVAL_RETURNVALUE = 0x0002,  
   EVAL_NOSIDEEFFECTS = 0x0004,  
   EVAL_ALLOWBPS = 0x0008,  
   EVAL_ALLOWERRORREPORT = 0x0010,  
   EVAL_FUNCTION_AS_ADDRESS = 0x0040,  
   EVAL_NOFUNCEVAL = 0x0080,  
   EVAL_NOEVENTS = 0x1000  
}  
```  
  
## <a name="members"></a>Membri  
 EVAL_RETURNVALUE  
 Specifica che il valore restituito, se presente, da valutare.  
  
 EVAL_NOSIDEEFFECTS  
 Specifica che gli effetti collaterali non saranno consentite.  
  
 EVAL_ALLOWBPS  
 Specifica l'arresto per i punti di interruzione.  
  
 EVAL_ALLOWERRORREPORT  
 Specifica la segnalazione errori per l'host deve essere autorizzato. Utilizzato principalmente per la valutazione dell'espressione in uno script in Internet Explorer.  
  
 EVAL_FUNCTION_AS_ADDRESS  
 Funzioni di forze deve essere valutata come indirizzi, anziché richiamare la funzione.  
  
 EVAL_NOFUNCEVAL  
 Impedisce che funzione viene valutata. Si consideri, ad esempio, il `int` token dell'espressione `myExpression(int) + 10`. Questa funzione può essere valutata correttamente come un indirizzo, ma non come un valore.  
  
 EVAL_NOEVENTS  
 Flag per indicare che gli eventi che si verificano durante la valutazione dell'espressione non devono essere inviati al gestore di sessione di debug (SDM) o all'IDE.  
  
## <a name="remarks"></a>Note  
 Questi flag vengono passati come argomento per il [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) e [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) metodi.  
  
 Questi flag possono essere combinati con un OR bit per bit.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)   
 [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)

