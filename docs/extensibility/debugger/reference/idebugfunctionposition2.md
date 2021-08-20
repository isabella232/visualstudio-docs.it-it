---
description: Questa interfaccia rappresenta una posizione astratta di una funzione in un documento di origine.
title: Oggetto IDebugFunctionPosition2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugFunctionPosition2
helpviewer_keywords:
- IDebugFunctionPosition2 interface
ms.assetid: a835f65b-91b0-48ad-8485-04534c814b1b
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: ab8fd2348ce7c8e84e38d8b8029c23712620816b
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122064161"
---
# <a name="idebugfunctionposition2"></a>IDebugFunctionPosition2
Questa interfaccia rappresenta una posizione astratta di una funzione in un documento di origine.

## <a name="syntax"></a>Sintassi

```
IDebugFunctionPosition2 : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Il motore di debug implementa questa interfaccia per rappresentare la posizione di una funzione all'interno di un documento di origine.

## <a name="notes-for-callers"></a>Note per i chiamanti
 Questa interfaccia viene fornita come parte di un'unione [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md) (in particolare, una struttura [BP_LOCATION_CODE_FUNC_OFFSET)](../../../extensibility/debugger/reference/bp-location-code-func-offset.md) che a sua volta fa parte della [struttura BP_REQUEST_INFO,](../../../extensibility/debugger/reference/bp-request-info.md) usata nella creazione di un punto di interruzione in sospeso.

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
 Nella tabella seguente vengono illustrati i metodi di `IDebugFunctionPosition2` .

|Metodo|Descrizione|
|------------|-----------------|
|[GetFunctionName](../../../extensibility/debugger/reference/idebugfunctionposition2-getfunctionname.md)|Ottiene il nome della funzione a cui è relativa questa posizione.|
|[GetOffset](../../../extensibility/debugger/reference/idebugfunctionposition2-getoffset.md)|Ottiene l'offset dall'inizio della funzione.|

## <a name="remarks"></a>Commenti
 La posizione rappresentata da questa interfaccia è basata sul testo, in particolare una [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) struttura .

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)
- [BP_LOCATION_CODE_FUNC_OFFSET](../../../extensibility/debugger/reference/bp-location-code-func-offset.md)
- [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md)
- [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)
