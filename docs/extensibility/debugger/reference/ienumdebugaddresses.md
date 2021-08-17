---
description: Questa interfaccia rappresenta una raccolta di oggetti che implementano l'interfaccia IDebugAddress.
title: IEnumDebugAddresses | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugAddresses
helpviewer_keywords:
- IEnumDebugAddresses interface
ms.assetid: 5f6f6751-e6d8-4c5a-8e81-414b6e5d8cc5
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 1cc2c55399b81d026c1f5c7529bc68ea45c807938bbc27ef784842a8e230bd83
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121338358"
---
# <a name="ienumdebugaddresses"></a>IEnumDebugAddresses
Questa interfaccia rappresenta una raccolta di oggetti che implementano [l'interfaccia IDebugAddress.](../../../extensibility/debugger/reference/idebugaddress.md)

## <a name="syntax"></a>Sintassi

```
IEnumDebugAdresses : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Questa interfaccia viene implementata dal provider di simboli per fornire set di oggetti che implementano [l'interfaccia IDebugAddress.](../../../extensibility/debugger/reference/idebugaddress.md) Si noti che non si tratta di un'enumerazione COM standard a causa della presenza del [metodo GetCount.](../../../extensibility/debugger/reference/ienumdebugaddresses-getcount.md)

## <a name="notes-for-callers"></a>Note per i chiamanti
 Questa interfaccia viene restituita [da GetAddressesFromContext](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromcontext.md) e [GetAddressesFromPosition.](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromposition.md)

## <a name="methods-in-vtable-order"></a>Metodi in ordine Vtable
 Questa interfaccia implementa i metodi seguenti.

|Metodo|Descrizione|
|------------|-----------------|
|[Avanti](../../../extensibility/debugger/reference/ienumdebugaddresses-next.md)|Recupera il set successivo di oggetti [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) dall'enumerazione .|
|[Skip](../../../extensibility/debugger/reference/ienumdebugaddresses-skip.md)|Ignora un numero specificato di voci.|
|[Reimpostazione](../../../extensibility/debugger/reference/ienumdebugaddresses-reset.md)|Reimposta l'enumerazione sulla prima voce.|
|[Clone](../../../extensibility/debugger/reference/ienumdebugaddresses-clone.md)|Recupera una copia dell'enumerazione corrente.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugaddresses-getcount.md)|Recupera il numero di voci nell'enumerazione .|

## <a name="remarks"></a>Commenti
 Questa interfaccia viene in genere utilizzata dal motore di debug per determinare l'indirizzo appropriato da assegnare all'analizzatore di espressioni.

## <a name="requirements"></a>Requisiti
 Intestazione: sh.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Interfacce del provider di simboli](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)
- [GetAddressesFromContext](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromcontext.md)
- [GetAddressesFromPosition](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromposition.md)
