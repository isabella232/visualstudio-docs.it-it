---
title: Interfaccia IMachineDebugManagerCookie | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IMachineDebugManagerCookie interface
ms.assetid: 04770935-3ccf-41e9-b0c1-c78376ab1e3c
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6b39c286f389c99187b0f3250fc68af92ff5dcc8
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573890"
---
# <a name="imachinedebugmanagercookie-interface"></a>Interfaccia IMachineDebugManagerCookie
Analogamente all'interfaccia `IMachineDebugManager`, l'interfaccia `IMachineDebugManagerCookie` supporta i cookie di debug.  
  
 Questa interfaccia (insieme all'interfaccia `IDebugCookie`) consente l'esecuzione di script in un processo di debugger di script senza richiedere che il debugger tenga traccia di tali script.  
  
 Un debugger di script chiama il metodo `IDebugCookie::SetDebugCookie` in Process Debug Manager (PDM). Quindi, il PDM Invia questo cookie insieme a qualsiasi richiesta di aggiunta o rimozione di un'applicazione script da o verso la gestione del debug del computer (MDM), usando i metodi dell'interfaccia `IMachineDebugManagerCookie`. Il MDM informa quindi ogni debugger della modifica, ad eccezione di quello con tale cookie.  
  
 Oltre ai metodi ereditati da `IUnknown`, l'interfaccia `IMachineDebugManagerCookie` espone i metodi seguenti.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IMachineDebugManagerCookie::AddApplication](../../winscript/reference/imachinedebugmanagercookie-addapplication.md)|Aggiunge un'applicazione all'elenco di applicazioni in esecuzione.|  
|[IMachineDebugManagerCookie::EnumApplications](../../winscript/reference/imachinedebugmanagercookie-enumapplications.md)|Restituisce un enumeratore dell'elenco corrente di applicazioni in esecuzione.|  
|[IMachineDebugManagerCookie::RemoveApplication](../../winscript/reference/imachinedebugmanagercookie-removeapplication.md)|Rimuove un'applicazione dall'elenco di applicazioni in esecuzione.|  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IMachineDebugManager](../../winscript/reference/imachinedebugmanager-interface.md)   
 [Interfaccia IDebugCookie](../../winscript/reference/idebugcookie-interface.md)