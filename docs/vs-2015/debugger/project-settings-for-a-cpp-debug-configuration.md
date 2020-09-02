---
title: Impostazioni di progetto per una configurazione di debug C++ | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- VC.Project.VCDebugSettings.WebBrowser.DebuggerType
- VC.Project.IVCGPUDebugPageObject.EnvironmentMerge
- VC.Project.VCDebugSettings.SymbolPath
- VC.Project.IVCClusterDebugPageObject.ApplicationCommand
- VC.Project.IVCRemoteDebugPageObject.WorkingDirectory
- VC.Project.VCDebugSettings.DebuggerType
- VC.Project.IVCLocalDebugPageObject.GPUDebuggerTargetType
- VC.Project.IVCRemoteDebugPageObject.SQLDebugging
- VC.Project.IVCRemoteDebugPageObject.Remote
- VC.Project.IVCGPUDebugPageObject.CommandArguments
- VC.Project.VCDebugSettings.CommandArguments
- VC.Project.IVCClusterDebugPageObject.MPIRunWorkingDirectory
- VC.Project.IVCLocalDebugPageObject.SQLDebugging
- VC.Project.IVCWebSvcDebugPageObject.HttpUrl
- VC.Project.IVCLocalDebugPageObject.WorkingDirectory
- VC.Project.IVCLocalDebugPageObject.CommandArguments
- VC.Project.IVCClusterDebugPageObject.MPIRunCommand
- VC.Project.IVCGPUDebugPageObject.WorkingDirectory
- VC.Project.IVCWebSvcDebugPageObject.DebuggerType
- VC.Project.IVCRemoteDebugPageObject.CommandArguments
- VC.Project.IVCRemoteDebugPageObject.DebuggerType
- VC.Project.IVCLocalDebugPageObject.GPUBreakOnAllThreads
- VC.Project.IVCRemoteDebugPageObject.RemoteMachine
- VC.Project.IVCClusterDebugPageObject.MPIRunArguments
- VC.Project.IVCClusterDebugPageObject.MPIAcceptFilter
- VC.Project.IVCGPUDebugPageObject.RemoteConnection
- VC.Project.VCDebugSettings.PDBPath
- VC.Project.IVCRemoteDebugPageObject.DeploymentDirectory
- VC.Project.VCDebugSettings.SQLDebugging
- VC.Project.VCDebugSettings.RemoteCommand
- VC.Project.IVCClusterDebugPageObject.ShimCommand
- VC.Project.IVCLocalDebugPageObject.Command
- VC.Project.IVCRemoteDebugPageObject.GPUBreakOnAllThreads
- VC.Project.IVCLocalDebugPageObject.Attach
- VC.Project.VCDebugSettings.Command
- VC.Project.IVCRemoteDebugPageObject.GPUDebuggerTargetType
- VC.Project.IVCRemoteDebugPageObject.RemoteCommand
- VC.Project.IVCClusterDebugPageObject.ApplicationArguments
- VC.Project.IVCLocalDebugPageObject.Environment
- VC.Project.IVCGPUDebugPageObject.DeploymentDirectory
- VC.Project.IVCLocalDebugPageObject.EnvironmentMerge
- VC.Project.VCDebugSettings.Environment
- VC.Project.IVCGPUDebugPageObject.BreakpointBehavior
- VC.Project.IVCLocalDebugPageObject.DebuggerType
- VC.Project.VCDebugSettings.WebBrowser.WebBrowserDebuggerHttpUrl
- VC.Project.IVCWebSvcDebugPageObject.SQLDebugging
- VC.Project.IVCGPUDebugPageObject.AcceleratorType
- VC.Project.IVCGPUDebugPageObject.Environment
- VC.Project.VCDebugSettings.RemoteMachine
- VC.Project.IVCGPUDebugPageObject.AdditionalFilesToDeploy
- VC.Project.VCDebugSettings.WorkingDirectory
- vs.debug.builds
- VC.Project.VCDebugSettings.Attach
- VC.Project.VCDebugSettings.HttpUrl
- VC.Project.IVCClusterDebugPageObject.MPIAcceptMode
- VC.Project.IVCGPUDebugPageObject.Attach
- VC.Project.IVCRemoteDebugPageObject.AdditionalFiles
- VC.Project.IVCGPUDebugPageObject.Command
- VC.Project.VCDebugSettings.Remote
- VC.Project.IVCRemoteDebugPageObject.Attach
- VC.Project.VCDebugSettings.EnvironmentMerge
- VC.Project.IVCGPUDebugPageObject.MachineName
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- DEBUG linker option
- -PDB linker option
- -Zl compiler option [C++]
- /DEBUG linker option
- /PDBSTRIPPED linker option
- /MAPINFO linker option
- -Zd compiler option [C++]
- -DEBUG linker option
- MAPINFO linker option
- /ZI compiler option [C++]
- ZI compiler option [C++]
- Z7 compiler option [C++]
- debugging [C++], debugger settings
- project settings [Visual Studio], debug configurations
- mapfiles, project settings
- debug configurations, C++
- project settings [Visual Studio]
- /PDB linker option
- -PDBSTRIPPED linker option
- debug builds, project settings
- PDB linker option
- projects [Visual Studio], debug configurations
- project configurations, debug
- Zd compiler option [C++]
- MAP linker option
- /Z7 compiler option [C++]
- .pdb files, debug build project settings
- -MAP linker option
- -MAPINFO linker option
- /Zd compiler option [C++]
- PDBSTRIPPED linker option
- -Z7 compiler option [C++]
- pdb files, debug build project settings
- /MAP linker option
ms.assetid: 860c7f13-a108-4fe5-8fca-d235cd3ca1cb
caps.latest.revision: 52
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: ca9ff0678ba2c7abafa0d988efa09437ccd27dca
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "65687563"
---
# <a name="project-settings-for-a-c-debug-configuration"></a>Impostazioni di progetto per una configurazione di debug C++
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

