---
description: Ottiene una rappresentazione dipendente dal computer dell'intervallo di indirizzi fisici associati a un stack frame.
title: IDebugStackFrame2::GetPhysicalStackRange | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugStackFrame2::GetPhysicalStackRange
helpviewer_keywords:
- IDebugStackFrame2::GetPhysicalStackRange
ms.assetid: 2f6992e2-ac1c-433f-83b7-a7f83a4ce63d
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 75bba9bd57f544b82dd459ca7e001de8657cbd79a05c3bdc01a6a5d1d72705bd
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121321597"
---
# <a name="idebugstackframe2getphysicalstackrange"></a>IDebugStackFrame2::GetPhysicalStackRange
Ottiene una rappresentazione dipendente dal computer dell'intervallo di indirizzi fisici associati a un stack frame.

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
[out] Restituisce l'indirizzo fisico più basso associato a questo stack frame.

`paddrMax`\
[out] Restituisce l'indirizzo fisico più alto associato a questo stack frame.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Commenti
 Le informazioni restituite da questo metodo vengono usate da Gestione debug sessione (SDM) per ordinare gli stack frame.

 Si presuppone che lo stack di chiamate si inasspori, cio' che i nuovi stack frame vengono aggiunti a indirizzi di memoria sempre più bassi. Un'architettura di run-time deve fornire intervalli di stack fisici che corrispondono a questo presupposto.

## <a name="see-also"></a>Vedi anche
- [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)
