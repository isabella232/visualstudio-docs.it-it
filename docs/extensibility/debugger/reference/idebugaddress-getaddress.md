---
description: Restituisce una struttura che descrive un oggetto e la relativa posizione all'interno del relativo ambito o contenitore.
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
ms.openlocfilehash: 0fe2245c39001f36fc763900c1c00a535663ceae
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122064916"
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
[in, out] Struttura [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) specificata da questo metodo.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce S_OK; In caso contrario, restituisce un codice di errore.

## <a name="remarks"></a>Commenti
 La [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) viene passata a questo metodo, che quindi la inserisce con le informazioni appropriate. Il modo in cui queste informazioni vengono interpretate dipende dal tipo di informazioni restituite e dal gestore dei simboli stesso. Per [altri DEBUG_ADDRESS,](../../../extensibility/debugger/reference/debug-address.md) vedere l'DEBUG_ADDRESS.

## <a name="see-also"></a>Vedi anche
- [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)
