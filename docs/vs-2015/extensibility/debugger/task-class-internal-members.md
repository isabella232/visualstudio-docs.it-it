---
title: Classe Task-membri interni | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debug engines, Task class [.NET Framework]
- Task class [.NET Framework debug engines]
ms.assetid: 28e47c3b-9323-424a-80ac-6cc3bf19e09b
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ef0cd907c25a90ee90e3ed23a773d0ae8ba0ce1f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "90839451"
---
# <a name="task-class---internal-members"></a>Classe Task - Membri interni
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

In questo argomento vengono descritti i membri interni della <xref:System.Threading.Tasks.Task?displayProperty=fullName> classe che consentono di implementare un debugger personalizzato. Per informazioni generali su questa classe, vedere l' <xref:System.Threading.Tasks.Task> argomento di riferimento.  
  
 **Spazio dei nomi:** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Assembly:** mscorlib (in mscorlib.dll)  
  
 Poiché non è possibile accedere a questi membri interni dalla .NET Framework, nella Common Intermediate Language (CIL) viene fornita la sintassi seguente.  
  
## <a name="syntax"></a>Sintassi  
  
```  
.class public auto ansi System.Threading.Tasks.Task  
       extends System.Object  
       implements System.Threading.IThreadPoolWorkItem,  
                  System.IAsyncResult,  
                  System.IDisposable,  
                  System.Threading.ICancelableOperation  
```  
  
## <a name="members"></a>Membri  
  
### <a name="methods"></a>Metodi  
  
|Nome|Descrizione|  
|----------|-----------------|  
|[Metodo SetNotificationForWaitCompletion](../../extensibility/debugger/setnotificationforwaitcompletion-method.md)|Imposta o cancella il bit di stato TASK_STATE_WAIT_COMPLETION_NOTIFICATION.|  
|[Metodo NotifyDebuggerOfWaitCompletion](../../extensibility/debugger/notifydebuggerofwaitcompletion-method.md)|Metodo segnaposto utilizzato come destinazione del punto di interruzione dal debugger.|  
  
### <a name="fields"></a>Campi  
  
|Nome|Descrizione|  
|----------|-----------------|  
|[m_action](../../extensibility/debugger/m-action-field.md)|Delegato che rappresenta il codice da eseguire nell' <xref:System.Threading.Tasks.Task> oggetto.|  
|[m_contingentProperties](../../extensibility/debugger/m-contingentproperties-field.md)|Archivia le proprietà aggiuntive dell' <xref:System.Threading.Tasks.Task> oggetto.|  
|[m_parent](../../extensibility/debugger/m-parent-field.md)|Campo sottostante per la <xref:System.Threading.Tasks.Task?displayProperty=fullName> proprietà padre.|  
|[m_stateFlags](../../extensibility/debugger/m-stateflags-field.md)|Archivia informazioni sullo stato corrente dell' <xref:System.Threading.Tasks.Task> oggetto.|  
|[m_stateObject](../../extensibility/debugger/m-stateobject-field.md)|Oggetto che rappresenta i dati che verranno utilizzati dall'azione.|  
|[m_taskId](../../extensibility/debugger/m-taskid-field.md)|Campo sottostante per la <xref:System.Threading.Tasks.Task.Id%2A?displayProperty=fullName> Proprietà.|  
|[s_taskIdCounter](../../extensibility/debugger/s-taskidcounter-field.md)|Identificatore successivo disponibile per un <xref:System.Threading.Tasks.Task> oggetto.|  
|[TASK_STATE_CANCELED](../../extensibility/debugger/task-state-canceled-field.md)|Indica che l'attività è stata annullata prima che raggiunga lo stato in esecuzione o che l'attività abbia riconosciuto l'annullamento e completata senza eccezione.|  
|[TASK_STATE_EXECUTED](../../extensibility/debugger/task-state-executed-field.md)|Indica che l'attività è in esecuzione.|  
|[TASK_STATE_FAULTED](../../extensibility/debugger/task-state-faulted-field.md)|Indica che l'attività è stata completata a causa di un'eccezione non gestita.|  
|[TASK_STATE_RAN_TO_COMPLETION](../../extensibility/debugger/task-state-ran-to-completion-field.md)|Indica che l'esecuzione dell'attività è stata completata correttamente.|  
|[TASK_STATE_WAITING_ON_CHILDREN](../../extensibility/debugger/task-state-waiting-on-children-field.md)|Indica che l'attività ha terminato l'esecuzione del delegato ed è in attesa implicita del completamento delle attività figlio connesse.|  
  
## <a name="remarks"></a>Commenti  
 I metodi interni seguenti sono utili per un motore di debugger perché contrassegnano l'ingresso per l' <xref:System.Threading.Tasks.Task> esecuzione del codice:  
  
- `Execute`  
  
- `ExecuteEntry`  
  
- `ExecuteWithThreadLocal`  
  
- `Finish`  
  
- `InnerInvoke`  
  
- `InternalWait`  
  
## <a name="see-also"></a>Vedere anche  
 <xref:System.Threading.Tasks.Task?displayProperty=fullName>   
 [Elementi interni delle estensioni parallele per .NET Framework](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)
