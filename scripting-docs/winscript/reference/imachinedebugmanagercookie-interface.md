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
ms.openlocfilehash: fdc02498360f2e3900012166474c5d1e35abd6ee
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2019
ms.locfileid: "58151050"
---
# <a name="imachinedebugmanagercookie-interface"></a>Interfaccia IMachineDebugManagerCookie
Simile al `IMachineDebugManager` interfaccia, il `IMachineDebugManagerCookie` interfaccia supporta i cookie di debug.  
  
 Questa interfaccia (insieme al `IDebugCookie` interface) consentire gli script da eseguire in un processo del debugger dello script senza richiedere che il debugger tenere traccia di tali script.  
  
 Un debugger di script chiama il `IDebugCookie::SetDebugCookie` metodo nel processo di Debug Manager (PDM). PDM invia quindi questo cookie insieme a qualsiasi richiesta per aggiungere o rimuovere un'applicazione di script a o dal computer eseguire il Debug Manager (MDM), usando i metodi del `IMachineDebugManagerCookie` interfaccia. MDM quindi comunica a ogni debugger della modifica, eccetto quello che ha tale cookie.  
  
 Oltre ai metodi ereditati da `IUnknown`, il `IMachineDebugManagerCookie` interfaccia espone i metodi seguenti.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IMachineDebugManagerCookie::AddApplication](../../winscript/reference/imachinedebugmanagercookie-addapplication.md)|Aggiunge un'applicazione in esecuzione l'elenco delle applicazioni.|  
|[IMachineDebugManagerCookie::EnumApplications](../../winscript/reference/imachinedebugmanagercookie-enumapplications.md)|Restituisce un enumeratore dell'elenco corrente delle applicazioni in esecuzione.|  
|[IMachineDebugManagerCookie::RemoveApplication](../../winscript/reference/imachinedebugmanagercookie-removeapplication.md)|Rimuove l'esecuzione di un'applicazione elenco di applicazioni.|  
  
## <a name="see-also"></a>Vedere anche  
 [IMachineDebugManager Interface](../../winscript/reference/imachinedebugmanager-interface.md)   
 [Interfaccia IDebugCookie](../../winscript/reference/idebugcookie-interface.md)