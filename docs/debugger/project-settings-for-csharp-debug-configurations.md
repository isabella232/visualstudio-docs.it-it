---
title: Impostazioni per le configurazioni di Debug c# del progetto | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
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
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: c5bd49d550cb03e8234c8740ea8c0f605ed721c2
ms.sourcegitcommit: 1ab675a872848c81a44d6b4bd3a49958fe673c56
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/10/2018
ms.locfileid: "44283262"
---
# <a name="project-settings-for--c-debug-configurations"></a>Impostazioni di progetto per le configurazioni di debug C#
È possibile modificare le impostazioni di progetto per una configurazione di debug c# nella **pagine delle proprietà** finestra, come descritto in [configurazioni Debug e Release](../debugger/how-to-set-debug-and-release-configurations.md). Le tabelle seguenti mostrano la posizione in cui sono disponibili le impostazioni correlate al debugger il **pagine delle proprietà** finestra.  
  
> [!WARNING]
>  Questo argomento non si applica alle app UWP. Vedere [avviare una sessione di debug (VB, c#, C++ e XAML)](../debugger/start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md)  
  
##  <a name="BKMK_Debug_tab"></a> Scheda Debug  
  
|**Impostazione**|**Descrizione**|  
|-----------------|---------------------|  
|**Configurazione**|Imposta la modalità per la compilazione dell'applicazione. Scegliere tra **attiva (Debug)**, **Debug**, **rilascio**, **tutte le configurazioni**.|  
|**Azione di avvio**|Questo gruppo di controlli specifica l'azione che verrà eseguita quando si sceglie Avvia dal menu Debug.<br /><br /> -   **Avvia progetto** è l'impostazione predefinita e avvia il progetto di avvio per il debug. Per altre informazioni, vedere [scegliendo il progetto di avvio](/previous-versions/visualstudio/visual-studio-2010/0s590bew(v=vs.100)).<br />-   **Avvia programma esterno** consente di avviare e connettersi a un programma che non fa parte di un [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] progetto. Per altre informazioni, vedere [connessione a un programma in esecuzione](/previous-versions/visualstudio/visual-studio-2010/c6wf8e4z(v=vs.100)).<br />-   **Avvia browser con URL** consente di eseguire il debug di un'applicazione Web.|  
|**Argomenti della riga di comando**|Specifica gli argomenti della riga di comando per il programma da sottoporre a debug. Il nome del comando è il nome del programma specificato in Avvia programma esterno. Se l'opzione Azione di avvio è impostata su Avvia URL, non è possibile specificare gli argomenti della riga di comando.|  
|**Directory di lavoro**|Specifica la cartella di lavoro del programma sottoposto a debug. In [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] la cartella di lavoro è la cartella dalla quale viene avviata l'applicazione, che per impostazione predefinita è \bin\debug.|  
|**Usa computer remoto**|Il nome di un computer remoto in cui verrà eseguita l'applicazione a scopo di debug o un' [nome di server Msvsmon](../debugger/remote-debugging.md). Il percorso del file EXE sul computer remoto è specificato dalla proprietà Percorso output nella cartella Proprietà di configurazione, categoria Compila. Il percorso deve essere una directory condivisibile del computer remoto.|
|**Abilita debug codice non gestito**|Consente di eseguire il debug delle chiamate al codice Win32 nativo (non gestito) dall'applicazione gestita in uso.|  
|**Abilita debug SQL Server**|Consente di eseguire il debug di oggetti di database di SQL Server.|  
  
##  <a name="BKMK_Build_tab"></a> Scheda compilazione  
  
|Impostazione|Descrizione|  
|-------------|-----------------|  
|**Simboli di compilazione condizionale:**|Le costanti DEBUG e TRACE vengono definite in questa posizione.<br /><br /> Esse attivano la compilazione condizionale del [classe Debug](/dotnet/api/system.diagnostics.debug) e [classe Trace](/dotnet/api/system.diagnostics.trace). Con queste costanti definite, eseguire il Debug e i metodi della classe Trace generano l'output per il [finestra di Output](../ide/reference/output-window.md). In caso contrario, tali metodi non verranno compilati e non verrà generato alcun output.<br /><br /> -Debug è in genere definito nella versione di Debug di un programma e non definito nella versione di rilascio.<br />-Trace è generalmente definito nelle versioni Debug e rilascio.|  
|**Ottimizza codice**|Questa impostazione deve rimanere disattivata nella versione di debug, a meno che non venga rilevato un bug solo nel codice ottimizzato. L'esecuzione del debug di un codice ottimizzato è più complessa poiché le istruzioni non corrispondono direttamente alle istruzioni presenti nelle finestre del codice sorgente.|  
|**Percorso di output:**|Generalmente impostato su bin\Debug per l'esecuzione del debug.|

> [!NOTE]
> Per altre informazioni sulle opzioni di debug trova nel **avanzate** pulsante, vedere [finestra di dialogo Impostazioni di compilazione avanzate (c#)](../ide/reference/advanced-build-settings-dialog-box-csharp.md). Il formato portabile per i file di simboli (PDB) è il più recente formato lo sviluppo multipiattaforma per .NET Core. 
  
## <a name="see-also"></a>Vedere anche  
 [Impostazioni di debug e preparazione](../debugger/debugger-settings-and-preparation.md)