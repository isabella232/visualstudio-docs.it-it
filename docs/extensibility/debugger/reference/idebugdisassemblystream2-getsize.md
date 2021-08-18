---
description: Ottiene le dimensioni nelle istruzioni di questo flusso disassembly.
title: IDebugDisassemblyStream2::GetSize | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDisassemblyStream2::GetSize
helpviewer_keywords:
- IDebugDisassemblyStream2::GetSize
ms.assetid: 8f512704-12d0-46d2-959a-4f8dffe117b5
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b2702b092102cc0a918a1604c79b27885d1e002a
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122111268"
---
# <a name="idebugdisassemblystream2getsize"></a>IDebugDisassemblyStream2::GetSize
Ottiene le dimensioni nelle istruzioni di questo flusso disassembly.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT GetSize( 
   UINT64* pnSize
);
```

```csharp
int GetSize( 
   out ulong pnSize
);
```

## <a name="parameters"></a>Parametri
`pnSize`\
[out] Restituisce le dimensioni, nelle istruzioni .

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Commenti
 Il valore restituito da questo metodo può essere usato per allocare una matrice [di strutture DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md) che viene quindi passata al [metodo Read.](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md)

## <a name="see-also"></a>Vedi anche
- [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)
- [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)
- [Lettura](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md)
