---
title: Proprietà IEnumDebugAddresses . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugAddresses
helpviewer_keywords:
- IEnumDebugAddresses interface
ms.assetid: 5f6f6751-e6d8-4c5a-8e81-414b6e5d8cc5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 14b42ec37babe72b47b0e832397d33029c4fc3d1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80717592"
---
# <a name="ienumdebugaddresses"></a>IEnumDebugAddresses
Questa interfaccia rappresenta una raccolta di oggetti che implementano il [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) interfaccia.

## <a name="syntax"></a>Sintassi

```
IEnumDebugAdresses : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Questa interfaccia viene implementata dal provider di simboli per fornire set di oggetti che implementano il [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) interfaccia. Si noti che non si tratta di un'enumerazione COM standard a causa della presenza del metodo [GetCount.](../../../extensibility/debugger/reference/ienumdebugaddresses-getcount.md)

## <a name="notes-for-callers"></a>Note per i chiamanti
 Questa interfaccia viene restituita da [GetAddressesFromContext](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromcontext.md) e [GetAddressesFromPosition](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromposition.md).

## <a name="methods-in-vtable-order"></a>Metodi in ordine Vtable
 Questa interfaccia implementa i metodi seguenti.

|Metodo|Descrizione|
|------------|-----------------|
|[Avanti](../../../extensibility/debugger/reference/ienumdebugaddresses-next.md)|Recupera il set successivo di [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) oggetti dall'enumerazione.|
|[Saltare](../../../extensibility/debugger/reference/ienumdebugaddresses-skip.md)|Salta un numero specificato di voci.|
|[Reimposta](../../../extensibility/debugger/reference/ienumdebugaddresses-reset.md)|Reimposta l'enumerazione sulla prima voce.|
|[Clone](../../../extensibility/debugger/reference/ienumdebugaddresses-clone.md) (Clona)|Recupera una copia dell'enumerazione corrente.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugaddresses-getcount.md)|Recupera il numero di voci nell'enumerazione.|

## <a name="remarks"></a>Osservazioni
 Questa interfaccia viene in genere utilizzata dal motore di debug per determinare l'indirizzo appropriato da assegnare all'analizzatore di espressioni.

## <a name="requirements"></a>Requisiti
 Intestazione: sh.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche
- [Interfacce del provider di simboli](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)
- [GetAddressesFromContext](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromcontext.md)
- [GetAddressesFromPosition](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromposition.md)
