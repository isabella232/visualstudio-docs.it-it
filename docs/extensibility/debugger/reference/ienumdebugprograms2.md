---
description: Questa interfaccia enumera i programmi in esecuzione nella sessione di debug corrente.
title: IEnumDebugPrograms2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugPrograms2
helpviewer_keywords:
- IEnumDebugPrograms2
ms.assetid: 7fbb8fb7-db64-4546-a364-dc668430c8af
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 3ff57a503094e018e65bdf9913c48cb3abc9f9c1
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126709600"
---
# <a name="ienumdebugprograms2"></a>IEnumDebugPrograms2
Questa interfaccia enumera i programmi in esecuzione nella sessione di debug corrente.

## <a name="syntax"></a>Sintassi

```
IEnumDebugPrograms2 : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Il motore di debug implementa questa interfaccia per fornire un elenco di programmi in fase di debug da parte del de.

## <a name="notes-for-callers"></a>Note per i chiamanti
 Visual Studio chiama [EnumPrograms](../../../extensibility/debugger/reference/idebugprocess2-enumprograms.md) per ottenere questa interfaccia. [EnumPrograms](../../../extensibility/debugger/reference/idebugengine2-enumprograms.md) non viene usato da Visual Studio.

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
 Nella tabella seguente vengono illustrati i metodi di `IEnumDebugPrograms2` .

|Metodo|Descrizione|
|------------|-----------------|
|[Avanti](../../../extensibility/debugger/reference/ienumdebugprograms2-next.md)|Recupera un numero specificato di programmi in una sequenza di enumerazione.|
|[Skip](../../../extensibility/debugger/reference/ienumdebugprograms2-skip.md)|Ignora un numero specificato di programmi in una sequenza di enumerazione.|
|[Reimpostazione](../../../extensibility/debugger/reference/ienumdebugprograms2-reset.md)|Riporta all'inizio la sequenza di enumerazione.|
|[Clone](../../../extensibility/debugger/reference/ienumdebugprograms2-clone.md)|Crea un enumeratore che contiene lo stesso stato di enumerazione dell'enumeratore corrente.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugprograms2-getcount.md)|Ottiene il numero di programmi in un enumeratore.|

## <a name="remarks"></a>Commenti
 Visual Studio usa questa interfaccia per:

- Popolare la finestra **Moduli** chiamando [EnumPrograms](../../../extensibility/debugger/reference/idebugprocess2-enumprograms.md) e quindi [EnumModules](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md) in ogni programma.

- Popolare **l'elenco Associa** a processo chiamando e quindi chiamando QueryInterface su ogni `IDebugProcess2::EnumPrograms` interfaccia [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) per ottenere [un'interfaccia IDebugEngineProgram2.](../../../extensibility/debugger/reference/idebugengineprogram2.md) [](/cpp/atl/queryinterface)

- Generare un elenco di DE in grado di eseguire il debug di ogni programma nel processo (usando [GetEngineInfo](../../../extensibility/debugger/reference/idebugprogram2-getengineinfo.md)).

- Applicare gli aggiornamenti di Modifica e continuazione (ENC) a ogni programma chiamando IDebugProcess2::EnumPrograms e quindi [chiamando GetENCUpdate](../../../extensibility/debugger/reference/idebugprogram2-getencupdate.md).

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)
- [EnumPrograms](../../../extensibility/debugger/reference/idebugengine2-enumprograms.md)
- [EnumPrograms](../../../extensibility/debugger/reference/idebugprocess2-enumprograms.md)
