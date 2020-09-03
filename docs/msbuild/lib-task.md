---
title: Attività LIB | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- VC.Project.VCLibrarianTool.Name
- VC.Project.VCLibrarianTool.TreatLibWarningsAsErrors
- VC.Project.VCLibrarianTool.Verbose
- vc.task.lib
- VC.Project.VCLibrarianTool.ErrorReporting
- VC.Project.VCLibrarianTool.LinkLibraryDependencies
- VC.Project.VCLibrarianTool.LinkTimeCodeGeneration
dev_langs:
- VB
- CSharp
- C++
- jsharp
- C++
helpviewer_keywords:
- MSBuild (C++), LIB task
- LIB task (MSBuild (C++))
ms.assetid: e062c7f9-cc69-4a83-9361-1bb5355e5fe8
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a5794d059a17f39531a7788895b604ae0e9590ce
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "77633590"
---
# <a name="lib-task"></a>LIB (attività)

Esegue il wrapping dello strumento di gestione librerie a 32 bit di Microsoft, *lib.exe*. Gestione librerie crea e gestisce una libreria di file oggetto COFF (Common Object File Format). Gestione librerie può inoltre creare file di esportazione e librerie di importazione per fare riferimento a definizioni esportate. Per ulteriori informazioni, vedere Guida di [riferimento a lib](/cpp/build/reference/lib-reference) ed [esecuzione di lib](/cpp/build/reference/running-lib).

## <a name="parameters"></a>Parametri

 La tabella seguente descrive i parametri dell'attività **LIB**. La maggior parte dei parametri attività corrisponde a un'opzione della riga di comando.

