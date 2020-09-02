---
author: ghogen
ms.author: ghogen
ms.topic: include
ms.date: 4/23/2020
ms.openlocfilehash: 6fd0fc6fd4f2e54c0d15f649139b649797f8336f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "89042998"
---
### <a name="tooltaskextension-parameters"></a>Parametri ToolTaskExtension

Questa attività eredita dalla classe <xref:Microsoft.Build.Tasks.ToolTaskExtension> , che eredita dalla classe <xref:Microsoft.Build.Utilities.ToolTask> , che a sua volta eredita dalla classe <xref:Microsoft.Build.Utilities.Task> . Questa catena di ereditarietà aggiunge diversi parametri alle attività che ne derivano.

Nella tabella seguente vengono descritti i parametri delle classi di base:

| Parametro | Descrizione |
| - | - |
| <xref:Microsoft.Build.Utilities.ToolTask.EchoOff%2A> | Parametro `bool` facoltativo.<br /><br /> Quando è impostato su `true` , questa attività passa **/q** alla riga di comando *cmd.exe* in modo che la riga di comando non venga copiata in stdout. |
| <xref:Microsoft.Build.Utilities.ToolTask.EnvironmentVariables%2A> | Parametro di matrice `String` facoltativo.<br /><br /> Matrice di definizioni di variabili di ambiente, separate da punti e virgola. Ogni definizione deve specificare un nome e un valore della variabile di ambiente separati da un segno di uguale. Queste variabili vengono passate all'eseguibile generato in aggiunta a o con override selettivo del blocco di ambiente standard. Ad esempio, `Variable1=Value1;Variable2=Value2` |
| <xref:Microsoft.Build.Utilities.ToolTask.ExitCode%2A> | Parametro di sola lettura di output `Int32` facoltativo.<br /><br /> Specifica il codice di uscita fornito dal comando eseguito. Se l'attività ha registrato errori, ma il processo ha un codice di uscita pari a 0 (esito positivo), il parametro viene impostato su -1. |
| <xref:Microsoft.Build.Utilities.ToolTask.LogStandardErrorAsError%2A> | Parametro `bool` facoltativo.<br /><br /> Se `true`, tutti i messaggi ricevuti nel flusso di errori standard vengono registrati come errori. |
| <xref:Microsoft.Build.Utilities.ToolTask.LogStandardErrorAsError%2A> | Parametro `bool` facoltativo.<br /><br /> Se `true`, tutti i messaggi ricevuti nel flusso di errori standard vengono registrati come errori. |
| <xref:Microsoft.Build.Utilities.ToolTask.StandardErrorImportance%2A> | Parametro `String` facoltativo.<br /><br /> Importanza con cui registrare il testo dal flusso di output standard. |
| <xref:Microsoft.Build.Utilities.ToolTask.StandardOutputImportance%2A> | Parametro `String` facoltativo.<br /><br /> Importanza con cui registrare il testo dal flusso di output standard. |
| <xref:Microsoft.Build.Utilities.ToolTask.Timeout%2A> | Parametro `Int32` facoltativo.<br /><br /> Specifica la quantità di tempo, in millisecondi, dopo i quali l'eseguibile dell'attività viene terminato. Il valore predefinito è `Int.MaxValue`, con cui si indica che non esiste alcun periodo di timeout. Il timeout è espresso in millisecondi. |
| <xref:Microsoft.Build.Utilities.ToolTask.ToolExe%2A> | Parametro `string` facoltativo.<br /><br /> I progetti possono implementarlo per eseguire l'override di un ToolName. Le attività possono eseguirne l'override per conservare il ToolName. |
| <xref:Microsoft.Build.Utilities.ToolTask.ToolPath%2A> | Parametro `string` facoltativo.<br /><br /> Specifica la posizione da cui l'attività carica il file eseguibile sottostante. Se questo parametro non viene specificato, l'attività usa il percorso di installazione SDK corrispondente alla versione del Framework che esegue MSBuild. |
| <xref:Microsoft.Build.Utilities.ToolTask.UseCommandProcessor%2A> | Parametro `bool` facoltativo.<br /><br /> Se `true`, questa attività crea un file batch per la riga di comando e lo esegue mediante il processore dei comandi anziché eseguire direttamente il comando. |
| <xref:Microsoft.Build.Utilities.ToolTask.YieldDuringToolExecution%2A> | Parametro `bool` facoltativo.<br /><br /> Se `true`, questa attività restituisce il nodo quando l'attività è in esecuzione. |
