---
description: Questa interfaccia rappresenta una raccolta di oggetti che implementano l'interfaccia IDebugField.
title: IEnumDebugFields | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugFields
helpviewer_keywords:
- IEnumDebugFields interface
ms.assetid: 403c2a51-3ba5-431f-a1dd-2f3b2046c00c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 20fe0885186fefd2514be40e04cb27f3d92220c579f02f5679b48cabefde5c59
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121415403"
---
# <a name="ienumdebugfields"></a>IEnumDebugFields
Questa interfaccia rappresenta una raccolta di oggetti che implementano [l'interfaccia IDebugField.](../../../extensibility/debugger/reference/idebugfield.md)

## <a name="syntax"></a>Sintassi

```
IEnumDebugFields : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Questa interfaccia viene implementata dal provider di simboli per fornire set di oggetti che implementano [l'interfaccia IDebugField.](../../../extensibility/debugger/reference/idebugfield.md) Si noti che non si tratta di un'enumerazione COM standard a causa della presenza del [metodo GetCount.](../../../extensibility/debugger/reference/ienumdebugfields-getcount.md)

## <a name="notes-for-callers"></a>Note per i chiamanti
 Questa interfaccia viene restituita [da GetMethodFieldsByName](../../../extensibility/debugger/reference/idebugsymbolprovider-getmethodfieldsbyname.md) e [GetNamespacesUsedAtAddress.](../../../extensibility/debugger/reference/idebugsymbolprovider-getnamespacesusedataddress.md)

## <a name="methods-in-vtable-order"></a>Metodi in ordine Vtable
 Questa interfaccia implementa i metodi seguenti.

|Metodo|Descrizione|
|------------|-----------------|
|[Avanti](../../../extensibility/debugger/reference/ienumdebugfields-next.md)|Recupera il set successivo di oggetti [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) dall'enumerazione .|
|[Skip](../../../extensibility/debugger/reference/ienumdebugfields-skip.md)|Ignora un numero specificato di voci.|
|[Reimpostazione](../../../extensibility/debugger/reference/ienumdebugfields-reset.md)|Reimposta l'enumerazione sulla prima voce.|
|[Clone](../../../extensibility/debugger/reference/ienumdebugfields-clone.md)|Recupera una copia dell'enumerazione corrente.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugfields-getcount.md)|Recupera il numero di voci nell'enumerazione .|

## <a name="remarks"></a>Osservazioni

## <a name="requirements"></a>Requisiti
 Intestazione: sh.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Interfacce del provider di simboli](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [GetMethodFieldsByName](../../../extensibility/debugger/reference/idebugsymbolprovider-getmethodfieldsbyname.md)
- [GetNamespacesUsedAtAddress](../../../extensibility/debugger/reference/idebugsymbolprovider-getnamespacesusedataddress.md)