|Parametro|Descrizione|
|---------------|-----------------|
|**AdditionalDependencies**|Parametro **String []** facoltativo.<br /><br /> Specifica altri elementi da aggiungere alla riga di comando.|
|**AdditionalLibraryDirectories**|Parametro **String []** facoltativo.<br /><br /> Esegue l'override del percorso delle librerie dell'ambiente. Specificare un nome di directory.<br /><br /> Per altre informazioni, vedere [/LIBPATH (Percorso LIB aggiuntivo)](/cpp/build/reference/libpath-additional-libpath).|
|**AdditionalOptions**|Parametro **stringa** facoltativo.<br /><br /> Elenco di opzioni di *lib.exe* come specificato nella riga di comando. Ad esempio,/ \<option1>  / \<option2>  / \<option#> . Utilizzare questo parametro per specificare le opzioni di *lib.exe* che non sono rappresentate da altri parametri dell'attività **lib** .<br /><br /> Per altre informazioni, vedere [Esecuzione di LIB](/cpp/build/reference/running-lib).|
|**DisplayLibrary**|Parametro **stringa** facoltativo.<br /><br /> Visualizza le informazioni sulla libreria di output. Specificare un nome di file per reindirizzare le informazioni a un file. Specificare "CON" o niente per reindirizzare le informazioni alla console.<br /><br /> Questo parametro corrisponde all'opzione **/List** di *lib.exe*.|
|**Errorreporting-**|Parametro **stringa** facoltativo.<br /><br /> Specifica come inviare a Microsoft informazioni sull'errore interno se *lib.exe* non riesce in fase di esecuzione.<br /><br /> Specificare uno dei valori seguenti, ognuno dei quali corrisponde a un'opzione della riga di comando.<br /><br /> -   **NoErrorReport**  -  **/errorreport: nessuna**<br />-   **PromptImmediately**  -  **/errorreport: prompt**<br />-   **QueueForNextLogin**  -  **/errorreport: Queue**<br />-   **SendErrorReport**  -  **/errorreport: Send**<br /><br /> Per altre informazioni, vedere l'opzione della riga di comando **/ERRORREPORT** in [Esecuzione di LIB](/cpp/build/reference/running-lib).|
|**ExportNamedFunctions**|Parametro **String []** facoltativo.<br /><br /> Specifica una o più funzioni da esportare.<br /><br /> Questo parametro corrisponde all'opzione **/Export:** di *lib.exe*.|
|**ForceSymbolReferences**|Parametro **stringa** facoltativo.<br /><br /> Impone *lib.exe* includere un riferimento al simbolo specificato.<br /><br /> Questo parametro corrisponde all'opzione **/include:** di *lib.exe*.|
|**IgnoreAllDefaultLibraries**|Parametro `Boolean` facoltativo.<br /><br /> Se `true` , rimuove tutte le librerie predefinite dall'elenco di librerie che *lib.exe* cerca durante la risoluzione dei riferimenti esterni.<br /><br /> Questo parametro corrisponde al formato senza parametri dell'opzione **/NODEFAULTLIB** di *lib.exe*.|
|**IgnoreSpecificDefaultLibraries**|Parametro **String []** facoltativo.<br /><br /> Rimuove le librerie specificate dall'elenco di librerie che *lib.exe* cerca quando risolve i riferimenti esterni.<br /><br /> Questo parametro corrisponde all'opzione **/NODEFAULTLIB** di *lib.exe* che accetta un `library` argomento.|
|**LinkLibraryDependencies**|Parametro `Boolean` facoltativo.<br /><br /> Se `true`, specifica che gli output della libreria dalle dipendenze del progetto vengono collegati automaticamente.|
|**LinkTimeCodeGeneration**|Parametro `Boolean` facoltativo.<br /><br /> Se `true`, specifica la generazione del codice in fase di collegamento.<br /><br /> Questo parametro corrisponde all'opzione **/LCTG** di *lib.exe*.|
|**MinimumRequiredVersion**|Parametro **stringa** facoltativo.<br /><br /> Specifica la versione minima richiesta del sottosistema. Specificare un elenco delimitato da virgole di numeri decimali nell'intervallo compreso tra 0 e 65535.|
|**ModuleDefinitionFile**|Parametro **stringa** facoltativo.<br /><br /> Specifica il nome del file di definizione moduli (con*estensione def*).<br /><br /> Questo parametro corrisponde all'opzione **/def** di *lib.exe* che accetta un `filename` argomento.|
|**Name**|Parametro **stringa** facoltativo.<br /><br /> Quando si compila una libreria di importazione, è necessario specificare il nome della DLL per la quale compilare la libreria di importazione.<br /><br /> Questo parametro corrisponde all'opzione **/Name** di *lib.exe* che accetta un `filename` argomento.|
|**OutputFile**|Parametro **stringa** facoltativo.<br /><br /> Esegue l'override del nome e del percorso predefiniti del programma creato da *lib.exe* .<br /><br /> Questo parametro corrisponde all'opzione **/out** di *lib.exe* che accetta un `filename` argomento.|
|**RemoveObjects**|Parametro **String []** facoltativo.<br /><br /> Omette l'oggetto specificato dalla libreria di output. *Lib.exe* crea una libreria di output combinando tutti gli oggetti (in file oggetto o in librerie) e quindi eliminando tutti gli oggetti specificati da questa opzione.<br /><br /> Questo parametro corrisponde all'opzione **/Remove** di *lib.exe* che accetta un `membername` argomento.|
|**recenti**|Parametro `ITaskItem[]` obbligatorio.<br /><br /> Specifica un elenco dei file di origine separati da spazi.|
|**Sottosistema**|Parametro **stringa** facoltativo.<br /><br /> Specifica l'ambiente per il file eseguibile. La scelta del sottosistema riguarda il simbolo del punto di ingresso o la funzione di punto di ingresso.<br /><br /> Specificare uno dei valori seguenti, ognuno dei quali corrisponde a un'opzione della riga di comando.<br /><br /> -   **Console**  -  di **/SUBSYSTEM: console**<br />-   **Windows**  -  **/SUBSYSTEM: Windows**<br />-   **Nativo**  -  **/SUBSYSTEM: nativo**<br />-   **Applicazione EFI**  -  **/SUBSYSTEM: EFI_APPLICATION**<br />-   Driver del servizio di **avvio EFI**  -  **/SUBSYSTEM: EFI_BOOT_SERVICE_DRIVER**<br />-   **ROM EFI**  -  **/SUBSYSTEM: EFI_ROM**<br />-   **Runtime EFI**  -  **/SUBSYSTEM: EFI_RUNTIME_DRIVER**<br />-   **Windows**  -  **/SUBSYSTEM: WindowsCE**<br />-   **POSIX**  -  **/SUBSYSTEM: POSIX**<br /><br /> Per altre informazioni, vedere [/SUBSYSTEM (Specifica il sottosistema)](/cpp/build/reference/subsystem-specify-subsystem).|
|**SuppressStartupBanner**|Parametro **booleano** facoltativo.<br /><br /> Se `true`, impedisce la visualizzazione del messaggio sul copyright e sul numero di versione all'avvio dell'attività.<br /><br /> Per altre informazioni, vedere l'opzione **/NOLOGO** in [Esecuzione di LIB](/cpp/build/reference/running-lib).|
|**TargetMachine**|Parametro **stringa** facoltativo.<br /><br /> Specifica la piattaforma di destinazione per il programma o DLL.<br /><br /> Specificare uno dei valori seguenti, ognuno dei quali corrisponde a un'opzione della riga di comando.<br /><br /> -   **MachineARM**  -  **/Machine: ARM**<br />-   **MachineEBC**  -  **/Machine: EBC**<br />-   **MachineIA64**  -  **/Machine: ia64**<br />-   **MachineMIPS**  -  **/Machine: MIPS**<br />-   **MachineMIPS16**  -  **/Machine: MIPS16**<br />-   **MachineMIPSFPU**  - **/Machine: MIPSFPU**<br />-   **MachineMIPSFPU16**  -  **/Machine: MIPSFPU16**<br />-   **MachineSH4**  -  **/Machine: SH4**<br />-   **MachineTHUMB**  -  **/Machine: Thumb**<br />-   **MachineX64**  -  **/Machine: x64**<br />-   **MachineX86**  -  **/Machine: x86**<br /><br /> Per ulteriori informazioni, vedere [/Machine (specifica la piattaforma di destinazione)](/cpp/build/reference/machine-specify-target-platform).|
|**TrackerLogDirectory**|Parametro **stringa** facoltativo.<br /><br /> Specifica la directory del log di Tracker.|
|**TreatLibWarningAsErrors**|Parametro **booleano** facoltativo.<br /><br /> Se `true` , fa in modo che l'attività **lib** non generi un file di output se *lib.exe* genera un avviso. Se `false`, viene generato un file di output.<br /><br /> Per altre informazioni, vedere l'opzione **/WX** in [Esecuzione di LIB](/cpp/build/reference/running-lib).|
|**UseUnicodeResponseFiles**|Parametro **booleano** facoltativo.<br /><br /> Se `true`, consente al sistema di progetto di generare file di risposta UNICODE quando viene generata la Gestione di librerie. Specificare `true` quando i percorsi dei file nel progetto sono UNICODE.|
|**Verbose**|Parametro **booleano** facoltativo.<br /><br /> Se `true` , Visualizza i dettagli sullo stato di avanzamento della sessione, inclusi i nomi dei file con *estensione obj* da aggiungere. Le informazioni vengono inviate all'output standard e possono essere reindirizzate a un file.<br /><br /> Per altre informazioni, vedere l'opzione **/VERBOSE** in [Esecuzione di LIB](/cpp/build/reference/running-lib).|

## <a name="see-also"></a>Vedere anche

- [Informazioni di riferimento sulle attività](../msbuild/msbuild-task-reference.md)