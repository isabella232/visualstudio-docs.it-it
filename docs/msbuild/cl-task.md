---
title: Attività CL | Microsoft Docs
description: Descrive lo scopo e i parametri dell'attività CL MSBuild, che esegue il wrapping dello strumento compilatore Microsoft C++, cl.exe.
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
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: b3f2d4fb5ce1a3ef2f5b4710067efdfe335231f0
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122040047"
---
# <a name="cl-task"></a>attività CL

Esegue il wrapping dello strumento del compilatore Microsoft C++, *cl.exe*. Il compilatore genera file *eseguibili*(.exe), file della libreria a collegamento dinamico *(.dll*) o file del modulo di codice (con estensione *netmodule).* Per altre informazioni, vedere [Opzioni](/cpp/build/reference/compiler-options) del compilatore e [Usare MSBuild](/cpp/build/msbuild-visual-cpp) dalla riga di comando e Usare il set di strumenti [Microsoft C++ dalla riga di comando.](/cpp/build/building-on-the-command-line)

## <a name="parameters"></a>Parametri

 Nell'elenco che segue vengono descritti i parametri dell'attività **CL**. La maggior parte dei parametri di attività e alcuni set di parametri corrispondono a un'opzione della riga di comando.

- **AdditionalIncludeDirectories**

   Parametro String[] facoltativo.

   Aggiunge una directory all'elenco delle directory in cui vengono cercati i file di inclusione.

   Per altre informazioni, vedere [/I (Directory di inclusione aggiuntive).](/cpp/build/reference/i-additional-include-directories)

- **Opzioni aggiuntive**

   Parametro String facoltativo.

   Elenco di opzioni della riga di comando. Ad esempio, "/ \<option1>  / \<option2>  / \<option#> ". Usare questo parametro per specificare le opzioni della riga di comando che non sono rappresentate da altri parametri dell'attività.

   Per altre informazioni, vedere [Opzioni del compilatore.](/cpp/build/reference/compiler-options)

- **AdditionalUsingDirectories**

   Parametro String[] facoltativo.

   Specifica una directory in cui il compilatore effettuerà la ricerca per risolvere i riferimenti di file passati alla direttiva **#using**.

   Per altre informazioni, vedere [/AI (Specifica directory di metadati).](/cpp/build/reference/ai-specify-metadata-directories)

- **AlwaysAppend**

   Parametro String facoltativo.

   Stringa che viene sempre generata sulla riga di comando. Il valore predefinito è "**/c**".

- **AssemblerListingLocation**

   Crea un file di elenco che contiene il codice assembly.

   Per altre informazioni, vedere **l'opzione /Fa** in [/FA, /Fa (file di listato).](/cpp/build/reference/fa-fa-listing-file)

- **AssemblerOutput**

   Parametro String facoltativo.

   Crea un file di elenco che contiene il codice assembly.

   Specificare uno dei valori seguenti, ognuno dei quali corrisponde a un'opzione della riga di comando.

  - **NoListing** - *\<none>*

  - **AssemblyCode**  -  **/FA**

  - **AssemblyAndMachineCode**  -  **/FAc**

  - **AssemblyAndSourceCode**  -  **/FAs**

  - **Tutti**  -  **/FAcs**

    Per altre informazioni, vedere le opzioni **/FA**, **/FAc**, **/FAs** e **/FAcs** in [/FA, /Fa (file di listato).](/cpp/build/reference/fa-fa-listing-file)

- **BasicRuntimeChecks**

   Parametro String facoltativo.

   Abilita e disabilita la funzionalità di controllo degli errori di run-time, con il pragma [runtime_checks](/cpp/preprocessor/runtime-checks).

   Specificare uno dei valori seguenti, ognuno dei quali corrisponde a un'opzione della riga di comando.

  - **Predefinito** -                          *\<none>*

  - **StackFrameRuntimeCheck**  -  **/RTCs**

  - **UninitializedLocalUsageCheck**  -  **/RTCu**

  - **EnableFastChecks**  -                           **/RTC1**

    Per altre informazioni, vedere [/RTC (Controlli degli errori di runtime).](/cpp/build/reference/rtc-run-time-error-checks)

