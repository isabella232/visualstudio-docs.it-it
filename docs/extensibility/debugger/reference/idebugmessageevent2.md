---
title: Proprietà IDebugMessageEvent2 . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMessageEvent2
helpviewer_keywords:
- IDebugMessageEvent2 interface
ms.assetid: a9ff3d00-e9ac-4cd6-bda9-584a4815aff8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 180162988cbb09f98b7fc2e8f33f6b5d0ed322ae
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80727368"
---
# <a name="idebugmessageevent2"></a>IDebugMessageEvent2
Questa interfaccia viene utilizzata dal motore di debug (DE) per inviare un messaggio a Visual Studio che richiede una risposta dall'utente.

## <a name="syntax"></a>Sintassi

```
IDebugMessageEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Il DE implementa questa interfaccia per inviare un messaggio a Visual Studio che richiede una risposta dell'utente. Il [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) interfaccia deve essere implementata sullo stesso oggetto di questa interfaccia. Il modello SDM utilizza `IDebugEvent2` [QueryInterface](/cpp/atl/queryinterface) per accedere all'interfaccia.

 L'implementazione di questa interfaccia deve comunicare la chiamata di Visual Studio di [SetResponse](../../../extensibility/debugger/reference/idebugmessageevent2-setresponse.md) al DE. Ad esempio, questa operazione può essere eseguita con un messaggio inviato al thread di gestione dei messaggi del DE oppure l'oggetto che implementa questa interfaccia può contenere un riferimento al DE e richiamare il DE con la risposta passata in `IDebugMessageEvent2::SetResponse`.

## <a name="notes-for-callers"></a>Note per i chiamanti
 Il DE crea e invia questo oggetto evento per visualizzare un messaggio all'utente che richiede una risposta. L'evento viene inviato utilizzando la funzione di callback [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) fornita dal modello SDM quando è collegato al programma in fase di debug.

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
 Nella tabella seguente vengono `IDebugMessageEvent2`illustrati i metodi di .

|Metodo|Descrizione|
|------------|-----------------|
|[GetMessage](../../../extensibility/debugger/reference/idebugmessageevent2-getmessage.md)|Ottiene il messaggio da visualizzare.|
|[SetResponse](../../../extensibility/debugger/reference/idebugmessageevent2-setresponse.md)|Imposta la risposta, se presente, dalla finestra di messaggio.|

## <a name="remarks"></a>Osservazioni
 Il DE utilizzerà questa interfaccia se richiede una risposta specifica da parte dell'utente per un determinato messaggio. Ad esempio, se il DE ottiene un messaggio "Accesso negato" dopo un tentativo di associazione remota `IDebugMessageEvent2` a un programma, il DE invia questo particolare messaggio a Visual Studio in un evento con lo stile `MB_RETRYCANCEL`della finestra di messaggio . Ciò consente all'utente di riprovare o annullare l'operazione di collegamento.

 Il DE specifica come questo messaggio deve essere gestito seguendo le convenzioni della funzione `MessageBox` Win32 (vedere [AfxMessageBox](/cpp/mfc/reference/cstring-formatting-and-message-box-display#afxmessagebox) per informazioni dettagliate).

 Utilizzare il [IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md) interfaccia per inviare messaggi a Visual Studio che non richiedono una risposta da parte dell'utente.

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche
- [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md)
