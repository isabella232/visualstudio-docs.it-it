---
description: Sposta il puntatore in lettura nel flusso disassembly in un determinato numero di istruzioni rispetto a una posizione specificata.
title: IDebugDisassemblyStream2::Seek | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDisassemblyStream2::Seek
helpviewer_keywords:
- IDebugDisassemblyStream2::Seek
ms.assetid: afec3008-b1e0-4803-ad24-195dbfb6497e
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2dc5c80d58ceb3efbf7007178252dadcb66a0692
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122127298"
---
# <a name="idebugdisassemblystream2seek"></a>IDebugDisassemblyStream2::Seek
Sposta il puntatore in lettura nel flusso disassembly in un determinato numero di istruzioni rispetto a una posizione specificata.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT Seek( 
   SEEK_START          dwSeekStart,
   IDebugCodeContext2* pCodeContext,
   UINT64              uCodeLocationId,
   INT64               iInstructions
);
```

```csharp
int Seek( 
   enum_SEEK_START    dwSeekStart,
   IDebugCodeContext2 pCodeContext,
   ulong              uCodeLocationId,
   long               iInstructions
);
```

## <a name="parameters"></a>Parametri
`dwSeekStart`\
[in] Valore [dell'enumerazione SEEK_START](../../../extensibility/debugger/reference/seek-start.md) che specifica la posizione relativa in cui iniziare il processo di ricerca.

`pCodeContext`\
[in] Oggetto [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) che rappresenta il contesto del codice a cui è relativa l'operazione di ricerca. Questo parametro viene utilizzato solo se `dwSeekStart`  =  `SEEK_START_CODECONTEXT` ; in caso contrario, questo parametro viene ignorato e può essere un valore Null.

`uCodeLocationId`\
[in] Identificatore della posizione del codice a cui è relativa l'operazione di ricerca. Questo parametro viene usato se `dwSeekStart`  =  `SEEK_START_CODELOCID` ; in caso contrario, questo parametro viene ignorato e può essere impostato su 0. Per una descrizione di un identificatore di posizione del codice, vedere la sezione Osservazioni per il metodo [GetCodeLocationId.](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodelocationid.md)

`iInstructions`\
[in] Numero di istruzioni da spostare rispetto alla posizione specificata in `dwSeekStart` . Questo valore può essere negativo per spostarsi all'indietro.

## <a name="return-value"></a>Valore restituito
 Se l'esito è positivo, restituisce `S_OK`. Restituisce `S_FALSE` se la posizione di ricerca era a un punto oltre l'elenco di istruzioni disponibili. In caso contrario, verrà restituito un codice di errore.

## <a name="remarks"></a>Commenti
 Se la ricerca si trova in una posizione precedente all'inizio dell'elenco, la posizione di lettura viene impostata sulla prima istruzione nell'elenco. Se see si trova in una posizione dopo la fine dell'elenco, la posizione di lettura viene impostata sull'ultima istruzione nell'elenco.

## <a name="see-also"></a>Vedi anche
- [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)
- [SEEK_START](../../../extensibility/debugger/reference/seek-start.md)
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
- [GetCodeLocationId](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodelocationid.md)
