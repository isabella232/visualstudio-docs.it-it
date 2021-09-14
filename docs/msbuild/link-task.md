---
title: Attività Link | Microsoft Docs
description: Informazioni su MSBuild'attività Collega per eseguire il wrapping dello strumento del linker Microsoft C++, link.exe, che collega librerie e file di oggetti COFF.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- VC.Project.VCLinkerTool.ForceFileOutput
- VC.Project.VCLinkerTool.LinkStatus
- VC.Project.VCLinkerTool.CLRUnmanagedCodeCheck
- VC.Project.VCLinkerTool.SpecifySectionAttributes
- VC.Project.VCLinkerTool.SupportNobindOfDelayLoadedDLL
- VC.Project.VCLinkerTool.MinimumRequiredVersion
- VC.Project.VCLinkerTool.PerUserRedirection
- VC.Project.VCLinkerTool.CreateHotPatchableImage
- VC.Project.VCLinkerTool.DataExecutionPrevention
- VC.Project.VCLinkerTool.TreatLinkerWarningsAsErrors
- vc.task.link
- VC.Project.VCLinkerTool.ImageHasSafeExceptionHandlers
- VC.Project.VCLinkerTool.CLRSupportLastError
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild (C++), Link task
- Link task (MSBuild (C++))
ms.assetid: 0a61f168-3113-4fa7-83a3-d9142e2a33f8
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: 6a7f986674aa215e2fae98dc469bd1807afcedbc
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126625667"
---
# <a name="link-task"></a>Link (attività)

Esegue il wrapping dello strumento del linker Microsoft C++, *link.exe*. Lo strumento linker consente di collegare file in formato COFF (Common Object File Format ) e librerie per creare un file eseguibile (con estensione *exe*) o una libreria di collegamento dinamico (DLL). Per altre informazioni, vedere [](/cpp/build/msbuild-visual-cpp) Opzioni del [linker](/cpp/build/reference/linker-options) e Usare MSBuild dalla riga di comando e Usare il set di strumenti [Microsoft C++ dalla riga di comando.](/cpp/build/building-on-the-command-line)

## <a name="parameters"></a>Parametri

 Di seguito vengono descritti i parametri dell'attività **Link**. La maggior parte dei parametri di attività e alcuni set di parametri corrispondono a un'opzione della riga di comando.

- **AdditionalDependencies**

  Parametro **Facoltativo String[].**

  Specifica un elenco di file di input da aggiungere al comando.

  Per altre informazioni, vedere [File di input LINK](/cpp/build/reference/link-input-files).

- **AdditionalLibraryDirectories**

  Parametro **Facoltativo String[].**

  Esegue l'override del percorso delle librerie dell'ambiente. Specificare un nome di directory.

  Per altre informazioni, vedere [/LIBPATH (Percorso LIB aggiuntivo)](/cpp/build/reference/libpath-additional-libpath).

- **AdditionalManifestDependencies**

  Parametro **Facoltativo String[].**

  Specifica gli attributi che verranno inseriti nella sezione `dependency` del file manifesto.

  Per altre informazioni, vedere [/MANIFESTDEPENDENCY (Specifica le dipendenze tra manifesti)](/cpp/build/reference/manifestdependency-specify-manifest-dependencies). Vedere anche [Publisher Configuration Files](/windows/desktop/SbsCs/publisher-configuration-files) (File di configurazione del server di pubblicazione).

- **AdditionalOptions**

  Parametro **String** facoltativo.

  Un elenco di opzioni del linker come specificato nella riga di comando. Ad esempio, / \<option1>  / \<option2>  / \<option#> . Usare questo parametro per specificare le opzioni del linker che non sono rappresentate da altri parametri dell'attività **Link**.

  Per altre informazioni, vedere [Opzioni del linker](/cpp/build/reference/linker-options).

