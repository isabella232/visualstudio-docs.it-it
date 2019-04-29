---
title: IEnumDebugFields | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugFields
helpviewer_keywords:
- IEnumDebugFields interface
ms.assetid: 403c2a51-3ba5-431f-a1dd-2f3b2046c00c
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9f557b722a36665b20f5e06093027f8085a014ed
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62914711"
---
# <a name="ienumdebugfields"></a>IEnumDebugFields
Questa interfaccia rappresenta una raccolta di oggetti che implementano il [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) interfaccia.

## <a name="syntax"></a>Sintassi

```
IEnumDebugFields : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Questa interfaccia viene implementata dal provider di simboli per specificare set di oggetti che implementano il [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) interfaccia. Si noti che questo non è un'enumerazione standard COM a causa della presenza del [GetCount](../../../extensibility/debugger/reference/ienumdebugfields-getcount.md) (metodo).

## <a name="notes-for-callers"></a>Note per i chiamanti
 Questa interfaccia viene restituita da [GetMethodFieldsByName](../../../extensibility/debugger/reference/idebugsymbolprovider-getmethodfieldsbyname.md) e [GetNamespacesUsedAtAddress](../../../extensibility/debugger/reference/idebugsymbolprovider-getnamespacesusedataddress.md).

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
 Questa interfaccia implementa i metodi seguenti.

|Metodo|Descrizione|
|------------|-----------------|
|[avanti](../../../extensibility/debugger/reference/ienumdebugfields-next.md)|Recupera il set successivo di [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) oggetti dall'enumerazione.|
|[Skip](../../../extensibility/debugger/reference/ienumdebugfields-skip.md)|Ignora un determinato numero di voci.|
|[Reset](../../../extensibility/debugger/reference/ienumdebugfields-reset.md)|Reimposta l'enumerazione per la prima voce.|
|[Clone](../../../extensibility/debugger/reference/ienumdebugfields-clone.md)|Recupera una copia dell'enumerazione corrente.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugfields-getcount.md)|Recupera il numero di voci nell'enumerazione.|

## <a name="remarks"></a>Note

## <a name="requirements"></a>Requisiti
 Intestazione: sh.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche
- [Interfacce del provider di simboli](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [GetMethodFieldsByName](../../../extensibility/debugger/reference/idebugsymbolprovider-getmethodfieldsbyname.md)
- [GetNamespacesUsedAtAddress](../../../extensibility/debugger/reference/idebugsymbolprovider-getnamespacesusedataddress.md)