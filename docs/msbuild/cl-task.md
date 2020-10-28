---
title: Attività CL | Microsoft Docs
description: Vengono descritti lo scopo e i parametri dell'attività CL di MSBuild, che esegue il wrapping dello strumento compilatore Microsoft C++ cl.exe.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- VC.Project.VCCLCompilerTool.UseUnicodeForAssemblerListing
- vc.task.cl
- VC.Project.VCCLCompilerTool.TreatSpecificWarningsAsErrors
- VC.Project.VCCLCompilerTool.CreateHotpatchableImage
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild (C++), CL task
- CL task (MSBuild (C++))
ms.assetid: 651ba971-b755-4f03-a549-4816beb3cc0d
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7d930ed8d918a08503a6eaa6b60848abeec7683a
ms.sourcegitcommit: bd9417123c6ef67aa2215307ba5eeec511e43e02
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/28/2020
ms.locfileid: "92796836"
---
# <a name="cl-task"></a>attività CL

Esegue il wrapping dello strumento compilatore Microsoft C++ *cl.exe* . Il compilatore produce file eseguibili (con *estensione exe* ), file di libreria a collegamento dinamico (con estensione *dll* ) o file di modulo di codice (con *estensione netmodule* ). Per ulteriori informazioni, vedere [Opzioni del compilatore](/cpp/build/reference/compiler-options) e [utilizzare MSBuild dalla riga di comando](/cpp/build/msbuild-visual-cpp) e [utilizzare il set di strumenti di Microsoft C++ dalla riga di comando](/cpp/build/building-on-the-command-line).

## <a name="parameters"></a>Parametri

 Nell'elenco che segue vengono descritti i parametri dell'attività **CL** . La maggior parte dei parametri di attività e alcuni set di parametri corrispondono a un'opzione della riga di comando.

- **AdditionalIncludeDirectories**

   Parametro String[] facoltativo.

   Aggiunge una directory all'elenco delle directory in cui vengono cercati i file di inclusione.

   Per ulteriori informazioni, vedere [/i (directory di inclusione aggiuntive)](/cpp/build/reference/i-additional-include-directories).

- **AdditionalOptions**

   Parametro String facoltativo.

   Elenco di opzioni della riga di comando. Ad esempio, "/ \<option1>  / \<option2>  / \<option#> ". Usare questo parametro per specificare le opzioni della riga di comando che non sono rappresentate da altri parametri dell'attività.

   Per ulteriori informazioni, vedere [Opzioni del compilatore](/cpp/build/reference/compiler-options).

- **AdditionalUsingDirectories**

   Parametro String[] facoltativo.

   Specifica una directory in cui il compilatore effettuerà la ricerca per risolvere i riferimenti di file passati alla direttiva **#using** .

   Per ulteriori informazioni, vedere [/ai (specifica directory dei metadati)](/cpp/build/reference/ai-specify-metadata-directories).

- **AlwaysAppend**

   Parametro String facoltativo.

   Stringa che viene sempre generata sulla riga di comando. Il valore predefinito è " **/c** ".

- **AssemblerListingLocation**

   Crea un file di elenco che contiene il codice assembly.

   Per ulteriori informazioni, vedere l'opzione **/fa** in [/fa,/fa (file di listato)](/cpp/build/reference/fa-fa-listing-file).

- **AssemblerOutput**

   Parametro String facoltativo.

   Crea un file di elenco che contiene il codice assembly.

   Specificare uno dei valori seguenti, ognuno dei quali corrisponde a un'opzione della riga di comando.

  - **Nolisting** - *\<none>*

  - **AssemblyCode**  -  **/Fa**

  - **AssemblyAndMachineCode**  -  **/Fac**

  - **AssemblyAndSourceCode**  -  **/FAS**

  - **Tutto**  -  **/FACS**

    Per ulteriori informazioni, vedere le opzioni **/fa** , **/fac** , **/FAS** e **/FACS** in [/fa,/fa (file di listato)](/cpp/build/reference/fa-fa-listing-file).

