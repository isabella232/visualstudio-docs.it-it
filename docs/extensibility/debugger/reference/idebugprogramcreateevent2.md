---
description: Questa interfaccia viene inviata dal motore di debug (DE) al gestore di debug sessione (SDM) quando un programma è collegato a .
title: IDebugProgramCreateEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramCreateEvent2
helpviewer_keywords:
- IDebugProgramCreateEvent2 interface
ms.assetid: b19a7934-6179-4a68-9075-bd7dcd640b05
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: b778bf5a3267bf95895825b5dd6cc09aa428e3a8
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122126466"
---
# <a name="idebugprogramcreateevent2"></a>IDebugProgramCreateEvent2
Questa interfaccia viene inviata dal motore di debug (DE) al gestore di debug sessione (SDM) quando un programma è collegato a .

## <a name="syntax"></a>Sintassi

```
IDebugProgramCreateEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 La de o il fornitore di porte personalizzato implementa questa interfaccia per segnalare che è stato creato un programma, in genere nel momento in cui il programma è collegato. [L'interfaccia IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) deve essere implementata nello stesso oggetto di questa interfaccia. SDM usa il `QueryInterface` metodo per accedere `IDebugEvent2` all'interfaccia .

## <a name="notes-for-callers"></a>Note per i chiamanti
 La de o il fornitore di porte personalizzato crea e invia questo oggetto evento per segnalare la creazione di un programma. Il de invia questo evento usando la funzione di callback [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) fornita da SDM quando è collegata al programma di cui è in corso il debug. Il fornitore di porte personalizzato invia questo evento usando [l'interfaccia IDebugPortEvents2.](../../../extensibility/debugger/reference/idebugportevents2.md)

## <a name="remarks"></a>Commenti
 Il provider di porte personalizzato o DE pubblica una nuova [interfaccia IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) chiamando [PublishProgramNode](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogramnode.md).

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
