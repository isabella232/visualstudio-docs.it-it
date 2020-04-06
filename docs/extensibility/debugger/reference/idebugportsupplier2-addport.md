---
title: Metodo IDebugPortSupplier2::AddPort . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortSupplier2::AddPort
helpviewer_keywords:
- IDebugPortSupplier2::AddPort
ms.assetid: df491161-6bf3-4fcc-b478-b9ec88ec995f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 00954ceaa0ddd750a3d08e372d1edaa1905f01c1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80724732"
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
[in] Oggetto [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md) che descrive la porta da aggiungere.

`ppPort`\
[fuori] Restituisce un [oggetto IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) che rappresenta la porta.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Osservazioni
 Questo metodo crea effettivamente la porta richiesta e la aggiunge all'elenco interno delle porte attive del fornitore della porta. Il [CanAddPort](../../../extensibility/debugger/reference/idebugportsupplier2-canaddport.md) metodo può essere chiamato prima per evitare possibili ritardi che richiedono molto tempo.

## <a name="see-also"></a>Vedere anche
- [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)
- [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md)
- [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)
- [CanAddPort](../../../extensibility/debugger/reference/idebugportsupplier2-canaddport.md)