- **BasicRuntimeChecks**

   Parametro String facoltativo.

   Abilita e disabilita la funzionalità di controllo degli errori di run-time, con il pragma [runtime_checks](/cpp/preprocessor/runtime-checks).

   Specificare uno dei valori seguenti, ognuno dei quali corrisponde a un'opzione della riga di comando.

  - **Predefinita** -                          *\<none>*

  - **StackFrameRuntimeCheck**  -  **/RTCs**

  - **UninitializedLocalUsageCheck**  -  **/RTCu**

  - **EnableFastChecks**  -                           **/RTC1**

    Per ulteriori informazioni, vedere [/RTC (controlli degli errori di run-time)](/cpp/build/reference/rtc-run-time-error-checks).

- **BrowseInformation**

   Parametro booleano facoltativo.

   Se `true`, crea un file di informazioni di visualizzazione.

   Per ulteriori informazioni, vedere l'opzione **/fr** in [/fr,/fr (Crea file SBR)](/cpp/build/reference/fr-fr-create-dot-sbr-file).

- **BrowseInformationFile**

   Parametro String facoltativo.

   Specifica un nome di file per il file di informazioni di visualizzazione.

   Per ulteriori informazioni, vedere il parametro **BrowseInformation** in questa tabella e vedere anche [/fr,/fr (Crea file SBR)](/cpp/build/reference/fr-fr-create-dot-sbr-file).

- **BufferSecurityCheck**

   Parametro booleano facoltativo.

   Se `true`, rileva alcuni sovraccarichi del buffer che sovrascrivono l'indirizzo del mittente, una tecnica comune per sfruttare il codice che non applica restrizioni per le dimensioni del buffer.

   Per altre informazioni, vedere [/GS (Controllo sicurezza buffer)](/cpp/build/reference/gs-buffer-security-check).

- **BuildingInIDE**

   Parametro booleano facoltativo.

   Se `true`, indica che **MSBuild** viene richiamato dall'IDE. In caso contrario, **MSBuild** viene richiamato sulla riga di comando.

- **CallingConvention**

   Parametro String facoltativo.

   Specifica la convenzione di chiamata, che determina l'ordine in cui gli argomenti della funzione vengono inseriti nello stack, se la funzione chiamante o la funzione chiamata rimuove gli argomenti dallo stack alla fine della chiamata e la convenzione di decorazione dei nomi che il compilatore usa per identificare le singole funzioni.

   Specificare uno dei valori seguenti, ognuno dei quali corrisponde a un'opzione della riga di comando.

  - **Cdecl**  -  **/GD**

  - **Fastcall**  -                           **/Gr**

  - **Stdcall**  -                           **/GZ**

    Per ulteriori informazioni, vedere [/GD,/gr,/Gv,/gz (convenzione di chiamata)](/cpp/build/reference/gd-gr-gv-gz-calling-convention).

- **CompileAs**

   Parametro String facoltativo.

   Specifica se compilare il file di input come file di origine C o C++.

   Specificare uno dei valori seguenti, ognuno dei quali corrisponde a un'opzione della riga di comando.

  - **Predefinita** - *\<none>*

  - **CompileAsC**  -  **/TC**

  - **CompileAsCpp**  -  **/TP**

    Per ulteriori informazioni, vedere [/TC,/TP,/TC,/TP (specifica il tipo di file di origine)](/cpp/build/reference/tc-tp-tc-tp-specify-source-file-type).

- **CompileAsManaged**

   Parametro String facoltativo.

   Consente alle applicazioni e ai componenti di usare le funzionalità di Common Language Runtime (CLR).

   Specificare uno dei valori seguenti, ognuno dei quali corrisponde a un'opzione della riga di comando.

  - **false** - *\<none>*

  - valore **true**  -  **/CLR**

  - **Pure**  -  **/CLR: pure**

  - **Sicurezza**  -  **/CLR: safe**

  - **OldSyntax**  -  **/CLR: oldSyntax**

    Per altre informazioni, vedere [/clr (Compilazione Common Language Runtime)](/cpp/build/reference/clr-common-language-runtime-compilation).

- **CreateHotpatchableImage**

   Parametro booleano facoltativo.

   Se `true`, indica al compilatore di preparare un'immagine per *l'applicazione di una patch a caldo* . Questo parametro assicura che la prima istruzione di ogni funzione sia di due byte, condizione necessaria per l'applicazione di una patch a caldo.

   Per ulteriori informazioni, vedere [/hotpatch (Crea immagine Hotpatchable)](/cpp/build/reference/hotpatch-create-hotpatchable-image).

