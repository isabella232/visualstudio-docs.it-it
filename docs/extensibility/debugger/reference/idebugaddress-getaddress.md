---
description: Restituisce una struttura che descrive un oggetto e la relativa posizione all'interno del relativo ambito o contenitore.
title: 'IDebugAddress:: GetAddress | Microsoft Docs'
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
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 92e616ded029c22b16b81ccd5f25086b11be6ff4
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105094398"
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

## <a name="remarks"></a>Commenti
 La struttura [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) viene passata a questo metodo, che quindi la compila con le informazioni appropriate. Il modo in cui queste informazioni vengono interpretate dipende dal tipo di informazioni restituite e dal gestore di simboli stesso. Per ulteriori informazioni, vedere [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) .

## <a name="see-also"></a>Vedi anche
- [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)
