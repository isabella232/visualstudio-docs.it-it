---
title: Attività Link | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
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
- MSBuild (Visual C++), Link task
- Link task (MSBuild (Visual C++))
ms.assetid: 0a61f168-3113-4fa7-83a3-d9142e2a33f8
caps.latest.revision: 16
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b0aaf4d5f6862e2b5ef40b88e8041aa9ccc5a317
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/05/2018
ms.locfileid: "47590775"
---
# <a name="link-task"></a>Attività Link
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [attività Link](https://docs.microsoft.com/visualstudio/msbuild/link-task).  
  
  
Esegue il wrapping dello strumento linker di Visual C++, link.exe. Lo strumento linker consente di collegare file in formato COFF (Common Object File Format ) e librerie per creare un file eseguibile (con estensione exe) o una libreria di collegamento dinamico (DLL). Per altre informazioni, vedere [Opzioni linker](http://msdn.microsoft.com/library/c1d51b8a-bd23-416d-81e4-900e02b2c129).  
  
## <a name="parameters"></a>Parametri  
 Nella tabella che segue vengono descritti i parametri dell'attività  **Link**. La maggior parte dei parametri di attività e alcuni set di parametri corrispondono a un'opzione della riga di comando.  
  
-   **AdditionalDependencies**  
  
     Parametro **String[]** facoltativo.  
  
     Specifica un elenco di file di input da aggiungere al comando.  
  
     Per altre informazioni, vedere [File di input LINK](http://msdn.microsoft.com/library/bb26fcc5-509a-4620-bc3e-b6c6e603a412).  
  
-   **AdditionalLibraryDirectories**  
  
     Parametro **String[]** facoltativo.  
  
     Esegue l'override del percorso delle librerie dell'ambiente. Specificare un nome di directory.  
  
     Per altre informazioni, vedere [/LIBPATH (Percorso LIB aggiuntivo)](http://msdn.microsoft.com/library/7240af0b-9a3d-4d53-8169-2a92cd6958ba).  
  
-   **AdditionalManifestDependencies**  
  
     Parametro **String[]** facoltativo.  
  
     Specifica gli attributi che verranno inseriti nella sezione `dependency` del file manifesto.  
  
     Per altre informazioni, vedere [/MANIFESTDEPENDENCY (Specifica le dipendenze tra manifesti)](http://msdn.microsoft.com/library/e4b68313-33a2-4c3e-908e-ac2b9f7d6a73). Vedere anche "Publisher Configuration Files" (File di configurazione del server di pubblicazione) sul sito Web [MSDN](http://go.microsoft.com/fwlink/?LinkId=737).  
  
-   **AdditionalOptions**  
  
     Parametro **String** facoltativo.  
  
     Un elenco di opzioni del linker come specificato nella riga di comando. Ad esempio, **"**_/opzione1 /opzione2 /opzione#_". Usare questo parametro per specificare le opzioni del linker che non sono rappresentate da altri parametri dell'attività **Link**.  
  
     Per altre informazioni, vedere [Opzioni linker](http://msdn.microsoft.com/library/c1d51b8a-bd23-416d-81e4-900e02b2c129).  
  
-   **AddModuleNamesToAssembly**  
  
     Parametro **String[]** facoltativo.  
  
     Aggiunge un riferimento del modulo a un assembly.  
  
     Per altre informazioni, vedere [/ASSEMBLYMODULE (Aggiunge un modulo MSIL all'assembly)](http://msdn.microsoft.com/library/67357da8-e4b6-49fd-932c-329a5777f143).  
  
-   **AllowIsolation**  
  
     Parametro **Boolean** facoltativo.  
  
     Se `true`, fa eseguire al sistema operativo ricerche e caricamenti del manifesto. Se `false`, indica che le DLL vengono caricate come se il manifesto non esistesse.  
  
     Per altre informazioni, vedere [/ALLOWISOLATION (Ricerca di manifesti)](http://msdn.microsoft.com/library/6d41851e-b3c1-4bdf-beaa-031773089d6f).  
  
-   **AssemblyDebug**  
  
     Parametro **Boolean** facoltativo.  
  
     Se `true`, crea l'attributo **DebuggableAttribute** con il rilevamento delle informazioni di debug e disabilita le ottimizzazioni JIT. Se `false`, crea l'attributo **DebuggableAttribute**, ma disabilita il rilevamento delle informazioni di debug e abilita le ottimizzazioni JIT.  
  
     Per altre informazioni, vedere [/ASSEMBLYDEBUG (Aggiunge DebuggableAttribute)](http://msdn.microsoft.com/library/94443af3-470c-41d7-83a0-7434563d7982).  
  
-   **AssemblyLinkResource**  
  
     Parametro **String[]** facoltativo.  
  
     Crea un collegamento a una risorsa .NET Framework nel file di output. Il file di risorse non viene inserito nel file di output. Specificare il nome della risorsa.  
  
     Per altre informazioni, vedere [/ASSEMBLYLINKRESOURCE (Collegamento a risorse .NET Framework)](http://msdn.microsoft.com/library/8b6ad184-1b33-47a4-8513-4803cf915b64).  
  
-   **AttributeFileTracking**  
  
     Parametro **Boolean** implicito.  
  
     Abilita un rilevamento file più approfondito per acquisire il comportamento del collegamento incrementale. Restituisce sempre `true`.  
  
-   **BaseAddress**  
  
     Parametro **String** facoltativo.  
  
     Imposta un indirizzo di base per il programma o la DLL da compilare. Specificare `{address[,size] | @filename,key}`.  
  
     Per altre informazioni, vedere [/BASE (indirizzo di base)](http://msdn.microsoft.com/library/00b9f6fe-0bd2-4772-a69c-7365eb199069).  
  
-   **BuildingInIDE**  
  
     Parametro **Boolean** facoltativo.  
  
     Se true, indica che MSBuild viene richiamato dall'ambiente IDE. In caso contrario, indica che MSBuild viene richiamato dalla riga di comando.  
  
     Questo parametro non ha un'opzione del linker equivalente.  
  
-   **CLRImageType**  
  
     Parametro **String** facoltativo.  
  
     Imposta il tipo di un'immagine Common Language Runtime (CLR).  
  
     Specificare uno dei valori seguenti, ognuno dei quali corrisponde a un'opzione del linker.  
  
    -   **Default** - *\<none>*  
  
    -   **ForceIJWImage** - **/CLRIMAGETYPE:IJW**  
  
    -   **ForcePureILImage** - **/CLRIMAGETYPE:PURE**  
  
    -   **ForceSafeILImage** - **/CLRIMAGETYPE:SAFE**  
  
     Per altre informazioni, vedere [/CLRIMAGETYPE (Specifica il tipo di immagine CLR)](http://msdn.microsoft.com/library/04c60ee6-9dd7-4391-bc03-6926ad0fa116).  
  
-   **CLRSupportLastError**  
  
     Parametro **String** facoltativo.  
  
     Conserva l'ultimo codice di errore delle funzioni chiamate con il meccanismo P/Invoke.  
  
     Specificare uno dei valori seguenti, ognuno dei quali corrisponde a un'opzione del linker.  
  
    -   **Enabled** - **/CLRSupportLastError**  
  
    -   **Disabled** - **/CLRSupportLastError:NO**  
  
    -   **SystemDlls** - **/CLRSupportLastError:SYSTEMDLL**  
  
     Per altre informazioni, vedere [/CLRSUPPORTLASTERROR (Mantiene l'ultimo codice di errore per le chiamate PInvoke)](http://msdn.microsoft.com/library/b7057990-4154-4b1d-9fc9-6236f7be7575).  
  
-   **CLRThreadAttribute**  
  
     Parametro **String** facoltativo.  
  
     Specifica in modo esplicito l'attributo threading per il punto di ingresso del programma CLR.  
  
     Specificare uno dei valori seguenti, ognuno dei quali corrisponde a un'opzione del linker.  
  
    -   **DefaultThreadingAttribute** - **/CLRTHREADATTRIBUTE:NONE**  
  
    -   **MTAThreadingAttribute** - **/CLRTHREADATTRIBUTE:MTA**  
  
    -   **STAThreadingAttribute** - **/CLRTHREADATTRIBUTE:STA**  
  
     Per altre informazioni, vedere [/CLRTHREADATTRIBUTE (Imposta l'attributo thread CLR)](http://msdn.microsoft.com/library/4907e9ef-5031-446c-aecf-0a0b32fae1e8).  
  
-   **CLRUnmanagedCodeCheck**  
  
     Parametro **Boolean** facoltativo.  
  
     Specifica se verrà applicato **SuppressUnmanagedCodeSecurityAttribute** alle chiamate P/Invoke generate dal linker effettuate dal codice gestito in DLL native.  
  
     Per altre informazioni, vedere [/CLRUNMANAGEDCODECHECK (Aggiunge SupressUnmanagedCodeSecurityAttribute)](http://msdn.microsoft.com/library/73abc426-dab0-45e2-be85-0f9a14206cc2).  
  
-   **CreateHotPatchableImage**  
  
     Parametro **String** facoltativo.  
  
     Prepara un'immagine per l'applicazione di una patch a caldo.  
  
     Specificare uno dei valori seguenti, che corrisponde a un'opzione del linker.  
  
    -   **Enabled** - **/FUNCTIONPADMIN**  
  
    -   **X86Image** - **/FUNCTIONPADMIN:5**  
  
    -   **X64Image** - **/FUNCTIONPADMIN:6**  
  
    -   **ItaniumImage** - **/FUNCTIONPADMIN:16**  
  
     Per altre informazioni, vedere [/FUNCTIONPADMIN (Crea immagine con funzionalità di patch a caldo)](http://msdn.microsoft.com/library/25b02c13-1add-4fbd-add9-fcb30eb2cae7).  
  
-   **DataExecutionPrevention**  
  
     Parametro **Boolean** facoltativo.  
  
     Se `true`, indica che è stato eseguito il test di un eseguibile per verificarne la compatibilità con la funzionalità Protezione esecuzione programmi di Windows.  
  
     Per altre informazioni, vedere [/NXCOMPAT (compatibile con Protezione esecuzione programmi)](http://msdn.microsoft.com/library/5858e7ff-24d3-4ac3-9046-af2c9e220d9b).  
  
-   **DelayLoadDLLs**  
  
     Parametro **String[]** facoltativo.  
  
     Questo parametro fa in modo che le DLL vengano *caricate in ritardo*. Specificare il nome di una DLL di cui ritardare il caricamento.  
  
     Per altre informazioni, vedere [/DELAYLOAD (Importazione a caricamento ritardato)](http://msdn.microsoft.com/library/39ea0f1e-5c01-450f-9c75-2d9761ff9b28).  
  
-   **DelaySign**  
  
     Parametro **Boolean** facoltativo.  
  
     Se `true`, firma parzialmente un assembly. Per impostazione predefinita, il valore è `false`.  
  
     Per altre informazioni, vedere [/DELAYSIGN (Firma parzialmente un assembly)](http://msdn.microsoft.com/library/15244d30-3ecb-492f-a408-ffe81f38de20).  
  
-   **Driver**  
  
     Parametro **String** facoltativo.  
  
     Specificare questo parametro per compilare un driver in modalità kernel Windows NT.  
  
     Specificare uno dei valori seguenti, ognuno dei quali corrisponde a un'opzione del linker.  
  
    -   **NotSet** - *\<nessuno>*  
  
    -   **Driver** - **/Driver**  
  
    -   **UpOnly** - **/DRIVER:UPONLY**  
  
    -   **WDM** - **/DRIVER:WDM**  
  
     Per altre informazioni, vedere [/DRIVER (Driver in modalità kernel di Windows NT)](http://msdn.microsoft.com/library/aeee8e28-5d97-40f5-ba16-9f370fe8a1b8).  
  
-   **EmbedManagedResourceFile**  
  
     Parametro **String[]** facoltativo.  
  
     Incorpora un file di risorse in un assembly. Specificare il nome file di risorse necessario. Facoltativamente, specificare il nome logico, che viene usato per caricare la risorsa, e l'opzione **PRIVATE**, che indica nel manifesto dell'assembly che il file di risorse è privato.  
  
     Per altre informazioni, vedere [/ASSEMBLYRESOURCE (Incorpora una risorsa gestita)](http://msdn.microsoft.com/library/0ce6e1fb-921b-4b1b-a59c-d35388d789f2).  
  
-   **EnableCOMDATFolding**  
  
     Parametro **Boolean** facoltativo.  
  
     Se `true`, abilita la riduzione dei dati COMDAT identici.  
  
     Per altre informazioni, vedere l'argomento `ICF[= iterations]` di [/OPT (Ottimizzazioni)](http://msdn.microsoft.com/library/8f229863-5f53-48a8-9478-243a647093ac).  
  
-   **EnableUAC**  
  
     Parametro **Boolean** facoltativo.  
  
     Se `true`, specifica che le informazioni di Controllo dell'account utente sono incorporate nel manifesto del programma.  
  
     Per altre informazioni, vedere [/MANIFESTUAC (incorporazione delle informazioni di Controllo dell'account utente nel manifesto)](http://msdn.microsoft.com/library/2d243c39-fa13-493c-b56f-d0d972a1603a).  
  
-   **EntryPointSymbol**  
  
     Parametro **String** facoltativo.  
  
     Specifica una funzione del punto di ingresso come indirizzo iniziale per un file EXE o una DLL. Specificare un nome di funzione come valore del parametro.  
  
     Per altre informazioni, vedere [/ENTRY (Simbolo del punto di ingresso)](http://msdn.microsoft.com/library/26c62ba2-4f52-4882-a7bd-7046a0abf445).  
  
-   **FixedBaseAddress**  
  
     Parametro **Boolean** facoltativo.  
  
     Se `true`, crea un programma o una DLL caricabile solo nel relativo indirizzo di base preferito.  
  
     Per altre informazioni, vedere [/FIXED (Indirizzo di base fisso)](http://msdn.microsoft.com/library/929bba5e-b7d8-40ed-943e-056aa3710fc5).  
  
-   **ForceFileOutput**  
  
     Parametro **String** facoltativo.  
  
     Indica al linker di creare un file EXE o una DLL valida anche se viene fatto riferimento a un simbolo che non è definito oppure è definito più volte.  
  
     Specificare uno dei valori seguenti, ognuno dei quali corrisponde a un'opzione della riga di comando.  
  
    -   **Enabled** - **/FORCE**  
  
    -   **MultiplyDefinedSymbolOnly** - **/FORCE:MULTIPLE**  
  
    -   **UndefinedSymbolOnly** - **/FORCE:UNRESOLVED**  
  
     Per altre informazioni, vedere [/FORCE (Forza l'output del file)](http://msdn.microsoft.com/library/b1e9a218-a5eb-4e60-a4a4-65b4be15e5da).  
  
-   **ForceSymbolReferences**  
  
     Parametro **String[]** facoltativo.  
  
     Questo parametro indica al linker di aggiungere un simbolo specificato alla tabella dei simboli.  
  
     Per altre informazioni, vedere [/INCLUDE (Forza riferimenti al simbolo)](http://msdn.microsoft.com/library/4a039677-360a-480f-bd0b-448e239b449c).  
  
-   **FunctionOrder**  
  
     Parametro **String** facoltativo.  
  
     Questo parametro ottimizza il programma inserendo le funzioni incluse nel pacchetto specificate (COMDATs) nell'immagine secondo un ordine predeterminato.  
  
     Per altre informazioni, vedere [/ORDER (Inserisce le funzioni in ordine)](http://msdn.microsoft.com/library/ecf5eb3e-e404-4e86-9a91-4e5ec157261a).  
  
-   **GenerateDebugInformation**  
  
     Parametro **Boolean** facoltativo.  
  
     Se `true`, crea informazioni di debug per il file EXE o per la DLL.  
  
     Per altre informazioni, vedere [/DEBUG (Genera informazioni di debug)](http://msdn.microsoft.com/library/1af389ae-3f8b-4d76-a087-1cdf861e9103).  
  
-   **GenerateManifest**  
  
     Parametro **Boolean** facoltativo.  
  
     Se `true`, crea un file manifesto side-by-side.  
  
     Per altre informazioni, vedere [/MANIFEST (Crea manifesto dell'assembly syde-by-side)](http://msdn.microsoft.com/library/98c52e1e-712c-4f49-b149-4d0a3501b600).  
  
-   **GenerateMapFile**  
  
     Parametro **Boolean** facoltativo.  
  
     Se `true`, crea un *file di mappa*. L'estensione di file di mappa è map.  
  
     Per altre informazioni, vedere [/MAP (Genera file Map)](http://msdn.microsoft.com/library/9ccce53d-4e36-43da-87b0-7603ddfdea63).  
  
-   **HeapCommitSize**  
  
     Parametro **String** facoltativo.  
  
     Specifica la quantità di memoria fisica nellheap da allocare alla volta.  
  
     Per altre informazioni, vedere l'argomento `commit` in [/HEAP (Imposta la dimensione dell'heap)](http://msdn.microsoft.com/library/a3f71927-7f1d-492c-9fdb-dfccb1a043da). Vedere anche il parametro **HeapReserveSize**.  
  
-   **HeapReserveSize**  
  
     Parametro **String** facoltativo.  
  
     Specifica il totale di allocazione dell'heap nella memoria virtuale.  
  
     Per altre informazioni, vedere l'argomento `reserve` in [/HEAP (Imposta la dimensione dell'heap)](http://msdn.microsoft.com/library/a3f71927-7f1d-492c-9fdb-dfccb1a043da). Vedere anche il parametro **HeapCommitSize** in questa tabella.  
  
-   **IgnoreAllDefaultLibraries**  
  
     Parametro **Boolean** facoltativo.  
  
     Se `true`, indica al linker di rimuovere una o più librerie predefinite dall'elenco di librerie in cui effettua la ricerca quando risolve i riferimenti esterni.  
  
     Per altre informazioni, vedere [/NODEFAULTLIB (ignorare le librerie)](http://msdn.microsoft.com/library/7270b673-6711-468e-97a7-c2925ac2be6e).  
  
-   **IgnoreEmbeddedIDL**  
  
     Parametro **Boolean** facoltativo.  
  
     Se `true`, specifica che gli eventuali attributi IDL presenti nel codice sorgente non devono essere elaborati in un file con estensione idl.  
  
     Per altre informazioni, vedere [/IGNOREIDL (Non elabora gli attributi in MIDL)](http://msdn.microsoft.com/library/29514098-6a1c-4317-af2f-1dc268972780).  
  
-   **IgnoreImportLibrary**  
  
     Parametro **Boolean** facoltativo.  
  
     Se `true`, specifica che la libreria di importazione generata da questa configurazione non deve essere importata nei progetti dipendenti.  
  
     Questo parametro non corrisponde a un'opzione del linker.  
  
-   **IgnoreSpecificDefaultLibraries**  
  
     Parametro **String[]** facoltativo.  
  
     Specifica il nome di una o più librerie predefinite da ignorare. Separare più librerie usando il punto e virgola.  
  
     Per altre informazioni, vedere [/NODEFAULTLIB (ignorare le librerie)](http://msdn.microsoft.com/library/7270b673-6711-468e-97a7-c2925ac2be6e).  
  
-   **ImageHasSafeExceptionHandlers**  
  
     Parametro **Boolean** facoltativo.  
  
     Se `true`, il linker produce un'immagine solo se può produrre anche una tabella dei gestori di eccezioni sicuri dell'immagine.  
  
     Per altre informazioni, vedere [/SAFESEH (L'immagine ha gestori delle eccezioni sicuri)](http://msdn.microsoft.com/library/7722ff99-b833-4c65-a855-aaca902ffcb7).  
  
-   **ImportLibrary**  
  
     Nome della libreria di importazione specificato dall'utente che sostituisce il nome predefinito della libreria.  
  
     Per altre informazioni, vedere [/IMPLIB (Assegna un nome alla libreria di importazione)](http://msdn.microsoft.com/library/fe8f71ab-7055-41b5-8ef8-2b97cfa4a432).  
  
-   **KeyContainer**  
  
     Parametro **String** facoltativo.  
  
     Contenitore che contiene la chiave per un assembly firmato.  
  
     Per altre informazioni, vedere [/KEYCONTAINER (Specifica un contenitore di chiavi per firmare un assembly)](http://msdn.microsoft.com/library/94882d12-b77a-49c7-96d0-18a31aee001e). Vedere anche il parametro **KeyFile** in questa tabella.  
  
-   **KeyFile**  
  
     Parametro **String** facoltativo.  
  
     Specifica un file che contiene la chiave per un assembly firmato.  
  
     Per altre informazioni, vedere [/KEYFILE (Specifica una chiave o una coppia di chiavi per firmare un assembly)](http://msdn.microsoft.com/library/9b71f8c0-541c-4fe5-a0c7-9364f42ecb06). Vedere anche il parametro **KeyContainer**.  
  
-   **LargeAddressAware**  
  
     Parametro **Boolean** facoltativo.  
  
     Se `true`, l'applicazione può gestire indirizzi superiori a 2 gigabyte.  
  
     Per altre informazioni, vedere [/LARGEADDRESSAWARE (Gestione di indirizzi di grandi dimensioni)](http://msdn.microsoft.com/library/a29756c8-e893-47a9-9750-1f0d25359385).  
  
-   **LinkDLL**  
  
     Parametro **Boolean** facoltativo.  
  
     Se `true`, compila una DLL come file di output principale.  
  
     Per altre informazioni, vedere [/DLL (compilazione di una DLL)](http://msdn.microsoft.com/library/c7685aec-31d0-490f-9503-fb5171a23609).  
  
-   **LinkErrorReporting**  
  
     Parametro **String** facoltativo.  
  
     Consente di inviare informazioni sugli errori interni del compilatore direttamente a Microsoft.  
  
     Specificare uno dei valori seguenti, ognuno dei quali corrisponde a un'opzione della riga di comando.  
  
    -   **NoErrorReport** - **/ERRORREPORT:NONE**  
  
    -   **PromptImmediately** - **/ERRORREPORT:PROMPT**  
  
    -   **QueueForNextLogin** - **/ERRORREPORT:QUEUE**  
  
    -   **SendErrorReport** - **/ERRORREPORT:SEND**  
  
     Per altre informazioni, vedere [/ERRORREPORT (Segnala gli errori interni del linker)](http://msdn.microsoft.com/library/f5fab595-a2f1-4eb0-ab5c-1c0fbd3d8c28).  
  
-   **LinkIncremental**  
  
     Parametro **Boolean** facoltativo.  
  
     Se `true`, abilita il collegamento incrementale.  
  
     Per altre informazioni, vedere [/INCREMENTAL (collegamento incrementale)](http://msdn.microsoft.com/library/135656ff-94fa-4ad4-a613-22e1a2a5d16b).  
  
-   **LinkLibraryDependencies**  
  
     Parametro **Boolean** facoltativo.  
  
     Se `true`, specifica che gli output della libreria dalle dipendenze del progetto vengono collegati automaticamente.  
  
     Questo parametro non corrisponde a un'opzione del linker.  
  
-   **LinkStatus**  
  
     Parametro **Boolean** facoltativo.  
  
     Se `true`, specifica che il linker deve visualizzare un indicatore di stato che mostra la percentuale di completamento del collegamento.  
  
     Per altre informazioni, vedere l'argomento `STATUS` di [/LTCG (Generazione di codice in fase di collegamento)](http://msdn.microsoft.com/library/788c6f52-fdb8-40c2-90af-4026ea2cf2e2).  
  
-   **LinkTimeCodeGeneration**  
  
     Parametro **String** facoltativo.  
  
     Specifica le opzioni per l'ottimizzazione PGO.  
  
     Specificare uno dei valori seguenti, ognuno dei quali corrisponde a un'opzione della riga di comando.  
  
    -   **Default** - *\<none>*  
  
    -   **UseLinkTimeCodeGeneration** - **/LTCG**  
  
    -   **PGInstrument** - **/LTCG:PGInstrument**  
  
    -   **PGOptimization** - **/LTCG:PGOptimize**  
  
    -   **PGUpdate**  
  
         \- **/LTCG:PGUpdate**  
  
     Per altre informazioni, vedere [/LTCG (Generazione di codice in fase di collegamento)](http://msdn.microsoft.com/library/788c6f52-fdb8-40c2-90af-4026ea2cf2e2).  
  
-   **ManifestFile**  
  
     Parametro **String** facoltativo.  
  
     Sostituisce il nome file manifesto predefinito con il nome file specificato.  
  
     Per altre informazioni, vedere [/MANIFESTFILE (Assegna un nome al file manifesto)](http://msdn.microsoft.com/library/befa5ab2-a9cf-4c9b-969a-e7b4a930f08d).  
  
-   **MapExports**  
  
     Parametro **Boolean** facoltativo.  
  
     Se `true`, indica al linker di includere le funzioni esportate in un file di mappa.  
  
     Per altre informazioni, vedere l'argomento `EXPORTS` di [/MAPINFO (Include informazioni in file MAP)](http://msdn.microsoft.com/library/533d2bce-f9b7-4fea-ae1c-0b4864c9d10b).  
  
-   **MapFileName**  
  
     Parametro **String** facoltativo.  
  
     Sostituisce il nome file di mappa predefinito con il nome file specificato.  
  
-   **MergedIDLBaseFileName**  
  
     Parametro **String** facoltativo.  
  
     Specifica il nome file e l'estensione di file del file IDL.  
  
     Per altre informazioni, vedere [/IDLOUT (Assegna un nome ai file di output MIDL)](http://msdn.microsoft.com/library/10d00a6a-85b4-4de1-8732-e422c6931509).  
  
-   **MergeSections**  
  
     Parametro **String** facoltativo.  
  
     Combina le sezioni in un'immagine. Specificare `from-section=to-section`.  
  
     Per altre informazioni, vedere [/MERGE (Combina sezioni)](http://msdn.microsoft.com/library/10fb20c2-0b3f-4c8d-98a8-f69aedf03d52).  
  
-   **MidlCommandFile**  
  
     Parametro **String** facoltativo.  
  
     Specificare il nome di un file che contiene opzioni della riga di comando MIDL.  
  
     Per altre informazioni, vedere [/MIDL (Specifica opzioni della riga di comando MIDL)](http://msdn.microsoft.com/library/22dc259e-b34c-4ed3-a380-4beb734482c1).  
  
-   **MinimumRequiredVersion**  
  
     Parametro **String** facoltativo.  
  
     Specifica la versione minima richiesta del sottosistema. Gli argomenti sono numeri decimali compresi tra 0 e 65535.  
  
-   **ModuleDefinitionFile**  
  
     Parametro **String** facoltativo.  
  
     Specifica il nome di un [file di definizione moduli](http://msdn.microsoft.com/library/08c0bc28-c5d2-47aa-9624-7fc68bcaa4d8).  
  
     Per altre informazioni, vedere [/DEF (Specifica il file di definizione moduli)](http://msdn.microsoft.com/library/6497fa68-65f0-48ca-8f66-b87166fc631a).  
  
-   **MSDOSStubFileName**  
  
     Parametro **String** facoltativo.  
  
     Collega il programma stub MS-DOS specificato a un programma Win32.  
  
     Per altre informazioni, vedere [STUB (nome file stub MS-DOS)](http://msdn.microsoft.com/library/65221ffe-4f9a-4a14-ac69-3cfb79b40b5f).  
  
-   **NoEntryPoint**  
  
     Parametro **Boolean** facoltativo.  
  
     Se `true`, crea una DLL di sole risorse.  
  
     Per altre informazioni, vedere [/NOENTRY (nessun punto di ingresso)](http://msdn.microsoft.com/library/0214dd41-35ad-43ab-b892-e636e038621a).  
  
-   **ObjectFiles**  
  
     Parametro **String[]** implicito.  
  
     Specifica i file oggetto collegati.  
  
-   **OptimizeReferences**  
  
     Parametro **Boolean** facoltativo.  
  
     Se `true`, elimina funzioni e/o dati a cui non viene mai fatto riferimento.  
  
     Per altre informazioni, vedere l'argomento `REF` in [/OPT (Ottimizzazioni)](http://msdn.microsoft.com/library/8f229863-5f53-48a8-9478-243a647093ac).  
  
-   **OutputFile**  
  
     Parametro **String** facoltativo.  
  
     Esegue l'override del nome e del percorso predefiniti del programma creato dal linker.  
  
     Per altre informazioni, vedere [/OUT (nome file di output)](http://msdn.microsoft.com/library/976210a4-e51f-4cfb-af5e-c16344455834).  
  
-   **PerUserRedirection**  
  
     Parametro **Boolean** facoltativo.  
  
     Se `true` e se l'opzione Registra output è abilitata, forza il reindirizzamento su **HKEY_CURRENT_USER** delle scritture del Registro di sistema in **HKEY_CLASSES_ROOT**.  
  
-   **PreprocessOutput**  
  
     Parametro `ITaskItem[]` facoltativo.  
  
     Definisce una matrice di elementi di output del preprocessore che può essere usata ed emessa dalle attività.  
  
-   **PreventDllBinding**  
  
     Parametro **Boolean** facoltativo.  
  
     Se `true`, indica a Bind.exe che l'immagine collegata non deve essere associata.  
  
     Per altre informazioni, vedere [/ALLOWBIND (prevenzione dell'associazione di DLL)](http://msdn.microsoft.com/library/30e37e24-12e4-407e-988a-39d357403598).  
  
-   **Profile**  
  
     Parametro **Boolean** facoltativo.  
  
     Se `true`, produce un file di output che può essere usato con il profiler di **strumenti per le prestazioni**.  
  
     Per altre informazioni, vedere [/PROFILE (Profiler strumenti per le prestazioni)](http://msdn.microsoft.com/library/e676baa1-5063-47a3-a357-ba0d1f0d1699).  
  
-   **ProfileGuidedDatabase**  
  
     Parametro **String** facoltativo.  
  
     Specifica il nome del file PGD che verrà usato per salvare le informazioni sul programma in esecuzione.  
  
     Per altre informazioni, vedere [/PGD (Specifica il database per le ottimizzazioni PGO)](http://msdn.microsoft.com/library/9f312498-493b-461f-886f-92652257e443).  
  
-   **ProgramDatabaseFile**  
  
     Parametro **String** facoltativo.  
  
     Specifica un nome per il database di programma (PDB) creato dal linker.  
  
     Per altre informazioni, vedere [/PDB (Usa database di programma)](http://msdn.microsoft.com/library/d23db0ce-10cb-427a-bc60-d6b2a852723d).  
  
-   **RandomizedBaseAddress**  
  
     Parametro **Boolean** facoltativo.  
  
     Se `true`, genera un'immagine eseguibile che può essere riassegnata in modo casuale in fase di caricamento usando la funzionalità *ASLR* (Address Space Layout Randomization) di Windows.  
  
     Per altre informazioni, vedere [/DYNAMICBASE (uso della funzionalità ASLR)](http://msdn.microsoft.com/library/6c0ced8e-fe9c-4b63-b956-eb8a55fbceb2).  
  
-   **RegisterOutput**  
  
     Parametro **Boolean** facoltativo.  
  
     Se `true`, registra l'output primario di questa compilazione.  
  
-   **SectionAlignment**  
  
     Parametro **Integer** facoltativo.  
  
     Specifica l'allineamento di ogni sezione nello spazio degli indirizzi lineare del programma. Il valore del parametro è un numero di unità di byte e una potenza di due.  
  
     Per altre informazioni, vedere [/ALIGN (Allineamento sezione)](http://msdn.microsoft.com/library/f2f8ac24-e90e-4bea-8205-f2960a3b1740).  
  
-   **SetChecksum**  
  
     Parametro **Boolean** facoltativo.  
  
     Se `true`, imposta il checksum nell'intestazione di un file EXE.  
  
     Per altre informazioni, vedere [/RELEASE (Imposta checksum)](http://msdn.microsoft.com/library/93bcadf4-29ac-4824-914b-6997e3751d22).  
  
-   **ShowProgress**  
  
     Parametro **String** facoltativo.  
  
     Specifica il livello di dettaglio dei report di stato per l'operazione di collegamento.  
  
     Specificare uno dei valori seguenti, ognuno dei quali corrisponde a un'opzione della riga di comando.  
  
    -   **NotSet** - *\<nessuno>*  
  
    -   **LinkVerbose** - **/VERBOSE**  
  
    -   **LinkVerboseLib** - **/VERBOSE:Lib**  
  
    -   **LinkVerboseICF** - **/VERBOSE:ICF**  
  
    -   **LinkVerboseREF** - **/VERBOSE:REF**  
  
    -   **LinkVerboseSAFESEH** - **/VERBOSE:SAFESEH**  
  
    -   **LinkVerboseCLR** - **/VERBOSE:CLR**  
  
     Per altre informazioni, vedere [/VERBOSE (stampa di messaggi sullo stato)](http://msdn.microsoft.com/library/9c347d98-4c37-4724-a39e-0983934693ab).  
  
-   **Sources**  
  
     Parametro `ITaskItem[]` obbligatorio.  
  
     Definisce una matrice di elementi del file di origine MSBuild che può essere usata ed emessa dalle attività.  
  
-   **SpecifySectionAttributes**  
  
     Parametro **String** facoltativo.  
  
     Specifica gli attributi di una sezione. Esegue l'override degli attributi impostati quando è stato compilato il file OBJ per la sezione.  
  
     Per altre informazioni, vedere [/SECTION (Specifica attributi di sezione)](http://msdn.microsoft.com/library/92b69d81-e421-462e-b46f-7d0dff9b9d16).  
  
-   **StackCommitSize**  
  
     Parametro **String** facoltativo.  
  
     Specifica la quantità di memoria fisica in ogni allocazione quando viene allocata altra memoria.  
  
     Per altre informazioni, vedere l'argomento `commit` di [/STACK (Allocazioni stack)](http://msdn.microsoft.com/library/73283660-e4bd-47cc-b5ca-04c5d739034c).  
  
-   **StackReserveSize**  
  
     Parametro **String** facoltativo.  
  
     Specifica la dimensione totale di allocazione dello stack nella memoria virtuale.  
  
     Per altre informazioni, vedere l'argomento `reserve` di [/STACK (Allocazioni stack)](http://msdn.microsoft.com/library/73283660-e4bd-47cc-b5ca-04c5d739034c).  
  
-   **StripPrivateSymbols**  
  
     Parametro **String** facoltativo.  
  
     Crea un secondo file database di programma (PDB) che omette i simboli che non si vuole distribuire ai clienti. Specificare il nome del secondo file PDB.  
  
     Per altre informazioni, vedere [/PDBSTRIPPED (Rimuove simboli privati)](http://msdn.microsoft.com/library/9b9e0070-6a13-4142-8180-19c003fbbd55).  
  
-   **SubSystem**  
  
     Parametro **String** facoltativo.  
  
     Specifica l'ambiente per il file eseguibile.  
  
     Specificare uno dei valori seguenti, ognuno dei quali corrisponde a un'opzione della riga di comando.  
  
    -   **NotSet** - *\<nessuno>*  
  
    -   **Console** - **/SUBSYSTEM:CONSOLE**  
  
    -   **Windows** - **/SUBSYSTEM:WINDOWS**  
  
    -   **Native** - **/SUBSYSTEM:NATIVE**  
  
    -   **EFI Application** - **/SUBSYSTEM:EFI_APPLICATION**  
  
    -   **EFI Boot Service Driver** - **/SUBSYSTEM:EFI_BOOT_SERVICE_DRIVER**  
  
    -   **EFI ROM** - **/SUBSYSTEM:EFI_ROM**  
  
    -   **EFI Runtime** - **/SUBSYSTEM:EFI_RUNTIME_DRIVER**  
  
    -   **WindowsCE** - **/SUBSYSTEM:WINDOWSCE**  
  
    -   **POSIX** - **/SUBSYSTEM:POSIX**  
  
     Per altre informazioni, vedere [/SUBSYSTEM (Specifica il sottosistema)](http://msdn.microsoft.com/library/d7b133cf-cf22-4da8-ab46-6552702c0b9b).  
  
-   **SupportNobindOfDelayLoadedDLL**  
  
     Parametro **Boolean** facoltativo.  
  
     Se `true`, indica al linker di non includere una tabella di indirizzi di importazione nell'immagine finale.  
  
     Per altre informazioni, vedere l'argomento `NOBIND` di [/DELAY (Impostazioni dell'importazione a caricamento ritardato)](http://msdn.microsoft.com/library/9334b332-cc58-4dae-b10f-a4c75972d50c).  
  
-   **SupportUnloadOfDelayLoadedDLL**  
  
     Parametro **Boolean** facoltativo.  
  
     Se `true`, indica alla funzione dell'helper di caricamento ritardato di supportare lo scaricamento esplicito della DLL.  
  
     Per altre informazioni, vedere l'argomento `UNLOAD` di [/DELAY (Impostazioni dell'importazione a caricamento ritardato)](http://msdn.microsoft.com/library/9334b332-cc58-4dae-b10f-a4c75972d50c).  
  
-   **SuppressStartupBanner**  
  
     Parametro **Boolean** facoltativo.  
  
     Se `true`, impedisce la visualizzazione del messaggio sul copyright e sul numero di versione all'avvio dell'attività.  
  
     Per altre informazioni, vedere [/NOLOGO (Non visualizza il messaggio di avvio) (Linker)](http://msdn.microsoft.com/library/3b20dddd-eca6-4545-a331-9f70bf720197).  
  
-   **SwapRunFromCD**  
  
     Parametro **Boolean** facoltativo.  
  
     Se `true`, indica al sistema operativo di copiare prima di tutto l'output del linker in un file di scambio per poi eseguire l'immagine da tale posizione.  
  
     Per altre informazioni, vedere l'argomento `CD` di [/SWAPRUN (caricamento dell'output del linker nel file di scambio)](http://msdn.microsoft.com/library/4a1e7f46-4399-4161-8dfc-d6a71beaf683). Vedere anche il parametro **SwapRunFromNET**.  
  
-   **SwapRunFromNET**  
  
     Parametro **Boolean** facoltativo.  
  
     Se `true`, indica al sistema operativo di copiare prima di tutto l'output del linker in un file di scambio per poi eseguire l'immagine da tale posizione.  
  
     Per altre informazioni, vedere l'argomento `NET` di [/SWAPRUN (caricamento dell'output del linker nel file di scambio)](http://msdn.microsoft.com/library/4a1e7f46-4399-4161-8dfc-d6a71beaf683). Vedere anche il parametro **SwapRunFromCD** in questa tabella.  
  
-   **TargetMachine**  
  
     Parametro **String** facoltativo.  
  
     Specifica la piattaforma di destinazione per il programma o DLL.  
  
     Specificare uno dei valori seguenti, ognuno dei quali corrisponde a un'opzione della riga di comando.  
  
    -   **NotSet** - *\<nessuno>*  
  
    -   **MachineARM** - **/MACHINE:ARM**  
  
    -   **MachineEBC** - **/MACHINE:EBC**  
  
    -   **MachineIA64** - **/MACHINE:IA64**  
  
    -   **MachineMIPS** - **/MACHINE:MIPS**  
  
    -   **MachineMIPS16** - **/MACHINE:MIPS16**  
  
    -   **MachineMIPSFPU** - **/MACHINE:MIPSFPU**  
  
    -   **MachineMIPSFPU16** - **/MACHINE:MIPSFPU16**  
  
    -   **MachineSH4** - **/MACHINE:SH4**  
  
    -   **MachineTHUMB** - **/MACHINE:THUMB**  
  
    -   **MachineX64** - **/MACHINE:X64**  
  
    -   **MachineX86** - **/MACHINE:X86**  
  
     Per altre informazioni, vedere [/MACHINE (Specifica la piattaforma di destinazione)](http://msdn.microsoft.com/library/8d41bf4b-7e53-4ab9-9085-d852b08d31c2).  
  
-   **TerminalServerAware**  
  
     Parametro **Boolean** facoltativo.  
  
     Se `true`, imposta un flag nel campo IMAGE_OPTIONAL_HEADER DllCharacteristics nell'intestazione facoltativa dell'immagine del programma. Quando questo flag viene impostato, Terminal Server non apporta determinate modifiche all'applicazione.  
  
     Per altre informazioni, vedere [/TSAWARE (Crea un'applicazione con supporto Terminal Server)](http://msdn.microsoft.com/library/fe1c1846-de5b-4839-b562-93fbfe36cd29).  
  
-   **TrackerLogDirectory**  
  
     Parametro **String** facoltativo.  
  
     Specifica la directory del log di Tracker.  
  
-   **TreatLinkerWarningAsErrors**  
  
     Parametro **Boolean** facoltativo.  
  
     Se `true`, fa in modo che non venga generato alcun file di output se il linker genera un avviso.  
  
     Per altre informazioni, vedere [/WX (Considera gli avvisi del linker come errori)](http://msdn.microsoft.com/library/e4ba97c7-93f7-43ae-a4bb-d866790926c9).  
  
-   **TurnOffAssemblyGeneration**  
  
     Parametro **Boolean** facoltativo.  
  
     Se `true`, crea un'immagine per il file di output corrente senza un assembly .NET Framework.  
  
     Per altre informazioni, vedere [/NOASSEMBLY (Crea un modulo MSIL)](http://msdn.microsoft.com/library/3cea4e70-f451-4395-a626-1930b1b127fe).  
  
-   **TypeLibraryFile**  
  
     Parametro **String** facoltativo.  
  
     Specifica il nome file e l'estensione di file del file TLB. Specificare un nome file o un percorso e un nome file.  
  
     Per altre informazioni, vedere [/TLBOUT (Assegna un nome al file TLB)](http://msdn.microsoft.com/library/0df6d078-2e48-46c9-a1a5-02674d85dce8).  
  
-   **TypeLibraryResourceID**  
  
     Parametro **Integer** facoltativo.  
  
     Designa un valore specificato dall'utente per una libreria dei tipi creata dal linker. Specificare un valore compreso tra 1 e 65535.  
  
     Per altre informazioni, vedere [/TLBID (Specifica l'ID di risorsa per una libreria dei tipi)](http://msdn.microsoft.com/library/434b28a2-4656-4d52-ac82-8b18bf486fb2).  
  
-   **UACExecutionLevel**  
  
     Parametro **String** facoltativo.  
  
     Indica il livello di esecuzione richiesto per l'applicazione quando viene eseguita con Controllo dell'account utente.  
  
     Specificare uno dei valori seguenti, ognuno dei quali corrisponde a un'opzione della riga di comando.  
  
    -   **AsInvoker** - `level='asInvoker'`  
  
    -   **HighestAvailable** - `level='highestAvailable'`  
  
    -   **RequireAdministrator** - `level='requireAdministrator'`  
  
     Per altre informazioni, vedere l'argomento `level` di [/MANIFESTUAC (incorporazione delle informazioni di Controllo dell'account utente nel manifesto)](http://msdn.microsoft.com/library/2d243c39-fa13-493c-b56f-d0d972a1603a).  
  
-   **UACUIAccess**  
  
     Parametro **Boolean** facoltativo.  
  
     Se `true`, l'applicazione ignora i livelli di protezione dell'interfaccia utente e indirizza l'input verso finestre con un livello di autorizzazione superiore sul desktop; in caso contrario `false`.  
  
     Per altre informazioni, vedere l'argomento `uiAccess` di [/MANIFESTUAC (incorporazione delle informazioni di Controllo dell'account utente nel manifesto)](http://msdn.microsoft.com/library/2d243c39-fa13-493c-b56f-d0d972a1603a).  
  
-   **UseLibraryDependencyInputs**  
  
     Parametro **Boolean** facoltativo.  
  
     Se `true`, vengono usati gli input allo strumento Gestione librerie invece del file di libreria quando gli output di libreria delle dipendenze del progetto vengono collegati.  
  
-   **Version**  
  
     Parametro **String** facoltativo.  
  
     Inserire un numero di versione nell'intestazione del file DLL o EXE. Specificare "`major[.minor]`". Gli argomenti `major` e `minor` sono numeri decimali compresi tra 0 e 65535.  
  
     Per altre informazioni, vedere [/VERSION (Informazioni sulla versione)](http://msdn.microsoft.com/library/b86d0e86-dca6-4316-aee2-d863ccb9f223).  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimenti alle attività](../msbuild/msbuild-task-reference.md)



