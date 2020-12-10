---
title: Classe Task-membri interni | Microsoft Docs
description: Informazioni sui membri interni della classe System. Threading. Tasks. Task che consentono di implementare un debugger personalizzato.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 5f18de66a524fbc652b8153c5b34b4464cda60f5
ms.sourcegitcommit: d10f37dfdba5d826e7451260c8370fd1efa2c4e4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/10/2020
ms.locfileid: "96996019"
---
# <a name="task-class---internal-members"></a>Classe Task-membri interni
Questo articolo descrive i membri interni della <xref:System.Threading.Tasks.Task?displayProperty=fullName> classe che consentono di implementare un debugger personalizzato. Per informazioni generali su questa classe, vedere l' <xref:System.Threading.Tasks.Task> articolo di riferimento.

 **Spazio dei nomi:** <xref:System.Threading.Tasks?displayProperty=fullName>

 **Assembly:** mscorlib (in *mscorlib.dll*)

 Poiché non è possibile accedere a questi membri interni dalla .NET Framework, nella Common Intermediate Language (CIL) viene fornita la sintassi seguente.

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
|[TASK_STATE_CANCELED](../../extensibility/debugger/task-state-canceled-field.md)|Indica che l'attività è stata annullata prima che raggiunga lo stato in esecuzione o che l'attività abbia confermato l'annullamento e completata senza eccezione.|
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
- <xref:System.Threading.Tasks.Task?displayProperty=fullName>
- [Interni di estensioni parallele per la .NET Framework](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)
