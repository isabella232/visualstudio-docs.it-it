---
title: Proprietà IDebugProcessQueryProperties . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugProcessQueryProperties
ms.assetid: ce29a248-81a0-42c0-99a7-1606e8c548ec
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 08abf401b4e8f0e7a33d882e8178d77e6f248318
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80723287"
---
# <a name="idebugprocessqueryproperties"></a>IDebugProcessQueryProperties
Questa interfaccia è un'interfaccia di estensione implementata dagli implementatori [di IDebugProcess2.This](../../../extensibility/debugger/reference/idebugprocess2.md) interface is an extension interface implemented by IDebugProcess2 implementers. Consente all'implementatore di ottenere informazioni sull'ambiente del processo di debug.

## <a name="syntax"></a>Sintassi

```
IDebugProcessQueryProperties: IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Implementare questa interfaccia per ottenere informazioni sull'ambiente di esecuzione di un processo di debug.

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
 Nella tabella seguente vengono `IDebugProcessQueryProperties`illustrati i metodi di .

|Metodo|Descrizione|
|------------|-----------------|
|[QueryProperty](../../../extensibility/debugger/reference/idebugprocessqueryproperties-queryproperty.md)|Esegue una query per un valore della proprietà.|
|[QueryProperties](../../../extensibility/debugger/reference/idebugprocessqueryproperties-queryproperties.md)|Esegue una query per i valori delle proprietà.|

## <a name="remarks"></a>Osservazioni
 Questa interfaccia viene implementata raramente.

## <a name="requirements"></a>Requisiti
 Intestazione: Portpriv.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche
- [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