- **BrowseInformation**

   Parametro booleano facoltativo.

   Se `true`, crea un file di informazioni di visualizzazione.

   Per altre informazioni, vedere **l'opzione /FR** in [/FR, /Fr (Crea file con estensione sbr).](/cpp/build/reference/fr-fr-create-dot-sbr-file)

- **BrowseInformationFile**

   Parametro String facoltativo.

   Specifica un nome di file per il file di informazioni di visualizzazione.

   Per altre informazioni, vedere il **parametro BrowseInformation** in questa tabella e vedere anche [/FR, /Fr (Crea file con estensione sbr).](/cpp/build/reference/fr-fr-create-dot-sbr-file)

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

  - **Cdecl**  -  **/Gd**

  - **Chiamata rapida**  -                           **/Gr**

  - **StdCall**  -                           **/Gz**

    Per altre informazioni, vedere [/Gd, /Gr, /Gv, /Gz (convenzione di chiamata).](/cpp/build/reference/gd-gr-gv-gz-calling-convention)

- **CompileAs**

   Parametro String facoltativo.

   Specifica se compilare il file di input come file di origine C o C++.

   Specificare uno dei valori seguenti, ognuno dei quali corrisponde a un'opzione della riga di comando.

  - **Predefinito** - *\<none>*

  - **CompileAsC**  -  **/TC**

  - **CompileAsCpp**  -  **/TP**

    Per altre informazioni, vedere [/Tc, /Tp, /TC, /TP (Specifica il tipo di file di origine).](/cpp/build/reference/tc-tp-tc-tp-specify-source-file-type)

- **CompileAsManaged**

   Parametro String facoltativo.

   Consente alle applicazioni e ai componenti di usare le funzionalità di Common Language Runtime (CLR).

   Specificare uno dei valori seguenti, ognuno dei quali corrisponde a un'opzione della riga di comando.

  - **False** - *\<none>*

  - **true**  -  **/clr**

  - **Pure**  -  **/clr:pure**

  - **Cassaforte**  -  **/clr:safe**

  - **OldSyntax**  -  **/clr:oldSyntax**

    Per altre informazioni, vedere [/clr (Compilazione Common Language Runtime)](/cpp/build/reference/clr-common-language-runtime-compilation).

- **CreateHotpatchableImage**

   Parametro booleano facoltativo.

   Se `true`, indica al compilatore di preparare un'immagine per *l'applicazione di una patch a caldo*. Questo parametro assicura che la prima istruzione di ogni funzione sia di due byte, condizione necessaria per l'applicazione di una patch a caldo.

   Per altre informazioni, vedere [/hotpatch (Crea immagine con supporto per latch a caldo).](/cpp/build/reference/hotpatch-create-hotpatchable-image)

- **DebugInformationFormat**

   Parametro String facoltativo.

   Seleziona il tipo di informazioni di debug create per il programma e indica se queste informazioni vengono mantenute nei file oggetto *(obj*) o in un database di programma (PDB).

   Specificare uno dei valori seguenti, ognuno dei quali corrisponde a un'opzione della riga di comando.

  - **OldStyle**  -  **/Z7**

  - **ProgramDatabase**  -  **/Zi**

  - **EditAndContinue**  -  **/ZI**

    Per altre informazioni, vedere [/Z7, /Zi, /ZI (formato delle informazioni di debug).](/cpp/build/reference/z7-zi-zi-debug-information-format)

- **DisableLanguageExtensions**

   Parametro booleano facoltativo.

   Se **true**, indica al compilatore di generare un errore per i costrutti di linguaggio che non sono compatibili con ANSI C o ANSI C++.

   Per altre informazioni, vedere **l'opzione /Za** in [/Za, /Ze (Disabilita le estensioni del linguaggio).](/cpp/build/reference/za-ze-disable-language-extensions)

