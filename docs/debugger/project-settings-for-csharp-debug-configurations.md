---
title: Impostazioni di progetto per una configurazione di debug C# | Microsoft Docs
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
ms.openlocfilehash: a5108e195e5df245c72436752316e8ee91781e7d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "62904061"
---
# <a name="project-settings-for--c-debug-configurations"></a>Impostazioni di progetto per configurazioni di debug C#

È possibile modificare le impostazioni di debug del progetto C# nella [scheda debug](#debug-tab) e [nella scheda Compila](#build-tab) delle pagine delle proprietà del progetto.

Per aprire le pagine delle proprietà, selezionare il progetto in **Esplora soluzioni** , quindi selezionare l'icona **Proprietà** oppure fare clic con il pulsante destro del mouse sul progetto e scegliere **proprietà**.

Per altre informazioni, vedere [Configurazioni di debug e rilascio](how-to-set-debug-and-release-configurations.md).

>[!IMPORTANT]
>Queste impostazioni non si applicano alle app .NET Core, ASP.NET o UWP. Per configurare le impostazioni di debug per le app UWP, vedere [avviare una sessione di debug per un'app UWP](start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md).

## <a name="debug-tab"></a>Scheda Debug

|Impostazione|Descrizione|
|-------------------------------------| - |
| **Configurazione** | Imposta la modalità per la compilazione dell'app. Selezionare **Active (debug)**, **debug**, **Release**o **tutte le configurazioni** dall'elenco a discesa. |
| **Azione di avvio** | Specifica l'azione quando si seleziona **Avvia** in una configurazione di debug.<br />- **Avvia progetto** è l'azione predefinita e avvia il progetto di avvio per il debug. Per altre informazioni, vedere [Choose the Startup Project](/previous-versions/visualstudio/visual-studio-2010/0s590bew(v=vs.100)).<br />- **Avvia programma esterno** e si connette a un'app che non fa parte di un [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] progetto. Per ulteriori informazioni, vedere [Connetti a processi in esecuzione con il debugger](attach-to-running-processes-with-the-visual-studio-debugger.md).<br />- **Avvia browser con URL** consente di eseguire il debug di un'app Web. |
| **Opzioni**  >  di avvio **Argomenti della riga di comando** | Specifica gli argomenti della riga di comando per l'applicazione di cui è in corso il debug. Il nome del comando è il nome dell'app specificato in **Avvia programma esterno**. |
| **Opzioni**  >  di avvio **Directory di lavoro** | Specifica la directory di lavoro dell'app di cui è in corso il debug. In C# la directory di lavoro è *\bin\Debug* per impostazione predefinita.
| **Opzioni**  >  di avvio **Usa computer remoto**|Per il debug remoto, selezionare questa opzione e immettere il nome della destinazione di debug remoto oppure un [nome di server Msvsmon](../debugger/remote-debugging.md). <br />Il percorso di un'app nel computer remoto è specificato dalla proprietà **percorso output** nella scheda **Compila** . Il percorso deve essere una directory condivisibile nel computer remoto.
| **Motore**  >  di debugger **Abilita debug codice non gestito** | Esegue il debug delle chiamate al codice Win32 nativo (non gestito) dall'app gestita. |
| **Motore**  >  di debugger **Abilita debug SQL Server** | Esegue il debug di SQL Server oggetti di database. |

## <a name="build-tab"></a>Scheda Compila

|Impostazione|Descrizione|
|-------------|-----------------|
|**Informazioni generali**  >  **Simboli di compilazione condizionale**|Definire le costanti di DEBUG e di traccia, se selezionate.<br /><br /> Esse attivano la compilazione condizionale della [Classe Debug](/dotnet/api/system.diagnostics.debug) e della [Classe Trace](/dotnet/api/system.diagnostics.trace). Quando sono definite, i metodi delle classi Debug e Trace generano l'output per la [finestra di output](../ide/reference/output-window.md). In caso contrario, tali metodi non verranno compilati e non verrà generato alcun output.<br /><br />In genere, il DEBUG è definito nella versione di debug di una compilazione e non è definito nella versione di rilascio. TRACE è definito in entrambe le versioni di debug e di rilascio.|
|**Informazioni generali**  >  **Ottimizza codice**|A meno che non sia presente un bug solo nel codice ottimizzato, lasciare deselezionata questa impostazione per le compilazioni di debug. Il debug del codice ottimizzato è più difficile, perché le istruzioni non corrispondono direttamente alle istruzioni nel codice sorgente.|
|**Output**  >  di **Percorso di output**|Viene in genere impostato su *bin\Debug* per il debug.|
|Pulsante **Avanzate**|Per informazioni sulle opzioni di debug avanzate, vedere [finestra di dialogo Impostazioni di compilazione avanzate (C#)](../ide/reference/advanced-build-settings-dialog-box-csharp.md). Il formato portatile per i file di simboli (con*estensione PDB*) è un recente formato multipiattaforma per le app .NET Core.

## <a name="see-also"></a>Vedere anche
- [Impostazioni e preparazione del debugger](../debugger/debugger-settings-and-preparation.md)