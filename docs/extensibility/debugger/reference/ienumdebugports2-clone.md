---
title: IEnumDebugPorts2::Clone | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugPorts2::Clone
helpviewer_keywords:
- IEnumDebugPorts2::Clone
ms.assetid: d5ce77e8-bb99-409a-98fa-20fe5a0de25e
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 572d338fb010db9d0ff4aaaeefa5c692b2262e29
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/22/2019
ms.locfileid: "56681699"
---
# <a name="ienumdebugports2clone"></a>IEnumDebugPorts2::Clone
Restituisce una copia dell'enumerazione corrente come oggetto separato.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT Clone(
   IEnumDebugPorts2** ppEnum
);
```

```csharp
int Clone(
   out IEnumDebugPorts2 ppEnum
);
```

#### <a name="parameters"></a>Parametri
 `ppEnum`

 [out] Restituisce una copia di questa enumerazione come oggetto separato.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.

## <a name="remarks"></a>Note
 La copia dell'enumerazione ha lo stesso stato originale al momento che questo metodo viene chiamato. Tuttavia, gli Stati dell'originale e la copia sono separati e possono essere modificati singolarmente.

## <a name="see-also"></a>Vedere anche
- [IEnumDebugPorts2](../../../extensibility/debugger/reference/ienumdebugports2.md)