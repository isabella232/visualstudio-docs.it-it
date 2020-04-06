---
title: Classe di attività - Membri interni Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, Task class [.NET Framework]
- Task class [.NET Framework debug engines]
ms.assetid: 28e47c3b-9323-424a-80ac-6cc3bf19e09b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dcf278c0248b344cea4be7cf161ecc91581f5f2e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712743"
---
# <a name="task-class---internal-members"></a>Classe Task - membri interni
In questo articolo vengono descritti <xref:System.Threading.Tasks.Task?displayProperty=fullName> i membri interni della classe che consentono di implementare un debugger personalizzato. Per informazioni generali su questa <xref:System.Threading.Tasks.Task> classe, vedere l'articolo di riferimento.

 **Spazio dei nomi:**<xref:System.Threading.Tasks?displayProperty=fullName>

 **Assembly:** mscorlib (in *mscorlib.dll*)

 Poiché non è possibile accedere a questi membri interni da .NET Framework, la sintassi seguente è disponibile in Common Intermediate Language (CIL).

## <a name="syntax"></a>Sintassi

```csharp
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
|[Metodo SetNotificationForWaitCompletion](../../extensibility/debugger/setnotificationforwaitcompletion-method.md)|Imposta o cancella il bit di stato del TASK_STATE_WAIT_COMPLETION_NOTIFICATION.|
|[Metodo NotifyDebuggerOfWaitCompletion](../../extensibility/debugger/notifydebuggerofwaitcompletion-method.md)|Metodo segnaposto utilizzato come destinazione del punto di interruzione dal debugger.|

### <a name="fields"></a>Campi

|Nome|Descrizione|
|----------|-----------------|
|[m_action](../../extensibility/debugger/m-action-field.md)|Delegato che rappresenta il codice <xref:System.Threading.Tasks.Task> da eseguire nell'oggetto.|
|[m_contingentProperties](../../extensibility/debugger/m-contingentproperties-field.md)|Archivia le <xref:System.Threading.Tasks.Task> proprietà aggiuntive dell'oggetto.|
|[m_parent](../../extensibility/debugger/m-parent-field.md)|Campo di backup <xref:System.Threading.Tasks.Task?displayProperty=fullName> per la proprietà padre.|
|[m_stateFlags](../../extensibility/debugger/m-stateflags-field.md)|Archivia le informazioni sullo <xref:System.Threading.Tasks.Task> stato corrente dell'oggetto.|
|[m_stateObject](../../extensibility/debugger/m-stateobject-field.md)|Oggetto che rappresenta i dati che verranno utilizzati dall'azione.|
|[m_taskId](../../extensibility/debugger/m-taskid-field.md)|Campo di sostegno <xref:System.Threading.Tasks.Task.Id%2A?displayProperty=fullName> per la proprietà.|
|[s_taskIdCounter](../../extensibility/debugger/s-taskidcounter-field.md)|Successivo identificatore disponibile <xref:System.Threading.Tasks.Task> per un oggetto.|
|[TASK_STATE_CANCELED](../../extensibility/debugger/task-state-canceled-field.md)|Indica che l'attività è stata annullata prima del raggiungimenti dello stato di esecuzione o che l'attività ha confermato l'annullamento e completato senza eccezioni.|
|[TASK_STATE_EXECUTED](../../extensibility/debugger/task-state-executed-field.md)|Indica che l'attività è in esecuzione.|
|[TASK_STATE_FAULTED](../../extensibility/debugger/task-state-faulted-field.md)|Indica che l'attività è stata completata a causa di un'eccezione non gestita.|
|[TASK_STATE_RAN_TO_COMPLETION](../../extensibility/debugger/task-state-ran-to-completion-field.md)|Indica che l'esecuzione dell'attività è stata completata correttamente.|
|[TASK_STATE_WAITING_ON_CHILDREN](../../extensibility/debugger/task-state-waiting-on-children-field.md)|Indica che l'attività ha terminato l'esecuzione del delegato ed è implicitamente in attesa del completamento delle attività figlio associate.|

## <a name="remarks"></a>Osservazioni
 I metodi interni seguenti sono utili per un <xref:System.Threading.Tasks.Task> motore del debugger perché contrassegnano l'ingresso all'esecuzione del codice:The following internal methods are useful to a debugger engine because they mark the entrance to code execution:

- `Execute`

- `ExecuteEntry`

- `ExecuteWithThreadLocal`

- `Finish`

- `InnerInvoke`

- `InternalWait`

## <a name="see-also"></a>Vedere anche
- <xref:System.Threading.Tasks.Task?displayProperty=fullName>
- [Elementi interni delle estensioni parallele per .NET FrameworkParallel extension internals for the .NET Framework](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)
