---
description: Questa interfaccia viene inviata dal motore di debug (DE) al gestore di debug sessione (SDM) per l'output di una stringa.
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
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 6480b1018726d37d4bd51af5d3c4d66b8b42a9a56f04aceb530518876bd078a4
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121307141"
---
# <a name="idebugoutputstringevent2"></a>IDebugOutputStringEvent2
Questa interfaccia viene inviata dal motore di debug (DE) al gestore di debug sessione (SDM) per l'output di una stringa.

## <a name="syntax"></a>Sintassi

```
IDebugOutputStringEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Il de implementa questa interfaccia per inviare una stringa alla finestra **Output** dell'IDE. [L'interfaccia IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) deve essere implementata nello stesso oggetto di questa interfaccia. SDM usa [QueryInterface per](/cpp/atl/queryinterface) accedere all'interfaccia. `IDebugEvent2`

## <a name="notes-for-callers"></a>Note per i chiamanti
 Il de crea e invia questo oggetto evento per inviare una stringa alla **finestra Output.** L'evento viene inviato usando la funzione di callback [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) fornita da SDM quando è collegato al programma in fase di debug.

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
 Nella tabella seguente viene illustrato il metodo di `IDebugOutputStringEvent2` .

|Metodo|Descrizione|
|------------|-----------------|
|[Getstring](../../../extensibility/debugger/reference/idebugoutputstringevent2-getstring.md)|Ottiene il messaggio visualizzabile.|

## <a name="remarks"></a>Commenti
 Nel codice non gestito, ad esempio, la stringa da output può avere origine quando il programma in fase di debug invia una stringa alla funzione `OutputDebugString` Win32. Questa stringa viene intercettata dal de e inviata all'SDM come `IDebugOutputStringEvent2` evento.

 Usare [IDebugMessageEvent2](../../../extensibility/debugger/reference/idebugmessageevent2.md) per inviare un messaggio che richiede una risposta dell'utente.

 Usare [IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md) per inviare un messaggio di errore che non richiede una risposta.

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [IDebugMessageEvent2](../../../extensibility/debugger/reference/idebugmessageevent2.md)
- [IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
