---
description: Questa interfaccia viene inviata dal motore di debug (DE) a Gestione debug sessione (SDM) quando il programma in fase di debug completa un'istruzione, un'istruzione o un'istruzione all'uscita da una riga di codice sorgente, un'istruzione o un'istruzione.
title: IDebugStepCompleteEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugStepCompleteEvent2
helpviewer_keywords:
- IDebugStepCompleteEvent2 interface
ms.assetid: eba2b76e-f90d-486b-ae5c-c47f1b8ba2e5
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 9902ea1ea882c9d5ba0bf3f9770cce0cbc741f9a
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122095907"
---
# <a name="idebugstepcompleteevent2"></a>IDebugStepCompleteEvent2
Questa interfaccia viene inviata dal motore di debug (DE) a Gestione debug sessione (SDM) quando il programma in fase di debug completa un'istruzione, un'istruzione o un'istruzione all'uscita da una riga di codice sorgente, un'istruzione o un'istruzione.

## <a name="syntax"></a>Sintassi

```
IDebugStepCompleteEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 De implementa questa interfaccia per segnalare il completamento di un'operazione di passaggio. [L'interfaccia IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) deve essere implementata nello stesso oggetto di questa interfaccia. SDM usa [QueryInterface per](/cpp/atl/queryinterface) accedere all'interfaccia. `IDebugEvent2`

## <a name="notes-for-callers"></a>Note per i chiamanti
 De crea e invia questo oggetto evento per segnalare il completamento di un'operazione di passaggio. L'evento viene inviato usando la funzione di callback [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) fornita da SDM quando è collegato al programma di cui è in corso il debug.

## <a name="remarks"></a>Commenti
 Una volta completato il passaggio, il programma in fase di debug viene sospeso ancora una volta e l'IDE aggiorna tutte le relative finestre.

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
