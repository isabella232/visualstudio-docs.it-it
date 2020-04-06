---
title: Proprietà IDebugFunctionPosition2 . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugFunctionPosition2
helpviewer_keywords:
- IDebugFunctionPosition2 interface
ms.assetid: a835f65b-91b0-48ad-8485-04534c814b1b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c260b6316207b0079a2ca8893b851db8b1288ba6
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80728318"
---
# <a name="idebugfunctionposition2"></a>IDebugFunctionPosition2
Questa interfaccia rappresenta una posizione astratta di una funzione in un documento di origine.

## <a name="syntax"></a>Sintassi

```
IDebugFunctionPosition2 : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Il motore di debug (DE) implementa questa interfaccia per rappresentare la posizione di una funzione all'interno di un documento di origine.

## <a name="notes-for-callers"></a>Note per i chiamanti
 Questa interfaccia viene fornita come parte di un'unione [di BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md) (in particolare, una struttura [di BP_LOCATION_CODE_FUNC_OFFSET)](../../../extensibility/debugger/reference/bp-location-code-func-offset.md) che a sua volta fa parte della struttura [BP_REQUEST_INFO,](../../../extensibility/debugger/reference/bp-request-info.md) utilizzata nella creazione di un punto di interruzione in sospeso.

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
 Nella tabella seguente vengono `IDebugFunctionPosition2`illustrati i metodi di .

|Metodo|Descrizione|
|------------|-----------------|
|[GetFunctionName](../../../extensibility/debugger/reference/idebugfunctionposition2-getfunctionname.md)|Ottiene il nome della funzione relativa a questa posizione.|
|[GetOffset](../../../extensibility/debugger/reference/idebugfunctionposition2-getoffset.md)|Ottiene l'offset dall'inizio della funzione.|

## <a name="remarks"></a>Osservazioni
 La posizione rappresentata da questa interfaccia è basata su testo, in particolare una struttura [TEXT_POSITION.](../../../extensibility/debugger/reference/text-position.md)

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche
- [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)
- [BP_LOCATION_CODE_FUNC_OFFSET](../../../extensibility/debugger/reference/bp-location-code-func-offset.md)
- [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md)
- [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)
