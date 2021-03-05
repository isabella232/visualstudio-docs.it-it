---
description: Questa interfaccia è un'interfaccia di estensione implementata dagli implementatori IDebugProcess2.
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
ms.openlocfilehash: 8205b96723a1b48da46e6e19162c50139c9fe71d
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/05/2021
ms.locfileid: "102166216"
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
