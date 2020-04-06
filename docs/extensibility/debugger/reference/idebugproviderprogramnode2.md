---
title: Proprietà IDebugProviderProgramNode2 . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProviderProgramNode2
helpviewer_keywords:
- IDebugProviderProgramNode2
ms.assetid: f0bca1cc-afbe-44cf-b5aa-d078aa685d24
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 815a945f6fb591960ebf0bf4b4fcd9d842ffefd3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80720675"
---
# <a name="idebugproviderprogramnode2"></a>IDebugProviderProgramNode2
Questa interfaccia esegue il marshalling delle interfacce correlate al programma attraverso i limiti del processo.

## <a name="syntax"></a>Sintassi

```
IDebugProviderProgramNode2 : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Il motore di debug (DE) implementa questa interfaccia sullo stesso oggetto che implementa [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) per supportare le interfacce di marshalling attraverso i limiti del processo.

## <a name="notes-for-callers"></a>Note per i chiamanti
 Chiamare [QueryInterface](/cpp/atl/queryinterface) `IDebugProgramNode2` su un'interfaccia per ottenere questa interfaccia. Se non è possibile ottenere questa interfaccia, il DE non supporta il marshalling delle interfacce.

## <a name="methods-in-vtable-order"></a>Metodi in ordine Vtable
 Questa interfaccia implementa il metodo seguente:This interface implements the following method:

|Metodo|Descrizione|
|------------|-----------------|
|[UnmarshalDebuggeeInterface](../../../extensibility/debugger/reference/idebugproviderprogramnode2-unmarshaldebuggeeinterface.md)|Ottiene un'interfaccia specificata attraverso i limiti del processo.|

## <a name="remarks"></a>Osservazioni
 Questa interfaccia viene implementata quando il DE viene eseguito in uno spazio di processo separato dal programma in fase di debug: ad esempio, quando il DE è in esecuzione nello spazio di processo di Visual Studio anziché lo spazio di processo del programma in fase di debug.

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche
- [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
