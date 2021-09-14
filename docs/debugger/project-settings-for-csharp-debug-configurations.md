---
title: Project Impostazioni per una configurazione di debug C# | Microsoft Docs
description: Informazioni su come modificare le impostazioni di progetto per una configurazione di debug C# in Visual Studio, usando la scheda Debug e la scheda Compilazione delle pagine delle proprietà del progetto.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- dotnet
ms.openlocfilehash: 002d95684ffa7167ff0ff5bb10158f3e23622314
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126709893"
---
# <a name="project-settings-for--c-debug-configurations"></a>Impostazioni di progetto per configurazioni di debug C#

È possibile modificare le impostazioni di debug del progetto C# nella [scheda Debug e](#debug-tab) nella scheda [Compilazione](#build-tab) delle pagine delle proprietà del progetto.

Per aprire le pagine delle proprietà, selezionare il  progetto in **Esplora soluzioni** e quindi selezionare l'icona Proprietà oppure fare clic con il pulsante destro del mouse sul progetto e **scegliere Proprietà**.

Per altre informazioni, vedere [Configurazioni di debug e rilascio](how-to-set-debug-and-release-configurations.md).

>[!IMPORTANT]
>Queste impostazioni non si applicano alle app .NET Core, ASP.NET o UWP. Per configurare le impostazioni di debug per le app UWP, vedere [Avviare una sessione di debug per un'app UWP.](start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md)

## <a name="debug-tab"></a>Scheda Debug

|Impostazione|Descrizione|
|-------------------------------------| - |
| **Configuration** | Imposta la modalità per la compilazione dell'app. Selezionare **Active (Debug) (Attivo (Debug)**, **Debug**, **Release (Rilascio)** o All Configurations (Tutte le **configurazioni)** dall'elenco a discesa. |
| **Azione di avvio** | Specifica l'azione quando si seleziona **Avvia** in una configurazione di debug.<br />- **Avvia progetto** è l'azione predefinita e avvia il progetto di avvio per il debug. Per altre informazioni, vedere [Scegliere il progetto di avvio.](/previous-versions/visualstudio/visual-studio-2010/0s590bew(v=vs.100))<br />- **Avvia programma esterno** avvia e si collega a un'app che non fa parte di un [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] progetto. Per altre informazioni, vedere [Connettersi a processi in esecuzione con il debugger.](attach-to-running-processes-with-the-visual-studio-debugger.md)<br />- **Avvia browser con URL consente** di eseguire il debug di un'app Web. |
| **Opzioni di avvio**  >  **Argomenti della riga di comando** | Specifica gli argomenti della riga di comando per l'app di cui è in corso il debug. Il nome del comando è il nome dell'app specificato in **Avviare il programma esterno.** |
| **Opzioni di avvio**  >  **Directory di lavoro** | Specifica la directory di lavoro dell'app di cui è in corso il debug. In C# la directory di lavoro è *\bin\debug* per impostazione predefinita.
| **Opzioni di avvio**  >  **Usa computer remoto**|Per il debug remoto, selezionare questa opzione e immettere il nome della destinazione di debug remoto o il nome del [server Msvsmon](../debugger/remote-debugging.md). <br />Il percorso di un'app nel computer remoto viene specificato dalla **proprietà Percorso** di output nella **scheda** Compila. Il percorso deve essere una directory condivisibile nel computer remoto.
| **Motore del debugger**  >  **Abilitare il debug del codice non gestito** | Esegue il debug delle chiamate al codice Win32 nativo (non gestito) dall'app gestita. |
| **Motore del debugger**  >  **Abilitare SQL Server debug** | Esegue il debug SQL Server oggetti di database. |

## <a name="build-tab"></a>Scheda Compila

|Impostazione|Descrizione|
|-------------|-----------------|
|**Generale**  >  **Simboli di compilazione condizionale**|Definire le costanti DEBUG e TRACE, se selezionate.<br /><br /> Esse attivano la compilazione condizionale della [Classe Debug](/dotnet/api/system.diagnostics.debug) e della [Classe Trace](/dotnet/api/system.diagnostics.trace). Quando sono definite, i metodi delle classi Debug e Trace generano l'output per la [finestra di output](../ide/reference/output-window.md). In caso contrario, tali metodi non verranno compilati e non verrà generato alcun output.<br /><br />In genere, DEBUG è definito nella versione di debug di una build e non è definito nella versione di rilascio. TRACE è definito sia nelle versioni di debug che di rilascio.|
|**Generale**  >  **Ottimizzare il codice**|A meno che non venga visualizzato un bug solo nel codice ottimizzato, lasciare deselezionata questa impostazione per Compilazioni di debug. Il debug del codice ottimizzato è più difficile, perché le istruzioni non corrispondono direttamente alle istruzioni nel codice sorgente.|
|**Output**  >  **Percorso di output**|In genere è impostato *su bin\Debug per* il debug.|
|**Pulsante** Avanzate|Per informazioni sulle opzioni di debug avanzate, vedere [Finestra di dialogo Impostazioni di compilazione avanzate (C#).](../ide/reference/advanced-build-settings-dialog-box-csharp.md) Il formato portabile per i file di simboli *(con estensione pdb)* è un formato multipiattaforma recente per le app .NET Core.

## <a name="see-also"></a>Vedi anche
- [Impostazioni del debugger e preparazione](../debugger/debugger-settings-and-preparation.md)