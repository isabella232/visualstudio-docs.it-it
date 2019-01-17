---
title: Interfaccia IActiveScriptSiteDebugEx | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptSiteDebugEx Interface
ms.assetid: 76869378-1a7b-47bd-8cd0-acc31f91d58d
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c1e462630f7bf52c4ca94aa59df22616e9a335a7
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/16/2019
ms.locfileid: "54345877"
---
# <a name="iactivescriptsitedebugex-interface"></a>Interfaccia IActiveScriptSiteDebugEx
Implementare questa interfaccia con il `IActiveScriptSiteDebug` interfaccia se si sta scrivendo un host che deve ricevere una notifica di errore di run-time in un'applicazione e, facoltativamente, connettersi all'applicazione per il debug. Il gestore di eseguire il Debug di processi fornisce la notifica tramite `IActiveScriptDebug` se un Just-In-Time script debugger non viene trovato nel computer. Se nessun Just-In-Time script debugger viene trovato, PDM fornisce la notifica tramite `IActiveScriptDebugEx` invece.  
  
 Per ricevere una notifica di errore di run-time, è necessario gestire l'host [ActiveScriptSiteDebug::OnScriptErrorDebug](http://msdn.microsoft.com/en-us/cf7639f9-a699-4571-9f3a-82ef52c0b5f4). Basato su un'azione dell'utente, è possibile quindi decidere se collegare il debugger interno e restituire, o per restituire l'avvio del debugger nel OnScriptErrorDebug `pfEnterDebugger` parametro.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IActiveScriptSiteDebugEx::OnCanNotJITScriptErrorDebug](../../winscript/reference/iactivescriptsitedebugex-oncannotjitscripterrordebug.md)|Informa l'host su un errore in fase di esecuzione di script durante il processo di Debug di gestione non trova un debugger JIT esterno.|