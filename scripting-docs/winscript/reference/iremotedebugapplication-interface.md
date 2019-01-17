---
title: IRemoteDebugApplication Interface | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 02ddf409bf25cb86fc742cdc004e2f1b664d22e3
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/16/2019
ms.locfileid: "54348763"
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