- **DebugInformationFormat**

   Parametro String facoltativo.

   Consente di selezionare il tipo di informazioni di debug create per il programma e se tali informazioni vengono mantenute in file oggetto ( *obj* ) o in un database di programma (PDB).

   Specificare uno dei valori seguenti, ognuno dei quali corrisponde a un'opzione della riga di comando.

  - **Oldstyle**  -  **/Z7**

  - **ProgramDatabase**  -  **/Zi**

  - **EDITANDCONTINUE**  -  **/Zi**

    Per ulteriori informazioni, vedere [/Z7,/Zi,/Zi (formato informazioni di debug)](/cpp/build/reference/z7-zi-zi-debug-information-format).

- **DisableLanguageExtensions**

   Parametro booleano facoltativo.

   Se **true** , indica al compilatore di generare un errore per i costrutti di linguaggio che non sono compatibili con ANSI C o ANSI C++.

   Per ulteriori informazioni, vedere l'opzione **/za** in [/za,/ze (Disable Language Extensions)](/cpp/build/reference/za-ze-disable-language-extensions).

- **DisableSpecificWarnings**

   Parametro String[] facoltativo.

   Disabilita i numeri di avviso specificati in un elenco delimitato da punti e virgola.

   Per ulteriori informazioni, vedere l' `/wd` opzione in [/W,/W0,/W1,/W2,/W3,/W4,/W1,/W2,/W3,/W4,/Wall,/WD.,/we,/wo,/WV,/WX (livello di avviso)](/cpp/build/reference/compiler-option-warning-level).

- **EnableEnhancedInstructionSet**

   Parametro String facoltativo.

   Specifica l'architettura per la generazione di codice che usa le istruzioni Streaming SIMD Extensions (SSE) e Streaming SIMD Extensions 2 (SSE2).

   Specificare uno dei valori seguenti, ognuno dei quali corrisponde a un'opzione della riga di comando.

  - **StreamingSIMDExtensions**  -  **/Arch: SSE**

  - **StreamingSIMDExtensions2**  -  **/Arch: SSE2**

    Per altre informazioni, vedere [/arch (x86)](/cpp/build/reference/arch-x86).

- **EnableFiberSafeOptimizations**

   Parametro booleano facoltativo.

   Se `true`, supporta l'indipendenza da fiber per i dati allocati usando l'archiviazione locale di thread statici, ovvero dati allocati usando `__declspec(thread)`.

   Per altre informazioni, vedere [/gt (supporta archiviazione locale di thread indipendente da Fiber)](/cpp/build/reference/gt-support-fiber-safe-thread-local-storage).

- **EnablePREfast**

   Parametro booleano facoltativo.

   Se `true`, abilitare l'analisi del codice.

   Per ulteriori informazioni, vedere [/Analyze (analisi codice)](/cpp/build/reference/analyze-code-analysis).

- **Errorreporting-**

   Parametro String facoltativo.

   Consente di inviare informazioni sugli errori interni del compilatore direttamente a Microsoft. Per impostazione predefinita, l'impostazione nelle build IDE è **Prompt** e l'impostazione nelle build da riga di comando è **Queue** .

   Specificare uno dei valori seguenti, ognuno dei quali corrisponde a un'opzione della riga di comando.

  - **Nessuna**  -  **/errorreport: nessuna**

  - **Messaggio di richiesta**  -  **/errorreport: prompt**

  - **Coda**  -  di **/errorreport: Queue**

  - **Invia**  -  **/errorreport: Send**

    Per ulteriori informazioni, vedere [/errorreport (segnala gli errori interni del compilatore)](/cpp/build/reference/errorreport-report-internal-compiler-errors).

- **ExceptionHandling**

   Parametro String facoltativo.

   Specifica il modello di gestione delle eccezioni che deve essere usato dal compilatore.

   Specificare uno dei valori seguenti, ognuno dei quali corrisponde a un'opzione della riga di comando.

  - **false** - *\<none>*

  - **Asincrono**  -  **/EHA**

  - **Sincronizza**  -  **/EHsc**

  - **SyncCThrow**  -  **/EHS**

    Per ulteriori informazioni, vedere [/eh (modello di gestione delle eccezioni)](/cpp/build/reference/eh-exception-handling-model).

