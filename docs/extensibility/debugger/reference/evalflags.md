---
description: Specifica i flag che controllano la valutazione dell'espressione.
title: EVALFLAGS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- EVALFLAGS
helpviewer_keywords:
- EVALFLAGS enumeration
ms.assetid: 7b2cb14a-511a-4fef-9e4f-308139719fba
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 531d155104475b84d881358711a6aa3f1d0bf2ce
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/05/2021
ms.locfileid: "102150939"
---
# <a name="evalflags"></a>EVALFLAGS
Specifica i flag che controllano la valutazione dell'espressione.

## <a name="syntax"></a>Sintassi

```cpp
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

## <a name="fields"></a>Campi
`EVAL_RETURNVALUE`\
Specifica che il valore restituito, se presente, deve essere valutato.

`EVAL_NOSIDEEFFECTS`\
Specifica che gli effetti collaterali non sono consentiti.

`EVAL_ALLOWBPS`\
Specifica l'arresto in corrispondenza di punti di interruzione.

`EVAL_ALLOWERRORREPORT`\
Specifica la segnalazione degli errori all'host da consentire. Utilizzato principalmente per la valutazione di espressioni nello script in Internet Explorer.

`EVAL_FUNCTION_AS_ADDRESS`\
Impone la valutazione delle funzioni come indirizzi, anziché richiamare la funzione.

`EVAL_NOFUNCEVAL`\
Impedisce la valutazione della funzione. Si consideri, ad esempio, il `int` token nell'espressione `myExpression(int) + 10` . Questa funzione può essere valutata correttamente come un indirizzo, ma non come valore.

`EVAL_NOEVENTS`\
Flag che indica che gli eventi che si verificano durante la valutazione dell'espressione non devono essere inviati a gestione debug sessione (SDM) o all'IDE.

## <a name="remarks"></a>Commenti
Questi flag vengono passati come argomento ai metodi [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) e [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) .

Questi flag possono essere combinati con un OR bit per bit.

## <a name="requirements"></a>Requisiti
Intestazione: msdbg. h

Spazio dei nomi: Microsoft. VisualStudio. Debugger. Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)
- [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)
