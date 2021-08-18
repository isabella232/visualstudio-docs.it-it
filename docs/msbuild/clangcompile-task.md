---
title: Attività ClangCompile | Microsoft Docs
description: Descrive lo scopo e i parametri dell'MSBuild ClangCompile, che esegue il wrapping dello strumento del compilatore C++, clang.exe.
ms.custom: SEO-VS-2020
ms.date: 03/10/2019
ms.topic: reference
f1_keywords:
- vc.task.clangcompile
dev_langs:
- VB
- CSharp
- C++
- jsharp
- C++
helpviewer_keywords:
- MSBuild (C++), ClangCompile task
- ClangCompile task (MSBuild (C++))
author: corob-msft
ms.author: corob
ms.workload:
- multiple
ms.openlocfilehash: f4bc40eccaea9420bc61ccb95edf72322636e012fda03f5cd1592ebd88979f9a
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121428601"
---
# <a name="clangcompile-task"></a>Attività ClangCompile

Esegue il wrapping dello strumento del compilatore Microsoft C++, clang.exe.

## <a name="parameters"></a>Parametri

Nella tabella seguente vengono descritti i parametri dell'attività **ClangCompile**.

|Parametro|Descrizione|
|---------------|-----------------|
|**AdditionalIncludeDirectories**|Parametro **string[]** facoltativo.<br/><br/>Specifica una o più directory da aggiungere al percorso di inclusione. Usare il punto e virgola (;) come delimitatore per più percorsi.<br/><br/>Usare `-I[path]`.|
|**Opzioni aggiuntive**|Parametro **stringa facoltativo.**|
|**BufferSecurityCheck**|Parametro **stringa facoltativo.**<br/><br/>Il controllo di sicurezza facilita il rilevamento di sovraccarichi del buffer di stack, un attacco comunemente tentato alla sicurezza di un programma. <br/><br/>Usare `fstack-protector`.|
|**BuildingInIde**|Parametro **bool** facoltativo.|
|**CLanguageStandard**|Parametro **stringa facoltativo.**<br/><br/>Determina lo standard del linguaggio C.<br/><br/>Usare `std=[value]` con il valore **c89**, **c99**, **c11**, **gnu99** o **gnu11**.|
|**ClangVersion**|Parametro **stringa facoltativo.**|
|**CompileAs**|Parametro **stringa facoltativo.**<br/><br/>Specifica il linguaggio di compilazione per i file con estensione c e cpp. Il valore predefinito verrà rilevato in base all'estensione c o cpp.<br/><br/>Usare `-x c`, `-x c++`.|
|**CppLanguageStandard**|Parametro **stringa facoltativo.**<br/><br/>Determina lo standard del linguaggio C++.<br/><br/>Usare `std=[value]` con il valore **c++98**, **c++11**, **c++1y**, **gnu++98**, **gnu++11** o **gnu++1y**.|
|**DataLevelLinking**|Parametro **bool** facoltativo.<br/><br/>Consente alle ottimizzazioni del linker di rimuovere i dati non usati creando ogni elemento dati in una sezione distinta.|
|**DebugInformationFormat**|Parametro **stringa facoltativo.**<br/><br/>Specifica il tipo di informazioni di debug generate dal compilatore.<br/><br/>**None**: non produce informazioni di debug, quindi la compilazione può risultare più veloce (usare `g0`).<br/>**FullDebug**: genera le informazioni di debug DWARF2 (usare `g2 -gdwarf-2`).<br/>**LineNumber**: genera solo le informazioni sul numero di riga (usare `gline-tables-only`).|
|**EnableNeonCodegen**|Parametro **bool** facoltativo.<br/><br/>Abilita la generazione di codice per hardware per operazioni con virgola mobile NEON. Si applica solo per l'architettura ARM.|
|**ExceptionHandling**|Parametro **stringa facoltativo.**<br/><br/>Specifica il modello di gestione delle eccezioni che deve essere usato dal compilatore.<br/><br/>**Disabled**: disabilita la gestione delle eccezioni (usare `fno-exceptions`).<br/>**Enabled**: abilita la gestione delle eccezioni (usare `fexceptions`).<br/>**UnwindTables**: genera gli eventuali dati statici necessari senza influire sul codice generato (usare `funwind-tables`).|
|**FloatABI**|Parametro **stringa facoltativo.**<br/><br/>Opzione da selezionare per scegliere l'ABI a virgola mobile.<br/><br/>Con **soft** il compilatore genera output contenente chiamate di libreria per operazioni a virgola mobile (usare `mfloat-abi=soft`).<br/>**softfp** consente la generazione di codice con istruzioni a virgola mobile hardware, ma vengono comunque usate le convenzioni di chiamata soft-float (usare `mfloat-abi=softfp`).<br/>**hard** consente la generazione di istruzioni a virgola mobile e usa le convenzioni di chiamata specifiche di FPU (usare `mfloat-abi=hard`).|
|**ForcedIncludeFiles**|Parametro **string[]** facoltativo.<br/><br/>Uno o più file di inclusione il cui uso è forzato.<br/><br/>Usare `-include [name]`.|
|**FunctionLevelLinking**|Parametro **bool** facoltativo.<br/><br/>Consente al compilatore di assemblare le singole funzioni sotto forma di funzioni incluse nel pacchetto (COMDAT). Impostazione necessaria per le operazioni di modifica e continuazione.<br/><br/>Usare `ffunction-sections`.|
|**GccToolChain**|Parametro **stringa facoltativo.**<br/><br/>Percorso della cartella della catena di strumenti GCC.|
|**GNUMode**|Parametro **bool** facoltativo.<br/><br/>|
|**MSCompatibility**|Parametro **bool** facoltativo.<br/><br/>Abilitare la compatibilità completa con Microsoft C++.|
|**MSCompatibilityVersion**|Parametro **stringa facoltativo.**<br/><br/>Valore delimitato da punti che rappresenta il numero di versione del compilatore Microsoft da restituire in _MSC_VER (0 = non definito; impostazione predefinita).|
|**MSExtensions**|Parametro **bool** facoltativo.<br/><br/>Accetta alcuni costrutti non standard supportati dal compilatore Microsoft.|
|**MSCompilerVersion**|Parametro **stringa facoltativo.**<br/><br/>Numero di versione del compilatore Microsoft da restituire in _MSC_VER (0 = non definito; impostazione predefinita).|
|**MSVCErrorReport**|Parametro **bool** facoltativo.<br/><br/>Segnala gli errori che Visual Studio può usare per analizzare e ottenere informazioni su file e riga.|
|**ObjectFileName**|Parametro **stringa facoltativo.**<br/><br/>Consente di specificare un nome usato per eseguire l'override del nome del file oggetto predefinito. Può essere un nome di file o di directory.<br/><br/>Usare `/Fo[name]`.|
|**OmitFramePointers**|Parametro **bool** facoltativo.<br/><br/>Disabilita la creazione di puntatori ai frame nello stack di chiamate.|
|**Ottimizzazione**|Parametro **stringa facoltativo.**<br/><br/>Specifica il livello di ottimizzazione per l'applicazione.<br/><br/>**Custom**: consente di personalizzare l'ottimizzazione.<br/>**Disabled**: disabilita l'ottimizzazione (usare `O0`).<br/>**MinSize**: ottimizza in base alla dimensione (usare `Os`).<br/>**MaxSpeed**: ottimizza in base alla velocità (usare `O2`).<br/>**Full**: ottimizzazioni onerose (usare `O3`).|
|**PositionIndependentCode**|Parametro **bool** facoltativo.<br/><br/>Genera codice indipendente dalla posizione per l'uso in una libreria condivisa.|
|**PrecompiledHeader**|Parametro **stringa facoltativo.**<br/><br/>Abilita la creazione o l'uso di un'intestazione precompilata durante la compilazione.|
|**PrecompiledHeaderFile**|Parametro **stringa facoltativo.**<br/><br/>Specifica un nome di file di intestazione da usare come file di intestazione precompilato. Questo file verrà aggiunto anche ai file di **inclusione forzati durante** la compilazione.|
|**PrecompiledHeaderOutputFileDirectory**|Parametro **stringa facoltativo.**<br/><br/>Specifica la directory per l'intestazione precompilato generato. Questa directory verrà aggiunta anche a Directory **di inclusione aggiuntive durante** la compilazione.|
|**PrecompiledHeaderCompileAs**|Parametro **stringa facoltativo.**<br/><br/>Selezionare l'opzione del linguaggio di compilazione per il file di intestazione precompilato.<br/><br/>Usare `-x c-header`, `-x c++-header`.|
|**PreprocessorDefinitions**|Parametro **string[]** facoltativo.<br/><br/>Definisce i simboli di pre-elaborazione per il file di origine.<br/><br/>Usare `-D`.|
|**RuntimeLibrary**|Parametro **stringa facoltativo.**<br/><br/>Specifica la libreria di runtime per il collegamento.<br/><br/>Usare le opzioni `MSVC /MT`, `/MTd`, `/MD`, `/MDd`.<br/><br/>**MultiThreaded** fa in modo che l'applicazione usi la versione statica multithread della libreria di runtime.<br/>**MultiThreadedDebug** definisce _DEBUG e _MT. Fa inoltre in modo che il compilatore inserisca il nome della libreria LIBCMTD.lib nel file .obj affinché il linker utilizzi LIBCMTD.lib per risolvere i simboli esterni.<br/>**MultiThreadedDLL** fa in modo che l'applicazione usi la versione specifica per multithread e DLL della libreria di runtime. Definisce _MT e _DLL e fa inoltre in modo che il compilatore inserisca il nome della libreria MSVCRT.lib nel file con estensione obj.<br/>**MultiThreadedDebugDLL** definisce _DEBUG, _MT e _DLL e fa in modo che l'applicazione usi la versione specifica per multithread e DLL di debug della libreria di runtime. Fa inoltre in modo che il compilatore inserisca il nome della libreria MSVCRTD.lib nel file .obj.|
|**RuntimeTypeInfo**|Parametro **bool** facoltativo.<br/><br/>Aggiunge codice per il controllo dei tipi di oggetto C++ in fase di esecuzione (informazioni sui tipi in fase di esecuzione).<br/><br/>Usare `frtti`, `fno-rtti`.|
|**ShowIncludes**|Parametro **bool** facoltativo.<br/><br/>Indica al compilatore di generare un elenco dei file di inclusione.<br/><br/>Usare `-H`.|
|**recenti**|Parametro **ITaskItem[]** obbligatorio.|
|**StrictAliasing**|Parametro **bool** facoltativo.<br/><br/>Presuppone le regole di aliasing più restrittive. Un oggetto di un certo tipo non potrà mai risiedere nello stesso indirizzo di un oggetto di un tipo diverso.|
|**Sysroot**|Parametro **stringa facoltativo.**<br/><br/>Percorso della cartella della directory radice per intestazioni e librerie.|
|**TargetArch**|Parametro **stringa facoltativo.**<br/><br/>Architettura di destinazione.|
|**ThumbMode**|Parametro **stringa facoltativo.**<br/><br/>Generare il codice che viene eseguito per la microarchitettura thumb. Si applica solo per l'architettura ARM.<br/><br/>**Thumb**, genera codice Thumb (usare `mthumb`).<br/>**ARM**, genera codice Arm (usare `marm`).<br/>**Disabled**, opzione non applicabile per la piattaforma selezionata.|
|**TrackerLogDirectory**|Parametro **stringa facoltativo.**<br/><br/>Directory dei log di Tracker.|
|**TreatWarningAsError**|Parametro **bool** facoltativo.<br/><br/>Considera tutti gli avvisi del compilatore come errori.<br/><br/>Per un nuovo progetto, potrebbe essere preferibile usare `/WX` in tutte le compilazioni. La risoluzione degli avvisi garantirà il minor numero possibile di errori del codice di difficile individuazione.|
|**UndefinePreprocessorDefinitions**|Parametro **string[]** facoltativo.<br/><br/>Rimuove una o più definizioni per il preprocessore.<br/><br/>Usare `-U [macro]`.|
|**UndefineAllPreprocessorDefinitions**|Parametro **bool** facoltativo.<br/><br/>Rimuove tutti i valori precedentemente definiti per il preprocessore.<br/><br/>Usare `-undef`.|
|**UseMultiToolTask**|Parametro **bool** facoltativo.<br/><br/>Compilazione a più processori.|
|**UseShortEnums**|Parametro **bool** facoltativo.<br/><br/>Il tipo enum usa solo il numero di byte richiesti dall'insieme di possibili valori di input.|
|**Verbose**|Parametro **bool** facoltativo.<br/><br/>Visualizza i comandi da eseguire e usa l'output dettagliato.|
|**WarningLevel**|Parametro **stringa facoltativo.**<br/><br/>Specifica il grado di severità del controllo effettuato dal compilatore per trovare gli errori del codice. Altri flag devono essere aggiunti direttamente a **Opzioni aggiuntive** (se `/w` , `/Weverything` ).<br/><br/>**TurnOffAllWarnings**, disabilita tutti gli avvisi del compilatore (usare `w`).<br/>**EnableAllWarnings**, abilita tutti gli avvisi, inclusi quelli disabilitati per impostazione predefinita (usare `Wall`).|

## <a name="see-also"></a>Vedi anche

[Informazioni di riferimento sulle attività](../msbuild/msbuild-task-reference.md)
