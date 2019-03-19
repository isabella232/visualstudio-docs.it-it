---
title: IDebugApplicationThread110 Interface | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugApplicationThread110 Interface
ms.assetid: 25bc351f-3451-4387-9302-078f6292ddff
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a40b1a6f194ef0f335d8c6516b101250b0d980fe
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2019
ms.locfileid: "58158409"
---
# <a name="idebugapplicationthread110-interface"></a>Interfaccia IDebugApplicationThread110
Fornisce più funzionalità per la [interfaccia IDebugApplicationThread](../../winscript/reference/idebugapplicationthread-interface.md) interfaccia.  
  
> [!IMPORTANT]
>  Questa interfaccia è implementata da PDM v11.0 e versione successiva. Rilevata in activdbg100.h.  
  
## <a name="methods"></a>Metodi  
 L'interfaccia `IDebugApplicationThread110` espone i metodi riportati di seguito.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IDebugApplicationThread110::AsynchronousCallIntoThread](../../winscript/reference/idebugapplicationthread110-asynchronouscallintothread.md)|Effettua una chiamata asincrona sul thread principale.|  
|[IDebugApplicationThread110::GetActiveThreadRequestCount](../../winscript/reference/idebugapplicationthread110-getactivethreadrequestcount.md)|Conteggio del numero di richieste di thread da thread del PDM cambio meccanismi in fase di elaborazione. In genere 0 o 1, ma 's possibili per questa opzione per essere superiore se una chiamata di thread inizia l'elaborazione, ma attiva una chiamata sincrona all'esterno di thread o in caso contrario, sospende il thread (ad esempio, generando un evento IDebugApplicationEvents che viene eseguito nel debugger thread)|  
|[IDebugApplicationThread110::IsSuspendedForBreakPoint](../../winscript/reference/idebugapplicationthread110-issuspendedforbreakpoint.md)|[IDebugApplicationThreadEvents110::OnSuspendForBreakPoint](../../winscript/reference/idebugapplicationthreadevents110-onsuspendforbreakpoint.md) è stato chiamato su questo thread e non è stata ancora completata.|  
|[IDebugApplicationThread110::IsThreadCallable](../../winscript/reference/idebugapplicationthread110-isthreadcallable.md)|Questo thread è in uno stato in grado di elaborare le chiamate effettuate tramite il thread di PDM cambio meccanismi (ad esempio SynchronousCallInThread).|