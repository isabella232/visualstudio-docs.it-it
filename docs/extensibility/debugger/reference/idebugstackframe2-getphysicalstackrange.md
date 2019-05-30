---
title: IDebugStackFrame2::GetPhysicalStackRange | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugStackFrame2::GetPhysicalStackRange
helpviewer_keywords:
- IDebugStackFrame2::GetPhysicalStackRange
ms.assetid: 2f6992e2-ac1c-433f-83b7-a7f83a4ce63d
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2cf0db9fa776116f1536ae137444160385a8b6a1
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66347706"
---
# <a name="idebugstackframe2getphysicalstackrange"></a>IDebugStackFrame2::GetPhysicalStackRange
Ottiene una rappresentazione dipende dal computer dell'intervallo di indirizzi fisici associati a uno stack frame.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT GetPhysicalStackRange ( 
   UINT64* paddrMin,
   UINT64* paddrMax
);
```

```csharp
int GetPhysicalStackRange ( 
   out ulong paddrMin,
   out ulong paddrMax
);
```

## <a name="parameters"></a>Parametri
`paddrMin`\
[out] Restituisce l'indirizzo fisico più basso associato con questo stack frame.

`paddrMax`\
[out] Restituisce l'indirizzo fisico più alta associato con questo stack frame.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.

## <a name="remarks"></a>Note
 Le informazioni restituite da questo metodo vengano utilizzate dal gestore di sessione di debug (SDM) per ordinare gli stack frame.

 Si presuppone che lo stack di chiamate si espande verso il basso, vale a dire, che vengono aggiunti nuovo stack frame in bassi sempre più indirizzi di memoria. Un'architettura di runtime è necessario specificare gli intervalli di stack fisico che corrispondono a questo presupposto.

## <a name="see-also"></a>Vedere anche
- [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)