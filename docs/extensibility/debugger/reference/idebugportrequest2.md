---
title: IDebugPortRequest2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortRequest2
helpviewer_keywords:
- IDebugPortRequest2 interface
ms.assetid: 556e610d-7c4b-44a8-965a-76a9d02b601a
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 83f70a9fe027f004ef3829827ba8af40f7fb72e3
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66340317"
---
# <a name="idebugportrequest2"></a>IDebugPortRequest2
Questa interfaccia viene descritta una porta. Questa descrizione viene usata per aggiungere la porta a un fornitore di porte.

## <a name="syntax"></a>Sintassi

```
IDebugPortRequest2 : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Visual Studio implementa in genere questa interfaccia nel processo di recupero di una porta di debug da un fornitore di porte.

## <a name="notes-for-callers"></a>Note per i chiamanti
 Questa interfaccia viene passata [Aggiungi porta](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md) per creare una porta di debug. Una chiamata a [GetPortRequest](../../../extensibility/debugger/reference/idebugport2-getportrequest.md) restituisce questa interfaccia, che rappresenta la richiesta utilizzata per creare la porta in primo luogo.

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
 Nella tabella seguente sono illustrati i metodi di `IDebugPortRequest2`.

|Metodo|Descrizione|
|------------|-----------------|
|[GetPortName](../../../extensibility/debugger/reference/idebugportrequest2-getportname.md)|Ottiene il nome della porta da creare.|

## <a name="remarks"></a>Note
 In genere, un motore di debug non interagisce con un fornitore di porte e non disporrà di alcun uso per questa interfaccia.

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche
- [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)
- [AddPort](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md)
- [GetPortRequest](../../../extensibility/debugger/reference/idebugport2-getportrequest.md)