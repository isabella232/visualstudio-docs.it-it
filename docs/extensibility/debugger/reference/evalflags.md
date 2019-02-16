---
title: EVALFLAGS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- EVALFLAGS
helpviewer_keywords:
- EVALFLAGS enumeration
ms.assetid: 7b2cb14a-511a-4fef-9e4f-308139719fba
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3f780f06188d738deeb7f4b781fba1313e46db6d
ms.sourcegitcommit: 752f03977f45169585e407ef719450dbe219b7fc
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/15/2019
ms.locfileid: "56315768"
---
# <a name="evalflags"></a>EVALFLAGS
Specifica i flag che controllano la valutazione dell'espressione.

## <a name="syntax"></a>Sintassi

```cpp
enum enum_EVALFLAGS {
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
public enum enum_EVALFLAGS {
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

Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche
[Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)  
[EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)  
[EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)
