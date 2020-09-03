---
title: IDebugProviderProgramNode2 | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "80720675"
---
# <a name="idebugproviderprogramnode2"></a>IDebugProviderProgramNode2
Questa interfaccia esegue il marshalling delle interfacce correlate al programma tra i limiti dei processi.

## <a name="syntax"></a>Sintassi

```
IDebugProviderProgramNode2 : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Il motore di debug (DE) implementa questa interfaccia sullo stesso oggetto che implementa [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) per supportare le interfacce di marshalling tra i limiti dei processi.

## <a name="notes-for-callers"></a>Note per i chiamanti
 Chiamare [QueryInterface](/cpp/atl/queryinterface) su un' `IDebugProgramNode2` interfaccia per ottenere questa interfaccia. Se non è possibile ottenere questa interfaccia, il DE non supporta il marshalling delle interfacce.

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine vtable
 Questa interfaccia implementa il metodo seguente:

|Metodo|Descrizione|
|------------|-----------------|
|[UnmarshalDebuggeeInterface](../../../extensibility/debugger/reference/idebugproviderprogramnode2-unmarshaldebuggeeinterface.md)|Ottiene un'interfaccia specificata tra i limiti del processo.|

## <a name="remarks"></a>Osservazioni
 Questa interfaccia viene implementata quando il DE viene eseguito in uno spazio di processo separato dal programma di cui è in corso il debug, ad esempio quando il DE è in esecuzione nello spazio di processo di Visual Studio invece che nello spazio di elaborazione del programma di cui è in corso il debug.

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg. h

 Spazio dei nomi: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche
- [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
