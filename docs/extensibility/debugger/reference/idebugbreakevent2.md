---
description: Questa interfaccia indica a Gestione debug sessione (SDM) che un'interruzione asincrona è stata completata correttamente.
title: Interfaccia IDebugBreakEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBreakEvent2
helpviewer_keywords:
- IDebugBreakEvent2 interface
ms.assetid: 57dfdbc2-4e68-4dbf-9579-006cd6fb1c62
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: b07b7203f8ce3d557b0bbb2d4c1ca410e481aec67555da5f21f0563702e71656
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121293040"
---
# <a name="idebugbreakevent2"></a>IDebugBreakEvent2
Questa interfaccia indica a Gestione debug sessione (SDM) che un'interruzione asincrona è stata completata correttamente.

## <a name="syntax"></a>Sintassi

```
IDebugBreakEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 De implementa questa interfaccia per supportare interruzioni utente in un programma. [L'interfaccia IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) deve essere implementata nello stesso oggetto di questa interfaccia (SDM usa [QueryInterface](/cpp/atl/queryinterface) per accedere all'interfaccia). `IDebugEvent2`

## <a name="notes-for-callers"></a>Note per i chiamanti
 SDM chiama [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md) quando l'utente ha richiesto la sospensione del programma di cui è in corso il debug. Quando il programma è stato sospeso correttamente, de invia `IDebugBreakEvent2` l'evento. Questo evento viene inviato usando la funzione di callback [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) fornita da SDM quando è collegato al programma di cui è in corso il debug.

## <a name="remarks"></a>Commenti
 Ad esempio, un utente può selezionare il comando Interrompi **tutto** dal menu **Debug** per uscire da un programma che esegue un ciclo infinito. SDM indica al programma di arrestarsi chiamando [CauseBreak.](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md) De invia quando `IDebugBreakEvent2` il programma si arresta.

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
