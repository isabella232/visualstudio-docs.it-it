---
title: Attività CL | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
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
- MSBuild (Visual C++), CL task
- CL task (MSBuild (Visual C++))
ms.assetid: 651ba971-b755-4f03-a549-4816beb3cc0d
caps.latest.revision: 21
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 8307bc2c9efcbbab531754cd2d49fa18b04cc48a
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 05/15/2019
ms.locfileid: "65698632"
---
# <a name="cl-task"></a>Attività CL
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Esegue il wrapping dello strumento del compilatore Visual C++, cl.exe. Il compilatore genera file eseguibili (EXE), librerie a collegamento dinamico (DLL) o moduli di codice (NETMODULE). Per altre informazioni, vedere [Opzioni del compilatore](https://msdn.microsoft.com/library/ed3376c8-bef4-4c9a-80e9-3b5da232644c).  
  
## <a name="parameters"></a>Parametri  
 Nella tabella che segue vengono descritti i parametri dell'attività **CL**. La maggior parte dei parametri di attività e alcuni set di parametri corrispondono a un'opzione della riga di comando.  
  
- **AdditionalIncludeDirectories**  
  
   Parametro String[] facoltativo.  
  
   Aggiunge una directory all'elenco delle directory in cui vengono cercati i file di inclusione.  
  
   Per altre informazioni, vedere [/I (Directory di inclusione aggiuntive)](https://msdn.microsoft.com/library/3e9add2a-5ed8-4d15-ad79-5b411e313a49).  
  
- **AdditionalOptions**  
  
   Parametro String facoltativo.  
  
   Elenco di opzioni della riga di comando. Ad esempio, "/*option1* /*option2* /*option#*". Usare questo parametro per specificare le opzioni della riga di comando che non sono rappresentate da altri parametri dell'attività.  
  
   Per altre informazioni, vedere [Opzioni del compilatore](https://msdn.microsoft.com/library/ed3376c8-bef4-4c9a-80e9-3b5da232644c).  
  
- **AdditionalUsingDirectories** Parametro String [] facoltativo.  
  
   Specifica una directory in cui il compilatore effettuerà la ricerca per risolvere i riferimenti di file passati alla direttiva **#using**.  
  
   Per altre informazioni, vedere [/AI (Specifica le directory di metadati)](https://msdn.microsoft.com/library/fb9c1846-504c-4a3b-bb39-c8696de32f6f).  
  
- **AlwaysAppend**  
  
   Parametro String facoltativo.  
  
   Stringa che viene sempre generata sulla riga di comando. Il valore predefinito è "**/c**".  
  
- **AssemblerListingLocation**  
  
   Crea un file di elenco che contiene il codice assembly.  
  
   Per altre informazioni, vedere l'opzione **/Fa** in [/FA, /Fa (File di listato)](https://msdn.microsoft.com/library/c7507d0e-c69d-44f9-b8e2-d2c398697402).  
  
- **AssemblerOutput**  
  
   Parametro String facoltativo.  
  
   Crea un file di elenco che contiene il codice assembly.  
  
   Specificare uno dei valori seguenti, ognuno dei quali corrisponde a un'opzione della riga di comando.  
  
  - **NoListing** - *\<none>*  
  
  - **AssemblyCode** - **/FA**  
  
  - **AssemblyAndMachineCode** - **/FAc**  
  
  - **AssemblyAndSourceCode** - **/FAs**  
  
  - **All** - **/FAcs**  
  
    Per altre informazioni, vedere le opzioni **/FA**, **/FAc**, **/FAs** e **/FAcs** in [/FA, /Fa (File di listato)](https://msdn.microsoft.com/library/c7507d0e-c69d-44f9-b8e2-d2c398697402).  
  
- **BasicRuntimeChecks**  
  
   Parametro String facoltativo.  
  
   Abilita e disabilita la funzionalità di controllo degli errori di run-time, con il pragma [runtime_checks](https://msdn.microsoft.com/library/ae50b43f-f88d-47ad-a2db-3389e9e7df5b).  
  
   Specificare uno dei valori seguenti, ognuno dei quali corrisponde a un'opzione della riga di comando.  
  
  - **Default** -                          *\<none>*  
  
  - **StackFrameRuntimeCheck** - **/RTCs**  
  
  - **UninitializedLocalUsageCheck** - **/RTCu**  
  
  - **EnableFastChecks** -                          **/RTC1**  
  
    Per altre informazioni, vedere [/RTC (Controlli di runtime)](https://msdn.microsoft.com/library/9702c558-412c-4004-acd5-80761f589368).  
  
- **BrowseInformation**  
  
   Parametro booleano facoltativo.  
  
   Se `true`, crea un file di informazioni di visualizzazione.  
  
   Per altre informazioni, vedere l'opzione **/FR** in [/FR, /Fr (Crea file sbr)](https://msdn.microsoft.com/library/3fd8f88b-3924-4feb-9393-287036a28896).  
  
- **BrowseInformationFile**  
  
   Parametro String facoltativo.  
  
   Specifica un nome di file per il file di informazioni di visualizzazione.  
  
   Per altre informazioni, vedere il parametro **BrowseInformation** in questa tabella e [/FR, /Fr (Crea file sbr)](https://msdn.microsoft.com/library/3fd8f88b-3924-4feb-9393-287036a28896).  
  
- **BufferSecurityCheck**  
  
   Parametro booleano facoltativo.  
  
   Se `true`, rileva alcuni sovraccarichi del buffer che sovrascrivono l'indirizzo del mittente, una tecnica comune per sfruttare il codice che non applica restrizioni per le dimensioni del buffer.  
  
   Per altre informazioni, vedere [/GS (Controllo sicurezza buffer)](https://msdn.microsoft.com/library/8d8a5ea1-cd5e-42e1-bc36-66e1cd7e731e).  
  
- **BuildingInIDE**  
  
   Parametro booleano facoltativo.  
  
   Se `true`, indica che **MSBuild** viene richiamato dall'IDE. In caso contrario, **MSBuild** viene richiamato sulla riga di comando.  
  
- **CallingConvention**  
  
   Parametro String facoltativo.  
  
   Specifica la convenzione di chiamata, che determina l'ordine in cui gli argomenti della funzione vengono inseriti nello stack, se la funzione chiamante o la funzione chiamata rimuove gli argomenti dallo stack alla fine della chiamata e la convenzione di decorazione dei nomi che il compilatore usa per identificare le singole funzioni.  
  
   Specificare uno dei valori seguenti, ognuno dei quali corrisponde a un'opzione della riga di comando.  
  
  - **Cdecl** - **/Gd**  
  
  - **FastCall** -                          **/Gr**  
  
  - **StdCall** -                          **/Gz**  
  
    Per altre informazioni, vedere [/Gd, /Gr, /Gv, /Gz (Convenzioni di chiamata)](https://msdn.microsoft.com/library/fd3110cb-2d77-49f2-99cf-a03f9ead00a3).  
  
- **CompileAs**  
  
   Parametro String facoltativo.  
  
   Specifica se compilare il file di input come file di origine C o C++.  
  
   Specificare uno dei valori seguenti, ognuno dei quali corrisponde a un'opzione della riga di comando.  
  
  - **Default** - *\<none>*  
  
  - **CompileAsC** - **/TC**  
  
  - **CompileAsCpp** - **/TP**  
  
    Per altre informazioni, vedere [/Tc, /Tp, /TC, /TP (Specifica il tipo di file di origine)](https://msdn.microsoft.com/library/7d9d0a65-338b-427c-8b48-fff30e2f9d2b).  
  
- **CompileAsManaged**  
  
   Parametro String facoltativo.  
  
   Consente alle applicazioni e ai componenti di usare le funzionalità di Common Language Runtime (CLR).  
  
   Specificare uno dei valori seguenti, ognuno dei quali corrisponde a un'opzione della riga di comando.  
  
  - **false** - *\<none>*  
  
  - **true** - **/clr**  
  
  - **Pure** - **/clr:pure**  
  
  - **Safe** - **/clr:safe**  
  
  - **OldSyntax** - **/clr:oldSyntax**  
  
    Per altre informazioni, vedere [/clr (Compilazione Common Language Runtime)](https://msdn.microsoft.com/library/fec5a8c0-40ec-484c-a213-8dec918c1d6c).  
  
- **CreateHotPatchableImage**  
  
   Parametro booleano facoltativo.  
  
   Se `true`, indica al compilatore di preparare un'immagine per *l'applicazione di una patch a caldo*. Questo parametro assicura che la prima istruzione di ogni funzione sia di due byte, condizione necessaria per l'applicazione di una patch a caldo.  
  
   Per altre informazioni, vedere [/hotpatch (Crea immagine con funzionalità di patch a caldo)](https://msdn.microsoft.com/library/aad539b6-c053-4c78-8682-853d98327798).  
  
- **DebugInformationFormat**  
  
   Parametro String facoltativo.  
  
   Seleziona il tipo delle informazioni di debug create per il programma e indica se tali informazioni vengono mantenute in file oggetto (OBJ) o in un database di programma (PDB).  
  
   Specificare uno dei valori seguenti, ognuno dei quali corrisponde a un'opzione della riga di comando.  
  
  - **OldStyle** - **/Z7**  
  
  - **ProgramDatabase** - **/Zi**  
  
  - **EditAndContinue** - **/ZI**  
  
    Per altre informazioni, vedere [/Z7, /Zd, /Zi, /ZI (Formato informazioni di debug)](https://msdn.microsoft.com/library/ce9fa7e1-0c9b-47e3-98ea-26d1a16257c8).  
  
- **DisableLanguageExtensions**  
  
   Parametro booleano facoltativo.  
  
   Se **true**, indica al compilatore di generare un errore per i costrutti di linguaggio che non sono compatibili con ANSI C o ANSI C++.  
  
   Per altre informazioni, vedere l'opzione **/Za** in [/Za, /Ze (Disabilita estensioni linguaggio)](https://msdn.microsoft.com/library/65e49258-7161-4289-a176-7c5c0656b1a2).  
  
- **DisableSpecificWarnings**  
  
   Parametro String[] facoltativo.  
  
   Disabilita i numeri di avviso specificati in un elenco delimitato da punti e virgola.  
  
   Per altre informazioni, vedere l'opzione `/wd` in [/w, /W0, /W1, /W2, /W3, /W4, /w1, /w2, /w3, /w4, /Wall, /wd, /we, /wo, /Wv, /WX (Livello di avviso)](https://msdn.microsoft.com/library/d6bc7bf5-c754-4879-909c-8e3a67e2629f).  
  
- **EnableEnhancedInstructionSet**  
  
   Parametro String facoltativo.  
  
   Specifica l'architettura per la generazione di codice che usa le istruzioni Streaming SIMD Extensions (SSE) e Streaming SIMD Extensions 2 (SSE2).  
  
   Specificare uno dei valori seguenti, ognuno dei quali corrisponde a un'opzione della riga di comando.  
  
  - **StreamingSIMDExtensions** - **/arch:SSE**  
  
  - **StreamingSIMDExtensions2** - **/arch:SSE2**  
  
    Per altre informazioni, vedere [/arch (x86)](https://msdn.microsoft.com/library/9dd5a75d-06e4-4674-aade-33228486078d).  
  
- **EnableFiberSafeOptimizations**  
  
   Parametro booleano facoltativo.  
  
   Se `true`, supporta l'indipendenza da fiber per i dati allocati usando l'archiviazione locale di thread statici, ovvero dati allocati usando `__declspec(thread)`.  
  
   Per altre informazioni, vedere [/GT (Supporta archiviazione locale di thread indipendente da fiber)](https://msdn.microsoft.com/library/071fec79-c701-432b-9970-457344133159).  
  
- **EnablePREfast**  
  
   Parametro booleano facoltativo.  
  
   Se `true`, abilitare l'analisi del codice.  
  
   Per altre informazioni, vedere [/analyze (Analisi codice)](https://msdn.microsoft.com/library/81da536a-e030-4bd4-be18-383927597d08).  
  
- **ErrorReporting**  
  
   Parametro String facoltativo.  
  
   Consente di inviare informazioni sugli errori interni del compilatore direttamente a Microsoft. Per impostazione predefinita, l'impostazione nelle build IDE è **Prompt** e l'impostazione nelle build da riga di comando è **Queue**.  
  
   Specificare uno dei valori seguenti, ognuno dei quali corrisponde a un'opzione della riga di comando.  
  
  - **None** - **/errorReport:none**  
  
  - **Prompt** - **/errorReport:prompt**  
  
  - **Queue** - **/errorReport:queue**  
  
  - **Send** - **/errorReport:send**  
  
    Per altre informazioni, vedere [/errorReport (Segnala gli errori interni del compilatore)](https://msdn.microsoft.com/library/819828f8-b0a5-412c-9c57-bf822f17e667).  
  
- **ExceptionHandling**  
  
   Parametro String facoltativo.  
  
   Specifica il modello di gestione delle eccezioni che deve essere usato dal compilatore.  
  
   Specificare uno dei valori seguenti, ognuno dei quali corrisponde a un'opzione della riga di comando.  
  
  - **false** - *\<none>*  
  
  - **Async** - **/EHa**  
  
  - **Sync** - **/EHsc**  
  
  - **SyncCThrow** - **/EHs**  
  
    Per altre informazioni, vedere [/EH (Modello di gestione delle eccezioni)](https://msdn.microsoft.com/library/754b916f-d206-4472-b55a-b6f1b0f2cb4d).  
  
- **ExpandAttributedSource**  
  
   Parametro booleano facoltativo.  
  
   Se `true`, viene creato un file di listato con attributi espansi inseriti nel file di origine.  
  
   Per altre informazioni, vedere [/Fx (Esegue il merge del codice)](https://msdn.microsoft.com/library/14f0e301-3bab-45a3-bbdf-e7ce66f20560).  
  
- **FavorSizeOrSpeed**  
  
   Parametro String facoltativo.  
  
   Specifica se ottimizzare la dimensione o la velocità del codice.  
  
   Specificare uno dei valori seguenti, ognuno dei quali corrisponde a un'opzione della riga di comando.  
  
  - **Neither** - *\<none>*  
  
  - **Size** - **/Os**  
  
  - **Speed** - **/Ot**  
  
    Per altre informazioni, vedere [/Os, /Ot (Ottimizza per dimensione codice, Ottimizza per velocità codice)](https://msdn.microsoft.com/library/9a340806-fa15-4308-892c-355d83cac0f2).  
  
- **FloatingPointExceptions**  
  
   Parametro booleano facoltativo.  
  
   Se `true`, abilita il modello di eccezione a virgola mobile affidabile. Vengono generate eccezioni immediatamente dopo l'attivazione.  
  
   Per altre informazioni, vedere l'opzione /**fp:except** in [/fp (Specifica il comportamento della virgola mobile)](https://msdn.microsoft.com/library/10469d6b-e68b-4268-8075-d073f4f5d57e).  
  
- **FloatingPointModel**  
  
   Parametro String facoltativo.  
  
   Imposta il modello a virgola mobile.  
  
   Specificare uno dei valori seguenti, ognuno dei quali corrisponde a un'opzione della riga di comando.  
  
  - **Precise** - **/fp:precise**  
  
  - **Strict** - **/fp:strict**  
  
  - **Fast** - **/fp:fast**  
  
    Per altre informazioni, vedere [/fp (Specifica il comportamento della virgola mobile)](https://msdn.microsoft.com/library/10469d6b-e68b-4268-8075-d073f4f5d57e).  
  
- **ForceConformanceInForLoopScope**  
  
   Parametro booleano facoltativo.  
  
   Se `true`, consente di implementare il comportamento C++ standard per cicli [for](https://msdn.microsoft.com/library/6c7d01b3-c4c1-4c6a-aa58-e2d198f33d4a) con estensioni Microsoft ([/Ze](https://msdn.microsoft.com/library/65e49258-7161-4289-a176-7c5c0656b1a2)).  
  
   Per altre informazioni, vedere [/Zc:forScope (Imponi conformità nell'ambito di un ciclo For)](https://msdn.microsoft.com/library/3031f02d-3b14-4ad0-869e-22b0110c3aed).  
  
- **ForcedIncludeFiles**  
  
   Parametro `String[]` facoltativo.  
  
   Determina l'elaborazione di uno o più file di intestazione specificati da parte del preprocessore.  
  
   Per altre informazioni, vedere [/FI (Specifica il file di inclusione da utilizzare)](https://msdn.microsoft.com/library/07e79577-8152-4df9-a64c-aae08c603397).  
  
- **ForcedUsingFiles**  
  
   Parametro **String[]** facoltativo.  
  
   Determina l'elaborazione di uno o più file **#using** specificati da parte del preprocessore.  
  
   Per altre informazioni, vedere [/FU (Specifica file #using da utilizzare)](https://msdn.microsoft.com/library/698f8603-457f-435a-baff-5ac9243d6ca1).  
  
- **FunctionLevelLinking**  
  
   Parametro `Boolean` facoltativo.  
  
   Se `true`, indica al compilatore di assemblare le singole funzioni sotto forma di funzioni incluse nel pacchetto (COMDAT).  
  
   Per altre informazioni, vedere [/Gy (Attiva collegamento a livello di funzione)](https://msdn.microsoft.com/library/0d3cf14c-ed7d-4ad3-b4b6-104e56f61046).  
  
- **GenerateXMLDocumentationFiles**  
  
   Parametro `Boolean` facoltativo.  
  
   Se `true`, indica al compilatore di elaborare i commenti per la documentazione nei file del codice sorgente e di creare un file XDC per ogni file del codice sorgente che contiene commenti per la documentazione.  
  
   Per altre informazioni, vedere [/doc (Elabora i commenti per la documentazione) (C/C++)](https://msdn.microsoft.com/library/b54f7e2c-f28f-4f46-9ed6-0db09be2cc63). Vedere anche il parametro **XMLDocumentationFileName** in questa tabella.  
  
- **IgnoreStandardIncludePath**  
  
   Parametro `Boolean` facoltativo.  
  
   Se `true`, impedisce al compilatore di cercare file di inclusione nelle directory specificate nelle variabili di ambiente PATH e INCLUDE.  
  
   Per altre informazioni, vedere [/X (Ignora percorso di inclusione standard)](https://msdn.microsoft.com/library/16bdf2cc-c8dc-46e4-bdcc-f3caeba5e1ef).  
  
- **InlineFunctionExpansion**  
  
   Parametro **String** facoltativo.  
  
   Specifica il livello di espansione della funzione inline per la compilazione.  
  
   Specificare uno dei valori seguenti, ognuno dei quali corrisponde a un'opzione della riga di comando.  
  
  - **Default** - *\<none>*  
  
  - **Disabled** - **/Ob0**  
  
  - **OnlyExplicitInline** - **/Ob1**  
  
  - **AnySuitable** - **/Ob2**  
  
    Per altre informazioni, vedere [/Ob (Espansione funzioni inline)](https://msdn.microsoft.com/library/f134e6df-e939-4980-a01d-47425dbc562a).  
  
- **IntrinsicFunctions**  
  
   Parametro `Boolean` facoltativo.  
  
   Se `true`, sostituisce alcune chiamate di funzione con form intrinseci o speciali della funzione che consentono di eseguire l'applicazione più rapidamente.  
  
   Per altre informazioni, vedere [/Oi (Genera funzioni intrinseche)](https://msdn.microsoft.com/library/fa4a3bf6-0ed8-481b-91c0-add7636132b4).  
  
- **MinimalRebuild**  
  
   Parametro `Boolean` facoltativo.  
  
   Se `true`, abilita la ricompilazione minima, che determina se è necessario ricompilare i file di origine C++ che includono modifiche alle definizioni delle classi C++ archiviate nei file di intestazione (estensione h).  
  
   Per altre informazioni, vedere [/Gm (Abilita ricompilazione minima)](https://msdn.microsoft.com/library/d8869ce0-d2ea-40eb-8dae-6d2cdb61dd59).  
  
- **MultiProcessorCompilation**  
  
   Parametro `Boolean` facoltativo.  
  
   Se `true`, usare più processori per la compilazione. Questo parametro crea un processo per ogni processore effettivo nel computer in uso.  
  
   Per altre informazioni, vedere [/MP (Compilazione con più processi)](https://msdn.microsoft.com/library/a932b14a-74fe-4b45-84e4-6bf53f0f5e07). Vedere anche il parametro **ProcessorNumber** in questa tabella.  
  
- **ObjectFileName**  
  
   Parametro **String** facoltativo.  
  
   Specifica un nome file oggetto (OBJ) o una directory da usare al posto dell'impostazione predefinita.  
  
   Per altre informazioni, vedere [/Fo (Nome file oggetto)](https://msdn.microsoft.com/library/0e6d593e-4e7f-4990-9e6e-92e1dcbcf6e6).  
  
- **ObjectFiles**  
  
   Parametro **String[]** facoltativo.  
  
   Elenco di file oggetto.  
  
- **OmitDefaultLibName**  
  
   Parametro `Boolean` facoltativo.  
  
   Se `true`, omette il nome della libreria di runtime C predefinita nel file oggetto (OBJ). Per impostazione predefinita, il compilatore inserisce il nome della libreria nel file OBJ per indirizzare il linker alla libreria corretta.  
  
   Per altre informazioni, vedere [/Zl (Omette il nome della libreria predefinita)](https://msdn.microsoft.com/library/b27d39d0-44d6-498c-84ae-27c1326fee59).  
  
- **OmitFramePointers**  
  
   Parametro `Boolean` facoltativo.  
  
   Se `true`, disabilita la creazione di puntatori ai frame nello stack di chiamate.  
  
   Per altre informazioni, vedere [/Oy (Omissione dei puntatori ai frame)](https://msdn.microsoft.com/library/c451da86-5297-4c5a-92bc-561d41379853).  
  
- **OpenMPSupport**  
  
   Parametro `Boolean` facoltativo.  
  
   Se `true`, indica al compilatore di elaborare direttive e clausole OpenMP.  
  
   Per altre informazioni, vedere [/openmp (Attiva supporto OpenMP 2.0)](https://msdn.microsoft.com/library/9082b175-18d3-4378-86a7-c0eb95664e13).  
  
- **Optimization**  
  
   Parametro **String** facoltativo.  
  
   Specifica diverse ottimizzazioni del codice per velocità e dimensioni.  
  
   Specificare uno dei valori seguenti, ognuno dei quali corrisponde a un'opzione della riga di comando.  
  
  - **Disabled** - **/Od**  
  
  - **MinSpace** - **/O1**  
  
  - **MaxSpeed** - **/O2**  
  
  - **Full** - **/Ox**  
  
    Per altre informazioni, vedere [Opzioni /O (Ottimizza codice)](https://msdn.microsoft.com/library/77997af9-5555-4b3d-aa57-6615b27d4d5d).  
  
- **PrecompiledHeader**  
  
   Parametro **String** facoltativo.  
  
   Creare o usare un file di intestazione precompilata (PCH) durante la compilazione.  
  
   Specificare uno dei valori seguenti, ognuno dei quali corrisponde a un'opzione della riga di comando.  
  
  - **NotUsing** - *\<none>*  
  
  - **Create** - **/Yc**  
  
  - **Use** - **/Yu**  
  
    Per altre informazioni, vedere [/Yc (Crea il file di intestazione precompilata)](https://msdn.microsoft.com/library/47c2e555-b4f5-46e6-906e-ab5cf21f0678) e [/Yu (Usa il file di intestazione precompilata)](https://msdn.microsoft.com/library/24f1bd0e-b624-4296-a17e-d4b53e374e1f). Vedere anche i parametri **PrecompiledHeaderFile** e **PrecompiledHeaderOutputFile** in questa tabella.  
  
- **PrecompiledHeaderFile**  
  
   Parametro **String** facoltativo.  
  
   Specifica un nome di file di intestazione precompilata da creare o usare.  
  
   Per altre informazioni, vedere [/Yc (Crea il file di intestazione precompilata)](https://msdn.microsoft.com/library/47c2e555-b4f5-46e6-906e-ab5cf21f0678) e [/Yu (Usa il file di intestazione precompilata)](https://msdn.microsoft.com/library/24f1bd0e-b624-4296-a17e-d4b53e374e1f).  
  
- **PrecompiledHeaderOutputFile**  
  
   Parametro **String** facoltativo.  
  
   Specifica un nome di percorso per un'intestazione precompilata anziché usare il nome di percorso predefinito.  
  
   Per altre informazioni, vedere [/Fp (Specifica file pch)](https://msdn.microsoft.com/library/0fcd9cbd-e09f-44d3-9715-b41efb5d0be2).  
  
- **PreprocessKeepComments**  
  
   Parametro `Boolean` facoltativo.  
  
   Se `true`, conserva i commenti durante la pre-elaborazione.  
  
   Per altre informazioni, vedere [/C (Conserva i commenti durante la pre-elaborazione)](https://msdn.microsoft.com/library/944567ca-16bc-4728-befe-d414a7787f26).  
  
- **PreprocessorDefinitions**  
  
   Parametro `String[]` facoltativo.  
  
   Definisce un simbolo di pre-elaborazione per il file di origine.  
  
   Per altre informazioni, vedere [/D (definizioni preprocessore)](https://msdn.microsoft.com/library/b53fdda7-8da1-474f-8811-ba7cdcc66dba).  
  
- **PreprocessOutput**  
  
   Parametro `ITaskItem[]` facoltativo.  
  
   Definisce una matrice di elementi di output del preprocessore che può essere usata ed emessa dalle attività.  
  
- **PreprocessOutputPath**  
  
   Parametro `String` facoltativo.  
  
   Specifica il nome del file di output in cui il parametro **PreprocessToFile** scrive l'output pre-elaborato.  
  
   Per altre informazioni, vedere [/Fi (pre-elaborazione nome file di output)](https://msdn.microsoft.com/library/6d0ba983-a8b7-41ec-84f5-b4688ef8efee).  
  
- **PreprocessSuppressLineNumbers**  
  
   Parametro `Boolean` facoltativo.  
  
   Se `true`, pre-elabora i file di origine C e C++ e copia i file pre-elaborati nel dispositivo di output standard.  
  
   Per altre informazioni, vedere [/EP (Pre-elabora in stdout senza direttive #line)](https://msdn.microsoft.com/library/6ec411ae-e33d-4ef5-956e-0054635eabea).  
  
- **PreprocessToFile**  
  
   Parametro `Boolean` facoltativo.  
  
   Se `true`, pre-elabora i file di origine C e C++ e scrive l'output pre-elaborato in un file.  
  
   Per altre informazioni, vedere [/P (Pre-elabora in un file)](https://msdn.microsoft.com/library/123ee54f-8219-4a6f-9876-4227023d83fc).  
  
- **ProcessorNumber**  
  
   Parametro `Integer` facoltativo.  
  
   Specifica il numero massimo di processori da usare in una compilazione multiprocessore. Usare questo parametro in combinazione con il parametro **MultiProcessorCompilation**.  
  
- **ProgramDataBaseFileName**  
  
   Parametro `String` facoltativo.  
  
   Specifica un nome file per il file del database di programma (PDB).  
  
   Per altre informazioni, vedere [/Fd (Nome file database di programma)](https://msdn.microsoft.com/library/3977a9ed-f0ac-45df-bf06-01cedd2ba85a).  
  
- **RuntimeLibrary**  
  
   Parametro `String` facoltativo.  
  
   Indica se un modulo con multithreading è una DLL e seleziona versioni finali o di debug della libreria di runtime.  
  
   Specificare uno dei valori seguenti, ognuno dei quali corrisponde a un'opzione della riga di comando.  
  
  - **MultiThreaded** - **/MT**  
  
  - **MultiThreadedDebug** - **/MTd**  
  
  - **MultiThreadedDLL** - **/MD**  
  
  - **MultiThreadedDebugDLL** - **/MDd**  
  
    Per altre informazioni, vedere [/MD, /MT, /LD (utilizzo della libreria di runtime)](https://msdn.microsoft.com/library/cf7ed652-dc3a-49b3-aab9-ad60e5395579).  
  
- **RuntimeTypeInfo**  
  
   Parametro `Boolean` facoltativo.  
  
   Se `true`, aggiunge codice per il controllo dei tipi di oggetto C++ in fase di esecuzione (informazioni sui tipi di runtime).  
  
   Per altre informazioni, vedere [/GR (Attiva informazioni sui tipi in fase di esecuzione)](https://msdn.microsoft.com/library/d1f9f850-dcec-49fd-96ef-e72d01148906).  
  
- **ShowIncludes**  
  
   Parametro `Boolean` facoltativo.  
  
   Se `true`, indica al compilatore di generare un elenco di file di inclusione.  
  
   Per altre informazioni, vedere [/showIncludes (Elenca i file di inclusione)](https://msdn.microsoft.com/library/0b74b052-f594-45a6-a7c7-09e1a319547d).  
  
- **SmallerTypeCheck**  
  
   Parametro `Boolean` facoltativo.  
  
   Se `true`, segnala un errore di run-time se un valore viene assegnato a un tipo di dati più piccolo e provoca una perdita di dati.  
  
   Per altre informazioni, vedere l'opzione **/RTCc** in [/RTC (Controlli di runtime)](https://msdn.microsoft.com/library/9702c558-412c-4004-acd5-80761f589368).  
  
- **Sources**  
  
   Parametro `ITaskItem[]` obbligatorio.  
  
   Specifica un elenco dei file di origine separati da spazi.  
  
- **StringPooling**  
  
   Parametro `Boolean` facoltativo.  
  
   Se `true`, consente al compilatore di creare una copia di stringhe identiche nell'immagine del programma.  
  
   Per altre informazioni, vedere [/GF (Elimina stringhe duplicate)](https://msdn.microsoft.com/library/bb7b5d1c-8e1f-453b-9298-8fcebf37d16c).  
  
- **StructMemberAlignment**  
  
   Parametro `String` facoltativo.  
  
   Specifica l'allineamento dei byte per tutti i membri in una struttura.  
  
   Specificare uno dei valori seguenti, ognuno dei quali corrisponde a un'opzione della riga di comando.  
  
  - **Default** - **/Zp1**  
  
  - **1Byte** - **/Zp1**  
  
  - **2Bytes** - **/Zp2**  
  
  - **4Bytes** - **/Zp4**  
  
  - **8Bytes** - **/Zp8**  
  
  - **16Bytes** - **/Zp16**  
  
    Per altre informazioni, vedere [/Zp (Allineamento membri struct)](https://msdn.microsoft.com/library/5242f656-ed9b-48a3-bc73-cfcf3ed2520f).  
  
- **SuppressStartupBanner**  
  
   Parametro `Boolean` facoltativo.  
  
   Se `true`, impedisce la visualizzazione del messaggio sul copyright e sul numero di versione all'avvio dell'attività.  
  
   Per altre informazioni, vedere [/nologo (Non visualizza il messaggio di avvio) (C/C++)](https://msdn.microsoft.com/library/75930d8b-b11c-4db8-99e5-b52f97da0693).  
  
- **TrackerLogDirectory**  
  
   Parametro `String` facoltativo.  
  
   Specifica la directory intermedia in cui sono archiviati i log di rilevamento per questa attività.  
  
   Per altre informazioni, vedere i parametri **TLogReadFiles** e **TLogWriteFiles** in questa tabella.  
  
- **TreatSpecificWarningsAsErrors**  
  
   Parametro **String[]** facoltativo.  
  
   Considera l'elenco specificato di avvisi del compilatore come errori.  
  
   Per altre informazioni, vedere l'opzione **/we**`n` in [/w, /W0, /W1, /W2, /W3, /W4, /w1, /w2, /w3, /w4, /Wall, /wd, /we, /wo, /Wv, /WX (Livello di avviso)](https://msdn.microsoft.com/library/d6bc7bf5-c754-4879-909c-8e3a67e2629f).  
  
- **TreatWarningAsError**  
  
   Parametro `Boolean` facoltativo.  
  
   Se `true`, considera tutti gli avvisi del compilatore come errori.  
  
   Per altre informazioni, vedere l'opzione **/WX**in [/w, /W0, /W1, /W2, /W3, /W4, /w1, /w2, /w3, /w4, /Wall, /wd, /we, /wo, /Wv, /WX (Livello di avviso)](https://msdn.microsoft.com/library/d6bc7bf5-c754-4879-909c-8e3a67e2629f).  
  
- **TreatWChar_tAsBuiltInType**  
  
   Parametro `Boolean` facoltativo.  
  
   Se `true`, considerare il tipo `wchar_t` come un tipo nativo.  
  
   Per altre informazioni, vedere [/Zc:wchar_t (Tipo nativo wchar_t)](https://msdn.microsoft.com/library/b0de5a84-da72-4e5a-9a4e-541099f939e0).  
  
- **UndefineAllPreprocessorDefinitions**  
  
   Parametro `Boolean` facoltativo.  
  
   Se `true`, rimuove la definizione dei simboli specifici di Microsoft definiti dal compilatore.  
  
   Per altre informazioni, vedere l'opzione **/u** in [/U, /u (Annulla la definizione dei simboli)](https://msdn.microsoft.com/library/7bc0474f-6d1f-419b-807d-0d8816763b2a).  
  
- **UndefinePreprocessorDefinitions**  
  
   Parametro `String[]` facoltativo.  
  
   Specifica un elenco di uno o più simboli del preprocessore per cui rimuovere la definizione.  
  
   Per altre informazioni, vedere l'opzione **/U** in [/U, /u (Annulla la definizione dei simboli)](https://msdn.microsoft.com/library/7bc0474f-6d1f-419b-807d-0d8816763b2a).  
  
- **UseFullPaths**  
  
   Parametro `Boolean` facoltativo.  
  
   Se `true`, visualizza il percorso completo dei file di codice sorgente passati al compilatore nella diagnostica.  
  
   Per altre informazioni, vedere [/FC (Percorso completo del file di codice sorgente nella diagnostica)](https://msdn.microsoft.com/library/1f11414e-cb42-421b-be68-9d369aab036b).  
  
- **UseUnicodeForAssemblerListing**  
  
   Parametro `Boolean` facoltativo.  
  
   Se `true`, causa la creazione del file di output in formato UTF-8.  
  
   Per altre informazioni, vedere l'opzione **/FAu** in [/FA, /Fa (File di listato)](https://msdn.microsoft.com/library/c7507d0e-c69d-44f9-b8e2-d2c398697402).  
  
- **WarningLevel**  
  
   Parametro `String` facoltativo.  
  
   Specifica il livello massimo dell'avviso che verrà generato dal compilatore.  
  
   Specificare uno dei valori seguenti, ognuno dei quali corrisponde a un'opzione della riga di comando.  
  
  - **TurnOffAllWarnings** - **/W0**  
  
  - **Level1** - **/W1**  
  
  - **Level2** - **/W2**  
  
  - **Level3** - **/W3**  
  
  - **Level4** - **/W4**  
  
  - **EnableAllWarnings** - **/Wall**  
  
    Per altre informazioni, vedere l'opzione **/W**_n_ in [/w, /W0, /W1, /W2, /W3, /W4, /w1, /w2, /w3, /w4, /Wall, /wd, /we, /wo, /Wv, /WX (Livello di avviso)](https://msdn.microsoft.com/library/d6bc7bf5-c754-4879-909c-8e3a67e2629f).  
  
- **WholeProgramOptimization**  
  
   Parametro `Boolean` facoltativo.  
  
   Se `true`,abilita l'ottimizzazione dell'intero programma.  
  
   Per altre informazioni, vedere [/GL (Ottimizzazione intero programma)](https://msdn.microsoft.com/library/09d51e2d-9728-4bd0-b5dc-3b8284aca1d1).  
  
- **XMLDocumentationFileName**  
  
   Parametro `String` facoltativo.  
  
   Specifica il nome dei file di documentazione XML generati. Questo parametro può essere un nome di file o directory.  
  
   Per altre informazioni, vedere l'argomento `name` in [/doc (Elabora i commenti per la documentazione) (C/C++)](https://msdn.microsoft.com/library/b54f7e2c-f28f-4f46-9ed6-0db09be2cc63). Vedere anche il parametro **GenerateXMLDocumentationFiles** in questa tabella.  
  
- **MinimalRebuildFromTracking**  
  
   Parametro `Boolean` facoltativo.  
  
   Se `true`, viene eseguita una compilazione incrementale verificata; se `false`, viene eseguita una ricompilazione.  
  
- **TLogReadFiles**  
  
   Parametro `ITaskItem[]` facoltativo.  
  
   Specifica una matrice di elementi che rappresentano i *log di rilevamento dei file di lettura*.  
  
   Un log di rilevamento dei file di lettura (TLOG) contiene i nomi dei file di input letti da un'attività e viene usato dal sistema di compilazione del progetto per supportare le compilazioni incrementali. Per altre informazioni, vedere i parametri **TrackerLogDirectory** e **TrackFileAccess** in questa tabella.  
  
- **TLogWriteFiles**  
  
   Parametro `ITaskItem[]` facoltativo.  
  
   Specifica una matrice di elementi che rappresentano i *log di rilevamento dei file di scrittura*.  
  
   Un log di rilevamento dei file di scrittura (TLOG) contiene i nomi dei file di output scritti da un'attività e viene usato dal sistema di compilazione del progetto per supportare le compilazioni incrementali. Per altre informazioni, vedere i parametri **TrackerLogDirectory** e **TrackFileAccess** in questa tabella.  
  
- **TrackFileAccess**  
  
   Parametro `Boolean` facoltativo.  
  
   Se `true`, rileva i modelli di accesso ai file.  
  
   Per altre informazioni, vedere i parametri **TLogReadFiles** e **TLogWriteFiles** in questa tabella.  
  
## <a name="remarks"></a>Osservazioni  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimenti alle attività](../msbuild/msbuild-task-reference.md)
