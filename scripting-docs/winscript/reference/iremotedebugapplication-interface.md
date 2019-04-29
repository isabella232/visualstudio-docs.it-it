---
title: IRemoteDebugApplication Interface | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IRemoteDebugApplication interface
ms.assetid: 96bf2a3f-049f-46ba-86ad-57fc184343a2
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2a231818def210f7c88ab031059f8561c67b33d1
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62944228"
---
# <a name="iremotedebugapplication-interface"></a>Interfaccia IRemoteDebugApplication
Rappresenta un'applicazione in esecuzione. Non dovrà corrispondere a un processo del sistema operativo. In genere, un debugger è destinato a un'applicazione per il debug. Il gestore di eseguire il Debug di processi in genere implementa l'oggetto applicazione.  
  
 Oltre ai metodi ereditati da `IUnknown`, il `IRemoteDebugApplication` interfaccia espone i metodi seguenti.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IRemoteDebugApplication::ResumeFromBreakPoint](../../winscript/reference/iremotedebugapplication-resumefrombreakpoint.md)|Continua un'applicazione che è attualmente disponibile in un punto di interruzione.|  
|[IRemoteDebugApplication::CauseBreak](../../winscript/reference/iremotedebugapplication-causebreak.md)|Fa sì che l'applicazione accede al debugger il prima possibile.|  
|[IRemoteDebugApplication::ConnectDebugger](../../winscript/reference/iremotedebugapplication-connectdebugger.md)|Connette un debugger all'applicazione.|  
|[IRemoteDebugApplication::DisconnectDebugger](../../winscript/reference/iremotedebugapplication-disconnectdebugger.md)|Consente di disconnettere il debugger corrente dall'applicazione.|  
|[IRemoteDebugApplication::GetDebugger](../../winscript/reference/iremotedebugapplication-getdebugger.md)|Restituisce il debugger corrente è connesso all'applicazione.|  
|[IRemoteDebugApplication::CreateInstanceAtApplication](../../winscript/reference/iremotedebugapplication-createinstanceatapplication.md)|Fornisce un meccanismo per il debug dell'IDE, l'esecuzione out-of-process per l'applicazione, per creare oggetti nel processo dell'applicazione.|  
|[IRemoteDebugApplication::QueryAlive](../../winscript/reference/iremotedebugapplication-queryalive.md)|Indica se l'applicazione è reattiva.|  
|[IRemoteDebugApplication::EnumThreads](../../winscript/reference/iremotedebugapplication-enumthreads.md)|Enumera tutti i thread noti da associare all'applicazione.|  
|[IRemoteDebugApplication::GetName](../../winscript/reference/iremotedebugapplication-getname.md)|Restituisce il nome del nodo dell'applicazione.|  
|[IRemoteDebugApplication::GetRootNode](../../winscript/reference/iremotedebugapplication-getrootnode.md)|Restituisce il nodo dell'applicazione in cui vengono aggiunti tutti i nodi associati all'applicazione.|  
|[IRemoteDebugApplication::EnumGlobalExpressionContexts](../../winscript/reference/iremotedebugapplication-enumglobalexpressioncontexts.md)|Enumera i contesti di espressione globale per tutte le lingue in esecuzione in questa applicazione.|