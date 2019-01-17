---
title: Interfaccia IApplicationDebugger | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IApplicationDebugger interface
ms.assetid: 27f6f8f5-2bf3-49bc-8abb-dfca98935aba
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8b364422afcdf72deaee3d56123a71672769ed61
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/16/2019
ms.locfileid: "54348321"
---
# <a name="iapplicationdebugger-interface"></a>Interfaccia IApplicationDebugger
L'interfaccia primaria esposta da un debugger. Oltre ai metodi ereditati da `IUnknown`, il `IApplicationDebugger` interfaccia espone i metodi seguenti.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IApplicationDebugger::QueryAlive](../../winscript/reference/iapplicationdebugger-queryalive.md)|Indica se il debugger è reattivo.|  
|[IApplicationDebugger::CreateInstanceAtDebugger](../../winscript/reference/iapplicationdebugger-createinstanceatdebugger.md)|Consente la creazione di oggetti nel processo del debugger dal codice che è out-of-process al debugger.|  
|[IApplicationDebugger::onDebugOutput](../../winscript/reference/iapplicationdebugger-ondebugoutput.md)|Gestisce un evento di output di debug.|  
|[IApplicationDebugger::onHandleBreakPoint](../../winscript/reference/iapplicationdebugger-onhandlebreakpoint.md)|Gestisce l'evento punto di interruzione.|  
|[IApplicationDebugger::onClose](../../winscript/reference/iapplicationdebugger-onclose.md)|Gestisce un evento di chiusura dell'applicazione di debug.|  
|[IApplicationDebugger::onDebuggerEvent](../../winscript/reference/iapplicationdebugger-ondebuggerevent.md)|Gestisce l'evento dell'applicazione personalizzata.|