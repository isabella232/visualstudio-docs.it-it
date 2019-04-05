---
title: IDebugMessageEvent2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugMessageEvent2
helpviewer_keywords:
- IDebugMessageEvent2 interface
ms.assetid: a9ff3d00-e9ac-4cd6-bda9-584a4815aff8
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 3c2b76d0972768bf4d77e7f6d9bd153920799970
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58955284"
---
# <a name="idebugmessageevent2"></a>IDebugMessageEvent2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Questa interfaccia viene utilizzata dal motore di debug (DE) per inviare un messaggio a Visual Studio che richiede una risposta da parte dell'utente.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IDebugMessageEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Note per gli implementatori  
 La Germania implementa questa interfaccia per inviare un messaggio a Visual Studio che richiede una risposta dell'utente. Il [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) interfaccia deve essere implementata per lo stesso oggetto di questa interfaccia. Usa il modello SDM [QueryInterface](http://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) per l'accesso di `IDebugEvent2` interfaccia.  
  
 L'implementazione di questa interfaccia deve comunicare chiamata Visual Studio [SetResponse](../../../extensibility/debugger/reference/idebugmessageevent2-setresponse.md) per la Germania. Ad esempio, questa operazione può essere eseguita con un messaggio inviato al thread di gestione dei messaggi della Germania, oppure l'oggetto che implementa questa interfaccia potrebbe contenere un riferimento per la Germania e richiamare il DE con la risposta passata nel `IDebugMessageEvent2::SetResponse`.  
  
## <a name="notes-for-callers"></a>Note per i chiamanti  
 La Germania crea e invia l'oggetto evento per visualizzare un messaggio all'utente che richiede una risposta. L'evento viene inviato tramite il [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) funzione di callback che viene fornito per il modello SDM quando è associato al programma in fase di debug.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
 Nella tabella seguente sono illustrati i metodi di `IDebugMessageEvent2`.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[GetMessage](../../../extensibility/debugger/reference/idebugmessageevent2-getmessage.md)|Ottiene il messaggio da visualizzare.|  
|[SetResponse](../../../extensibility/debugger/reference/idebugmessageevent2-setresponse.md)|Imposta la risposta, se presente, nella finestra di messaggio.|  
  
## <a name="remarks"></a>Note  
 La Germania utilizzerà questa interfaccia se richiede una risposta specifica da parte dell'utente per un determinato messaggio. Ad esempio, se la Germania riceve un messaggio "Accesso negato" dopo un tentativo di connettersi in remoto a un programma, la Germania invia questo messaggio specifico per Visual Studio in un' `IDebugMessageEvent2` evento con lo stile di finestra di messaggio `MB_RETRYCANCEL`. Ciò consente all'utente di ripetere oppure annullare l'operazione di collegamento.  
  
 Specifica la Germania come questo messaggio deve essere gestito, seguire le convenzioni della funzione Win32 `MessageBox` (vedere [AfxMessageBox](http://msdn.microsoft.com/library/d66d0328-cdcc-48f6-96a4-badf089099c8) per informazioni dettagliate).  
  
 Usare la [IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md) interfaccia per inviare messaggi a Visual Studio che non richiedono una risposta da parte dell'utente.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg.h  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md)
