---
title: 'Classe Task : membri interni | Microsoft Docs'
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
ms.openlocfilehash: c552a4069af343ea45721edc9abb841526124163
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126626394"
---
# <a name="task-class---internal-members"></a>Classe Task : membri interni
Questo articolo descrive i membri interni della classe <xref:System.Threading.Tasks.Task?displayProperty=fullName> che consentono di implementare un debugger personalizzato. Per informazioni generali su questa classe, vedere <xref:System.Threading.Tasks.Task> l'articolo di riferimento.

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
|[Metodo SetNotificationForWaitCompletion](../../extensibility/debugger/setnotificationforwaitcompletion-method.md)|Imposta o cancella il bit TASK_STATE_WAIT_COMPLETION_NOTIFICATION stato corrente.|
|[Metodo NotifyDebuggerOfWaitCompletion](../../extensibility/debugger/notifydebuggerofwaitcompletion-method.md)|Metodo segnaposto utilizzato come destinazione del punto di interruzione dal debugger.|

### <a name="fields"></a>Campi

|Nome|Descrizione|
|----------|-----------------|
|[m_action](../../extensibility/debugger/m-action-field.md)|Delegato che rappresenta il codice da eseguire <xref:System.Threading.Tasks.Task> nell'oggetto .|
|[m_contingentProperties](../../extensibility/debugger/m-contingentproperties-field.md)|Archivia proprietà aggiuntive <xref:System.Threading.Tasks.Task> dell'oggetto .|
|[m_parent](../../extensibility/debugger/m-parent-field.md)|Campo di supporto per la <xref:System.Threading.Tasks.Task?displayProperty=fullName> proprietà padre.|
|[m_stateFlags](../../extensibility/debugger/m-stateflags-field.md)|Archivia informazioni sullo stato corrente <xref:System.Threading.Tasks.Task> dell'oggetto .|
|[m_stateObject](../../extensibility/debugger/m-stateobject-field.md)|Oggetto che rappresenta i dati che verranno utilizzati dall'azione.|
|[m_taskId](../../extensibility/debugger/m-taskid-field.md)|Campo di supporto per la <xref:System.Threading.Tasks.Task.Id%2A?displayProperty=fullName> proprietà.|
|[s_taskIdCounter](../../extensibility/debugger/s-taskidcounter-field.md)|Identificatore successivo disponibile per un <xref:System.Threading.Tasks.Task> oggetto .|
|[TASK_STATE_CANCELED](../../extensibility/debugger/task-state-canceled-field.md)|Indica che l'attività è stata annullata prima di raggiungere lo stato di esecuzione oppure che l'attività ha confermato l'annullamento e completata senza eccezioni.|
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
