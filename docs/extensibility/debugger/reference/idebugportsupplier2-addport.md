---
description: Aggiunge una porta.
title: 'IDebugPortSupplier2:: AddPort | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortSupplier2::AddPort
helpviewer_keywords:
- IDebugPortSupplier2::AddPort
ms.assetid: df491161-6bf3-4fcc-b478-b9ec88ec995f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4c2b9c4c7c5378670c87926e76d185d54448a244
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105072195"
---
# <a name="idebugportsupplier2addport"></a>IDebugPortSupplier2::AddPort
Aggiunge una porta.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT AddPort( 
   IDebugPortRequest2* pRequest,
   IDebugPort2**       ppPort
);
```

```csharp
int AddPort( 
   IDebugPortRequest2 pRequest,
   out IDebugPort2    ppPort
);
```

## <a name="parameters"></a>Parametri
`pRequest`\
in Oggetto [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md) che descrive la porta da aggiungere.

`ppPort`\
out Restituisce un oggetto [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) che rappresenta la porta.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Commenti
 Questo metodo crea effettivamente la porta richiesta e la aggiunge all'elenco interno di porte attive del fornitore della porta. Il metodo [CanAddPort](../../../extensibility/debugger/reference/idebugportsupplier2-canaddport.md) può essere chiamato per primo per evitare possibili ritardi che richiedono molto tempo.

## <a name="see-also"></a>Vedi anche
- [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)
- [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md)
- [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)
- [CanAddPort](../../../extensibility/debugger/reference/idebugportsupplier2-canaddport.md)
