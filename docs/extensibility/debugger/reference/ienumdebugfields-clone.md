---
title: 'IEnumDebugFields:: Clone | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugFields::Clone
helpviewer_keywords:
- IEnumDebugFields::Clone method
ms.assetid: 7ec265a8-696f-45ce-a2a2-0a83e96fee1b
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b2a9cc66e0e3b56d27c71147bd1b77ee3e559b6b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99896950"
---
# <a name="ienumdebugfieldsclone"></a>IEnumDebugFields::Clone
Questo metodo restituisce una copia dell'enumerazione corrente come oggetto separato.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT Clone(
   IEnumDebugFields** ppEnum
);
```

```csharp
int Clone(
   out IEnumDebugFields ppEnum
);
```

## <a name="parameters"></a>Parametri
`ppEnum`\
[out] Restituisce una copia di questa enumerazione come oggetto separato.

## <a name="property-valuereturn-value"></a>Valore proprietà/Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Commenti
 La copia dell'enumerazione ha lo stesso stato dell'originale al momento della chiamata di questo metodo. Tuttavia, gli Stati della copia e dell'originale sono separati e possono essere modificati singolarmente.

## <a name="see-also"></a>Vedi anche
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
