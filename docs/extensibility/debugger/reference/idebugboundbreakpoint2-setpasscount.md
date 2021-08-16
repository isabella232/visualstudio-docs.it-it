---
description: Imposta o modifica il numero di passaggi associato a questo punto di interruzione associato.
title: IDebugBoundBreakpoint2::SetPassCount | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBoundBreakpoint2::SetPassCount
helpviewer_keywords:
- SetPassCount method
- IDebugBoundBreakpoint2::SetPassCount method
ms.assetid: b32c12f9-b34d-43bd-a1b9-61af6cf8e51b
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 91332f8781b81b6b087dbeae4fabd3f121018020de6c1b6e68090f65a73d56cb
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121378002"
---
# <a name="idebugboundbreakpoint2setpasscount"></a>IDebugBoundBreakpoint2::SetPassCount
Imposta o modifica il numero di passaggi associato a questo punto di interruzione associato.

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
[in] Struttura [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md) che specifica il numero di passi.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore. Restituisce `E_BP_DELETED` se lo stato dell'oggetto punto di interruzione associato è impostato su (parte dell'BP_STATE `BPS_DELETED` enumerazione). [](../../../extensibility/debugger/reference/bp-state.md)

## <a name="remarks"></a>Commenti
 Il numero di passaggi determina quando viene attivato il punto di interruzione. Il passaggio o il numero di hit corrente può essere ottenuto chiamando il [metodo GetHitCount.](../../../extensibility/debugger/reference/idebugboundbreakpoint2-gethitcount.md)

 Qualsiasi numero di passaggi precedentemente associato a questo punto di interruzione viene perso.

## <a name="see-also"></a>Vedi anche
- [IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md)
- [GetHitCount](../../../extensibility/debugger/reference/idebugboundbreakpoint2-gethitcount.md)
- [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md)
- [BP_STATE](../../../extensibility/debugger/reference/bp-state.md)
