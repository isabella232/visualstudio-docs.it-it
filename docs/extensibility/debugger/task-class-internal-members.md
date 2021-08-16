---
title: Classe task - Membri interni | Microsoft Docs
description: Informazioni sui membri interni della classe System.Threading.Tasks.Task che consentono di implementare un debugger personalizzato.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- debug engines, Task class [.NET Framework]
- Task class [.NET Framework debug engines]
ms.assetid: 28e47c3b-9323-424a-80ac-6cc3bf19e09b
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: a8c6a40cb19315c6b754ef8e81208f78f1e1996837d6ee352d84a6df25041dc4
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121414961"
---
# <a name="task-class---internal-members"></a>Classe di attività : membri interni
Questo articolo descrive i membri interni della classe che consentono <xref:System.Threading.Tasks.Task?displayProperty=fullName> di implementare un debugger personalizzato. Per informazioni generali su questa classe, vedere <xref:System.Threading.Tasks.Task> l'articolo di riferimento.

 **Spazio dei nomi:** <xref:System.Threading.Tasks?displayProperty=fullName>

 **Assembly:** mscorlib (in *mscorlib.dll*)

 Poiché non è possibile accedere a questi membri interni dal .NET Framework, in Common Intermediate Language (CIL) viene fornita la sintassi seguente.

## <a name="syntax"></a>Sintassi

```csharp
.class public auto ansi System.Threading.Tasks.Task
       extends System.Object
       implements System.Threading.IThreadPoolWorkItem,
                  System.IAsyncResult,
                  System.IDisposable,
                  System.Threading.ICancelableOperation
```

## <a name="members"></a>Members

### <a name="methods"></a>Metodi

|Nome|Descrizione|
|----------|-----------------|
|[Metodo SetNotificationForWaitCompletion](../../extensibility/debugger/setnotificationforwaitcompletion-method.md)|Imposta o cancella il bit TASK_STATE_WAIT_COMPLETION_NOTIFICATION stato.|
|[Metodo NotifyDebuggerOfWaitCompletion](../../extensibility/debugger/notifydebuggerofwaitcompletion-method.md)|Metodo segnaposto usato come destinazione del punto di interruzione dal debugger.|

### <a name="fields"></a>Campi

|Nome|Descrizione|
|----------|-----------------|
|[m_action](../../extensibility/debugger/m-action-field.md)|Delegato che rappresenta il codice da eseguire <xref:System.Threading.Tasks.Task> nell'oggetto .|
|[m_contingentProperties](../../extensibility/debugger/m-contingentproperties-field.md)|Archivia proprietà aggiuntive <xref:System.Threading.Tasks.Task> dell'oggetto .|
|[m_parent](../../extensibility/debugger/m-parent-field.md)|Campo di supporto per la <xref:System.Threading.Tasks.Task?displayProperty=fullName> proprietà padre.|
|[m_stateFlags](../../extensibility/debugger/m-stateflags-field.md)|Archivia informazioni sullo stato corrente <xref:System.Threading.Tasks.Task> dell'oggetto .|
|[m_stateObject](../../extensibility/debugger/m-stateobject-field.md)|Oggetto che rappresenta i dati che verranno usati dall'azione.|
|[m_taskId](../../extensibility/debugger/m-taskid-field.md)|Campo di supporto per la <xref:System.Threading.Tasks.Task.Id%2A?displayProperty=fullName> proprietà.|
|[s_taskIdCounter](../../extensibility/debugger/s-taskidcounter-field.md)|Identificatore disponibile successivo per un <xref:System.Threading.Tasks.Task> oggetto .|
|[TASK_STATE_CANCELED](../../extensibility/debugger/task-state-canceled-field.md)|Indica che l'attività è stata annullata prima di raggiungere lo stato in esecuzione o che l'attività ha confermato l'annullamento e completata senza eccezioni.|
|[TASK_STATE_EXECUTED](../../extensibility/debugger/task-state-executed-field.md)|Indica che l'attività è in esecuzione.|
|[TASK_STATE_FAULTED](../../extensibility/debugger/task-state-faulted-field.md)|Indica che l'attività è stata completata a causa di un'eccezione non gestita.|
|[TASK_STATE_RAN_TO_COMPLETION](../../extensibility/debugger/task-state-ran-to-completion-field.md)|Indica che l'esecuzione dell'attività è stata completata correttamente.|
|[TASK_STATE_WAITING_ON_CHILDREN](../../extensibility/debugger/task-state-waiting-on-children-field.md)|Indica che l'attività ha terminato l'esecuzione del delegato ed è in attesa implicita del completamento delle attività figlio associate.|

## <a name="remarks"></a>Commenti
 I metodi interni seguenti sono utili per un motore del debugger perché contrassegnano l'ingresso <xref:System.Threading.Tasks.Task> all'esecuzione del codice:

- `Execute`

- `ExecuteEntry`

- `ExecuteWithThreadLocal`

- `Finish`

- `InnerInvoke`

- `InternalWait`

## <a name="see-also"></a>Vedi anche
- <xref:System.Threading.Tasks.Task?displayProperty=fullName>
- [Estensioni interne parallele per l'.NET Framework](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)
