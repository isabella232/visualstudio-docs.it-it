---
title: 'IDebugPendingBreakpoint2:: SetPassCount | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPendingBreakpoint2::SetPassCount
helpviewer_keywords:
- SetPassCount method
- IDebugPendingBreakpoint2::SetPassCount method
ms.assetid: 08ddd328-57eb-42e0-baa9-8424dcd1bf04
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 37aebea3e5dfa9e4693de8ed5b4b6b4b08557a2a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99893880"
---
# <a name="idebugpendingbreakpoint2setpasscount"></a>IDebugPendingBreakpoint2::SetPassCount
Imposta o modifica il numero di passaggi associato al punto di interruzione in sospeso.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT SetPassCount( 
   BP_PASSCOUNT bpPassCount
);
```

```csharp
int SetPassCount( 
   BP_PASSCOUNT bpPassCount
);
```

## <a name="parameters"></a>Parametri
`bpPassCount`\
in Struttura [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md) contenente il numero di passaggi.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore. Restituisce `E_BP_DELETED` se il punto di interruzione è stato eliminato.

## <a name="remarks"></a>Commenti
 Qualsiasi numero di passaggi precedentemente associato al punto di interruzione in sospeso viene perso. Tutti i punti di interruzione associati dal punto di interruzione in sospeso vengono chiamati per impostare il numero di passaggi sul `bpPassCount` parametro.

## <a name="see-also"></a>Vedi anche
- [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)
- [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md)
