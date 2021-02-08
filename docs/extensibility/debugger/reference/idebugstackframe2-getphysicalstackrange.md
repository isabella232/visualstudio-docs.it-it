---
title: 'IDebugStackFrame2:: GetPhysicalStackRange | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugStackFrame2::GetPhysicalStackRange
helpviewer_keywords:
- IDebugStackFrame2::GetPhysicalStackRange
ms.assetid: 2f6992e2-ac1c-433f-83b7-a7f83a4ce63d
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 8c4c4bbc468403aaf94aca1b5133a732e0c050b2
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99837476"
---
# <a name="idebugstackframe2getphysicalstackrange"></a>IDebugStackFrame2::GetPhysicalStackRange
Ottiene una rappresentazione dipendente dal computer dell'intervallo di indirizzi fisici associato a un stack frame.

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
out Restituisce l'indirizzo fisico più basso associato a questo stack frame.

`paddrMax`\
out Restituisce l'indirizzo fisico più elevato associato a questo stack frame.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Commenti
 Le informazioni restituite da questo metodo vengono utilizzate da gestione debug sessione (SDM) per ordinare gli stack frame.

 Si presuppone che lo stack di chiamate diventi inattivo, ovvero che i nuovi stack frame vengano aggiunti a indirizzi di memoria sempre più bassi. Un'architettura di runtime deve fornire intervalli di stack fisici corrispondenti A questo presupposto.

## <a name="see-also"></a>Vedi anche
- [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)