- **ExpandAttributedSource**

   Parametro booleano facoltativo.

   Se `true`, viene creato un file di listato con attributi espansi inseriti nel file di origine.

   Per altre informazioni, vedere [/FX (merge del codice inserito)](/cpp/build/reference/fx-merge-injected-code).

- **FavorSizeOrSpeed**

   Parametro String facoltativo.

   Specifica se ottimizzare la dimensione o la velocità del codice.

   Specificare uno dei valori seguenti, ognuno dei quali corrisponde a un'opzione della riga di comando.

  - **Né** - *\<none>*

  - **Dimensioni**  -  **/OS**

  - **Velocità**  -  **/OT**

    Per ulteriori informazioni, vedere [/OS,/OT (Ottimizza per dimensione codice, ottimizza per velocità codice)](/cpp/build/reference/os-ot-favor-small-code-favor-fast-code).

- **FloatingPointExceptions**

   Parametro booleano facoltativo.

   Se `true`, abilita il modello di eccezione a virgola mobile affidabile. Vengono generate eccezioni immediatamente dopo l'attivazione.

   Per ulteriori informazioni, vedere l'opzione/ **FP: except** in [/FP (specifica il comportamento](/cpp/build/reference/fp-specify-floating-point-behavior)della virgola mobile).

- **FloatingPointModel**

   Parametro String facoltativo.

   Imposta il modello a virgola mobile.

   Specificare uno dei valori seguenti, ognuno dei quali corrisponde a un'opzione della riga di comando.

  - **Precisione**  -  **/FP: precisa**

  - **Strict**  -  **/FP: Strict**

  - **Veloce**  -  **/FP: Fast**

    Per altre informazioni, vedere [/FP (specifica il comportamento](/cpp/build/reference/fp-specify-floating-point-behavior)della virgola mobile).

