---
description: Ottiene il flusso disassembly per questo programma o una parte di questo programma.
title: Interfaccia IDebugProgram2::GetDisassemblyStream | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::GetDisassemblyStream
helpviewer_keywords:
- IDebugProgram2::GetDisassemblyStream
ms.assetid: beda0da5-267e-4bf3-96c4-b659d29e2254
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 562edd4bf17216a1baa6248966d61e33083341dc
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122126570"
---
# <a name="idebugprogram2getdisassemblystream"></a>IDebugProgram2::GetDisassemblyStream
Ottiene il flusso disassembly per questo programma o una parte di questo programma.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT GetDisassemblyStream( 
   DISASSEMBLY_STREAM_SCOPE   dwScope,
   IDebugCodeContext2*        pCodeContext,
   IDebugDisassemblyStream2** ppDisassemblyStream
);
```

```csharp
int GetDisassemblyStream( 
   enum_DISASSEMBLY_STREAM_SCOPE  dwScope,
   IDebugCodeContext2             pCodeContext,
   out IDebugDisassemblyStream2   ppDisassemblyStream
);
```

## <a name="parameters"></a>Parametri
`dwScope`\
[in] Specifica un valore [dell'enumerazione DISASSEMBLY_STREAM_SCOPE](../../../extensibility/debugger/reference/disassembly-stream-scope.md) che definisce l'ambito del flusso disassembly.

`pCodeContext`\
[in] Oggetto [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) che rappresenta la posizione in cui avviare il flusso disassembly.

`ppDisassemblyStream`\
[out] Restituisce un [oggetto IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md) che rappresenta il flusso disassembly.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore. Restituisce `E_DISASM_NOTSUPPORTED` se il disassembly non è supportato per questa particolare architettura.

## <a name="remarks"></a>Commenti
 Se per il parametro è impostato il flag dell'enumerazione DISASSEMBLY_STREAM_SCOPE, è previsto che il disassembly restituirà un numero elevato di istruzioni `dwScopes` `DSS_HUGE` disassembly, [](../../../extensibility/debugger/reference/disassembly-stream-scope.md) ad esempio per un intero file o modulo. Se il flag non è impostato, si prevede che il disassembly sia limitato a una piccola area, in genere `DSS_HUGE` quella di una singola funzione.

## <a name="see-also"></a>Vedi anche
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [DISASSEMBLY_STREAM_SCOPE](../../../extensibility/debugger/reference/disassembly-stream-scope.md)
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
- [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)
