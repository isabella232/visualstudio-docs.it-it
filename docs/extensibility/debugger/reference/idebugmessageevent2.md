---
description: Questa interfaccia viene usata dal motore di debug (DE) per inviare un messaggio Visual Studio che richiede una risposta dall'utente.
title: IDebugMessageEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMessageEvent2
helpviewer_keywords:
- IDebugMessageEvent2 interface
ms.assetid: a9ff3d00-e9ac-4cd6-bda9-584a4815aff8
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 4940d8d19c76b9e64da4dbbb3b659519bace24e3
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122126986"
---
# <a name="idebugmessageevent2"></a>IDebugMessageEvent2
Questa interfaccia viene usata dal motore di debug (DE) per inviare un messaggio Visual Studio che richiede una risposta dall'utente.

## <a name="syntax"></a>Sintassi

```
IDebugMessageEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Il de implementa questa interfaccia per inviare un messaggio a Visual Studio che richiede una risposta dell'utente. [L'interfaccia IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) deve essere implementata nello stesso oggetto di questa interfaccia. SDM usa [QueryInterface per](/cpp/atl/queryinterface) accedere all'interfaccia. `IDebugEvent2`

 L'implementazione di questa interfaccia deve Visual Studio la chiamata di [SetResponse](../../../extensibility/debugger/reference/idebugmessageevent2-setresponse.md) al de. Ad esempio, questa operazione può essere eseguita con un messaggio inviato al thread di gestione dei messaggi del de oppure l'oggetto che implementa questa interfaccia può contenere un riferimento al de e chiamare nuovamente il de con la risposta passata in `IDebugMessageEvent2::SetResponse` .

## <a name="notes-for-callers"></a>Note per i chiamanti
 Il de crea e invia questo oggetto evento per visualizzare un messaggio all'utente che richiede una risposta. L'evento viene inviato usando la funzione di callback [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) fornita da SDM quando è collegato al programma di cui viene eseguito il debug.

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
 Nella tabella seguente vengono illustrati i metodi di `IDebugMessageEvent2` .

|Metodo|Descrizione|
|------------|-----------------|
|[GetMessage](../../../extensibility/debugger/reference/idebugmessageevent2-getmessage.md)|Ottiene il messaggio da visualizzare.|
|[SetResponse](../../../extensibility/debugger/reference/idebugmessageevent2-setresponse.md)|Imposta la risposta, se presente, dalla finestra di messaggio.|

## <a name="remarks"></a>Commenti
 Il de userà questa interfaccia se richiede una risposta specifica dell'utente per un messaggio specifico. Ad esempio, se il de ottiene un messaggio "Accesso negato" dopo un tentativo di connessione remota a un programma, il de invia questo particolare messaggio a Visual Studio in un evento con lo stile della finestra di messaggio `IDebugMessageEvent2` `MB_RETRYCANCEL` . In questo modo l'utente può riprovare o annullare l'operazione di collegamento.

 De specifica come deve essere gestito questo messaggio seguendo le convenzioni della funzione Win32 (per informazioni dettagliate, vedere `MessageBox` [AfxMessageBox).](/cpp/mfc/reference/cstring-formatting-and-message-box-display#afxmessagebox)

 Usare [l'interfaccia IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md) per inviare messaggi Visual Studio che non richiedono una risposta dall'utente.

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md)
