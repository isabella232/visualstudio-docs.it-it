---
title: Impostazioni di Project per un C# configurazione di debug | Microsoft Docs
ms.custom: seodec18
ms.date: 11/21/2018
ms.topic: reference
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debug configurations, C#
- project settings [Visual Studio], debug configurations
- debug builds, project settings
- projects [Visual Studio], debug configurations
- project configurations, debug
- debugging [C#], debugger settings
ms.assetid: e30ca810-66e9-4d6e-9cf6-9f285cd0b100
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 77fa0d60c4c702e2594121d5db54bf6c5e7cc6f4
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "55005969"
---
# <a name="project-settings-for--c-debug-configurations"></a>Impostazioni di progetto per configurazioni di debug C#

È possibile modificare C# impostazioni di debug nel progetto di [scheda Debug](#debug-tab) e [scheda compilazione](#build-tab) delle pagine delle proprietà di progetto. 

Per aprire le pagine delle proprietà, selezionare il progetto in **Esplora soluzioni** e quindi selezionare la **delle proprietà** icona, o il progetto e scegliere **proprietà**.

Per altre informazioni, vedere [Configurazioni di debug e rilascio](how-to-set-debug-and-release-configurations.md). 

>[!IMPORTANT]
>Queste impostazioni non si applicano alle app .NET Core, ASP.NET o UWP. Per configurare le impostazioni di debug per le app UWP, vedere [avviare una sessione di debug per un'app UWP](start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md).  
  
## <a name="debug-tab"></a>Scheda Debug  
  
|Impostazione|Description|
|-------------------------------------| - |
| **Configurazione** | Imposta la modalità per la compilazione dell'app. Selezionare **attiva (Debug)**, **Debug**, **rilascio**, oppure **tutte le configurazioni** dall'elenco a discesa. |
| **Azione di avvio** | Specifica l'azione quando si seleziona **avviare** in una configurazione di Debug.<br />- **Avvia progetto** è l'azione predefinita e avvia il progetto di avvio per il debug. Per altre informazioni, vedere [scegliere il progetto di avvio](/previous-versions/visualstudio/visual-studio-2010/0s590bew(v=vs.100)).<br />- **Avvia programma esterno** viene avviato e collegato a un'app che non fa parte di un [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] progetto. Per altre informazioni, vedere [Collega a processi in esecuzione con il debugger](attach-to-running-processes-with-the-visual-studio-debugger.md).<br />- **Avvia il browser con URL** ti permette di eseguire il debug di un'app web. |
| **Opzioni di avvio** > **argomenti della riga di comando** | Specifica gli argomenti della riga di comando per l'app in fase di debug. Il nome del comando è il nome dell'app specificato nel **Avvia programma esterno**. |
| **Opzioni di avvio** > **directory di lavoro** | Specifica la directory di lavoro dell'app in fase di debug. In C#, la directory di lavoro *\bin\debug* per impostazione predefinita.
| **Opzioni di avvio** > **Usa computer remoto**|Selezionare questa opzione per il debug remoto e immettere il nome della destinazione di debug remoto, o un' [nome di server Msvsmon](../debugger/remote-debugging.md). <br />La posizione di un'app nel computer remoto specificata dal **percorso di Output** proprietà di **compilare** scheda. Il percorso deve essere una directory condivisibile del computer remoto. 
| **Motore di debugger** > **Abilita debug codice non gestito** | Esegue il debug di chiamate per il codice Win32 nativo (non gestito) dall'app gestite. |
| **Motore di debugger** > **Abilita debug SQL Server** | Esegue il debug di oggetti di database di SQL Server. |
  
## <a name="build-tab"></a>Scheda Compila  
  
|Impostazione|Description|  
|-------------|-----------------|  
|**Generali** > **simboli di compilazione condizionale**|Se selezionata, definire le costanti DEBUG e TRACE.<br /><br /> Esse attivano la compilazione condizionale della [Classe Debug](/dotnet/api/system.diagnostics.debug) e della [Classe Trace](/dotnet/api/system.diagnostics.trace). Quando sono definite, i metodi delle classi Debug e Trace generano l'output per la [finestra di output](../ide/reference/output-window.md). In caso contrario, tali metodi non verranno compilati e non verrà generato alcun output.<br /><br />DEBUG in genere, viene definito nella versione di Debug di una compilazione e non definito nella versione di rilascio. TRACE viene definito nelle versioni di Debug e rilascio.|  
|**Generali** > **Ottimizza codice**|A meno che un bug presente solo nel codice ottimizzato, lasciare questa impostazione deselezionate per le compilazioni di Debug. Codice ottimizzato è più difficile eseguire il debug, poiché le istruzioni non corrispondono direttamente alle istruzioni nel codice sorgente.|  
|**Output** > **percorso Output**|Generalmente impostato su *bin\Debug* per l'esecuzione del debug.|
|**Advanced** pulsante|Per informazioni sulle opzioni di debug avanzate, vedere [finestra di dialogo Impostazioni di compilazione avanzate (C#)](../ide/reference/advanced-build-settings-dialog-box-csharp.md). Il formato portabile per il simbolo (*PDB*) i file è un formato multipiattaforma recenti per le app .NET Core. 
  
## <a name="see-also"></a>Vedere anche  
 [Impostazioni del debugger e preparazione](../debugger/debugger-settings-and-preparation.md)