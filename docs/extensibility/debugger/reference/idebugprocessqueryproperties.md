---
title: IDebugProcessQueryProperties | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugProcessQueryProperties
ms.assetid: ce29a248-81a0-42c0-99a7-1606e8c548ec
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ae588724f19f9722244ce69f77b64fad07552f9c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99938174"
---
# <a name="idebugprocessqueryproperties"></a>IDebugProcessQueryProperties
Questa interfaccia è un'interfaccia di estensione implementata dagli implementatori [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) . Consente all'implementatore di ottenere informazioni sull'ambiente del processo di debug.

## <a name="syntax"></a>Sintassi

```
IDebugProcessQueryProperties: IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Implementare questa interfaccia per ottenere informazioni sull'ambiente di esecuzione di un processo di debug.

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
 La tabella seguente illustra i metodi di `IDebugProcessQueryProperties` .

|Metodo|Descrizione|
|------------|-----------------|
|[QueryProperty](../../../extensibility/debugger/reference/idebugprocessqueryproperties-queryproperty.md)|Esegue una query per un valore della proprietà.|
|[QueryProperties](../../../extensibility/debugger/reference/idebugprocessqueryproperties-queryproperties.md)|Esegue una query per i valori delle proprietà.|

## <a name="remarks"></a>Commenti
 Questa interfaccia viene raramente implementata.

## <a name="requirements"></a>Requisiti
 Intestazione: Portpriv. h

 Spazio dei nomi: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
