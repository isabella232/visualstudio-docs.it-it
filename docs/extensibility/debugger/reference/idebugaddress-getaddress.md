---
description: Restituisce una struttura che descrive un oggetto e la relativa posizione all'interno dell'ambito o del contenitore.
title: IDebugAddress::GetAddress | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugAddress::GetAddress
helpviewer_keywords:
- IDebugAddress:GetAddress method
ms.assetid: 2590387b-5d36-4116-9a75-737957b8898e
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f7cfdadd5a2acb31525e0329f485ac289a8ecc4c888a1ff73ca7accaea736574
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121239230"
---
# <a name="idebugaddressgetaddress"></a>IDebugAddress::GetAddress
Restituisce una struttura che descrive un oggetto e la relativa posizione all'interno dell'ambito o del contenitore.

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
 Se ha esito positivo, restituisce S_OK; In caso contrario, restituisce un codice di errore.

## <a name="remarks"></a>Commenti
 La [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) viene passata a questo metodo, che quindi la compila con le informazioni appropriate. La modalità di interpretazione di queste informazioni dipende dal tipo di informazioni restituite e dal gestore di simboli stesso. Vedere [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) per altri dettagli.

## <a name="see-also"></a>Vedi anche
- [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)
