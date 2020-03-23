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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/18/2020
ms.locfileid: "77633590"
---
# <a name="lib-task"></a>LIB (attività)

Esegue il wrapping dello strumento Gestione librerie a 32 bit di Microsoft, *lib.exe*. Gestione librerie crea e gestisce una libreria di file oggetto COFF (Common Object File Format). Gestione librerie può inoltre creare file di esportazione e librerie di importazione per fare riferimento a definizioni esportate. Per ulteriori informazioni, vedere [Riferimento a LIB](/cpp/build/reference/lib-reference) ed Esecuzione di [LIB](/cpp/build/reference/running-lib).

## <a name="parameters"></a>Parametri

 La tabella seguente descrive i parametri dell'attività **LIB**. La maggior parte dei parametri attività corrisponde a un'opzione della riga di comando.

|Parametro|Descrizione|
|---------------|-----------------|
|**AdditionalDependencies**|Parametro **String[]** facoltativo.<br /><br /> Specifica altri elementi da aggiungere alla riga di comando.|
|**AdditionalLibraryDirectories**|Parametro **String[]** facoltativo.<br /><br /> Esegue l'override del percorso delle librerie dell'ambiente. Specificare un nome di directory.<br /><br /> Per altre informazioni, vedere [/LIBPATH (Percorso LIB aggiuntivo)](/cpp/build/reference/libpath-additional-libpath).|
|**AdditionalOptions**|Parametro **String** facoltativo.<br /><br /> Un elenco di opzioni di *lib.exe* come specificato nella riga di comando. Ad esempio, /\<opzione1> /\<opzione2> /\<opzione#>. Utilizzare questo parametro per specificare le opzioni *lib.exe* che non sono rappresentate da altri parametri dell'attività **LIB.**<br /><br /> Per altre informazioni, vedere [Esecuzione di LIB](/cpp/build/reference/running-lib).|
|**DisplayLibrary**|Parametro **String** facoltativo.<br /><br /> Visualizza le informazioni sulla libreria di output. Specificare un nome di file per reindirizzare le informazioni a un file. Specificare "CON" o niente per reindirizzare le informazioni alla console.<br /><br /> Questo parametro corrisponde all'opzione **/LIST** di *lib.exe*.|
|**Segnalazione errori**|Parametro **String** facoltativo.<br /><br /> Specifica come inviare informazioni sugli errori interni a Microsoft se *lib.exe* ha esito negativo in fase di esecuzione.<br /><br /> Specificare uno dei valori seguenti, ognuno dei quali corrisponde a un'opzione della riga di comando.<br /><br /> -   **NoErrorReport** - **/ERRORREPORT:NESSUNO**<br />-   **PromptImmediately** - **/ERRORREPORT:PROMPT**<br />-   **QueueForNextLogin** - **/ERRORREPORT:QUEUE**<br />-   **SendErrorReport** - **/ERRORREPORT:SEND**<br /><br /> Per altre informazioni, vedere l'opzione della riga di comando **/ERRORREPORT** in [Esecuzione di LIB](/cpp/build/reference/running-lib).|
|**ExportNamedFunctions**|Parametro **String[]** facoltativo.<br /><br /> Specifica una o più funzioni da esportare.<br /><br /> Questo parametro corrisponde all'opzione **/EXPORT:** di *lib.exe*.|
|**ForceSymbolReferences**|Parametro **String** facoltativo.<br /><br /> Impone a *lib.exe di* includere un riferimento al simbolo specificato.<br /><br /> Questo parametro corrisponde all'opzione **/INCLUDE:** di *lib.exe*.|
|**IgnoreAllDefaultLibraries**|Parametro `Boolean` facoltativo.<br /><br /> Se `true`, rimuove tutte le librerie predefinite dall'elenco delle librerie che *lib.exe* cerca quando risolve i riferimenti esterni.<br /><br /> Questo parametro corrisponde al formato senza parametri dell'opzione **/NODEFAULTLIB** di *lib.exe*.|
|**IgnoreSpecificDefaultLibraries**|Parametro **String[]** facoltativo.<br /><br /> Rimuove le librerie specificate dall'elenco di librerie che *lib.exe* cerca quando risolve i riferimenti esterni.<br /><br /> Questo parametro corrisponde all'opzione **/NODEFAULTLIB** di `library` *lib.exe* che accetta un argomento.|
|**LinkLibraryDependencies**|Parametro `Boolean` facoltativo.<br /><br /> Se `true`, specifica che gli output della libreria dalle dipendenze del progetto vengono collegati automaticamente.|
|**LinkTimeCodeGeneration**|Parametro `Boolean` facoltativo.<br /><br /> Se `true`, specifica la generazione del codice in fase di collegamento.<br /><br /> Questo parametro corrisponde all'opzione **/LCTG** di *lib.exe*.|
|**MinimumRequiredVersion**|Parametro **String** facoltativo.<br /><br /> Specifica la versione minima richiesta del sottosistema. Specificare un elenco delimitato da virgole di numeri decimali nell'intervallo compreso tra 0 e 65535.|
|**ModuleDefinitionFile**|Parametro **String** facoltativo.<br /><br /> Specifica il nome del file di definizione del modulo (*def*).<br /><br /> Questo parametro corrisponde all'opzione **/DEF** di `filename` *lib.exe* che accetta un argomento.|
|**Nome**|Parametro **String** facoltativo.<br /><br /> Quando si compila una libreria di importazione, è necessario specificare il nome della DLL per la quale compilare la libreria di importazione.<br /><br /> Questo parametro corrisponde all'opzione **/NAME** di `filename` *lib.exe* che accetta un argomento.|
|**Outputfile**|Parametro **String** facoltativo.<br /><br /> Sostituisce il nome e il percorso predefiniti del programma creato da *lib.exe.*<br /><br /> Questo parametro corrisponde all'opzione **/OUT** di `filename` *lib.exe* che accetta un argomento.|
|**RemoveObjects**|Parametro **String[]** facoltativo.<br /><br /> Omette l'oggetto specificato dalla libreria di output. *Lib.exe* crea una libreria di output combinando tutti gli oggetti (sia in file oggetto che in librerie) e quindi eliminando tutti gli oggetti specificati da questa opzione.<br /><br /> Questo parametro corrisponde all'opzione **/REMOVE** di `membername` *lib.exe* che accetta un argomento.|
|**recenti**|Parametro `ITaskItem[]` obbligatorio.<br /><br /> Specifica un elenco dei file di origine separati da spazi.|
|**Sottosistema**|Parametro **String** facoltativo.<br /><br /> Specifica l'ambiente per il file eseguibile. La scelta del sottosistema riguarda il simbolo del punto di ingresso o la funzione di punto di ingresso.<br /><br /> Specificare uno dei valori seguenti, ognuno dei quali corrisponde a un'opzione della riga di comando.<br /><br /> -   **Console** - **/SUBSYSTEM:CONSOLE**<br />-   **Windows** - **/SUBSYSTEM:WINDOWS**<br />-   **Nativo** - **/SUBSYSTEM:NATIVE**<br />-   **Applicazione EFI** - **/SUBSYSTEM:EFI_APPLICATION**<br />-   **Driver del servizio di avvio EFI** - **/SUBSYSTEM:EFI_BOOT_SERVICE_DRIVER**<br />-   **EFI ROM** - **/SUBSYSTEM:EFI_ROM**<br />-   **Runtime EFI** - **/SUBSYSTEM:EFI_RUNTIME_DRIVER**<br />-   **WindowsCE** - **/SUBSYSTEM:WINDOWSCE (informazioni in inglese)**<br />-   **POSIX** - **/SOTTOSISTEMA:POSIX**<br /><br /> Per altre informazioni, vedere [/SUBSYSTEM (Specifica il sottosistema)](/cpp/build/reference/subsystem-specify-subsystem).|
|**SuppressStartupBanner**|Parametro **booleano** facoltativo.<br /><br /> Se `true`, impedisce la visualizzazione del messaggio sul copyright e sul numero di versione all'avvio dell'attività.<br /><br /> Per altre informazioni, vedere l'opzione **/NOLOGO** in [Esecuzione di LIB](/cpp/build/reference/running-lib).|
|**TargetMachine**|Parametro **String** facoltativo.<br /><br /> Specifica la piattaforma di destinazione per il programma o DLL.<br /><br /> Specificare uno dei valori seguenti, ognuno dei quali corrisponde a un'opzione della riga di comando.<br /><br /> -   **MachineARM** - **/MACHINE:ARM**<br />-   **MachineEBC** - **/MACHINE:EBC**<br />-   **MachineIA64** - **/MACHINE:IA64**<br />-   **MachineMIPS** - **/MACHINE:MIPS**<br />-   **MachineMIPS16** - **/MACHINE:MIPS16**<br />-   **MachineMIPSFPU** -**/MACHINE:MIPSFPU**<br />-   **MachineMIPSFPU16** - **/MACHINE:MIPSFPU16**<br />-   **MachineSH4** - **/MACHINE:SH4 (informazioni in** inglese)<br />-   **MACHINETHUMB** - **/MACHINE:THUMB**<br />-   **MachineX64** - **/MACHINE:X64 (in inglese)**<br />-   **MachineX86** - **/MACHINE:X86**<br /><br /> Per ulteriori informazioni, vedere [/MACHINE (Specificare](/cpp/build/reference/machine-specify-target-platform)la piattaforma di destinazione) .|
|**TrackerLogDirectory**|Parametro **String** facoltativo.<br /><br /> Specifica la directory del log di Tracker.|
|**TreatLibWarningAsErrors**|Parametro **booleano** facoltativo.<br /><br /> Se `true`, fa sì che l'attività **LIB** non generi un file di output se *lib.exe* genera un avviso. Se `false`, viene generato un file di output.<br /><br /> Per altre informazioni, vedere l'opzione **/WX** in [Esecuzione di LIB](/cpp/build/reference/running-lib).|
|**UseUnicodeResponseFiles**|Parametro **booleano** facoltativo.<br /><br /> Se `true`, consente al sistema di progetto di generare file di risposta UNICODE quando viene generata la Gestione di librerie. Specificare `true` quando i percorsi dei file nel progetto sono UNICODE.|
|**Dettagliato**|Parametro **booleano** facoltativo.<br /><br /> Se `true`, visualizza i dettagli sullo stato di avanzamento della sessione; inclusi i nomi dei file *obj* aggiunti. Le informazioni vengono inviate all'output standard e possono essere reindirizzate a un file.<br /><br /> Per altre informazioni, vedere l'opzione **/VERBOSE** in [Esecuzione di LIB](/cpp/build/reference/running-lib).|

## <a name="see-also"></a>Vedere anche

- [Riferimento alle attività](../msbuild/msbuild-task-reference.md)