- **ForceConformanceInForLoopScope**

   Parametro booleano facoltativo.

   Se `true`, consente di implementare il comportamento C++ standard per cicli [for](/cpp/cpp/for-statement-cpp) con estensioni Microsoft ([/Ze](/cpp/build/reference/za-ze-disable-language-extensions)).

   Per altre informazioni, vedere [/Zc: forScope (Imponi conformità nell'ambito di un ciclo for)](/cpp/build/reference/zc-forscope-force-conformance-in-for-loop-scope).

- **ForcedIncludeFiles**

   Parametro `String[]` facoltativo.

   Determina l'elaborazione di uno o più file di intestazione specificati da parte del preprocessore.

   Per ulteriori informazioni, vedere [/Fi (nome file di inclusione forzata)](/cpp/build/reference/fi-name-forced-include-file).

- **ForcedUsingFiles**

   Parametro **String []** facoltativo.

   Determina l'elaborazione di uno o più file **#using** specificati da parte del preprocessore.

   Per ulteriori informazioni, vedere [/fu (nome file forced #using)](/cpp/build/reference/fu-name-forced-hash-using-file).

- **FunctionLevelLinking**

   Parametro `Boolean` facoltativo.

   Se `true`, indica al compilatore di assemblare le singole funzioni sotto forma di funzioni incluse nel pacchetto (COMDAT).

   Per altre informazioni, vedere [/Gy (Abilita collegamento a livello di funzione)](/cpp/build/reference/gy-enable-function-level-linking).

- **GenerateXMLDocumentationFiles**

   Parametro `Boolean` facoltativo.

   Se `true` , il compilatore elabora i commenti relativi alla documentazione nei file di codice sorgente e crea un file *. xdc* per ogni file di codice sorgente con commenti sulla documentazione.

   Per ulteriori informazioni, vedere [/doc (elabora i commenti relativi alla documentazione) (C/C++)](/cpp/build/reference/doc-process-documentation-comments-c-cpp). Vedere anche il parametro **XMLDocumentationFileName** in questa tabella.

- **IgnoreStandardIncludePath**

   Parametro `Boolean` facoltativo.

   Se `true`, impedisce al compilatore di cercare file di inclusione nelle directory specificate nelle variabili di ambiente PATH e INCLUDE.

   Per ulteriori informazioni, vedere [/x (Ignora percorsi di inclusione standard)](/cpp/build/reference/x-ignore-standard-include-paths).

- **InlineFunctionExpansion**

   Parametro **stringa** facoltativo.

   Specifica il livello di espansione della funzione inline per la compilazione.

   Specificare uno dei valori seguenti, ognuno dei quali corrisponde a un'opzione della riga di comando.

  - **Predefinita** - *\<none>*

  - **Disabilitato**  -  **/Ob0**

  - **OnlyExplicitInline**  -  **/OB1**

  - **AnySuitable**  -  **/Ob2**

    Per altre informazioni, vedere [/OB (espansione funzioni inline)](/cpp/build/reference/ob-inline-function-expansion).

- **IntrinsicFunctions**

   Parametro `Boolean` facoltativo.

   Se `true`, sostituisce alcune chiamate di funzione con form intrinseci o speciali della funzione che consentono di eseguire l'applicazione più rapidamente.

   Per ulteriori informazioni, vedere [/OI (genera funzioni intrinseche)](/cpp/build/reference/oi-generate-intrinsic-functions).

- **MinimalRebuild**

   Parametro `Boolean` facoltativo.

   Se `true`, abilita la ricompilazione minima, che determina se è necessario ricompilare i file di origine C++ che includono modifiche alle definizioni delle classi C++ archiviate nei file di intestazione (estensione h).

   Per ulteriori informazioni, vedere [/GM (Abilita ricompilazione minima)](/cpp/build/reference/gm-enable-minimal-rebuild).

- **MultiProcessorCompilation**

   Parametro `Boolean` facoltativo.

   Se `true`, usare più processori per la compilazione. Questo parametro crea un processo per ogni processore effettivo nel computer in uso.

   Per altre informazioni, vedere [/MP (compilazione con più processi)](/cpp/build/reference/mp-build-with-multiple-processes). Vedere anche il parametro **ProcessorNumber** in questa tabella.

- **ObjectFileName**

   Parametro **stringa** facoltativo.

   Specifica un nome file oggetto (OBJ) o una directory da usare al posto dell'impostazione predefinita.

   Per altre informazioni, vedere [/Fo (Nome file oggetto)](/cpp/build/reference/fo-object-file-name).

- **ObjectFiles**

   Parametro **String []** facoltativo.

   Elenco di file oggetto.

- **OmitDefaultLibName**

   Parametro `Boolean` facoltativo.

   Se `true` , omette il nome della libreria di runtime del linguaggio C predefinito dal file oggetto ( *obj* ). Per impostazione predefinita, il compilatore inserisce il nome della libreria nel file con *estensione obj* per indirizzare il linker alla libreria corretta.

   Per ulteriori informazioni, vedere [/Zl (omette il nome della libreria predefinita)](/cpp/build/reference/zl-omit-default-library-name).

- **OmitFramePointers**

   Parametro `Boolean` facoltativo.

   Se `true`, disabilita la creazione di puntatori ai frame nello stack di chiamate.

   Per altre informazioni, vedere [/Oy (omissione dei puntatori ai frame)](/cpp/build/reference/oy-frame-pointer-omission).

- **OpenMPSupport**

   Parametro `Boolean` facoltativo.

   Se `true`, indica al compilatore di elaborare direttive e clausole OpenMP.

   Per ulteriori informazioni, vedere [/OpenMP (abilitazione del supporto openmp 2,0)](/cpp/build/reference/openmp-enable-openmp-2-0-support).

- **Ottimizzazione**

   Parametro **stringa** facoltativo.

   Specifica diverse ottimizzazioni del codice per velocità e dimensioni.

   Specificare uno dei valori seguenti, ognuno dei quali corrisponde a un'opzione della riga di comando.

  - **Disabilitato**  -  **/Od**

  - **MinSpace**  -  **/O1**

  - **Maxspeed**  -  **/O2**

  - **Completo**  -  **/Ox**

    Per altre informazioni, vedere [Opzioni /O (Ottimizza codice)](/cpp/build/reference/o-options-optimize-code).

- **PrecompiledHeader**

   Parametro **stringa** facoltativo.

   Creare o usare un file di intestazione precompilata ( *PCH* ) durante la compilazione.

   Specificare uno dei valori seguenti, ognuno dei quali corrisponde a un'opzione della riga di comando.

  - **Non utilizzare** - *\<none>*

  - **Crea**  -  **/YC**

  - **USA**  -  **/Yu**

    Per altre informazioni, vedere [/YC (crea il file di intestazione precompilata)](/cpp/build/reference/yc-create-precompiled-header-file) e [/Yu (usare il file di intestazione precompilata)](/cpp/build/reference/yu-use-precompiled-header-file). Vedere anche i parametri **PrecompiledHeaderFile** e **PrecompiledHeaderOutputFile** in questa tabella.

- **PrecompiledHeaderFile**

   Parametro **stringa** facoltativo.

   Specifica un nome di file di intestazione precompilata da creare o usare.

   Per altre informazioni, vedere [/YC (crea il file di intestazione precompilata)](/cpp/build/reference/yc-create-precompiled-header-file) e [/Yu (usare il file di intestazione precompilata)](/cpp/build/reference/yu-use-precompiled-header-file).

- **PrecompiledHeaderOutputFile**

   Parametro **stringa** facoltativo.

   Specifica un nome di percorso per un'intestazione precompilata anziché usare il nome di percorso predefinito.

   Per altre informazioni, vedere [/FP (nome file PCH)](/cpp/build/reference/fp-name-dot-pch-file).

- **PreprocessKeepComments**

   Parametro `Boolean` facoltativo.

   Se `true`, conserva i commenti durante la pre-elaborazione.

   Per ulteriori informazioni, vedere [/c (Mantieni i commenti durante la pre-elaborazione)](/cpp/build/reference/c-preserve-comments-during-preprocessing).

- **PreprocessorDefinitions**

   Parametro `String[]` facoltativo.

   Definisce un simbolo di pre-elaborazione per il file di origine.

   Per ulteriori informazioni, vedere [/d (definizioni preprocessore)](/cpp/build/reference/d-preprocessor-definitions).

- **PreprocessOutput**

   Parametro `ITaskItem[]` facoltativo.

   Definisce una matrice di elementi di output del preprocessore che può essere usata ed emessa dalle attività.

- **PreprocessOutputPath**

   Parametro `String` facoltativo.

   Specifica il nome del file di output in cui il parametro **PreprocessToFile** scrive l'output pre-elaborato.

   Per ulteriori informazioni, vedere [/Fi (pre-elaborazione nome file di output)](/cpp/build/reference/fi-preprocess-output-file-name).

- **PreprocessSuppressLineNumbers**

   Parametro `Boolean` facoltativo.

   Se `true`, pre-elabora i file di origine C e C++ e copia i file pre-elaborati nel dispositivo di output standard.

   Per altre informazioni, vedere [/EP (pre-elabora in stdout senza direttive #line)](/cpp/build/reference/ep-preprocess-to-stdout-without-hash-line-directives).

- **PreprocessToFile**

   Parametro `Boolean` facoltativo.

   Se `true`, pre-elabora i file di origine C e C++ e scrive l'output pre-elaborato in un file.

   Per ulteriori informazioni, vedere [/p (pre-elabora in un file)](/cpp/build/reference/p-preprocess-to-a-file).

- **ProcessorNumber**

   Parametro `Integer` facoltativo.

   Specifica il numero massimo di processori da usare in una compilazione multiprocessore. Usare questo parametro in combinazione con il parametro **MultiProcessorCompilation** .

- **ProgramDataBaseFileName**

   Parametro `String` facoltativo.

   Specifica un nome file per il file del database di programma (PDB).

   Per ulteriori informazioni, vedere [/FD (nome file database di programma)](/cpp/build/reference/fd-program-database-file-name).

- **RuntimeLibrary**

   Parametro `String` facoltativo.

   Indica se un modulo con multithreading è una DLL e seleziona versioni finali o di debug della libreria di runtime.

   Specificare uno dei valori seguenti, ognuno dei quali corrisponde a un'opzione della riga di comando.

  - **Multithreading**  -  **/Mt**

  - **MultiThreadedDebug**  -  **/MTD**

  - **MultiThreadedDLL**  -  **/MD**

  - **MultiThreadedDebugDLL**  -  **/MDD**

    Per ulteriori informazioni, vedere [/MD,/MT,/LD (utilizzare la libreria di Runtime)](/cpp/build/reference/md-mt-ld-use-run-time-library).

- **RuntimeTypeInfo**

   Parametro `Boolean` facoltativo.

   Se `true`, aggiunge codice per il controllo dei tipi di oggetto C++ in fase di esecuzione (informazioni sui tipi di runtime).

   Per ulteriori informazioni, vedere [/gr (Abilita informazioni sui tipi in fase di esecuzione)](/cpp/build/reference/gr-enable-run-time-type-information).

- **ShowIncludes**

   Parametro `Boolean` facoltativo.

   Se `true`, indica al compilatore di generare un elenco di file di inclusione.

   Per ulteriori informazioni, vedere [/showIncludes (elenca i file di inclusione)](/cpp/build/reference/showincludes-list-include-files).

- **SmallerTypeCheck**

   Parametro `Boolean` facoltativo.

   Se `true`, segnala un errore di run-time se un valore viene assegnato a un tipo di dati più piccolo e provoca una perdita di dati.

   Per ulteriori informazioni, vedere l'opzione **/RTCC** in [/RTC (controlli degli errori di run-time)](/cpp/build/reference/rtc-run-time-error-checks).

- **recenti**

   Parametro `ITaskItem[]` obbligatorio.

   Specifica un elenco dei file di origine separati da spazi.

- **StringPooling**

   Parametro `Boolean` facoltativo.

   Se `true`, consente al compilatore di creare una copia di stringhe identiche nell'immagine del programma.

   Per altre informazioni, vedere [/GF (Elimina stringhe duplicate)](/cpp/build/reference/gf-eliminate-duplicate-strings).

- **StructMemberAlignment**

   Parametro `String` facoltativo.

   Specifica l'allineamento dei byte per tutti i membri in una struttura.

   Specificare uno dei valori seguenti, ognuno dei quali corrisponde a un'opzione della riga di comando.

  - **Impostazione predefinita**  -  **/Zp1**

  - **1Byte**  -  **/Zp1**

  - **2Bytes**  -  **/Zp2**

  - **4Bytes**  -  **/Zp4**

  - **8Bytes**  -  **/ZP8**

  - **16bytes**  -  **/Zp16**

    Per altre informazioni, vedere [/ZP (allineamento membri struct)](/cpp/build/reference/zp-struct-member-alignment).

- **SuppressStartupBanner**

   Parametro `Boolean` facoltativo.

   Se `true`, impedisce la visualizzazione del messaggio sul copyright e sul numero di versione all'avvio dell'attività.

   Per ulteriori informazioni, vedere [/nologo (non visualizzare il banner di avvio) (C/C++)](/cpp/build/reference/nologo-suppress-startup-banner-c-cpp).

- **TrackerLogDirectory**

   Parametro `String` facoltativo.

   Specifica la directory intermedia in cui sono archiviati i log di rilevamento per questa attività.

   Per altre informazioni, vedere i parametri **TLogReadFiles** e **TLogWriteFiles** in questa tabella.

- **TreatSpecificWarningsAsErrors**

   Parametro **String []** facoltativo.

   Considera l'elenco specificato di avvisi del compilatore come errori.

   Per ulteriori informazioni, vedere l' **/we** `n` opzione/we in [/W,/W0,/W1,/W2,/W3,/W4,/W1,/W2,/W3,/W4,/Wall,/WD.,/we,/wo,/WV,/WX (livello di avviso)](/cpp/build/reference/compiler-option-warning-level).

- **TreatWarningAsError**

   Parametro `Boolean` facoltativo.

   Se `true`, considera tutti gli avvisi del compilatore come errori.

   Per ulteriori informazioni, vedere l'opzione **/WX** in [/w,/W0,/W1,/W2,/W3,/W4,/W1,/W2,/W3,/W4,/Wall,/WD.,/we,/wo,/WV,/WX (livello di avviso)](/cpp/build/reference/compiler-option-warning-level).

- **TreatWChar_tAsBuiltInType**

   Parametro `Boolean` facoltativo.

   Se `true`, considerare il tipo `wchar_t` come un tipo nativo.

   Per ulteriori informazioni, vedere [/Zc: wchar_t (wchar_t è di tipo nativo)](/cpp/build/reference/zc-wchar-t-wchar-t-is-native-type).

- **UndefineAllPreprocessorDefinitions**

   Parametro `Boolean` facoltativo.

   Se `true`, rimuove la definizione dei simboli specifici di Microsoft definiti dal compilatore.

   Per ulteriori informazioni, vedere l'opzione **/u** in [/u,/u (annullare la definizione dei simboli)](/cpp/build/reference/u-u-undefine-symbols).

- **UndefinePreprocessorDefinitions**

   Parametro `String[]` facoltativo.

   Specifica un elenco di uno o più simboli del preprocessore per cui rimuovere la definizione.

   Per ulteriori informazioni, vedere l'opzione **/u** in [/u,/u (annullare la definizione dei simboli)](/cpp/build/reference/u-u-undefine-symbols).

- **UseFullPaths**

   Parametro `Boolean` facoltativo.

   Se `true`, visualizza il percorso completo dei file di codice sorgente passati al compilatore nella diagnostica.

   Per ulteriori informazioni, vedere [/FC (percorso completo del file di codice sorgente nella diagnostica)](/cpp/build/reference/fc-full-path-of-source-code-file-in-diagnostics).

- **UseUnicodeForAssemblerListing**

   Parametro `Boolean` facoltativo.

   Se `true`, causa la creazione del file di output in formato UTF-8.

   Per ulteriori informazioni, vedere l'opzione **/FAU** in [/fa,/fa (file di listato)](/cpp/build/reference/fa-fa-listing-file).

- **WarningLevel**

   Parametro `String` facoltativo.

   Specifica il livello massimo dell'avviso che verrà generato dal compilatore.

   Specificare uno dei valori seguenti, ognuno dei quali corrisponde a un'opzione della riga di comando.

  - **TurnOffAllWarnings**  -  **/W0**

  - **Level1**  -  **/W1**

  - **Level2**  -  **/W2**

  - **Level3**  -  **/W3**

  - **Level4**  -  **/W4**

  - **EnableAllWarnings**  -  **/Wall**

    Per ulteriori informazioni, vedere l'opzione **/W**_n_ in [/W,/W0,/W1,/W2,/W3,/W4,/W1,/W2,/W3,/W4,/Wall,/WD.,/we,/wo,/WV,/WX (livello di avviso)](/cpp/build/reference/compiler-option-warning-level).

- **WholeProgramOptimization**

   Parametro `Boolean` facoltativo.

   Se `true`,abilita l'ottimizzazione dell'intero programma.

   Per ulteriori informazioni, vedere [/GL (Ottimizzazione intero programma)](/cpp/build/reference/gl-whole-program-optimization).

- **XMLDocumentationFileName**

   Parametro `String` facoltativo.

   Specifica il nome dei file di documentazione XML generati. Questo parametro può essere un nome di file o directory.

   Per ulteriori informazioni, vedere l' `name` argomento in [/doc (elaborare i commenti relativi alla documentazione) (C/C++)](/cpp/build/reference/doc-process-documentation-comments-c-cpp). Vedere anche il parametro **GenerateXMLDocumentationFiles** in questa tabella.

- **MinimalRebuildFromTracking**

   Parametro `Boolean` facoltativo.

   Se `true`, viene eseguita una compilazione incrementale verificata; se `false`, viene eseguita una ricompilazione.

- **TLogReadFiles**

   Parametro `ITaskItem[]` facoltativo.

   Specifica una matrice di elementi che rappresentano i *log di rilevamento dei file di lettura* .

   Un log di rilevamento dei file di lettura (con *estensione tlog* ) contiene i nomi dei file di input letti da un'attività e viene usato dal sistema di compilazione del progetto per supportare le compilazioni incrementali. Per altre informazioni, vedere i parametri **TrackerLogDirectory** e **TrackFileAccess** in questa tabella.

- **TLogWriteFiles**

   Parametro `ITaskItem[]` facoltativo.

   Specifica una matrice di elementi che rappresentano i *log di rilevamento dei file di scrittura* .

   Un log di rilevamento dei file di scrittura (con *estensione tlog* ) contiene i nomi dei file di output scritti da un'attività e viene usato dal sistema di compilazione del progetto per supportare le compilazioni incrementali. Per altre informazioni, vedere i parametri **TrackerLogDirectory** e **TrackFileAccess** in questa tabella.

- **TrackFileAccess**

   Parametro `Boolean` facoltativo.

   Se `true`, rileva i modelli di accesso ai file.

   Per altre informazioni, vedere i parametri **TLogReadFiles** e **TLogWriteFiles** in questa tabella.

## <a name="see-also"></a>Vedere anche

- [Informazioni di riferimento sulle attività](../msbuild/msbuild-task-reference.md)
