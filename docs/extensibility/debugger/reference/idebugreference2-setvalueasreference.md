---
title: IDebugReference2::SetValueAsReference | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugReference2::SetValueAsReference
helpviewer_keywords:
- IDebugReference2::SetValueAsReference
ms.assetid: 94a545d2-16b9-45e9-b2e7-4e49ff90aad0
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c4af17f49e95818ed664e74aab53687540f653ba
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/22/2019
ms.locfileid: "56721160"
---
# <a name="idebugreference2setvalueasreference"></a>IDebugReference2::SetValueAsReference
Imposta il valore di un riferimento da un altro riferimento. Riservato per usi futuri.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT SetValueAsReference ( 
   IDebugReference2** rgpArgs,
   DWORD              dwArgCount,
   IDebugReference2*  pValue,
   DWORD              dwTimeout
);
```

```cpp
int SetValueAsReference ( 
   IDebugReference2[] rgpArgs,
   uint               dwArgCount,
   IDebugReference2   pValue,
   uint               dwTimeout
);
```

#### <a name="parameters"></a>Parametri
 `rgpArgs`

 [in] Matrice di [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) oggetti utilizzati per determinare come impostare il valore di riferimento.

 `dwArgCount`

 [in] Il numero di riferimenti nella matrice.

 `pValue`

 [in] Un' [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) oggetto da cui impostare il valore della proprietà.

 `dwTimeout`

 [in] Tempo massimo, espresso in millisecondi, di attesa prima della restituzione da questo metodo. Usare `INFINITE` per un'attesa indefinita.

## <a name="return-value"></a>Valore restituito
 Restituisce sempre `E_NOTIMPL`.

## <a name="see-also"></a>Vedere anche
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)