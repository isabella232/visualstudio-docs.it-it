---
title: IDebugApplicationThread110 Interface | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 170b345bdb4587d1fd29c1f0f906df0157abd877
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/16/2019
ms.locfileid: "54348919"
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