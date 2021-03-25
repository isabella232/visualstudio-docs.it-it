---
description: Questa interfaccia fornisce informazioni sull'host (processo) relative a un programma.
title: IDebugProgramHost2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramHost2
helpviewer_keywords:
- IDebugProgramHost2 interface
ms.assetid: 2c37b3aa-97a9-4665-8709-edd917f18cb1
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 6b58eb61a65ff8ed0a6455d81128539ad5e6d00a
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105058248"
---
# <a name="idebugprogramhost2"></a>IDebugProgramHost2
Questa interfaccia fornisce informazioni sull'host (processo) relative a un programma.

## <a name="syntax"></a>Sintassi

```
IDebugProgramHost2 : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Il motore di debug implementa questa interfaccia sullo stesso oggetto dell'interfaccia [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) per fornire informazioni sul processo di hosting. Si tratta di un'interfaccia facoltativa.

## <a name="notes-for-callers"></a>Note per i chiamanti
 Chiamare [QueryInterface](/cpp/atl/queryinterface) su un' `IDebugProgram2` interfaccia per ottenere questa interfaccia.

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
 La tabella seguente illustra i metodi di `IDebugProgramHost2` .

|Metodo|Descrizione|
|------------|-----------------|
|[GetHostName](../../../extensibility/debugger/reference/idebugprogramhost2-gethostname.md)|Ottiene il titolo, il nome descrittivo o il nome file del processo di hosting del programma.|
|[GetHostId](../../../extensibility/debugger/reference/idebugprogramhost2-gethostid.md)|Ottiene l'identificatore del processo di hosting del programma.|
|[GetHostMachineName](../../../extensibility/debugger/reference/idebugprogramhost2-gethostmachinename.md)|Ottiene il nome del computer in cui è in esecuzione il processo di hosting del programma.|

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg. h

 Spazio dei nomi: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
