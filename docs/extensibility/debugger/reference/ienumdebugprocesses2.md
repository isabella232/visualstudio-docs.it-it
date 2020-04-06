---
title: Proprietà IEnumDebugProcesses2 . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugProcesses2
helpviewer_keywords:
- IEnumDebugProcesses2
ms.assetid: 06a1368f-10f0-44eb-af61-e388c2327111
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8b9fe0e96ade081e8da11b5e1c06c5b45279b10b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80715753"
---
# <a name="ienumdebugprocesses2"></a>IEnumDebugProcesses2
Questa interfaccia enumera i processi in esecuzione su una porta di debug.

## <a name="syntax"></a>Sintassi

```
IEnumDebugProcesses : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Un fornitore di porta personalizzato implementa questa interfaccia per fornire un elenco di processi in esecuzione su una porta.

## <a name="notes-for-callers"></a>Note per i chiamanti
 Visual Studio chiama [EnumProcesses](../../../extensibility/debugger/reference/idebugport2-enumprocesses.md) per ottenere questa interfaccia.

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
 Nella tabella seguente vengono `IEnumDebugProcesses2`illustrati i metodi di .

|Metodo|Descrizione|
|------------|-----------------|
|[Avanti](../../../extensibility/debugger/reference/ienumdebugprocesses2-next.md)|Recupera un numero specificato di processi in una sequenza di enumerazione.|
|[Saltare](../../../extensibility/debugger/reference/ienumdebugprocesses2-skip.md)|Ignora un numero specificato di processi in una sequenza di enumerazione.|
|[Reimposta](../../../extensibility/debugger/reference/ienumdebugprocesses2-reset.md)|Riporta all'inizio la sequenza di enumerazione.|
|[Clone](../../../extensibility/debugger/reference/ienumdebugprocesses2-clone.md) (Clona)|Crea un enumeratore che contiene lo stesso stato di enumerazione dell'enumeratore corrente.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugprocesses2-getcount.md)|Ottiene il numero di processi in un enumeratore.|

## <a name="remarks"></a>Osservazioni
 Visual Studio usa questa interfaccia per popolare la finestra Processi.Visual Studio uses this interface to populate the **Processes** window.

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche
- [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)
- [EnumProcesses](../../../extensibility/debugger/reference/idebugport2-enumprocesses.md)
