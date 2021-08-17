---
description: Questa interfaccia viene inviata quando un processo viene terminato, esce atipicamente o viene scollegato.
title: IDebugProcessDestroyEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcessDestroyEvent2
helpviewer_keywords:
- IDebugProcessDestroyEvent2
ms.assetid: 1b8e0528-95bc-48fa-9653-2cea66c8dc3a
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: cb57adb1ad3e553a1045d63626841ec23f36a8fe05a1e62042ae9aefc0e51666
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121338930"
---
# <a name="idebugprocessdestroyevent2"></a>IDebugProcessDestroyEvent2
Questa interfaccia viene inviata quando un processo viene terminato, esce atipicamente o viene scollegato.

## <a name="syntax"></a>Sintassi

```
IDebugProcessDestroyEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Il motore di debug (DE) o il fornitore di porte personalizzato implementano questa interfaccia per segnalare che un processo è stato terminato. [L'interfaccia IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) deve essere implementata nello stesso oggetto di questa interfaccia. SDM usa [QueryInterface per](/cpp/atl/queryinterface) accedere all'interfaccia. `IDebugEvent2`

## <a name="notes-for-callers"></a>Note per i chiamanti
 Il de o il fornitore di porte personalizzato crea e invia questo oggetto evento per segnalare la terminazione di un processo. Il de invia questo evento usando la funzione di callback [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) fornita da SDM quando è collegato al programma in fase di debug. Il fornitore della porta personalizzata invia questo evento usando [l'interfaccia IDebugPortEvents2.](../../../extensibility/debugger/reference/idebugportevents2.md)

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md)
