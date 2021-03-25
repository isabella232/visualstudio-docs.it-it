---
description: Questa interfaccia viene inviata dal motore di debug (DE) a gestione debug sessione (SDM) per restituire una stringa.
title: IDebugOutputStringEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugOutputStringEvent2
helpviewer_keywords:
- IDebugOutputStringEvent2 interface
ms.assetid: 86596fd1-cecc-4813-8add-dc3d70068f9b
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 4576914ada9a575569ce09c120dbbd9bc11fdfa9
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105084649"
---
# <a name="idebugoutputstringevent2"></a>IDebugOutputStringEvent2
Questa interfaccia viene inviata dal motore di debug (DE) a gestione debug sessione (SDM) per restituire una stringa.

## <a name="syntax"></a>Sintassi

```
IDebugOutputStringEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Il DE implementa questa interfaccia per inviare una stringa alla finestra di **output** dell'IDE. L'interfaccia [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) deve essere implementata nello stesso oggetto di questa interfaccia. SDM utilizza [QueryInterface](/cpp/atl/queryinterface) per accedere all' `IDebugEvent2` interfaccia.

## <a name="notes-for-callers"></a>Note per i chiamanti
 Il DE crea e invia questo oggetto evento per inviare una stringa alla finestra di **output** . L'evento viene inviato utilizzando la funzione di callback [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) fornita da SDM quando è collegata al programma di cui è in corso il debug.

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
 Nella tabella seguente viene illustrato il metodo di `IDebugOutputStringEvent2` .

|Metodo|Descrizione|
|------------|-----------------|
|[GetString](../../../extensibility/debugger/reference/idebugoutputstringevent2-getstring.md)|Ottiene il messaggio visualizzabile.|

## <a name="remarks"></a>Commenti
 Nel codice non gestito, ad esempio, la stringa da restituire può provenire quando il programma di cui è in corso il debug invia una stringa alla `OutputDebugString` funzione Win32. Questa stringa viene intercettata da DE e inviata al SDM come `IDebugOutputStringEvent2` evento.

 Usare [IDebugMessageEvent2](../../../extensibility/debugger/reference/idebugmessageevent2.md) per inviare un messaggio che richiede una risposta dell'utente.

 Usare [IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md) per inviare un messaggio di errore che non richiede una risposta.

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg. h

 Spazio dei nomi: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [IDebugMessageEvent2](../../../extensibility/debugger/reference/idebugmessageevent2.md)
- [IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
