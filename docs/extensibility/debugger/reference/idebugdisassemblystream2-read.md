---
description: Legge le istruzioni a partire dalla posizione corrente nel flusso di Disassembly.
title: 'IDebugDisassemblyStream2:: Read | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDisassemblyStream2::Read
helpviewer_keywords:
- IDebugDisassemblyStream2::Read
ms.assetid: 7db5f6bb-73ee-45bc-b187-c1b6aa2dfdd5
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: bcabd0cc42f013b579ee32deeb33d68cd9d45f5d
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105066919"
---
# <a name="idebugdisassemblystream2read"></a>IDebugDisassemblyStream2::Read
Legge le istruzioni a partire dalla posizione corrente nel flusso di Disassembly.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT Read( 
   DWORD                     dwInstructions,
   DISASSEMBLY_STREAM_FIELDS dwFields,
   DWORD*                    pdwInstructionsRead,
   DisassemblyData*          prgDisassembly
);
```

```csharp
int Read( 
   uint                           dwInstructions,
   enum_DISASSEMBLY_STREAM_FIELDS dwFields,
   out uint                       pdwInstructionsRead,
   DisassemblyData[]              prgDisassembly
);
```

## <a name="parameters"></a>Parametri
`dwInstructions`\
in Numero di istruzioni da disassemblare. Questo valore è anche la lunghezza massima della `prgDisassembly` matrice.

`dwFields`\
in Combinazione di flag dell'enumerazione [DISASSEMBLY_STREAM_FIELDS](../../../extensibility/debugger/reference/disassembly-stream-fields.md) che indicano i campi da `prgDisassembly` compilare.

`pdwInstructionsRead`\
out Restituisce il numero di istruzioni effettivamente disassemblate.

`prgDisassembly`\
out Matrice di strutture [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md) compilata con il codice disassemblato, una struttura per istruzione disassemblata. La lunghezza di questa matrice è determinata dal `dwInstructions` parametro.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Commenti
 Il numero massimo di istruzioni disponibili nell'ambito corrente può essere ottenuto chiamando il metodo [GetSize](../../../extensibility/debugger/reference/idebugdisassemblystream2-getsize.md) .

 La posizione corrente da cui viene letta l'istruzione successiva può essere modificata chiamando il metodo [Seek](../../../extensibility/debugger/reference/idebugdisassemblystream2-seek.md) .

 Il `DSF_OPERANDS_SYMBOLS` flag può essere aggiunto al `DSF_OPERANDS` flag nel `dwFields` parametro per indicare che i nomi dei simboli devono essere utilizzati per le istruzioni di disassemblaggio.

## <a name="see-also"></a>Vedi anche
- [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)
- [DISASSEMBLY_STREAM_FIELDS](../../../extensibility/debugger/reference/disassembly-stream-fields.md)
- [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)
- [GetSize](../../../extensibility/debugger/reference/idebugdisassemblystream2-getsize.md)
- [Seek](../../../extensibility/debugger/reference/idebugdisassemblystream2-seek.md)
