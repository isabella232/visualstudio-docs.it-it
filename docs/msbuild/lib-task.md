---
title: Attività LIB | Microsoft Docs
description: Informazioni su MSBuild'attività LIB per eseguire il wrapping dello strumento gestione librerie di Microsoft a 32 bit, lib.exe, che crea e gestisce una libreria di file oggetto COFF.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: 8b0f7f475b8226630133fa6c4617c7c3c4fe8060
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122143170"
---
# <a name="lib-task"></a>LIB (attività)

Esegue il wrapping dello strumento Gestione librerie microsoft a 32 bit, *lib.exe*. Gestione librerie crea e gestisce una libreria di file oggetto COFF (Common Object File Format). Gestione librerie può inoltre creare file di esportazione e librerie di importazione per fare riferimento a definizioni esportate. Per altre informazioni, vedere Informazioni [di riferimento su LIB e](/cpp/build/reference/lib-reference) Esecuzione di [LIB.](/cpp/build/reference/running-lib)

## <a name="parameters"></a>Parametri

 La tabella seguente descrive i parametri dell'attività **LIB**. La maggior parte dei parametri attività corrisponde a un'opzione della riga di comando.

|Parametro|Descrizione|
|---------------|-----------------|
|**AdditionalDependencies**|Parametro **String[]** facoltativo.<br /><br /> Specifica altri elementi da aggiungere alla riga di comando.|
|**AdditionalLibraryDirectories**|Parametro **String[]** facoltativo.<br /><br /> Esegue l'override del percorso delle librerie dell'ambiente. Specificare un nome di directory.<br /><br /> Per altre informazioni, vedere [/LIBPATH (Percorso LIB aggiuntivo)](/cpp/build/reference/libpath-additional-libpath).|
|**Opzioni aggiuntive**|Parametro **String** facoltativo.<br /><br /> Elenco di opzioni *lib.exe* specificate nella riga di comando. Ad esempio, / \<option1>  / \<option2>  / \<option#> . Usare questo parametro per specificare *lib.exe* opzioni che non sono rappresentate da altri parametri **dell'attività LIB.**<br /><br /> Per altre informazioni, vedere [Esecuzione di LIB](/cpp/build/reference/running-lib).|
|**DisplayLibrary**|Parametro **String** facoltativo.<br /><br /> Visualizza le informazioni sulla libreria di output. Specificare un nome di file per reindirizzare le informazioni a un file. Specificare "CON" o niente per reindirizzare le informazioni alla console.<br /><br /> Questo parametro corrisponde **all'opzione /LIST** *dilib.exe*.|
|**Segnalazione errori**|Parametro **String** facoltativo.<br /><br /> Specifica come inviare informazioni sugli errori interni a Microsoft se *lib.exe* ha esito negativo in fase di esecuzione.<br /><br /> Specificare uno dei valori seguenti, ognuno dei quali corrisponde a un'opzione della riga di comando.<br /><br /> -   **NoErrorReport**  -  **/ERRORREPORT:NONE**<br />-   **PromptImmediately**  -  **/ERRORREPORT:PROMPT**<br />-   **QueueForNextLogin**  -  **/ERRORREPORT:QUEUE**<br />-   **SendErrorReport**  -  **/ERRORREPORT:SEND**<br /><br /> Per altre informazioni, vedere l'opzione della riga di comando **/ERRORREPORT** in [Esecuzione di LIB](/cpp/build/reference/running-lib).|
|**ExportNamedFunctions**|Parametro **String[]** facoltativo.<br /><br /> Specifica una o più funzioni da esportare.<br /><br /> Questo parametro corrisponde **all'opzione /EXPORT:** *dilib.exe*.|
|**ForceSymbolReferences**|Parametro **String** facoltativo.<br /><br /> Forza *lib.exe* includere un riferimento al simbolo specificato.<br /><br /> Questo parametro corrisponde **all'opzione /INCLUDE:** *dilib.exe*.|
|**IgnoreAllDefaultLibraries**|Parametro `Boolean` facoltativo.<br /><br /> Se `true` , rimuove tutte le librerie  predefinite dall'elenco di librerie chelib.execerca quando risolve i riferimenti esterni.<br /><br /> Questo parametro corrisponde al formato senza parametri **dell'opzione /NODEFAULTLIB** *dilib.exe*.|
|**IgnoreSpecificDefaultLibraries**|Parametro **String[]** facoltativo.<br /><br /> Rimuove le librerie specificate dall'elenco di librerie in *cui* lib.execerca quando risolve i riferimenti esterni.<br /><br /> Questo parametro corrisponde **all'opzione /NODEFAULTLIB** *lib.exe* che accetta un `library` argomento .|
|**LinkLibraryDependencies**|Parametro `Boolean` facoltativo.<br /><br /> Se `true`, specifica che gli output della libreria dalle dipendenze del progetto vengono collegati automaticamente.|
|**LinkTimeCodeGeneration**|Parametro `Boolean` facoltativo.<br /><br /> Se `true`, specifica la generazione del codice in fase di collegamento.<br /><br /> Questo parametro corrisponde **all'opzione /LCTG** *dilib.exe*.|
|**MinimumRequiredVersion**|Parametro **String** facoltativo.<br /><br /> Specifica la versione minima richiesta del sottosistema. Specificare un elenco delimitato da virgole di numeri decimali nell'intervallo compreso tra 0 e 65535.|
|**ModuleDefinitionFile**|Parametro **String** facoltativo.<br /><br /> Specifica il nome del file di definizione del modulo (*def*).<br /><br /> Questo parametro corrisponde **all'opzione /DEF** *dilib.exe* che accetta un argomento `filename` .|
|**Nome**|Parametro **String** facoltativo.<br /><br /> Quando si compila una libreria di importazione, è necessario specificare il nome della DLL per la quale compilare la libreria di importazione.<br /><br /> Questo parametro corrisponde **all'opzione /NAME** *dilib.exe* che accetta un argomento `filename` .|
|**Outputfile**|Parametro **String** facoltativo.<br /><br /> Esegue l'override del nome e del percorso predefiniti del *programmalib.exe* creato.<br /><br /> Questo parametro corrisponde **all'opzione /OUT** *dilib.exe* che accetta un argomento `filename` .|
|**RemoveObjects**|Parametro **String[]** facoltativo.<br /><br /> Omette l'oggetto specificato dalla libreria di output. *Lib.exe* crea una libreria di output combinando tutti gli oggetti (in file oggetto o librerie) e quindi eliminando tutti gli oggetti specificati da questa opzione.<br /><br /> Questo parametro corrisponde **all'opzione /REMOVE** *lib.exe* che accetta un `membername` argomento .|
|**recenti**|Parametro `ITaskItem[]` obbligatorio.<br /><br /> Specifica un elenco dei file di origine separati da spazi.|
|**Sottosistema**|Parametro **String** facoltativo.<br /><br /> Specifica l'ambiente per il file eseguibile. La scelta del sottosistema riguarda il simbolo del punto di ingresso o la funzione di punto di ingresso.<br /><br /> Specificare uno dei valori seguenti, ognuno dei quali corrisponde a un'opzione della riga di comando.<br /><br /> -   **Console**  -  **/SUBSYSTEM:CONSOLE**<br />-   **Windows**  -  **/SUBSYSTEM:WINDOWS**<br />-   **Nativo**  -  **/SUBSYSTEM:NATIVE**<br />-   **Applicazione EFI**  -  **/SUBSYSTEM:EFI_APPLICATION**<br />-   Driver del **servizio di avvio EFI**  -  **/SUBSYSTEM:EFI_BOOT_SERVICE_DRIVER**<br />-   ROM EFI   -  **/SUBSYSTEM:EFI_ROM**<br />-   **Runtime EFI**  -  **/SUBSYSTEM:EFI_RUNTIME_DRIVER**<br />-   **WindowsCE**  -  **/SUBSYSTEM:WINDOWSCE**<br />-   **POSIX**  -  **/SUBSYSTEM:POSIX**<br /><br /> Per altre informazioni, vedere [/SUBSYSTEM (Specifica il sottosistema)](/cpp/build/reference/subsystem-specify-subsystem).|
|**SuppressStartupBanner**|Parametro **booleano** facoltativo.<br /><br /> Se `true`, impedisce la visualizzazione del messaggio sul copyright e sul numero di versione all'avvio dell'attività.<br /><br /> Per altre informazioni, vedere l'opzione **/NOLOGO** in [Esecuzione di LIB](/cpp/build/reference/running-lib).|
|**TargetMachine**|Parametro **String** facoltativo.<br /><br /> Specifica la piattaforma di destinazione per il programma o DLL.<br /><br /> Specificare uno dei valori seguenti, ognuno dei quali corrisponde a un'opzione della riga di comando.<br /><br /> -   **MachineARM**  -  **/MACHINE:ARM**<br />-   **MachineEBC**  -  **/MACHINE:EBC**<br />-   **MachineIA64**  -  **/MACHINE:IA64**<br />-   **MachineMIPS**  -  **/MACHINE:MIPS**<br />-   **MachineMIPS16**  -  **/MACHINE:MIPS16**<br />-   **MachineMIPSFPU**  - **/MACHINE:MIPSFPU**<br />-   **MachineMIPSFPU16**  -  **/MACHINE:MIPSFPU16**<br />-   **MachineSH4**  -  **/MACHINE:SH4**<br />-   **MachineTHUMB**  -  **/MACHINE:THUMB**<br />-   **MachineX64**  -  **/MACHINE:X64**<br />-   **MachineX86**  -  **/MACHINE:X86**<br /><br /> Per altre informazioni, vedere [/MACHINE (Specifica piattaforma di destinazione)](/cpp/build/reference/machine-specify-target-platform).|
|**TrackerLogDirectory**|Parametro **String** facoltativo.<br /><br /> Specifica la directory del log di Tracker.|
|**TreatLibWarningAsErrors**|Parametro **booleano** facoltativo.<br /><br /> Se `true` , **l'attività LIB** non genera un file di output *selib.exe* genera un avviso. Se `false`, viene generato un file di output.<br /><br /> Per altre informazioni, vedere l'opzione **/WX** in [Esecuzione di LIB](/cpp/build/reference/running-lib).|
|**UseUnicodeResponseFiles**|Parametro **booleano** facoltativo.<br /><br /> Se `true`, consente al sistema di progetto di generare file di risposta UNICODE quando viene generata la Gestione di librerie. Specificare `true` quando i percorsi dei file nel progetto sono UNICODE.|
|**Verbose**|Parametro **booleano** facoltativo.<br /><br /> Se , visualizza i dettagli sullo stato della sessione, inclusi i nomi dei file `true` *obj* aggiunti. Le informazioni vengono inviate all'output standard e possono essere reindirizzate a un file.<br /><br /> Per altre informazioni, vedere l'opzione **/VERBOSE** in [Esecuzione di LIB](/cpp/build/reference/running-lib).|

## <a name="see-also"></a>Vedi anche

- [Informazioni di riferimento sulle attività](../msbuild/msbuild-task-reference.md)