- **DisableSpecificWarnings**

   Parametro String[] facoltativo.

   Disabilita i numeri di avviso specificati in un elenco delimitato da punti e virgola.

   Per altre informazioni, vedere l'opzione `/wd` in [/w, /W0, /W1, /W2, /W3, /W4, /w1, /w2, /w3, /w4, /Wall, /wd, /we, /wo, /Wv, /WX (livello di avviso).](/cpp/build/reference/compiler-option-warning-level)

- **EnableEnhancedInstructionSet**

   Parametro String facoltativo.

   Specifica l'architettura per la generazione di codice che usa le istruzioni Streaming SIMD Extensions (SSE) e Streaming SIMD Extensions 2 (SSE2).

   Specificare uno dei valori seguenti, ognuno dei quali corrisponde a un'opzione della riga di comando.

  - **StreamingSIMDExtensions**  -  **/arch:SSE**

  - **StreamingSIMDExtensions2**  -  **/arch:SSE2**

    Per altre informazioni, vedere [/arch (x86)](/cpp/build/reference/arch-x86).

- **EnableFiberSafeOptimizations**

   Parametro booleano facoltativo.

   Se `true`, supporta l'indipendenza da fiber per i dati allocati usando l'archiviazione locale di thread statici, ovvero dati allocati usando `__declspec(thread)`.

   Per altre informazioni, vedere [/GT (supporta l'archiviazione thread-local fiber-safe).](/cpp/build/reference/gt-support-fiber-safe-thread-local-storage)

- **EnablePREfast**

   Parametro booleano facoltativo.

   Se `true`, abilitare l'analisi del codice.

   Per altre informazioni, vedere [/analyze (analisi del codice).](/cpp/build/reference/analyze-code-analysis)

- **Segnalazione errori**

   Parametro String facoltativo.

   Consente di inviare informazioni sugli errori interni del compilatore direttamente a Microsoft. Per impostazione predefinita, l'impostazione nelle build IDE è **Prompt** e l'impostazione nelle build da riga di comando è **Queue**.

   Specificare uno dei valori seguenti, ognuno dei quali corrisponde a un'opzione della riga di comando.

  - **Nessuno**  -  **/errorReport:none**

  - **Richiesta di conferma**  -  **/errorReport:prompt**

  - **Coda**  -  **/errorReport:queue**

  - **Invia**  -  **/errorReport:send**

    Per altre informazioni, vedere [/errorReport (segnala errori interni del compilatore).](/cpp/build/reference/errorreport-report-internal-compiler-errors)

- **ExceptionHandling**

   Parametro String facoltativo.

   Specifica il modello di gestione delle eccezioni che deve essere usato dal compilatore.

   Specificare uno dei valori seguenti, ognuno dei quali corrisponde a un'opzione della riga di comando.

  - **False** - *\<none>*

  - **Async**  -  **/EHa**

  - **Sincronizza**  -  **/EHsc**

  - **SyncCThrow**  -  **/EHs**

    Per altre informazioni, vedere [/EH (modello di gestione delle eccezioni).](/cpp/build/reference/eh-exception-handling-model)

- **ExpandAttributedSource**

   Parametro booleano facoltativo.

   Se `true`, viene creato un file di listato con attributi espansi inseriti nel file di origine.

   Per altre informazioni, vedere [/Fx (Merge injected code)](/cpp/build/reference/fx-merge-injected-code).

- **FavorSizeOrSpeed**

   Parametro String facoltativo.

   Specifica se ottimizzare la dimensione o la velocità del codice.

   Specificare uno dei valori seguenti, ognuno dei quali corrisponde a un'opzione della riga di comando.

  - **Né** - *\<none>*

  - **Dimensioni**  -  **/Os**

  - **Velocità**  -  **/Ot**

    Per altre informazioni, vedere [/Os, /Ot (favorisce il codice di piccole dimensioni, favorisce il codice rapido).](/cpp/build/reference/os-ot-favor-small-code-favor-fast-code)

- **FloatingPointExceptions**

   Parametro booleano facoltativo.

   Se `true`, abilita il modello di eccezione a virgola mobile affidabile. Vengono generate eccezioni immediatamente dopo l'attivazione.

   Per altre informazioni, vedere l'opzione /**fp:except** in [/fp (Specifica il comportamento a virgola mobile).](/cpp/build/reference/fp-specify-floating-point-behavior)

- **FloatingPointModel**

   Parametro String facoltativo.

   Imposta il modello a virgola mobile.

   Specificare uno dei valori seguenti, ognuno dei quali corrisponde a un'opzione della riga di comando.

  - **Preciso**  -  **/fp:precise**

  - **Strict**  -  **/fp:strict**

  - **Veloce**  -  **/fp:fast**

    Per altre informazioni, vedere [/fp (Specifica il comportamento a virgola mobile).](/cpp/build/reference/fp-specify-floating-point-behavior)

- **ForceConformanceInForLoopScope**

   Parametro booleano facoltativo.

   Se `true`, consente di implementare il comportamento C++ standard per cicli [for](/cpp/cpp/for-statement-cpp) con estensioni Microsoft ([/Ze](/cpp/build/reference/za-ze-disable-language-extensions)).

   Per altre informazioni, vedere [/Zc:forScope (Forza conformità nell'ambito del ciclo for).](/cpp/build/reference/zc-forscope-force-conformance-in-for-loop-scope)

- **ForcedIncludeFiles**

   Parametro `String[]` facoltativo.

   Determina l'elaborazione di uno o più file di intestazione specificati da parte del preprocessore.

   Per altre informazioni, vedere [/FI (Nome file di inclusione forzato).](/cpp/build/reference/fi-name-forced-include-file)

- **ForcedUsingFiles**

   Parametro **String[]** facoltativo.

   Determina l'elaborazione di uno o più file **#using** specificati da parte del preprocessore.

   Per altre informazioni, vedere [/FU (Denomi](/cpp/build/reference/fu-name-forced-hash-using-file)file #using) .

- **FunctionLevelLinking**

   Parametro `Boolean` facoltativo.

   Se `true`, indica al compilatore di assemblare le singole funzioni sotto forma di funzioni incluse nel pacchetto (COMDAT).

   Per altre informazioni, vedere [/Gy (Abilita collegamento a livello di funzione).](/cpp/build/reference/gy-enable-function-level-linking)

- **GenerateXMLDocumentationFiles**

   Parametro `Boolean` facoltativo.

   Se , fa in modo che il compilatore eelaborare i commenti relativi alla documentazione nei file di codice sorgente e crei un file con estensione xdc per ogni file di codice sorgente che `true` contiene commenti relativi alla documentazione. 

   Per altre informazioni, vedere [/doc (Elabora i commenti della documentazione) (C/C++).](/cpp/build/reference/doc-process-documentation-comments-c-cpp) Vedere anche il parametro **XMLDocumentationFileName** in questa tabella.

- **IgnoreStandardIncludePath**

   Parametro `Boolean` facoltativo.

   Se `true`, impedisce al compilatore di cercare file di inclusione nelle directory specificate nelle variabili di ambiente PATH e INCLUDE.

   Per altre informazioni, vedere [/X (Ignora percorsi di inclusione standard).](/cpp/build/reference/x-ignore-standard-include-paths)

- **InlineFunctionExpansion**

   Parametro **String** facoltativo.

   Specifica il livello di espansione della funzione inline per la compilazione.

   Specificare uno dei valori seguenti, ognuno dei quali corrisponde a un'opzione della riga di comando.

  - **Predefinito** - *\<none>*

  - **Disabilitato**  -  **/Ob0**

  - **OnlyExplicitInline**  -  **/Ob1**

  - **AnySuitable**  -  **/Ob2**

    Per altre informazioni, vedere [/Ob (espansione della funzione inline).](/cpp/build/reference/ob-inline-function-expansion)

- **IntrinsicFunctions**

   Parametro `Boolean` facoltativo.

   Se `true`, sostituisce alcune chiamate di funzione con form intrinseci o speciali della funzione che consentono di eseguire l'applicazione più rapidamente.

   Per altre informazioni, vedere [/Oi (Genera funzioni intrinseche).](/cpp/build/reference/oi-generate-intrinsic-functions)

- **MinimalRebuild**

   Parametro `Boolean` facoltativo.

   Se `true`, abilita la ricompilazione minima, che determina se è necessario ricompilare i file di origine C++ che includono modifiche alle definizioni delle classi C++ archiviate nei file di intestazione (estensione h).

   Per altre informazioni, vedere [/Gm (Abilita ricompilazione minima).](/cpp/build/reference/gm-enable-minimal-rebuild)

- **MultiProcessorCompilation**

   Parametro `Boolean` facoltativo.

   Se `true`, usare più processori per la compilazione. Questo parametro crea un processo per ogni processore effettivo nel computer in uso.

   Per altre informazioni, vedere [/MP (Compilazione con più processi).](/cpp/build/reference/mp-build-with-multiple-processes) Vedere anche il parametro **ProcessorNumber** in questa tabella.

- **ObjectFileName**

   Parametro **String** facoltativo.

   Specifica un nome file oggetto (OBJ) o una directory da usare al posto dell'impostazione predefinita.

   Per altre informazioni, vedere [/Fo (Nome file oggetto)](/cpp/build/reference/fo-object-file-name).

- **ObjectFiles**

   Parametro **String[]** facoltativo.

   Elenco di file oggetto.

- **OmitDefaultLibName**

   Parametro `Boolean` facoltativo.

   Se , omette il nome predefinito della libreria di `true` runtime C dal file dell'oggetto (*obj*). Per impostazione predefinita, il compilatore inserisce il nome della libreria nel file *obj* per indirizzare il linker alla libreria corretta.

   Per altre informazioni, vedere [/Zl (omette il nome della libreria predefinita).](/cpp/build/reference/zl-omit-default-library-name)

- **OmitFramePointers**

   Parametro `Boolean` facoltativo.

   Se `true`, disabilita la creazione di puntatori ai frame nello stack di chiamate.

   Per altre informazioni, vedere [/Oy (omissione del puntatore ai frame).](/cpp/build/reference/oy-frame-pointer-omission)

- **OpenMPSupport**

   Parametro `Boolean` facoltativo.

   Se `true`, indica al compilatore di elaborare direttive e clausole OpenMP.

   Per altre informazioni, vedere [/openmp (abilita il supporto di OpenMP 2.0).](/cpp/build/reference/openmp-enable-openmp-2-0-support)

- **Ottimizzazione**

   Parametro **String** facoltativo.

   Specifica diverse ottimizzazioni del codice per velocità e dimensioni.

   Specificare uno dei valori seguenti, ognuno dei quali corrisponde a un'opzione della riga di comando.

  - **Disabilitato**  -  **/Od**

  - **MinSpace**  -  **/O1**

  - **MaxSpeed**  -  **/O2**

  - **Completo**  -  **/Ox**

    Per altre informazioni, vedere [Opzioni /O (Ottimizza codice)](/cpp/build/reference/o-options-optimize-code).

- **PrecompiledHeader**

   Parametro **String** facoltativo.

   Creare o usare un file di intestazione precompilata *(con estensione pch)* durante la compilazione.

   Specificare uno dei valori seguenti, ognuno dei quali corrisponde a un'opzione della riga di comando.

  - **Uso non in uso** - *\<none>*

  - **Creare**  -  **/Yc**

  - **Usare**  -  **/Yu**

    Per altre informazioni, vedere /Yc (Crea file di intestazione [precompilata)](/cpp/build/reference/yc-create-precompiled-header-file) e [/Yu (Usa file di intestazione precompilata).](/cpp/build/reference/yu-use-precompiled-header-file) Vedere anche i parametri **PrecompiledHeaderFile** e **PrecompiledHeaderOutputFile** in questa tabella.

- **PrecompiledHeaderFile**

   Parametro **String** facoltativo.

   Specifica un nome di file di intestazione precompilata da creare o usare.

   Per altre informazioni, vedere /Yc (Crea file di intestazione [precompilata)](/cpp/build/reference/yc-create-precompiled-header-file) e [/Yu (Usa file di intestazione precompilata).](/cpp/build/reference/yu-use-precompiled-header-file)

- **PrecompiledHeaderOutputFile**

   Parametro **String** facoltativo.

   Specifica un nome di percorso per un'intestazione precompilata anziché usare il nome di percorso predefinito.

   Per altre informazioni, vedere [/Fp (Nome file con estensione pch).](/cpp/build/reference/fp-name-dot-pch-file)

- **PreprocessKeepComments**

   Parametro `Boolean` facoltativo.

   Se `true`, conserva i commenti durante la pre-elaborazione.

   Per altre informazioni, vedere [/C (Mantiene i commenti durante la pre-elaborazione).](/cpp/build/reference/c-preserve-comments-during-preprocessing)

- **PreprocessorDefinitions**

   Parametro `String[]` facoltativo.

   Definisce un simbolo di pre-elaborazione per il file di origine.

   Per altre informazioni, vedere [/D (definizioni del preprocessore).](/cpp/build/reference/d-preprocessor-definitions)

- **PreprocessOutput**

   Parametro `ITaskItem[]` facoltativo.

   Definisce una matrice di elementi di output del preprocessore che può essere usata ed emessa dalle attività.

- **PreprocessOutputPath**

   Parametro `String` facoltativo.

   Specifica il nome del file di output in cui il parametro **PreprocessToFile** scrive l'output pre-elaborato.

   Per altre informazioni, vedere [/Fi (Preprocess output file name)](/cpp/build/reference/fi-preprocess-output-file-name).

- **PreprocessSuppressLineNumbers**

   Parametro `Boolean` facoltativo.

   Se `true`, pre-elabora i file di origine C e C++ e copia i file pre-elaborati nel dispositivo di output standard.

   Per altre informazioni, vedere [/EP (Preprocess to stdout without #line directives)](/cpp/build/reference/ep-preprocess-to-stdout-without-hash-line-directives).

- **PreprocessToFile**

   Parametro `Boolean` facoltativo.

   Se `true`, pre-elabora i file di origine C e C++ e scrive l'output pre-elaborato in un file.

   Per altre informazioni, vedere [/P (Pre-elabora in un file).](/cpp/build/reference/p-preprocess-to-a-file)

- **ProcessorNumber**

   Parametro `Integer` facoltativo.

   Specifica il numero massimo di processori da usare in una compilazione multiprocessore. Usare questo parametro in combinazione con il parametro **MultiProcessorCompilation**.

- **ProgramDataBaseFileName**

   Parametro `String` facoltativo.

   Specifica un nome file per il file del database di programma (PDB).

   Per altre informazioni, vedere [/Fd (Nome file di database di programma)](/cpp/build/reference/fd-program-database-file-name).

- **RuntimeLibrary**

   Parametro `String` facoltativo.

   Indica se un modulo con multithreading è una DLL e seleziona versioni finali o di debug della libreria di runtime.

   Specificare uno dei valori seguenti, ognuno dei quali corrisponde a un'opzione della riga di comando.

  - **MultiThreading**  -  **/MT**

  - **MultiThreadedDebug**  -  **/MTd**

  - **MultiThreadedDLL**  -  **/MD**

  - **MultiThreadedDebugDLL**  -  **/MDd**

    Per altre informazioni, vedere [/MD, /MT, /LD (Usa libreria di runtime)](/cpp/build/reference/md-mt-ld-use-run-time-library).

- **RuntimeTypeInfo**

   Parametro `Boolean` facoltativo.

   Se `true`, aggiunge codice per il controllo dei tipi di oggetto C++ in fase di esecuzione (informazioni sui tipi di runtime).

   Per altre informazioni, vedere [/GR (Abilita informazioni sul tipo di run-time).](/cpp/build/reference/gr-enable-run-time-type-information)

- **ShowIncludes**

   Parametro `Boolean` facoltativo.

   Se `true`, indica al compilatore di generare un elenco di file di inclusione.

   Per altre informazioni, vedere [/showIncludes (Elencare i file di inclusione).](/cpp/build/reference/showincludes-list-include-files)

- **SmallerTypeCheck**

   Parametro `Boolean` facoltativo.

   Se `true`, segnala un errore di run-time se un valore viene assegnato a un tipo di dati più piccolo e provoca una perdita di dati.

   Per altre informazioni, vedere **l'opzione /RTCc** in [/RTC (controlli degli errori di runtime)](/cpp/build/reference/rtc-run-time-error-checks).

- **recenti**

   Parametro `ITaskItem[]` obbligatorio.

   Specifica un elenco dei file di origine separati da spazi.

- **StringPooling**

   Parametro `Boolean` facoltativo.

   Se `true`, consente al compilatore di creare una copia di stringhe identiche nell'immagine del programma.

   Per altre informazioni, vedere [/GF (Elimina stringhe duplicate).](/cpp/build/reference/gf-eliminate-duplicate-strings)

- **StructMemberAlignment**

   Parametro `String` facoltativo.

   Specifica l'allineamento dei byte per tutti i membri in una struttura.

   Specificare uno dei valori seguenti, ognuno dei quali corrisponde a un'opzione della riga di comando.

  - **Impostazione predefinita**  -  **/Zp1**

  - **1Byte**  -  **/Zp1**

  - **2Byte**  -  **/Zp2**

  - **4 Byte**  -  **/Zp4**

  - **8Byte**  -  **/Zp8**

  - **16Byte**  -  **/Zp16**

    Per altre informazioni, vedere [/Zp (allineamento dei membri struct)](/cpp/build/reference/zp-struct-member-alignment).

- **SuppressStartupBanner**

   Parametro `Boolean` facoltativo.

   Se `true`, impedisce la visualizzazione del messaggio sul copyright e sul numero di versione all'avvio dell'attività.

   Per altre informazioni, vedere [/nologo (Elimina banner di avvio) (C/C++).](/cpp/build/reference/nologo-suppress-startup-banner-c-cpp)

- **TrackerLogDirectory**

   Parametro `String` facoltativo.

   Specifica la directory intermedia in cui sono archiviati i log di rilevamento per questa attività.

   Per altre informazioni, vedere i parametri **TLogReadFiles** e **TLogWriteFiles** in questa tabella.

- **TreatSpecificWarningsAsErrors**

   Parametro **Facoltativo String[].**

   Considera l'elenco specificato di avvisi del compilatore come errori.

   Per altre informazioni, vedere l'opzione **/we** `n` in [/w, /W0, /W1, /W2, /W3, /W4, /w1, /w2, /w3, /w4, /Wall, /wd, /we, /wo, /Wv, /WX (livello di avviso).](/cpp/build/reference/compiler-option-warning-level)

- **TreatWarningAsError**

   Parametro `Boolean` facoltativo.

   Se `true`, considera tutti gli avvisi del compilatore come errori.

   Per altre informazioni, vedere l'opzione **/WX** in [/w, /W0, /W1, /W2, /W3, /W4, /w1, /w2, /w3, /w4, /Wall, /wd, /we, /wo, /Wv, /WX (livello di avviso).](/cpp/build/reference/compiler-option-warning-level)

- **TreatWChar_tAsBuiltInType**

   Parametro `Boolean` facoltativo.

   Se `true`, considerare il tipo `wchar_t` come un tipo nativo.

   Per altre informazioni, vedere [/Zc:wchar_t (wchar_t è un tipo nativo).](/cpp/build/reference/zc-wchar-t-wchar-t-is-native-type)

- **UndefineAllPreprocessorDefinitions**

   Parametro `Boolean` facoltativo.

   Se `true`, rimuove la definizione dei simboli specifici di Microsoft definiti dal compilatore.

   Per altre informazioni, vedere **l'opzione /u** in [/U, /u (Undefine symbols)](/cpp/build/reference/u-u-undefine-symbols).

- **UndefinePreprocessorDefinitions**

   Parametro `String[]` facoltativo.

   Specifica un elenco di uno o più simboli del preprocessore per cui rimuovere la definizione.

   Per altre informazioni, vedere **l'opzione /U** in [/U, /u (Undefine symbols)](/cpp/build/reference/u-u-undefine-symbols).

- **UseFullPaths**

   Parametro `Boolean` facoltativo.

   Se `true`, visualizza il percorso completo dei file di codice sorgente passati al compilatore nella diagnostica.

   Per altre informazioni, vedere [/FC (percorso completo del file di codice sorgente nella diagnostica).](/cpp/build/reference/fc-full-path-of-source-code-file-in-diagnostics)

- **UseUnicodeForAssemblerListing**

   Parametro `Boolean` facoltativo.

   Se `true`, causa la creazione del file di output in formato UTF-8.

   Per altre informazioni, vedere **l'opzione /FAu** in [/FA, /Fa (file di elenco)](/cpp/build/reference/fa-fa-listing-file).

- **WarningLevel**

   Parametro `String` facoltativo.

   Specifica il livello massimo dell'avviso che verrà generato dal compilatore.

   Specificare uno dei valori seguenti, ognuno dei quali corrisponde a un'opzione della riga di comando.

  - **TurnOffAllWarnings**  -  **/W0**

  - **Livello 1**  -  **/W1**

  - **Livello 2**  -  **/W2**

  - **Livello 3**  -  **/W3**

  - **Livello 4**  -  **/W4**

  - **EnableAllWarnings**  -  **/Wall**

    Per altre informazioni, vedere l'opzione **/W**_n_ in [/w, /W0, /W1, /W2, /W3, /W4, /w1, /w2, /w3, /w4, /Wall, /wd, /we, /wo, /Wv, /WX (livello di avviso).](/cpp/build/reference/compiler-option-warning-level)

- **WholeProgramOptimization**

   Parametro `Boolean` facoltativo.

   Se `true`,abilita l'ottimizzazione dell'intero programma.

   Per altre informazioni, vedere [/GL (Ottimizzazione dell'intero programma).](/cpp/build/reference/gl-whole-program-optimization)

- **XMLDocumentationFileName**

   Parametro `String` facoltativo.

   Specifica il nome dei file di documentazione XML generati. Questo parametro può essere un nome di file o directory.

   Per altre informazioni, vedere l'argomento in /doc (Elaborare i commenti della `name` [documentazione) (C/C++).](/cpp/build/reference/doc-process-documentation-comments-c-cpp) Vedere anche il parametro **GenerateXMLDocumentationFiles** in questa tabella.

- **MinimalRebuildFromTracking**

   Parametro `Boolean` facoltativo.

   Se `true`, viene eseguita una compilazione incrementale verificata; se `false`, viene eseguita una ricompilazione.

- **TLogReadFiles**

   Parametro `ITaskItem[]` facoltativo.

   Specifica una matrice di elementi che rappresentano i *log di rilevamento dei file di lettura*.

   Un log di rilevamento dei file di lettura ( con estensione *tlog*) contiene i nomi dei file di input letti da un'attività e viene usato dal sistema di compilazione del progetto per supportare le compilazioni incrementali. Per altre informazioni, vedere i parametri **TrackerLogDirectory** e **TrackFileAccess** in questa tabella.

- **TLogWriteFiles**

   Parametro `ITaskItem[]` facoltativo.

   Specifica una matrice di elementi che rappresentano i *log di rilevamento dei file di scrittura*.

   Un log di rilevamento dei file di scrittura ( con estensione *tlog*) contiene i nomi dei file di output scritti da un'attività e viene usato dal sistema di compilazione del progetto per supportare le compilazioni incrementali. Per altre informazioni, vedere i parametri **TrackerLogDirectory** e **TrackFileAccess** in questa tabella.

- **TrackFileAccess**

   Parametro `Boolean` facoltativo.

   Se `true`, rileva i modelli di accesso ai file.

   Per altre informazioni, vedere i parametri **TLogReadFiles** e **TLogWriteFiles** in questa tabella.

## <a name="see-also"></a>Vedi anche

- [Informazioni di riferimento sulle attività](../msbuild/msbuild-task-reference.md)
