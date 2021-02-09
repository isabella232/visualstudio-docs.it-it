---
title: 'IDebugDisassemblyStream2:: GetSize | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDisassemblyStream2::GetSize
helpviewer_keywords:
- IDebugDisassemblyStream2::GetSize
ms.assetid: 8f512704-12d0-46d2-959a-4f8dffe117b5
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e6d97c41023f0bc8ca80c36a5bfaf33735f48d07
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99901704"
---
# <a name="idebugdisassemblystream2getsize"></a>IDebugDisassemblyStream2::GetSize
Ottiene le dimensioni nelle istruzioni del flusso di Disassembly.

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
out Restituisce le dimensioni, nelle istruzioni.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Commenti
 Il valore restituito da questo metodo può essere utilizzato per allocare una matrice di strutture [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md) che viene quindi passata al metodo [Read](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md) .

## <a name="see-also"></a>Vedi anche
- [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)
- [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)
- [Lettura](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md)
