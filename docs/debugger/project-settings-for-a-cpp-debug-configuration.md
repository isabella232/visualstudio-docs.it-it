---
title: Impostazioni di progetto per una configurazione di debug C++
ms.custom: seodec18
ms.date: 11/26/2018
ms.technology: vs-ide-debug
ms.topic: reference
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
- CSharp
- VB
- FSharp
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- cplusplus
ms.openlocfilehash: 951b46bfc6ef0910731dfe76cc9913f2c4a423ad
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 12/07/2018
ms.locfileid: "53066901"
---
# <a name="project-settings-for-a-c-debug-configuration"></a>Impostazioni di progetto per una configurazione di debug C++
È possibile modificare le impostazioni di progetto per una configurazione di debug C o Visual C++ nel **pagine delle proprietà** finestra di dialogo, come descritto in [come: impostazione del debug e rilascio delle configurazioni](../debugger/how-to-set-debug-and-release-configurations.md). Nelle tabelle riportate di seguito sono indicate le sezioni della finestra di dialogo **Pagine delle proprietà** in cui sono disponibili le impostazioni correlate al debugger.  
  
> [!NOTE]
>  Le impostazioni di progetto di debug nel **proprietà configurazione/Debug** categoria sono diversi per le app UWP e per i componenti scritti in C++. Visualizzare [avviare una sessione di debug (Visual Basic, C#, C++ e XAML)](../debugger/start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md).  
  
 Ogni impostazione di proprietà di debug viene automaticamente scritto e salvato nel file "per utente" (. vcxproj) per la soluzione quando si salva la soluzione.  

 Specificare il debugger da usare nel **Debugger da avviare** casella di riepilogo, come descritto nella tabella seguente. Le proprietà visualizzate variano in funzione del debugger selezionato.  
    
## <a name="configuration-properties-folder-debugging-category"></a>Cartella Proprietà di configurazione (categoria Debug)  
  
| **Impostazione** | **Descrizione** |
| - | - |
| **Debugger da avviare** | Specifica il debugger da eseguire. È possibile scegliere tra le seguenti opzioni:<br /><br /> -   **Debugger Windows locale**<br />-   **Debugger Windows remoto**<br />-   **Debugger del Web browser**<br />-   **Debugger servizi Web** |
| **Comando** (debugger Windows locale) | Specifica il comando per l'avvio del programma di cui si esegue il debug nel computer locale. |
| **Comando remoto** (debugger Windows remoto) | Percorso del file exe nel computer remoto. Immettere il percorso come se lo si immettesse nel computer remoto. |
| **Argomenti del comando** (Debugger Windows locale)<br /><br /> **Argomenti del comando remoto** (Debugger Windows remoto) | - Specifica gli argomenti relativi al comando specificato in precedenza.<br /><br /> In questa casella è possibile utilizzare i seguenti operatori di reindirizzamento:<br /><br /> < `file`<br /> Legge stdin dal file.<br /><br /> > `file`<br /> Scrive stdout nel file.<br /><br /> >> `file`<br /> Accoda stdout al file.<br /><br /> 2> `file`<br /> Scrive stderr nel file.<br /><br /> 2>> `file`<br /> Accoda stderr al file.<br /><br /> 2> &1<br /> Invia l'output di stderr (2) nello stesso percorso di stdout (1).<br /><br /> 1> &2<br /> Invia l'output di stdout (1) nello stesso percorso di stderr (2).<br /><br /> Nella maggior parte dei casi, questi operatori sono applicabili solo alle applicazioni console. |
| **Directory di lavoro** | Specifica la cartella di lavoro del programma di cui viene eseguito il debug, relativamente alla directory di progetto in cui si trova il file EXE. Se non viene specificata, la cartella di lavoro corrisponde a quella del progetto. Per eseguire il debug remoto, la directory del progetto è nel server remoto. |
| **Connetti** (debugger Windows locale e debugger Windows remoto) | Specifica se avviare l'applicazione o se connettersi a essa. L'impostazione predefinita è No. |
| **Nome server remoto** (debugger Windows remoto) | Specifica il nome di un computer (diverso dal computer in uso) nel quale si desidera eseguire il debug di un'applicazione.<br /><br /> La macro di compilazione RemoteMachine viene impostata sul valore di questa proprietà. Per altre informazioni, vedere [Macro per comandi e proprietà di compilazione](/cpp/ide/common-macros-for-build-commands-and-properties). |
| **Connessione** (debugger Windows remoto) | Consente di passare tra tipi di connessione standard e senza autenticazione per il debug remoto. Specificare il nome di un computer remoto nella casella **Nome server remoto**. I tipi di connessione includono:<br /><br /> -   **Remoto con autenticazione di Windows**<br />-   **Remoto senza autenticazione**<br /><br /> **Nota** Il debug remoto senza autenticazione può rendere vulnerabile il computer remoto alle violazioni della sicurezza. La modalità di autenticazione Windows garantisce un maggiore livello di sicurezza.<br /><br /> Per altre informazioni, vedere [Configurazione del debug remoto](../debugger/remote-debugging.md). |
| **URL HTTP** (debugger servizi Web e debugger Web browser) | Specifica l'URL in cui si trova il progetto di cui si esegue il debug. |
| **Tipo di debugger** | Specifica il tipo di debugger da usare: **Solo nativo**, **solo gestito**, **solo GPU**, **Mixed**, **automatico** (impostazione predefinita), o **Script**.<br /><br /> -   **Solo nativo** è destinato a codice C++ non gestito.<br />-   **Solo gestito** è destinato a codice eseguibile in Common Language Runtime (codice gestito).<br />-   **Misto** richiama debugger sia per codice gestito che per codice non gestito.<br />-   **Automatico** determina il tipo di debugger in base alle informazioni del compilatore e del file EXE.<br />-   **Script** richiama un debugger per gli script.<br />-   **Solo GPU** è destinato al codice AMP C++ eseguibile in un dispositivo GPU o nell'unità di rasterizzazione dei riferimenti DirectX. Visualizzare [codice debug GPU](../debugger/debugging-gpu-code.md). |
| **Ambiente** (Debugger Windows locale e Debugger Windows remoto) | Specifica le variabili di ambiente per il programma di cui si esegue il debug. Usare la sintassi di variabili di ambiente standard (ad esempio, `PATH="%SystemRoot%\..."`). Queste variabili eseguono l'override dell'ambiente di sistema oppure ne viene eseguito il merge con l'ambiente di sistema in base all'impostazione **Esegui merge ambiente**. Quando fa clic su nella colonna impostazioni, un "modifica..." viene visualizzato. Selezionare questo collegamento per modificare le variabili di ambiente. |
| **Esegui merge ambiente** (debugger Windows locale) | Determina se verrà eseguito il merge delle variabili specificate nella casella **Ambiente** con l'ambiente definito dal sistema operativo. L'impostazione predefinita è Sì. |
| **Debug SQL** (tutti ad eccezione del debugger cluster MPI) | Attiva il debug delle procedure SQL dall'applicazione [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)]. L'impostazione predefinita è No. |
| **Tipo acceleratore debug** (solo debug GPU) | Specifica il dispositivo GPU da utilizzare per il debug. L'installazione dei driver per dispositivi GPU compatibili comporta l'aggiunta di altre opzioni. L'impostazione predefinita è **GPU - Emulatore software**. |
| **Comportamento punto di interruzione predefinito GPU** (solo debug GPU) | Specifica se un evento del punto di interruzione deve essere generato per ogni thread in una distorsione SIMD. L'impostazione predefinita consiste nel generare l'evento del punto di interruzione una volta sola per distorsione. |
| **Tasto di scelta rapida predefinito AMP** | Specifica il tasto di scelta rapida AMP predefinito quando si esegue il debug del codice GPU. Scegliere **Acceleratore software WARP** per determinare se un problema è causato dall'hardware o da un driver anziché dal codice. |
| **Directory di distribuzione** (debugger Windows remoto) | Specifica il percorso nel computer remoto in cui l'output del progetto verrà copiato prima dell'avvio. Il percorso può essere una condivisione di rete nel computer remoto o un percorso a una cartella nel computer remoto. L'impostazione predefinita è vuota, ovvero l'output del progetto non viene copiato in una condivisione di rete. Per abilitare la distribuzione dei file, è inoltre necessario selezionare la casella di controllo **Distribuisci** nella finestra di dialogo Gestione configurazione. Per altre informazioni, vedere [Procedura: Creare e modificare le configurazioni](../ide/how-to-create-and-edit-configurations.md). |
| **File aggiuntivi da distribuire** (debugger Windows remoto) | Se la Directory di distribuzione è impostata, questo è un elenco delimitato da punto e virgola di altri file da copiare nella directory di distribuzione. L'impostazione predefinita è vuota, ovvero nessun altro file viene copiato nella directory di distribuzione. Per abilitare la distribuzione dei file, è inoltre necessario selezionare la casella di controllo **Distribuisci** nella finestra di dialogo Gestione configurazione. Per altre informazioni, vedere [Procedura: Creare e modificare le configurazioni](../ide/how-to-create-and-edit-configurations.md). |
| **Distribuisci librerie di runtime di debug Visual C++** (debugger Windows remoto) | Se la proprietà Directory di distribuzione è impostata, specifica se le librerie di runtime di debug di Visual C++ per la piattaforma corrente devono essere copiate nella condivisione di rete. L'impostazione predefinita è Sì. |
  
## <a name="cc-folder-general-category"></a>Cartella C/C++ (categoria Generale)  
  
|Impostazione|Description|  
|-------------|-----------------|  
|**Formato informazioni di debug** ([/Z7, /Zd, Zi, /ZI](/cpp/build/reference/z7-zi-zi-debug-information-format))|Specifica il tipo di informazioni di debug da creare per il progetto.<br /><br /> In base all'opzione predefinita (/ZI), viene creato un database di programma (PDB) in un formato compatibile con la funzionalità Modifica e continuazione. Per altre informazioni, vedere [/Z7, /Zd, /Zi, /ZI (Formato informazioni di debug)](/cpp/build/reference/z7-zi-zi-debug-information-format).|  
  
## <a name="cc-folder-optimization-category"></a>Cartella C/C++ (categoria Ottimizzazione)  
  
|Impostazione|Description|  
|-------------|-----------------|  
|**Optimization**|Specifica se il codice generato dal compilatore deve essere ottimizzato. Per effetto dell'ottimizzazione, il codice eseguito viene modificato. Codice ottimizzato non corrisponde più al codice sorgente, che rende più difficile il debug.<br /><br /> In base all'opzione predefinita (**Disabilitato (/0d)**), l'ottimizzazione non viene eseguita. È possibile disattivare l'ottimizzazione durante la fase di sviluppo e attivarla quando si crea la versione di produzione del codice.|  
  
## <a name="linker-folder-debugging-category"></a>Cartella Linker (categoria Debug)  
  
|Impostazione|Description|  
|-------------|-----------------|  
|**Genera informazioni di debug** ([/DEBUG](/cpp/build/reference/debug-generate-debug-info))|Comunica al linker di includere informazioni di debug con il formato specificato da [/Z7, /Zd, Zi, or /ZI](/cpp/build/reference/z7-zi-zi-debug-information-format).|  
|**Genera file del database di programma** ([/PDB:nome](/cpp/build/reference/pdb-use-program-database))|Specificare il nome di un programma (PDB) del file di database in questa casella. Selezionare ZI o /Zi per Formato informazioni di debug.|  
|**Rimuovi simboli privati** ([/PDBSTRIPPED:nome file](/cpp/build/reference/pdbstripped-strip-private-symbols))|In questa casella specificare il nome di un file PDB, se non si desidera includere simboli privati nel file PDB. Questa opzione Crea un secondo file PDB quando si compila l'immagine del programma con qualsiasi del compilatore o del linker opzioni che generano un file PDB, ad esempio /DEBUG, / Z7, /Zd. Oppure /Zi. Il secondo file PDB omette i simboli che non si desidera fornire ai clienti. Per altre informazioni, vedere [/PDBSTRIPPED (rimuove simboli privati)](/cpp/build/reference/pdbstripped-strip-private-symbols).|  
|**Genera file di mapping** ([/MAP](/cpp/build/reference/map-generate-mapfile))|Comunica al linker di generare un file di mapping durante il collegamento. L'impostazione predefinita è No. Per altre informazioni, vedere [/MAP (Genera file Map)](/cpp/build/reference/map-generate-mapfile).|  
|**Nome File di mapping** ([/Map:](/cpp/build/reference/map-generate-mapfile)*nome*)|Se si sceglie Genera file di mapping, è possibile specificare il file di mapping in questa casella. Per altre informazioni, vedere [/MAP (Genera file Map)](/cpp/build/reference/map-generate-mapfile).|  
|**Esportazioni mapping** ([/MAPINFO:EXPORTS](/cpp/build/reference/mapinfo-include-information-in-mapfile))|Include le funzioni esportate nel file di mapping. L'impostazione predefinita è No. Per altre informazioni, vedere [/MAPINFO (Include informazioni in file MAP)](/cpp/build/reference/mapinfo-include-information-in-mapfile).|  
|**Assembly Debuggable** ([/ASSEMBLYDEBUG](/cpp/build/reference/mapinfo-include-information-in-mapfile))|Specifica le impostazioni per l'opzione /ASSEMBLYDEBUG del linker. I possibili valori sono:<br /><br /> -   **Nessun attributo Debuggable creato**.<br />-   **Controllo di runtime e ottimizzazioni disabilitate (/ASSEMBLYDEBUG)**. Impostazione predefinita.<br />-   **Nessun controllo di runtime e ottimizzazioni abilitate (/ASSEMBLYDEBUG:DISABLE)**.<br />-   **\<eredita da padre o da impostazioni predefinite progetto>**.<br />- Per altre informazioni, vedere [/ASSEMBLYDEBUG (Aggiunge DebuggableAttribute)](/cpp/build/reference/assemblydebug-add-debuggableattribute).|  
  
 Queste impostazioni possono essere modificate a livello di codice nella cartella Proprietà di configurazione (categoria Debug) mediante l'interfaccia Microsoft.VisualStudio.VCProjectEngine.VCDebugSettings. Per ulteriori informazioni, vedere <xref:Microsoft.VisualStudio.VCProjectEngine.VCDebugSettings>.

## <a name="other-project-settings"></a>Altre impostazioni del progetto

Per eseguire il debug di tipi di progetto, ad esempio le librerie statiche e DLL, il progetto di Visual Studio deve essere in grado di trovare i file corretti. Quando il codice sorgente è disponibile, è possibile aggiungere le librerie statiche e DLL come progetti separati per la stessa soluzione, per semplificare il debug. Per informazioni sulla creazione di questi tipi di progetto, vedere [creazione e uso di una libreria a collegamento dinamico (DLL)](/cpp/build/walkthrough-creating-and-using-a-dynamic-link-library-cpp) e [creazione di una libreria statica tramite](/cpp/windows/walkthrough-creating-and-using-a-static-library-cpp). Con il codice sorgente è disponibile, è anche possibile creare un nuovo progetto di Visual Studio, scegliendo **File** > **New** > **progetto da codice esistente**.

Per eseguire il debug di DLL esterne al progetto, vedere [progetti di DLL di debug](../debugger/debugging-dll-projects.md#vxtskdebuggingdllprojectsexternal). Se è necessario eseguire il debug proprio progetto DLL, ma non hanno accesso al progetto per l'applicazione chiamante, vedere [come eseguire il debug da un progetto DLL](../debugger/how-to-debug-from-a-dll-project.md).
  
## <a name="see-also"></a>Vedere anche  
 [Debug del codice nativo](../debugger/debugging-native-code.md)   
 [Impostazioni del debugger e preparazione](../debugger/debugger-settings-and-preparation.md)   
 [Creare e gestire i progetti Visual C++](/cpp/ide/creating-and-managing-visual-cpp-projects)   
 [/ASSEMBLYDEBUG (aggiunge DebuggableAttribute)](/cpp/build/reference/assemblydebug-add-debuggableattribute)   
 [Macro comuni per i comandi e le proprietà di compilazione](/cpp/ide/common-macros-for-build-commands-and-properties)