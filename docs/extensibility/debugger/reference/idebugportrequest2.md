---
title: Proprietà IDebugPortRequest2 . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortRequest2
helpviewer_keywords:
- IDebugPortRequest2 interface
ms.assetid: 556e610d-7c4b-44a8-965a-76a9d02b601a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 163718fda344ba5f3f44ef630b4eba3e5613dc61
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80724793"
---
# <a name="idebugportrequest2"></a>IDebugPortRequest2
Questa interfaccia descrive una porta. Questa descrizione viene utilizzata per aggiungere la porta a un fornitore di porta.

## <a name="syntax"></a>Sintassi

```
IDebugPortRequest2 : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Visual Studio implementa in genere questa interfaccia nel processo di recupero di una porta di debug da un fornitore di porta.

## <a name="notes-for-callers"></a>Note per i chiamanti
 Questa interfaccia viene passata in [AddPort](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md) per creare una porta di debug. Una chiamata a [GetPortRequest](../../../extensibility/debugger/reference/idebugport2-getportrequest.md) restituisce questa interfaccia, che rappresenta la richiesta utilizzata per creare la porta in primo luogo.

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
 Nella tabella seguente vengono `IDebugPortRequest2`illustrati i metodi di .

|Metodo|Descrizione|
|------------|-----------------|
|[GetPortName](../../../extensibility/debugger/reference/idebugportrequest2-getportname.md)|Ottiene il nome della porta da creare.|

## <a name="remarks"></a>Osservazioni
 Un motore di debug in genere non interagisce con un fornitore di porta e non avrà alcun utilizzo per questa interfaccia.

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche
- [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)
- [AddPort](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md)
- [GetPortRequest](../../../extensibility/debugger/reference/idebugport2-getportrequest.md)
