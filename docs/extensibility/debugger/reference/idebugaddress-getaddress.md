---
title: IDebugAddress::GetAddress . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugAddress::GetAddress
helpviewer_keywords:
- IDebugAddress:GetAddress method
ms.assetid: 2590387b-5d36-4116-9a75-737957b8898e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 162a64c9118bdcde23208082350005e607a237b8
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80736600"
---
# <a name="idebugaddressgetaddress"></a>IDebugAddress::GetAddress
Restituisce una struttura che descrive un oggetto e la relativa posizione all'interno del relativo ambito o contenitore.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT GetAddress (
   DEBUG_ADDRESS * pAddress
);
```

```csharp
int GetAddress(
   DEBUG_ADDRESS[] pAddress
);
```

## <a name="parameters"></a>Parametri
`pAddress`\
[in, out] Struttura [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) compilata da questo metodo.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce S_OK; in caso contrario, restituisce un codice di errore.

## <a name="remarks"></a>Osservazioni
 La [struttura DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) viene passata a questo metodo, che quindi lo inserisce con le informazioni appropriate. Il modo in cui queste informazioni vengono interpretate dipende dal tipo di informazioni restituite e dal gestore di simboli stesso. Per ulteriori [dettagli, vedere DEBUG_ADDRESS.](../../../extensibility/debugger/reference/debug-address.md)

## <a name="see-also"></a>Vedere anche
- [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)
