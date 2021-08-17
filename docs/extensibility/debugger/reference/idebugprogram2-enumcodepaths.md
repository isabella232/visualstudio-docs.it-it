---
description: Recupera un elenco di percorsi di codice per una determinata posizione in un file di origine.
title: IDebugProgram2::EnumCodePaths | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::EnumCodePaths
helpviewer_keywords:
- IDebugProgram2::EnumCodePaths
ms.assetid: fb100c3c-9c29-4d63-bd1f-a3e531cb395f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 23d2b0af61df6b84a9ba7b02d0bb73dcd51f8cbfc07dce816383d67eda9bf531
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121292364"
---
# <a name="idebugprogram2enumcodepaths"></a>IDebugProgram2::EnumCodePaths
Recupera un elenco di percorsi di codice per una determinata posizione in un file di origine.

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
[in] Parola sotto il cursore nella **visualizzazione Origine** o **Disassembly** nell'IDE.

`pStart`\
[in] Oggetto [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) che rappresenta il contesto del codice corrente.

`pFrame`\
[in] Oggetto [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) che rappresenta il stack frame associato al punto di interruzione corrente.

`fSource`\
[in] Diverso da zero ( `TRUE` ) se nella vista **Origine** oppure zero ( ) se nella `FALSE` vista **Disassembly.**

`ppEnum`\
[out] Restituisce un [oggetto IEnumCodePaths2](../../../extensibility/debugger/reference/ienumcodepaths2.md) contenente un elenco dei percorsi del codice.

`ppSafety`\
[out] Restituisce un [oggetto IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) che rappresenta un contesto di codice aggiuntivo da impostare come punto di interruzione nel caso in cui il percorso del codice scelto viene ignorato. Ciò può verificarsi, ad esempio, nel caso di un'espressione booleana con corto circuito.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Commenti
 Un percorso di codice descrive il nome di un metodo o di una funzione chiamata per raggiungere il punto corrente nell'esecuzione del programma. Un elenco di percorsi di codice rappresenta lo stack di chiamate.

## <a name="see-also"></a>Vedi anche
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IEnumCodePaths2](../../../extensibility/debugger/reference/ienumcodepaths2.md)
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
- [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)