È possibile modificare le impostazioni di progetto per una configurazione di debug C o Visual C++ nella finestra di dialogo **pagine delle proprietà** , come descritto in [procedura: impostare le configurazioni di debug e rilascio](../debugger/how-to-set-debug-and-release-configurations.md). Nelle tabelle riportate di seguito sono indicate le sezioni della finestra di dialogo **Pagine delle proprietà** in cui sono disponibili le impostazioni correlate al debugger.  
  
> [!WARNING]
> Le impostazioni del progetto di debug nella categoria **proprietà di configurazione/debug** per le applicazioni Windows Store e i componenti scritti in C++ sono diversi. Vedere [avviare una sessione di debug (VB, C#, C++ e XAML)](../debugger/start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md) nel centro per sviluppatori Windows.  
  
 Consente di specificare il debugger da utilizzare nella casella **di riepilogo Debugger da avviare** . Le proprietà visualizzate variano in funzione del debugger selezionato.  
  
 Ogni volta che si salva la soluzione, ciascuna impostazione delle proprietà di debug viene scritta e salvata automaticamente nel file della soluzione (vcxproj.user) specifico dell'utente.  
  
### <a name="configuration-properties-folder-debugging-category"></a>Cartella Proprietà di configurazione (categoria Debug)  
  
|**Impostazione**|**Descrizione**|  
|-----------------|---------------------|  
|**Debugger da avviare**|Specifica il debugger da eseguire. È possibile scegliere tra le seguenti opzioni:<br /><br /> -   **Debugger Windows locale**<br />-   **Debugger Windows remoto**<br />-   **Debugger del Web browser**<br />-   **Debugger servizi Web**|  
|**Comando** (debugger Windows locale)|Specifica il comando per l'avvio del programma di cui si esegue il debug nel computer locale.|  
|**Comando remoto** (debugger Windows remoto)|Percorso del file exe nel computer remoto. Immettere il percorso come se lo si immettesse nel computer remoto.|  
|**Argomenti del comando** (debugger Windows locale e debugger Windows remoto)|- Specifica gli argomenti relativi al comando specificato in precedenza.<br /><br /> In questa casella è possibile utilizzare i seguenti operatori di reindirizzamento:<br /><br /> < `file`<br /> Legge stdin dal file.<br /><br /> > `file`<br /> Scrive stdout nel file.<br /><br /> >> `file`<br /> Accoda stdout al file.<br /><br /> 2> `file`<br /> Scrive stderr nel file.<br /><br /> 2>> `file`<br /> Accoda stderr al file.<br /><br /> 2> &1<br /> Invia l'output di stderr (2) nello stesso percorso di stdout (1).<br /><br /> 1> &2<br /> Invia l'output di stdout (1) nello stesso percorso di stderr (2).<br /><br /> Nella maggior parte dei casi, questi operatori sono applicabili solo alle applicazioni console.|  
|**Directory di lavoro**|Specifica la cartella di lavoro del programma di cui viene eseguito il debug, relativamente alla directory di progetto in cui si trova il file EXE. Se non viene specificata, la cartella di lavoro corrisponde a quella del progetto. Per il debug remoto, la directory di progetto si troverà nel server remoto.|  
|**Connetti** (debugger Windows locale e debugger Windows remoto)|Specifica se avviare l'applicazione o se connettersi a essa. L'impostazione predefinita è No.|  
|**Nome server remoto** (debugger Windows remoto)|Specifica il nome di un computer (diverso dal computer in uso) nel quale si desidera eseguire il debug di un'applicazione.<br /><br /> La macro di compilazione RemoteMachine viene impostata sul valore di questa proprietà. Per ulteriori informazioni, vedere [macro per comandi e proprietà di compilazione](https://msdn.microsoft.com/library/239bd708-2ea9-4687-b264-043f1febf98b).|  
|**Connessione** (debugger Windows remoto)|Consente di passare tra tipi di connessione standard e senza autenticazione per il debug remoto. Specificare il nome di un computer remoto nella casella **Nome server remoto**. I tipi di connessione includono:<br /><br /> -   **Remoto con autenticazione di Windows**<br />-   **Remoto senza autenticazione (solo nativo)**<br /><br /> **Nota** Il debug remoto senza autenticazione può rendere vulnerabile il computer remoto alle violazioni della sicurezza. La modalità di autenticazione Windows garantisce un maggiore livello di sicurezza.<br /><br /> Per ulteriori informazioni, vedere [configurazione del debug remoto](../debugger/remote-debugging.md).|  
|**URL HTTP** (debugger servizi Web e debugger Web browser)|Specifica l'URL in cui si trova il progetto di cui si esegue il debug.|  
|**Tipo di debugger**|Specifica il tipo di debugger da usare: **Solo nativo**, **Solo gestito**, **Solo GPU**, **Misto**, **Automatico** (impostazione predefinita) o **Script**.<br /><br /> -   **Solo nativo** è destinato a codice C++ non gestito.<br />-   **Solo gestito** è destinato a codice eseguibile in Common Language Runtime (codice gestito).<br />-   **Misto** richiama debugger sia per codice gestito che per codice non gestito.<br />-   **Automatico** determina il tipo di debugger in base alle informazioni del compilatore e del file EXE.<br />-   **Script** richiama un debugger per gli script.<br />-   **Solo GPU** è destinato al codice AMP C++ eseguibile in un dispositivo GPU o nell'unità di rasterizzazione dei riferimenti DirectX. Vedere [debug del codice GPU](../debugger/debugging-gpu-code.md).|  
|**Ambiente** (debugger Windows locale)|Specifica le variabili di ambiente per il programma di cui si esegue il debug. Usare la sintassi delle variabili di ambiente standard (ad esempio, `PATH="%SystemRoot%\..."` ). Queste variabili eseguono l'override dell'ambiente di sistema oppure ne viene eseguito il merge con l'ambiente di sistema in base all'impostazione **Esegui merge ambiente**. Quando si fa clic nella colonna delle impostazioni, viene visualizzato "Modifica...". Fare clic su questo collegamento per modificare le variabili di ambiente.|  
|**Esegui merge ambiente** (debugger Windows locale)|Determina se verrà eseguito il merge delle variabili specificate nella casella **Ambiente** con l'ambiente definito dal sistema operativo. L'impostazione predefinita è Sì.|  
|**Debug SQL** (tutti ad eccezione del debugger cluster MPI)|Attiva il debug delle procedure SQL dall'applicazione [!INCLUDE[vcprvc](../includes/vcprvc-md.md)]. L'impostazione predefinita è No.|  
|**Tipo acceleratore debug** (solo debug GPU)|Specifica il dispositivo GPU da utilizzare per il debug. L'installazione dei driver per dispositivi GPU compatibili comporta l'aggiunta di altre opzioni. L'impostazione predefinita è "GPU - Emulatore software".|  
|**Comportamento punto di interruzione predefinito GPU** (solo debug GPU)|Specifica se un evento del punto di interruzione deve essere generato per ogni thread in una distorsione SIMD. L'impostazione predefinita consiste nel generare l'evento del punto di interruzione una volta sola per distorsione.|  
|**Acceleratore predefinito amp** (solo debug GPU)|Specifica il tasto di scelta rapida AMP predefinito quando si esegue il debug del codice GPU. Scegliere **Acceleratore software WARP** per determinare se un problema è causato dall'hardware o da un driver anziché dal codice.|  
|**Directory di distribuzione** (debugger Windows remoto)|Specifica il percorso nel computer remoto in cui l'output del progetto verrà copiato prima dell'avvio. Il percorso può essere una condivisione di rete nel computer remoto o un percorso a una cartella nel computer remoto. L'impostazione predefinita è vuota, ovvero l'output del progetto non viene copiato in una condivisione di rete. Per abilitare la distribuzione dei file, è inoltre necessario selezionare la casella di controllo **Distribuisci** nella finestra di dialogo Gestione configurazione. Per altre informazioni, vedere [procedura: creare e modificare le configurazioni](../ide/how-to-create-and-edit-configurations.md).|  
|**File aggiuntivi da distribuire** (debugger Windows remoto)|Se la proprietà della directory di distribuzione è impostata, è presente un elenco delimitato da punti e virgola di file aggiuntivi da copiare nella directory di distribuzione. L'impostazione predefinita è vuota, ovvero nessun altro file viene copiato nella directory di distribuzione. Per abilitare la distribuzione dei file, è inoltre necessario selezionare la casella di controllo **Distribuisci** nella finestra di dialogo Gestione configurazione. Per altre informazioni, vedere [procedura: creare e modificare le configurazioni](../ide/how-to-create-and-edit-configurations.md).|  
|**Distribuisci librerie di runtime di debug Visual C++** (debugger Windows remoto)|Se la proprietà Directory di distribuzione è impostata, specifica se le librerie di runtime di debug di Visual C++ per la piattaforma corrente devono essere copiate nella condivisione di rete. L'impostazione predefinita è Sì.|  
  
### <a name="cc-folder-general-category"></a>Cartella C/C++ (categoria Generale)  
  
|Impostazione|Descrizione|  
|-------------|-----------------|  
|**Formato informazioni di debug** ([/Z7, /Zd, Zi, /ZI](https://msdn.microsoft.com/library/ce9fa7e1-0c9b-47e3-98ea-26d1a16257c8))|Specifica il tipo di informazioni di debug da creare per il progetto.<br /><br /> In base all'opzione predefinita (/ZI), viene creato un database di programma (PDB) in un formato compatibile con la funzionalità Modifica e continuazione. Per ulteriori informazioni, vedere [/Z7,/ZD,/Zi,/Zi (formato informazioni di debug)](https://msdn.microsoft.com/library/ce9fa7e1-0c9b-47e3-98ea-26d1a16257c8).|  
  
### <a name="cc-folder-optimization-category"></a>Cartella C/C++ (categoria Ottimizzazione)  
  
|Impostazione|Descrizione|  
|-------------|-----------------|  
|**Ottimizzazione**|Specifica se il codice generato dal compilatore deve essere ottimizzato. Per effetto dell'ottimizzazione, il codice eseguito viene modificato. Poiché il codice ottimizzato non corrisponde più al codice sorgente, il debug risulterà più complesso.<br /><br /> L'opzione predefinita (**disabilitato (/0d**) impedisce l'ottimizzazione. È possibile disattivare l'ottimizzazione durante la fase di sviluppo e attivarla quando si crea la versione di produzione del codice.|  
  
### <a name="linker-folder-debugging-category"></a>Cartella Linker (categoria Debug)  
  
|Impostazione|Descrizione|  
|-------------|-----------------|  
|**Genera informazioni di debug** ([/DEBUG](https://msdn.microsoft.com/library/1af389ae-3f8b-4d76-a087-1cdf861e9103))|Comunica al linker di includere informazioni di debug con il formato specificato da /Z7, /Zd, Zi o /ZI.|  
|**Genera file del database di programma** ([/PDB:nome](https://msdn.microsoft.com/library/d23db0ce-10cb-427a-bc60-d6b2a852723d))|In questa casella specificare il nome di un file PDB. Selezionare ZI o /Zi per Formato informazioni di debug.|  
|**Rimuovi simboli privati** ([/PDBSTRIPPED:nome file](https://msdn.microsoft.com/library/9b9e0070-6a13-4142-8180-19c003fbbd55))|In questa casella specificare il nome di un file PDB, se non si desidera includere simboli privati nel file PDB. Questa opzione consente di creare un secondo file di database di programma (PDB) quando si compila l'immagine del programma con una qualsiasi delle opzioni del compilatore o del linker che generano un file PDB, ad esempio /DEBUG, /Z7, /Zd. Oppure /Zi. Il secondo file PDB omette i simboli che non si desidera fornire ai clienti. Per altre informazioni, vedere [/PDBSTRIPPED (Rimuove simboli privati)](https://msdn.microsoft.com/library/9b9e0070-6a13-4142-8180-19c003fbbd55).|  
|**Genera file di mapping** ([/MAP](https://msdn.microsoft.com/library/9ccce53d-4e36-43da-87b0-7603ddfdea63))|Comunica al linker di generare un file di mapping durante il collegamento. L'impostazione predefinita è No. Per altre informazioni, vedere [/MAP (Genera file Map)](https://msdn.microsoft.com/library/9ccce53d-4e36-43da-87b0-7603ddfdea63).|  
|**Nome file di mapping** ([/Map:](https://msdn.microsoft.com/library/9ccce53d-4e36-43da-87b0-7603ddfdea63)*nome*)|Se si sceglie Genera file di mapping, è possibile specificare il file di mapping in questa casella. Per altre informazioni, vedere [/MAP (Genera file Map)](https://msdn.microsoft.com/library/9ccce53d-4e36-43da-87b0-7603ddfdea63).|  
|**Esportazioni mapping** ([/MAPINFO:EXPORTS](https://msdn.microsoft.com/library/533d2bce-f9b7-4fea-ae1c-0b4864c9d10b))|Include le funzioni esportate nel file di mapping. L'impostazione predefinita è No. Per ulteriori informazioni, vedere [/MapInfo (include informazioni in file map)](https://msdn.microsoft.com/library/533d2bce-f9b7-4fea-ae1c-0b4864c9d10b).|  
|**Assembly Debuggable** ([/ASSEMBLYDEBUG](https://msdn.microsoft.com/library/533d2bce-f9b7-4fea-ae1c-0b4864c9d10b))|Specifica le impostazioni per l'opzione /ASSEMBLYDEBUG del linker. I possibili valori sono i seguenti:<br /><br /> -   **Nessun attributo Debuggable creato**.<br />-   **Controllo di runtime e ottimizzazioni disabilitate (/ASSEMBLYDEBUG)**. Impostazione predefinita.<br />-   **Nessun controllo di runtime e ottimizzazioni abilitate (/ASSEMBLYDEBUG:DISABLE)**.<br />-   **\<inherit from parent or project defaults>**.<br />- Per altre informazioni, vedere [/ASSEMBLYDEBUG (Aggiunge DebuggableAttribute)](https://msdn.microsoft.com/library/94443af3-470c-41d7-83a0-7434563d7982).|  
  
 Queste impostazioni possono essere modificate a livello di codice nella cartella Proprietà di configurazione (categoria Debug) mediante l'interfaccia Microsoft.VisualStudio.VCProjectEngine.VCDebugSettings. Per altre informazioni, vedere <xref:Microsoft.VisualStudio.VCProjectEngine.VCDebugSettings>.  
  
## <a name="see-also"></a>Vedere anche  
 [Debug del codice nativo](../debugger/debugging-native-code.md)   
 [Impostazioni e preparazione del debugger](../debugger/debugger-settings-and-preparation.md)   
 [Creazione e gestione di progetti Visual C++](https://msdn.microsoft.com/library/11003cd8-9046-4630-a189-a32bf3b88047)   
 [/ASSEMBLYDEBUG (aggiunge DebuggableAttribute)](https://msdn.microsoft.com/library/94443af3-470c-41d7-83a0-7434563d7982)   
 [Macro comuni per i comandi e le proprietà di compilazione](https://msdn.microsoft.com/library/239bd708-2ea9-4687-b264-043f1febf98b)
