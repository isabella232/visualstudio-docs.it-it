---
description: Imposta o modifica il numero di passaggi associato al punto di interruzione in sospeso.
title: IDebugPendingBreakpoint2::SetPassCount | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPendingBreakpoint2::SetPassCount
helpviewer_keywords:
- SetPassCount method
- IDebugPendingBreakpoint2::SetPassCount method
ms.assetid: 08ddd328-57eb-42e0-baa9-8424dcd1bf04
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 6e9a91f9d78e69af8c23b8bf1c43cddd8ac0fe8fded6af9f18049974b449d0bb
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121339099"
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
[in] Struttura [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md) che contiene il numero di pass.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore. Restituisce `E_BP_DELETED` se il punto di interruzione è stato eliminato.

## <a name="remarks"></a>Commenti
 Qualsiasi numero di passaggi precedentemente associato al punto di interruzione in sospeso viene perso. Tutti i punti di interruzione associati da questo punto di interruzione in sospeso vengono chiamati per impostare il numero di passaggi sul `bpPassCount` parametro .

## <a name="see-also"></a>Vedi anche
- [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)
- [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md)
