---
title: Proprietà IDebugProgramHost2 . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramHost2
helpviewer_keywords:
- IDebugProgramHost2 interface
ms.assetid: 2c37b3aa-97a9-4665-8709-edd917f18cb1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 64db456e0c438f8665f122c3cd1b079c2ad1cea1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80722218"
---
# <a name="idebugprogramhost2"></a>IDebugProgramHost2
Questa interfaccia fornisce informazioni sull'host (processo) su un programma.

## <a name="syntax"></a>Sintassi

```
IDebugProgramHost2 : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Il motore di debug implementa questa interfaccia sullo stesso oggetto di [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) interfaccia per fornire informazioni sul processo di hosting. Si tratta di un'interfaccia facoltativa.

## <a name="notes-for-callers"></a>Note per i chiamanti
 Chiamare [QueryInterface](/cpp/atl/queryinterface) `IDebugProgram2` su un'interfaccia per ottenere questa interfaccia.

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
 Nella tabella seguente vengono `IDebugProgramHost2`illustrati i metodi di .

|Metodo|Descrizione|
|------------|-----------------|
|[GetHostName](../../../extensibility/debugger/reference/idebugprogramhost2-gethostname.md)|Ottiene il titolo, il nome descrittivo o il nome file del processo di hosting di questo programma.|
|[GetHostId](../../../extensibility/debugger/reference/idebugprogramhost2-gethostid.md)|Ottiene l'identificatore di processo del processo di hosting di questo programma.|
|[GetHostMachineName](../../../extensibility/debugger/reference/idebugprogramhost2-gethostmachinename.md)|Ottiene il nome del computer su cui è in esecuzione il processo di hosting di questo programma.|

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche
- [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
