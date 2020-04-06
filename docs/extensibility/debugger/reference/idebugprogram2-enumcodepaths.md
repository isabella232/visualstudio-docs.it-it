---
title: Proprietà IDebugProgram2::EnumCodePaths . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::EnumCodePaths
helpviewer_keywords:
- IDebugProgram2::EnumCodePaths
ms.assetid: fb100c3c-9c29-4d63-bd1f-a3e531cb395f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b99651811cedbdb8ec0eca5b766e6d75651dd5d7
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80723040"
---
# <a name="idebugprogram2enumcodepaths"></a>IDebugProgram2::EnumCodePaths
Recupera un elenco dei percorsi di codice per una posizione specificata in un file di origine.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT EnumCodePaths( 
   LPCOLESTR            pszHint,
   IDebugCodeContext2*  pStart,
   IDebugStackFrame2*   pFrame,
   BOOL                 fSource,
   IEnumCodePaths2**    ppEnum,
   IDebugCodeContext2** ppSafety
);
```

```csharp
int EnumCodePaths( 
   string                 pszHint,
   IDebugCodeContext2     pStart,
   IDebugStackFrame2      pFrame,
   Int                    fSource,
   out IEnumCodePaths2    ppEnum,
   out IDebugCodeContext2 ppSafety
);
```

## <a name="parameters"></a>Parametri
`pszHint`\
[in] Parola sotto il cursore nella vista **origine** o **disassembly** nell'IDE.

`pStart`\
[in] Oggetto [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) che rappresenta il contesto del codice corrente.

`pFrame`\
[in] Oggetto [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) che rappresenta lo stack frame associato al punto di interruzione corrente.

`fSource`\
[in] Diverso da`TRUE`zero ( ) se nella`FALSE`vista **Origine** o zero ( ) se nella vista **Disassembly.**

`ppEnum`\
[fuori] Restituisce un oggetto [IEnumCodePaths2](../../../extensibility/debugger/reference/ienumcodepaths2.md) contenente un elenco dei percorsi del codice.

`ppSafety`\
[fuori] Restituisce un [oggetto IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) che rappresenta un contesto di codice aggiuntivo da impostare come punto di interruzione nel caso in cui il percorso del codice scelto venga ignorato. Ciò può verificarsi, ad esempio, nel caso di un'espressione booleana cortocircuito.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Osservazioni
 Un percorso di codice descrive il nome di un metodo o di una funzione chiamata per arrivare al punto corrente nell'esecuzione del programma. Un elenco di percorsi di codice rappresenta lo stack di chiamate.

## <a name="see-also"></a>Vedere anche
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IEnumCodePaths2](../../../extensibility/debugger/reference/ienumcodepaths2.md)
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
- [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)
