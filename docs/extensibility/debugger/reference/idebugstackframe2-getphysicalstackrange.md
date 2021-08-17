---
description: Ottiene una rappresentazione dipendente dal computer dell'intervallo di indirizzi fisici associati a un stack frame.
title: Interfaccia IDebugStackFrame2::GetPhysicalStackRange | Microsoft Docs
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
ms.openlocfilehash: f06a12af02ccf0eff164119a5a9de9058e88ec11
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122029684"
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
[out] Restituisce l'indirizzo fisico più basso associato all'stack frame.

`paddrMax`\
[out] Restituisce l'indirizzo fisico più alto associato all'stack frame.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Commenti
 Le informazioni restituite da questo metodo vengono usate dalla gestione del debug di sessione (SDM) per ordinare gli stack frame.

 Si presuppone che lo stack di chiamate si inserisca, ad esempio che i nuovi stack frame vengono aggiunti a indirizzi di memoria sempre più bassi. Un'architettura di run-time deve fornire intervalli di stack fisici che corrispondano a questo presupposto.

## <a name="see-also"></a>Vedi anche
- [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)