- **AddModuleNamesToAssembly**

  Parametro **Facoltativo String[].**

  Aggiunge un riferimento del modulo a un assembly.

  Per altre informazioni, vedere [/ASSEMBLYMODULE (aggiunge un modulo MSIL all'assembly)](/cpp/build/reference/assemblymodule-add-a-msil-module-to-the-assembly).

- **AllowIsolation**

  Parametro **booleano** facoltativo.

  Se `true`, fa eseguire al sistema operativo ricerche e caricamenti del manifesto. Se `false`, indica che le DLL vengono caricate come se il manifesto non esistesse.

  Per altre informazioni, vedere [/ALLOWISOLATION (Ricerca manifesto).](/cpp/build/reference/allowisolation-manifest-lookup)

- **AssemblyDebug**

  Parametro **booleano** facoltativo.

  Se `true`, crea l'attributo **DebuggableAttribute** con il rilevamento delle informazioni di debug e disabilita le ottimizzazioni JIT. Se `false`, crea l'attributo **DebuggableAttribute**, ma disabilita il rilevamento delle informazioni di debug e abilita le ottimizzazioni JIT.

  Per altre informazioni, vedere [/ASSEMBLYDEBUG (Aggiunge DebuggableAttribute)](/cpp/build/reference/assemblydebug-add-debuggableattribute).

- **AssemblyLinkResource**

  Parametro **Facoltativo String[].**

  Crea un collegamento a una risorsa .NET Framework nel file di output. Il file di risorse non viene inserito nel file di output. Specificare il nome della risorsa.

  Per altre informazioni, vedere [/ASSEMBLYLINKRESOURCE (collegamento .NET Framework risorsa)](/cpp/build/reference/assemblylinkresource-link-to-dotnet-framework-resource).

- **AttributeFileTracking**

  Parametro **Boolean** implicito.

  Abilita un rilevamento file più approfondito per acquisire il comportamento del collegamento incrementale. Restituisce sempre `true`.

- **Baseaddress**

  Parametro **String** facoltativo.

  Imposta un indirizzo di base per il programma o la DLL da compilare. Specificare `{address[,size] | @filename,key}`.

  Per altre informazioni, vedere [/BASE (indirizzo di base)](/cpp/build/reference/base-base-address).

- **BuildingInIDE**

  Parametro **booleano** facoltativo.

  Se true, indica che MSBuild viene richiamato dall'ambiente IDE. In caso contrario, indica che MSBuild viene richiamato dalla riga di comando.

  Questo parametro non ha un'opzione del linker equivalente.

- **CLRImageType**

  Parametro **String** facoltativo.

  Imposta il tipo di un'immagine Common Language Runtime (CLR).

  Specificare uno dei valori seguenti, ognuno dei quali corrisponde a un'opzione del linker.

  - **Predefinito** - *\<none>*

  - **ForceIJWImage**  -  **/CLRIMAGETYPE:IJW**

  - **ForcePureILImage**  -  **/CLRIMAGETYPE:PURE**

  - **ForceSafeILImage**  -  **/CLRIMAGETYPE:SAFE**

  Per altre informazioni, vedere [/CLRIMAGETYPE (Specificare il tipo di immagine CLR).](/cpp/build/reference/clrimagetype-specify-type-of-clr-image)

- **CLRSupportLastError**

  Parametro **String** facoltativo.

  Conserva l'ultimo codice di errore delle funzioni chiamate con il meccanismo P/Invoke.

  Specificare uno dei valori seguenti, ognuno dei quali corrisponde a un'opzione del linker.

  - **Abilitato**  -  **/CLRSupportLastError**

  - **Disabilitato**  -  **/CLRSupportLastError:NO**

  - **SystemDlls**  -  **/CLRSupportLastError:SYSTEMDLL**

  Per altre informazioni, vedere [/CLRSUPPORTLASTERROR (Mantieni l'ultimo codice di errore per le chiamate PInvoke).](/cpp/build/reference/clrsupportlasterror-preserve-last-error-code-for-pinvoke-calls)

- **CLRThreadAttribute**

  Parametro **String** facoltativo.

  Specifica in modo esplicito l'attributo threading per il punto di ingresso del programma CLR.

  Specificare uno dei valori seguenti, ognuno dei quali corrisponde a un'opzione del linker.

  - **DefaultThreadingAttribute**  -  **/CLRTHREADATTRIBUTE:NONE**

  - **MTAThreadingAttribute**  -  **/CLRTHREADATTRIBUTE:MTA**

  - **STAThreadingAttribute**  -  **/CLRTHREADATTRIBUTE:STA**

  Per altre informazioni, vedere [/CLRTHREADATTRIBUTE (Imposta attributo thread CLR)](/cpp/build/reference/clrthreadattribute-set-clr-thread-attribute).

- **CLRUnmanagedCodeCheck**

  Parametro **booleano** facoltativo.

  Specifica se verrà applicato **SuppressUnmanagedCodeSecurityAttribute** alle chiamate P/Invoke generate dal linker effettuate dal codice gestito in DLL native.

  Per altre informazioni, vedere [/CLRUNMANAGEDCODECHECK (Aggiungere SuppressUnmanagedCodeSecurityAttribute)](/cpp/build/reference/clrunmanagedcodecheck-add-suppressunmanagedcodesecurityattribute).

- **CreateHotPatchableImage**

  Parametro **String** facoltativo.

  Prepara un'immagine per l'applicazione di una patch a caldo.

  Specificare uno dei valori seguenti, che corrisponde a un'opzione del linker.

  - **Abilitato**  -  **/FUNCTIONPADMIN**

  - **X86Image**  -  **/FUNCTIONPADMIN:5**

  - **X64Image**  -  **/FUNCTIONPADMIN:6**

  - **ItaniumImage**  -  **/FUNCTIONPADMIN:16**

  Per altre informazioni, vedere [/FUNCTIONPADMIN (Crea un'immagine con hotpatch).](/cpp/build/reference/functionpadmin-create-hotpatchable-image)

- **DataExecutionPrevention**

  Parametro **booleano** facoltativo.

  Se `true`, indica che è stato eseguito il test di un eseguibile per verificarne la compatibilità con la funzionalità Protezione esecuzione programmi di Windows.

  Per altre informazioni, vedere [/NXCOMPAT (compatibile con Protezione esecuzione programmi)](/cpp/build/reference/nxcompat-compatible-with-data-execution-prevention).

- **DelayLoadDLLs**

  Parametro **String[]** facoltativo.

  Questo parametro fa in modo che le DLL vengano *caricate in ritardo*. Specificare il nome di una DLL di cui ritardare il caricamento.

  Per altre informazioni, vedere [/DELAYLOAD (importazione a caricamento ritardato)](/cpp/build/reference/delayload-delay-load-import).

- **DelaySign**

  Parametro **booleano** facoltativo.

  Se `true`, firma parzialmente un assembly. Per impostazione predefinita, il valore è `false`.

  Per altre informazioni, vedere [/DELAYSIGN (firma parzialmente un assembly)](/cpp/build/reference/delaysign-partially-sign-an-assembly).

- **Driver**

  Parametro **String** facoltativo.

  Specificare questo parametro per compilare un driver in modalità kernel Windows NT.

  Specificare uno dei valori seguenti, ognuno dei quali corrisponde a un'opzione del linker.

  - **Notset** - *\<none>*

  - **Driver**  -  **/Driver**

  - **UpOnly**  -  **/DRIVER:UPONLY**

  - **WDM**  -  **/DRIVER:WDM**

  Per altre informazioni, vedere [/DRIVER (Windows NT driver in modalità kernel).](/cpp/build/reference/driver-windows-nt-kernel-mode-driver)

- **EmbedManagedResourceFile**

  Parametro **String[]** facoltativo.

  Incorpora un file di risorse in un assembly. Specificare il nome file di risorse necessario. Facoltativamente, specificare il nome logico, che viene usato per caricare la risorsa, e l'opzione **PRIVATE**, che indica nel manifesto dell'assembly che il file di risorse è privato.

  Per altre informazioni, vedere [/ASSEMBLYRESOURCE (Incorpora una risorsa gestita).](/cpp/build/reference/assemblyresource-embed-a-managed-resource)

- **EnableCOMDATFolding**

  Parametro **booleano** facoltativo.

  Se `true`, abilita la riduzione dei dati COMDAT identici.

  Per altre informazioni, vedere l'argomento `ICF[= iterations]` di [/OPT (Ottimizzazioni)](/cpp/build/reference/opt-optimizations).

- **EnableUAC**

  Parametro **booleano** facoltativo.

  Se `true`, specifica che le informazioni di Controllo dell'account utente sono incorporate nel manifesto del programma.

  Per altre informazioni, vedere [/MANIFESTUAC (incorporazione delle informazioni di Controllo dell'account utente nel manifesto)](/cpp/build/reference/manifestuac-embeds-uac-information-in-manifest).

- **EntryPointSymbol**

  Parametro **String** facoltativo.

  Specifica una funzione del punto di ingresso come indirizzo iniziale per un file *EXE* o una DLL. Specificare un nome di funzione come valore del parametro.

  Per altre informazioni, vedere [/ENTRY (simbolo del punto di ingresso).](/cpp/build/reference/entry-entry-point-symbol)

- **FixedBaseAddress**

  Parametro **booleano** facoltativo.

  Se `true`, crea un programma o una DLL caricabile solo nel relativo indirizzo di base preferito.

  Per altre informazioni, vedere [/FIXED (Indirizzo di base fisso).](/cpp/build/reference/fixed-fixed-base-address)

- **ForceFileOutput**

  Parametro **String** facoltativo.

  Indica al linker di creare un file *EXE* o una DLL valida anche se viene fatto riferimento a un simbolo che non è definito oppure è definito più volte.

  Specificare uno dei valori seguenti, ognuno dei quali corrisponde a un'opzione della riga di comando.

  - **Abilitato**  -  **/FORCE**

  - **MultiplyDefinedSymbolOnly**  -  **/FORCE:MULTIPLE**

  - **UndefinedSymbolOnly**  -  **/FORCE:UNRESOLVED**

  Per altre informazioni, vedere [/FORCE (forza l'output del file)](/cpp/build/reference/force-force-file-output).

- **ForceSymbolReferences**

  Parametro **String[]** facoltativo.

  Questo parametro indica al linker di aggiungere un simbolo specificato alla tabella dei simboli.

  Per altre informazioni, vedere [/INCLUDE (forza riferimenti al simbolo)](/cpp/build/reference/include-force-symbol-references).

- **FunctionOrder**

  Parametro **String** facoltativo.

  Questo parametro ottimizza il programma inserendo le funzioni incluse nel pacchetto specificate (COMDATs) nell'immagine secondo un ordine predeterminato.

  Per altre informazioni, vedere [/ORDER (Inserisci funzioni nell'ordine).](/cpp/build/reference/order-put-functions-in-order)

- **GenerateDebugInformation**

  Parametro **booleano** facoltativo.

  Se `true`, crea informazioni di debug per il file *EXE* o per la DLL.

  Per altre informazioni, vedere [/DEBUG (Genera informazioni di debug).](/cpp/build/reference/debug-generate-debug-info)

- **GenerateManifest**

  Parametro **booleano** facoltativo.

  Se `true`, crea un file manifesto side-by-side.

  Per altre informazioni, vedere [/MANIFEST (crea manifesto dell'assembly syde-by-side)](/cpp/build/reference/manifest-create-side-by-side-assembly-manifest).

- **GenerateMapFile**

  Parametro **booleano** facoltativo.

  Se `true`, crea un *file di mappa*. L'estensione del nome file del file di mapping è *map.*

  Per altre informazioni, vedere [/MAP (Genera file map).](/cpp/build/reference/map-generate-mapfile)

- **HeapCommitSize**

  Parametro **String** facoltativo.

  Specifica la quantità di memoria fisica nellheap da allocare alla volta.

  Per altre informazioni, vedere `commit` l'argomento in [/HEAP (Imposta dimensioni heap).](/cpp/build/reference/heap-set-heap-size) Vedere anche il parametro **HeapReserveSize**.

- **HeapReserveSize**

  Parametro **String** facoltativo.

  Specifica il totale di allocazione dell'heap nella memoria virtuale.

  Per altre informazioni, vedere `reserve` l'argomento in [/HEAP (Imposta dimensioni heap).](/cpp/build/reference/heap-set-heap-size) Vedere anche il parametro **HeapCommitSize** in questa tabella.

- **IgnoreAllDefaultLibraries**

  Parametro **booleano** facoltativo.

  Se `true`, indica al linker di rimuovere una o più librerie predefinite dall'elenco di librerie in cui effettua la ricerca quando risolve i riferimenti esterni.

  Per altre informazioni, vedere [/NODEFAULTLIB (ignora librerie)](/cpp/build/reference/nodefaultlib-ignore-libraries).

- **IgnoreEmbeddedIDL**

  Parametro **booleano** facoltativo.

  Se `true`, specifica che gli eventuali attributi IDL presenti nel codice sorgente non devono essere elaborati in un file con estensione *idl*.

  Per altre informazioni, vedere [/IGNOREIDL (non elabora gli attributi in MIDL)](/cpp/build/reference/ignoreidl-don-t-process-attributes-into-midl).

- **IgnoreImportLibrary**

  Parametro **booleano** facoltativo.

  Se `true`, specifica che la libreria di importazione generata da questa configurazione non deve essere importata nei progetti dipendenti.

  Questo parametro non corrisponde a un'opzione del linker.

- **IgnoreSpecificDefaultLibraries**

  Parametro **String[]** facoltativo.

  Specifica il nome di una o più librerie predefinite da ignorare. Separare più librerie usando il punto e virgola.

  Per altre informazioni, vedere [/NODEFAULTLIB (ignora librerie)](/cpp/build/reference/nodefaultlib-ignore-libraries).

- **ImageHasSafeExceptionHandlers**

  Parametro **booleano** facoltativo.

  Se `true`, il linker produce un'immagine solo se può produrre anche una tabella dei gestori di eccezioni sicuri dell'immagine.

  Per altre informazioni, vedere [/SAFESEH (l'immagine ha gestori di eccezioni sicuri).](/cpp/build/reference/safeseh-image-has-safe-exception-handlers)

- **ImportLibrary**

  Nome della libreria di importazione specificato dall'utente che sostituisce il nome predefinito della libreria.

  Per altre informazioni, vedere [/IMPLIB (Assegnare un nome alla libreria di importazione).](/cpp/build/reference/implib-name-import-library)

- **KeyContainer**

  Parametro **String** facoltativo.

  Contenitore che contiene la chiave per un assembly firmato.

  Per altre informazioni, vedere [/KEYCONTAINER (Specifica un contenitore di chiavi per firmare un assembly).](/cpp/build/reference/keycontainer-specify-a-key-container-to-sign-an-assembly) Vedere anche il parametro **KeyFile** in questa tabella.

- **Keyfile**

  Parametro **String** facoltativo.

  Specifica un file che contiene la chiave per un assembly firmato.

  Per altre informazioni, vedere [/KEYFILE (specifica la chiave o la coppia di chiavi per firmare un assembly).](/cpp/build/reference/keyfile-specify-key-or-key-pair-to-sign-an-assembly) Vedere anche il parametro **KeyContainer**.

- **LargeAddressAware**

  Parametro **booleano** facoltativo.

  Se `true`, l'applicazione può gestire indirizzi superiori a 2 gigabyte.

  Per altre informazioni, vedere [/LARGEADDRESSAWARE (gestione di indirizzi di grandi dimensioni)](/cpp/build/reference/largeaddressaware-handle-large-addresses).

- **LinkDLL**

  Parametro **booleano** facoltativo.

  Se `true`, compila una DLL come file di output principale.

  Per altre informazioni, vedere [/DLL (compilazione di una DLL)](/cpp/build/reference/dll-build-a-dll).

- **LinkErrorReporting**

  Parametro **String** facoltativo.

  Consente di inviare informazioni sugli errori interni del compilatore direttamente a Microsoft.

  Specificare uno dei valori seguenti, ognuno dei quali corrisponde a un'opzione della riga di comando.

  - **NoErrorReport**  -  **/ERRORREPORT:NONE**

  - **PromptImmediately**  -  **/ERRORREPORT:PROMPT**

  - **QueueForNextLogin** - **/ERRORREPORT:QUEUE**

  - **SendErrorReport** - **/ERRORREPORT:SEND**

  Per altre informazioni, vedere [/ERRORREPORT (segnala gli errori interni del linker)](/cpp/build/reference/errorreport-report-internal-linker-errors).

- **LinkIncremental**

  Parametro **booleano** facoltativo.

  Se `true`, abilita il collegamento incrementale.

  Per altre informazioni, vedere [/INCREMENTAL (collegamento incrementale)](/cpp/build/reference/incremental-link-incrementally).

- **LinkLibraryDependencies**

  Parametro **booleano** facoltativo.

  Se `true`, specifica che gli output della libreria dalle dipendenze del progetto vengono collegati automaticamente.

  Questo parametro non corrisponde a un'opzione del linker.

- **LinkStatus**

  Parametro **booleano** facoltativo.

  Se `true`, specifica che il linker deve visualizzare un indicatore di stato che mostra la percentuale di completamento del collegamento.

  Per altre informazioni, vedere `STATUS` l'argomento di [/LTCG (generazione di time code collegamento).](/cpp/build/reference/ltcg-link-time-code-generation)

- **LinkTimeCodeGeneration**

  Parametro **String** facoltativo.

  Specifica le opzioni per l'ottimizzazione PGO.

  Specificare uno dei valori seguenti, ognuno dei quali corrisponde a un'opzione della riga di comando.

  - **Predefinito** - *\<none>*

  - **UseLinkTimeCodeGeneration**  -  **/LTCG**

  - **PGInstrument**  -  **/LTCG:PGInstrument**

  - **PGOptimization**  -  **/LTCG:PGOptimize**

  - **PGUpdate**

    \- **/LTCG:PGUpdate**

  Per altre informazioni, vedere [/LTCG (generazione di codice in fase di collegamento)](/cpp/build/reference/ltcg-link-time-code-generation).

- **File Manifesto**

  Parametro **String** facoltativo.

  Sostituisce il nome file manifesto predefinito con il nome file specificato.

  Per altre informazioni, vedere [/MANIFESTFILE (Denota file manifesto).](/cpp/build/reference/manifestfile-name-manifest-file)

- **MapExports**

  Parametro **booleano** facoltativo.

  Se `true`, indica al linker di includere le funzioni esportate in un file di mappa.

  Per altre informazioni, vedere `EXPORTS` l'argomento di [/MAPINFO (Include information in mapfile)](/cpp/build/reference/mapinfo-include-information-in-mapfile).

- **MapFileName**

  Parametro **String** facoltativo.

  Sostituisce il nome file di mappa predefinito con il nome file specificato.

- **MergedIDLBaseFileName**

  Parametro **String** facoltativo.

  Specifica il nome file e l'estensione di file del file *IDL*.

  Per altre informazioni, vedere [/IDLOUT (assegnare un nome ai file di output MIDL).](/cpp/build/reference/idlout-name-midl-output-files)

- **MergeSections**

  Parametro **String** facoltativo.

  Combina le sezioni in un'immagine. Specificare `from-section=to-section`.

  Per altre informazioni, vedere [/MERGE (Combina sezioni).](/cpp/build/reference/merge-combine-sections)

- **MidlCommandFile**

  Parametro **String** facoltativo.

  Specificare il nome di un file che contiene opzioni della riga di comando MIDL.

  Per altre informazioni, vedere [/MIDL (Specifica le opzioni della riga](/cpp/build/reference/midl-specify-midl-command-line-options)di comando MIDL).

- **MinimumRequiredVersion**

  Parametro **String** facoltativo.

  Specifica la versione minima richiesta del sottosistema. Gli argomenti sono numeri decimali compresi tra 0 e 65535.

- **ModuleDefinitionFile**

  Parametro **String** facoltativo.

  Specifica il nome di un [file di definizione moduli](/cpp/build/reference/module-definition-dot-def-files).

  Per altre informazioni, vedere [/DEF (Specifica il file di definizione del modulo).](/cpp/build/reference/def-specify-module-definition-file)

- **MSDOSStubFileName**

  Parametro **String** facoltativo.

  Collega il programma stub MS-DOS specificato a un programma Win32.

  Per altre informazioni, vedere [/STUB (nome file stub MS-DOS).](/cpp/build/reference/stub-ms-dos-stub-file-name)

- **NoEntryPoint**

  Parametro **booleano** facoltativo.

  Se `true`, crea una DLL di sole risorse.

  Per altre informazioni, vedere [/NOENTRY (nessun punto di ingresso).](/cpp/build/reference/noentry-no-entry-point)

- **ObjectFiles**

  Parametro **String[]** implicito.

  Specifica i file oggetto collegati.

- **OptimizeReferences**

  Parametro **booleano** facoltativo.

  Se `true`, elimina funzioni e/o dati a cui non viene mai fatto riferimento.

  Per altre informazioni, vedere l'argomento `REF` in [/OPT (Ottimizzazioni)](/cpp/build/reference/opt-optimizations).

- **Outputfile**

  Parametro **String** facoltativo.

  Esegue l'override del nome e del percorso predefiniti del programma creato dal linker.

  Per altre informazioni, vedere [/OUT (Nome file di output)](/cpp/build/reference/out-output-file-name).

- **PerUserRedirection**

  Parametro **booleano** facoltativo.

  Se `true` e se l'opzione Registra output è abilitata, forza il reindirizzamento su **HKEY_CURRENT_USER** delle scritture del Registro di sistema in **HKEY_CLASSES_ROOT**.

- **PreprocessOutput**

  Parametro `ITaskItem[]` facoltativo.

  Definisce una matrice di elementi di output del preprocessore che può essere usata ed emessa dalle attività.

- **PreventDllBinding**

  Parametro **booleano** facoltativo.

  Se `true`, indica a *Bind.exe* che l'immagine collegata non deve essere associata.

  Per altre informazioni, vedere [/ALLOWBIND (Impedisci associazione DLL).](/cpp/build/reference/allowbind-prevent-dll-binding)

- **Profilo**

  Parametro **booleano** facoltativo.

  Se `true`, produce un file di output che può essere usato con il profiler di **strumenti per le prestazioni**.

  Per altre informazioni, vedere [/PROFILE (profiler strumenti di prestazioni)](/cpp/build/reference/profile-performance-tools-profiler).

- **ProfileGuidedDatabase**

  Parametro **String** facoltativo.

  Specifica il nome del file *con estensione pgd* che verrà usato per contenere informazioni sul programma in esecuzione

  Per altre informazioni, vedere [/PGD (specifica il database per le ottimizzazioni PGO)](/cpp/build/reference/pgd-specify-database-for-profile-guided-optimizations).

- **ProgramDatabaseFile**

  Parametro **String** facoltativo.

  Specifica un nome per il database di programma (PDB) creato dal linker.

  Per altre informazioni, vedere [/PDB (usa database di programma)](/cpp/build/reference/pdb-use-program-database).

- **RandomizedBaseAddress**

  Parametro **booleano** facoltativo.

  Se `true`, genera un'immagine eseguibile che può essere riassegnata in modo casuale in fase di caricamento usando la funzionalità *ASLR* (Address Space Layout Randomization) di Windows.

  Per altre informazioni, vedere [/DYNAMICBASE (uso della funzionalità ASLR)](/cpp/build/reference/dynamicbase-use-address-space-layout-randomization).

- **RegisterOutput**

  Parametro **booleano** facoltativo.

  Se `true`, registra l'output primario di questa compilazione.

- **SectionAlignment**

  Parametro **Integer** facoltativo.

  Specifica l'allineamento di ogni sezione nello spazio degli indirizzi lineare del programma. Il valore del parametro è un numero di unità di byte e una potenza di due.

  Per altre informazioni, vedere [/ALIGN (allineamento sezione)](/cpp/build/reference/align-section-alignment).

- **SetChecksum**

  Parametro **booleano** facoltativo.

  Se `true`, imposta il checksum nell'intestazione di un file *EXE*.

  Per altre informazioni, vedere [/RELEASE (Imposta il checksum)](/cpp/build/reference/release-set-the-checksum).

- **ShowProgress**

  Parametro **String** facoltativo.

  Specifica il livello di dettaglio dei report di stato per l'operazione di collegamento.

  Specificare uno dei valori seguenti, ognuno dei quali corrisponde a un'opzione della riga di comando.

  - **Notset** - *\<none>*

  - **LinkVerbose**  -  **/VERBOSE**

  - **LinkVerboseLib**  -  **/VERBOSE:Lib**

  - **LinkVerboseICF**  -  **/VERBOSE:ICF**

  - **LinkVerboseREF**  -  **/VERBOSE:REF**

  - **LinkVerboseSAFESEH**  -  **/VERBOSE:SAFESEH**

  - **LinkVerboseCLR**  -  **/VERBOSE:CLR**

  Per altre informazioni, vedere [/VERBOSE (stampa i messaggi sullo stato)](/cpp/build/reference/verbose-print-progress-messages).

- **recenti**

  Parametro `ITaskItem[]` obbligatorio.

  Definisce una matrice di elementi del file di origine MSBuild che può essere usata ed emessa dalle attività.

- **SpecifySectionAttributes**

  Parametro **String** facoltativo.

  Specifica gli attributi di una sezione. Esegue l'override degli attributi impostati quando è stato compilato il file *OBJ* per la sezione.

  Per altre informazioni, vedere [/SECTION (Specificare gli attributi della sezione).](/cpp/build/reference/section-specify-section-attributes)

- **StackCommitSize**

  Parametro **String** facoltativo.

  Specifica la quantità di memoria fisica in ogni allocazione quando viene allocata altra memoria.

  Per altre informazioni, vedere l'argomento `commit` di [/STACK (allocazioni stack)](/cpp/build/reference/stack-stack-allocations).

- **StackReserveSize**

  Parametro **String** facoltativo.

  Specifica la dimensione totale di allocazione dello stack nella memoria virtuale.

  Per altre informazioni, vedere l'argomento `reserve` di [/STACK (allocazioni stack)](/cpp/build/reference/stack-stack-allocations).

- **StripPrivateSymbols**

  Parametro **String** facoltativo.

  Crea un secondo file database di programma (PDB) che omette i simboli che non si vuole distribuire ai clienti. Specificare il nome del secondo file PDB.

  Per altre informazioni, vedere [/PDBSTRIPPED (Strip private symbols)](/cpp/build/reference/pdbstripped-strip-private-symbols).

- **Sottosistema**

  Parametro **String** facoltativo.

  Specifica l'ambiente per il file eseguibile.

  Specificare uno dei valori seguenti, ognuno dei quali corrisponde a un'opzione della riga di comando.

  - **Notset** - *\<none>*

  - **Console**  -  **/SUBSYSTEM:CONSOLE**

  - **Windows**  -  **/SUBSYSTEM:WINDOWS**

  - **Native** - **/SUBSYSTEM:NATIVE**

  - **Applicazione EFI**  -  **/SUBSYSTEM:EFI_APPLICATION**

  - **Driver del servizio di avvio**  -  EFI **/SUBSYSTEM:EFI_BOOT_SERVICE_DRIVER**

  - ROM EFI   -  **/SUBSYSTEM:EFI_ROM**

  - **Runtime EFI**  -  **/SUBSYSTEM:EFI_RUNTIME_DRIVER**

  - **WindowsCE**  -  **/SUBSYSTEM:WINDOWSCE**

  - **POSIX**  -  **/SUBSYSTEM:POSIX**

  Per altre informazioni, vedere [/SUBSYSTEM (Specifica il sottosistema)](/cpp/build/reference/subsystem-specify-subsystem).

- **SupportNobindOfDelayLoadedDLL**

  Parametro **booleano** facoltativo.

  Se `true`, indica al linker di non includere una tabella di indirizzi di importazione nell'immagine finale.

  Per altre informazioni, vedere `NOBIND` l'argomento [/DELAY (Delay load import settings)](/cpp/build/reference/delay-delay-load-import-settings).

- **SupportUnloadOfDelayLoadedDLL**

  Parametro **booleano** facoltativo.

  Se `true`, indica alla funzione dell'helper di caricamento ritardato di supportare lo scaricamento esplicito della DLL.

  Per altre informazioni, vedere `UNLOAD` l'argomento di [/DELAY (impostazioni di importazione a caricamento ritardato).](/cpp/build/reference/delay-delay-load-import-settings)

- **SuppressStartupBanner**

  Parametro **booleano** facoltativo.

  Se `true`, impedisce la visualizzazione del messaggio sul copyright e sul numero di versione all'avvio dell'attività.

  Per altre informazioni, vedere [/NOLOGO (non visualizza il messaggio di avvio) (Linker)](/cpp/build/reference/nologo-suppress-startup-banner-linker).

- **SwapRunFromCD**

  Parametro **booleano** facoltativo.

  Se `true`, indica al sistema operativo di copiare prima di tutto l'output del linker in un file di scambio per poi eseguire l'immagine da tale posizione.

  Per altre informazioni, vedere `CD` l'argomento di [/SWAPRUN (carica l'output del linker nel file di scambio).](/cpp/build/reference/swaprun-load-linker-output-to-swap-file) Vedere anche il parametro **SwapRunFromNET**.

- **SwapRunFromNET**

  Parametro **booleano** facoltativo.

  Se `true`, indica al sistema operativo di copiare prima di tutto l'output del linker in un file di scambio per poi eseguire l'immagine da tale posizione.

  Per altre informazioni, vedere `NET` l'argomento di [/SWAPRUN (carica l'output del linker nel file di scambio).](/cpp/build/reference/swaprun-load-linker-output-to-swap-file) Vedere anche il parametro **SwapRunFromCD** in questa tabella.

- **TargetMachine**

  Parametro **String** facoltativo.

  Specifica la piattaforma di destinazione per il programma o DLL.

  Specificare uno dei valori seguenti, ognuno dei quali corrisponde a un'opzione della riga di comando.

  - **Notset** - *\<none>*

  - **MachineARM**  -  **/MACHINE:ARM**

  - **MachineEBC** - **/MACHINE:EBC**

  - **MachineIA64** - **/MACHINE:IA64**

  - **MachineMIPS**  -  **/MACHINE:MIPS**

  - **MachineMIPS16**  -  **/MACHINE:MIPS16**

  - **MachineMIPSFPU**  -  **/MACHINE:MIPSFPU**

  - **MachineMIPSFPU16**  -  **/MACHINE:MIPSFPU16**

  - **MachineSH4**  -  **/MACHINE:SH4**

  - **MachineTHUMB**  -  **/MACHINE:THUMB**

  - **MachineX64**  -  **/MACHINE:X64**

  - **MachineX86**  -  **/MACHINE:X86**

  Per altre informazioni, vedere [/MACHINE (Specifica la piattaforma di destinazione).](/cpp/build/reference/machine-specify-target-platform)

- **TerminalServerAware**

  Parametro **booleano** facoltativo.

  Se `true`, imposta un flag nel campo IMAGE_OPTIONAL_HEADER DllCharacteristics nell'intestazione facoltativa dell'immagine del programma. Quando questo flag viene impostato, Terminal Server non apporta determinate modifiche all'applicazione.

  Per altre informazioni, vedere [/TSAWARE (Crea applicazione con supporto terminal server).](/cpp/build/reference/tsaware-create-terminal-server-aware-application)

- **TrackerLogDirectory**

  Parametro **String** facoltativo.

  Specifica la directory del log di Tracker.

- **TreatLinkerWarningAsErrors**

  Parametro **booleano** facoltativo.

  Se `true`, fa in modo che non venga generato alcun file di output se il linker genera un avviso.

  Per altre informazioni, vedere [/WX (considera gli avvisi del linker come errori)](/cpp/build/reference/wx-treat-linker-warnings-as-errors).

- **TurnOffAssemblyGeneration**

  Parametro **booleano** facoltativo.

  Se `true`, crea un'immagine per il file di output corrente senza un assembly .NET Framework.

  Per altre informazioni, vedere [/NOASSEMBLY (Crea un modulo MSIL).](/cpp/build/reference/noassembly-create-a-msil-module)

- **TypeLibraryFile**

  Parametro **String** facoltativo.

  Specifica il nome file e l'estensione del file *con estensione tlb.* Specificare un nome file o un percorso e un nome file.

  Per altre informazioni, vedere [/TLBOUT (assegna un nome al file TLB)](/cpp/build/reference/tlbout-name-dot-tlb-file).

- **TypeLibraryResourceID**

  Parametro **Integer** facoltativo.

  Designa un valore specificato dall'utente per una libreria dei tipi creata dal linker. Specificare un valore compreso tra 1 e 65535.

  Per altre informazioni, vedere [/TLBID (Specifica l'ID risorsa per TypeLib).](/cpp/build/reference/tlbid-specify-resource-id-for-typelib)

- **UACExecutionLevel**

  Parametro **String** facoltativo.

  Indica il livello di esecuzione richiesto per l'applicazione quando viene eseguita con Controllo dell'account utente.

  Specificare uno dei valori seguenti, ognuno dei quali corrisponde a un'opzione della riga di comando.

  - **AsInvoker** - `level='asInvoker'`

  - **HighestAvailable** - `level='highestAvailable'`

  - **Requireadministrator** - `level='requireAdministrator'`

  Per altre informazioni, vedere l'argomento `level` di [/MANIFESTUAC (incorporazione delle informazioni di Controllo dell'account utente nel manifesto)](/cpp/build/reference/manifestuac-embeds-uac-information-in-manifest).

- **UACUIAccess**

  Parametro **booleano** facoltativo.

  Se `true`, l'applicazione ignora i livelli di protezione dell'interfaccia utente e indirizza l'input verso finestre con un livello di autorizzazione superiore sul desktop; in caso contrario `false`.

  Per altre informazioni, vedere l'argomento `uiAccess` di [/MANIFESTUAC (incorporazione delle informazioni di Controllo dell'account utente nel manifesto)](/cpp/build/reference/manifestuac-embeds-uac-information-in-manifest).

- **UseLibraryDependencyInputs**

  Parametro **booleano** facoltativo.

  Se `true`, vengono usati gli input allo strumento Gestione librerie invece del file di libreria quando gli output di libreria delle dipendenze del progetto vengono collegati.

- **Version**

  Parametro **String** facoltativo.

  Inserire un numero di versione nell'intestazione del file *DLL* o *EXE*. Specificare "`major[.minor]`". Gli argomenti `major` e `minor` sono numeri decimali compresi tra 0 e 65535.

  Per altre informazioni, vedere [/VERSION (informazioni sulla versione).](/cpp/build/reference/version-version-information)

## <a name="see-also"></a>Vedi anche

- [Informazioni di riferimento sulle attività](../msbuild/msbuild-task-reference.md)
